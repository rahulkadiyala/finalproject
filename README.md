Video: https://temple.zoom.us/rec/play/8Cmd7B8ZyvCHEUKsIIayjB522BMbSCUBvVMvmnXBi2cw7IwiLtSqx8wwOUKtL1WWx4HVDXSrqTxQ0AwI.iWDjIJ3pRdsofe2V?continueMode=true

#Wacky Pong
#My name Rahul Kadiyala and this is my final project for CIS 1051, 2022
import random
import turtle

#Background
window = turtle.Screen()
window.title("Wacky Pong")
window.bgcolor("black")
window.setup(width = 800, height = 600)
window.tracer(0)

#Score
scoreA = 0
scoreB = 0

#Paddle 1
paddle1 = turtle.Turtle()
paddle1.speed(0)
paddle1.shape("square")
paddle1.color("white")
paddle1.shapesize(stretch_wid=5, stretch_len = 1)
paddle1.penup()
paddle1.goto(-350,0)


#Paddle 2
paddle2 = turtle.Turtle()
paddle2.speed(0)
paddle2.shape("square")
paddle2.color("white")
paddle2.shapesize(stretch_wid=5, stretch_len = 1)
paddle2.penup()
paddle2.goto(350,0)


#Ball
ball = turtle.Turtle()
ball.speed(0)
ball.shape("circle")
ball.color("white")
ball.penup()
ball.goto(0,0)
ball.dx = 2
ball.dy = -2


#Pen
pen = turtle.Turtle()
pen.speed(0)
pen.color("white")
pen.penup()
pen.hideturtle()
pen.goto(0, 260)
pen.write("Player A: 0   Player B: 0", align="center", font=("Courier", 24, "normal"))

#Controls for paddles
def paddle1up():
    y = paddle1.ycor()
    y += 20
    paddle1.sety(y)

def paddle1down():
    y = paddle1.ycor()
    y -= 20
    paddle1.sety(y)

def paddle2up():
    y = paddle2.ycor()
    y += 20
    paddle2.sety(y)

def paddle2down():
    y = paddle2.ycor()
    y -= 20
    paddle2.sety(y)


#Keyboard input
window.listen()
window.onkeypress(paddle1up, "w")
window.onkeypress(paddle1down, "s")
window.onkeypress(paddle2up, "Up")
window.onkeypress(paddle2down, "Down")



#Main
while True:
    window.update()

    # Makes Ball Move
    ball.setx(ball.xcor() + ball.dx)
    ball.sety(ball.ycor() + ball.dy)

    #Border
    if ball.ycor() > 290:
        ball.sety(290)
        ball.dy *= -1

    if ball.ycor() < -290:
        ball.sety(-290)
        ball.dy *= -1
    
    #Changes score
    if ball.xcor() > 390:
        ball.goto(0,0)
        ball.dx *= -1
        scoreA += 1
        pen.clear()
        pen.write("Player A: {}   Player B: {}".format(scoreA, scoreB), align="center", font=("Courier", 24, "normal"))
    
    if ball.xcor() < -390:
        ball.goto(0,0)
        ball.dx *= -1
        scoreB += 1
        pen.clear()
        pen.write("Player A: {}   Player B: {}".format(scoreA, scoreB), align="center", font=("Courier", 24, "normal"))

    #Making the Ball bounce off paddle
    
    if (ball.xcor() > 340 and ball.xcor() < 350) and (ball.ycor() < paddle2.ycor() + 40 and ball.ycor() > paddle2.ycor() - 40):
        ball.setx(340)
        ball.dx *= -1
        ball.shapesize(random.randint(1, 7))
        paddle2.shapesize(stretch_wid=random.randint(1, 5), stretch_len = random.randint(1, 5))

    if (ball.xcor() < -340 and ball.xcor() > -350) and (ball.ycor() < paddle1.ycor() + 40 and ball.ycor() > paddle1.ycor() - 40):
        ball.setx(-340)
        ball.dx *= -1
        ball.shapesize(random.randint(1, 7))
        paddle1.shapesize(stretch_wid=random.randint(1, 5), stretch_len = random.randint(1, 5))
    
    

    
        
        

        
    
    

