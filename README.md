# Snakes-and-Ladders
<!-- Let's play Snakes and Ladders -->
from PIL import Image
import random
end=100
def show_board():
	img=Image.open('images\snakeladder.png')
	img.show()
def check_ladder(points):
	if points==1:
		print("Ladder")
		return 38
	elif points==4:
		print("Ladder")
		return 14
	elif points==8:
		print("Ladder")
		return 30
	elif points==21:
		print("Ladder")
		return 42
	elif points==28:
		print("Ladder")
		return 76
	elif points==50:
		print("Ladder")
		return 67
	elif points==71:
		print("Ladder")
		return 92
	elif points==88:
		print("Ladder")
		return 99
	else:
		return points
def check_snake(points):
	if points==32:
		print("Snake")
		return 10
	elif points==36:
		print("Snake")
		return 6
	elif points==48:
		print("Snake")
		return 26
	elif points==62:
		print("Snake")
		return 18
	elif points==88:
		print("Snake")
		return 24
	elif points==95:
		print("Snake")
		return 56
	elif points==97:
		print("Snake")
		return 78
	else :
		return points
def reached_end(points):
	if points==end:
		return True
	else:
		return False

def play():
	#input player 1 name
	p1_name=input("player 1, enter your name: ")
	#input player 2 name
	p2_name=input("player 2, enter your name: ")
	#inital points of player 1
	pp1=0
	#inital points of player 2
	pp2=0
	turn=0
	while(1):
	
		if turn%2 ==0:
			turn=turn+1
			#player 1 turn
			print(p1_name," your turn") 
			#ask player choice to continue
			c=input("press 1 to continue and press 0 to quite: ")
			if c==0:
				print(p1_name, " scored",pp1)
				print(p2_name, " scored",pp2)
				print("quiting the game, Thanks for playing") 
				break
			#generate a random no from 1,2,3,4,5,6
			dice= random.randint(1,6)
			print("dice showed: ",dice)
			#add points
			pp1=pp1+dice
			pp1=check_ladder(pp1)
			pp1=check_snake(pp1)
			#check if player goes beyond the board
			if pp1 >end:
				pp1=end
			print(p1_name, "your score",pp1)
			if reached_end(pp1):
				print(p1_name,"[[[WON]]]")
				break
		else:
			turn=turn+1
			#player 2  turn
			print(p2_name," your turn") 
			#ask player choice to continue
			c=input("press 1 to continue and press 0 to quite: ")
			if c==0:
				print(p1_name, " scored",pp1)
				print(p2_name, " scored",pp2)
				print("quiting the game, Thanks for playing") 
				break
			#generate a random no from 1,2,3,4,5,6
			dice= random.randint(1,6)
			print("dice showed: ",dice)
			#add points
			pp2=pp2+dice
			pp2=check_ladder(pp2)
			pp2=check_snake(pp2)
			#check if player goes beyond the board
			if pp2 >end:
				pp2=end
			print(p2_name, "your score",pp2)
			if reached_end(pp2):
				print(p2_name,"[[[WON]]]")
				break
	
show_board()
play()
