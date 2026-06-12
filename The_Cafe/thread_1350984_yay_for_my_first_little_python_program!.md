---
title: "yay for my first little python program!"
date: 2009-12-09
forum: The Cafe
---

### Post by earthpigg on 2009-12-09
so, im 50 pages into "[Python 3 for Absolute Beginners]("http://www.amazon.com/Python-Absolute-Beginners-Experts-Source/dp/1430216328/ref=sr_1_1?ie=UTF8&s=books&qid=1260414358&sr=8-1")" and it felt like i had read enough to construct my own happy little program from scratch.

i felt this because i knew how to take input from the user, manipulate it, give output, and the author had just started describing how to use basic logic statements like "if -this- then -do this-".

after about 2 hours of work, it turns out i was correct! :D

it tells you how much paint you will need to purchase to paint a given rectangular room.... i have no idea if my assumptions about paint use per square foot are correct, i got them from google.

below is the source, attached is the same. to run it:

```
python3 /path/to/howmuchpaint.py
```

if you want to "install" it, simply rename it from howmuchpaint.py to howmuchpaint, move the file to /usr/bin or /usr/share/bin (may have to "sudo nautilus" to be able to do that), right click on it and give it the "executable" permission for all users, and hit "ok".

now you can just enter this command from the terminal to run it:

```
howmuchpaint
```

i haven't gone to the trouble to correct the user in every possible given case of illogical inputs. for example: if you tell it you have a room "potato" feet long, it will simply drop back to the terminal with an obscure error message instead of helpfully notifying you that "potato" is not a number.

i haven't quite got my head around when i do and do not need to specify that something is an int() or float() [as opposed to a str()]. in the book, the author does not do it all the time in his examples... but i ended up getting so many syntax errors that i just used one or the other pretty much every time.

code:
```
#! /usr/bin/python3

"""
howmuchpaint.py
Problem: Find out how much paint user will need to paint a certain room.
Target Users: Me, anyone
Target System: GNU/Linux
Interface: CLI
Maintainer: earthpigg
License: Public Domain
"""

__version__ = 0.1


# description of program
print("\n\nhowmuchpaint \nBy earthpigg \nVersion 0.1\n\nThis program is designed to help you determine how much paint to purchase in order to paint all four walls and perhaps the ceiling of a given room with a given type of paint.")


# want to think 'per can' or 'per gallon'?
print("\n\nHow would you like to think about your paint purchases? \n1. Per Gallon (good if you intend to purchase in bulk)\nor \n2. Per 5 Gallon Can (good if you intend to purchase several individual standard sized cans of paint)")
paintunit = input("\n1 or 2? ")
int(paintunit)

if int(paintunit) == 1 or int(paintunit) == 2:
    paintunitgood = True
else:
    paintunitgood = False

if int(paintunitgood) == False:
    print("\nError: you must select 1 or 2. Results will not be valid.")
else:
    if int(paintunit) == 2:
        paintunit = int(5)

# explain paint coverage
    # 300 square feet avg per gallon. 
    # cheap covers less
    # dark covers less
    # expensive covers more
    # light covers more

sqfeet = int(paintunit) * int(300)
int(sqfeet)

if int(paintunit) == 1:
    print("\n\nA decent guess is that", paintunit, "gallon of paint is sufficient for a single coat on", sqfeet, "square feet of wall.")
else:
    print("\n\nA decent guess is that", paintunit, "gallons of paint (one can) is sufficient for a single coat on", sqfeet, "square feet of wall.")

print("\n\nIf you purchase low quality paint,", paintunit, "gallon(s) will cover less than", sqfeet, "square feet.\nIf you purchase especially high quality paint,", paintunit, "gallon(s) will cover more than", sqfeet, "square feet.\n\nIf you purchase a darker color,", paintunit, "gallon(s) will cover less than", sqfeet, "square feet.\nIf you purchase a lighter color (such as white or off white),", paintunit, "gallon(s) will cover just about", sqfeet, "square feet.\n\nThere is no exact formula for this part. It requires a bit of human intuition and experience.")

sqrangelow = sqfeet // int(2)
sqrangehigh = sqfeet * 1.5

print("\n\nDepending on all of the above", paintunit, "gallon(s) can be expected to cover anywhere from", sqrangelow, "square feet to", int(sqrangehigh), "square feet.\n\nIf you aren't sure which figure to use, but you are painting the room a light color such as white or yellow with normal quality paint, then", sqfeet, "will work for us.")

# ask how much sq feet per bucket/gallon user wants to use
print("\nHow many square feet do you think", paintunit, "gallon(s) of your chosen paint will cover? ")
sqfeet = input()
sqfeet = int(sqfeet) / int(paintunit)

# explain that only rectangular rooms are supported
print("\nGreat! Now, I need information about the exact dimensions of the room you wish to paint. Note that only rectangular shaped rooms are currently supported by this program. If you have an oddly shaped room, break your room down into smaller rectangles and run this program multiple times. Add the results together to determine how much paint you need to purchase..")

# get room dimensions
    # ask width
print("\nHow wide is the room, in feet?")
width = input()
int(width)
    # ask length
print("\nHow long is the room, in feet?")
length = input()
int(length)
    # ask hight 
print("\nHow tall is the room, in feet?")
height = input()
int(height)
    # ask if cealing will be painted
print("\nWill you be painting the cealing, too?\n1. Yes\n2. No")
ceiling = input("\n1 or 2? ")
int(ceiling)
if int(ceiling) == 1 or int(ceiling) == 2:
    ceilinggood = True
else:
    ceilinggood = False

if int(ceilinggood) == False:
    print("\nError: you must select 1 or 2. Results will not be valid.")
else:
    if int(ceiling) == 1:
        ceiling = True
    if int(ceiling) == 2:
        ceiling = False

numcoats = input("\nHow many coats of paint to do intend to do? ")

#announce that calcs starting...
print("\nOutstanding!\n\nI will now calculate how much paint you will need to purchase to paint", numcoats, "coats of paint on all four walls")
if ceiling == True:
    print(" and the ceiling")
print(" of a room", width, "feet by", length, "feet and", height, "feet tall.")

print("\nIf these figures are incorrect, the results will not be correct.")

# crunch numbers
side1 = int(width) * int(height) * int(2)
side2 = int(length) * int(height) * int(2)
side3 = int(0)
if ceiling == True:
    side3 = int(length) * int(width)

totalsqfoot = (int(side1) + int(side2) + int(side3)) * int(numcoats)

purchase = int(totalsqfoot) / int(sqfeet)


if int(paintunit) == int(1):
    print("\n\nYou need to purchase", purchase, "gallons of paint.")

if int(paintunit) == int(5):
    purchase = purchase / int(5)
    print("\n\nYou need to purchase", purchase, "buckets of paint.")

print("The decimal figure was left in so you can decide how much to purchase if you already have some paint laying around.")
```

---

### Post by chris200x9 on 2009-12-09
congrats! I don't get why python is  considered "easy", the code looks confusing :D

---

### Post by hoppipolla on 2009-12-09
I can't code either, but well done on learning so far and I wish you much luck and many great programming endeavours in the future ^_^

---

### Post by earthpigg on 2009-12-09
> **chris200x9 said:**
> congrats! I don't get why python is  considered "easy", the code looks confusing :D

i think that would be, at least partially, because i was able to do that after only 50 pages of reading. and the first 25 pages was super-novice stuff like "what is software?" and "what is source code?"... so, really, only 25 pages of reading.

let's see if i can make it 'human readable' as quickly as possible:

1. backslash followed by the letter n means newline. \n = start new line

2. any random word all by itself is a variable. in algebra, "X" and "Y" where common variables. in python, any word you like is a variable.

3. 'int' means 'intiger'... whole number, like 3 or 500. but not 1.2 or 500.1.

4. a single equal sign is me making the command: "make this equal to that"... two equal signs is asking the question: "is this equal to that?"

make a little more sense? :D

---

### Post by AllRadioisDead on 2009-12-09
Great little program! I've been wanting to get into coding but I just haven't gotten around to it. I salute you!

---

### Post by chris200x9 on 2009-12-09
> **earthpigg said:**
> i think that would be, at least partially, because i was able to do that after only 50 pages of reading. and the first 25 pages was super-novice stuff like "what is software?" and "what is source code?"... so, really, only 25 pages of reading.

let's see if i can make it 'human readable' as quickly as possible:

1. backslash followed by the letter n means newline. \n = start new line

2. any random word all by itself is a variable. in algebra, "X" and "Y" where common variables. in python, any word you like is a variable.

3. 'int' means 'intiger'... whole number, like 3 or 500. but not 1.2 or 500.1.

4. a single equal sign is me making the command: "make this equal to that"... two equal signs is asking the question: "is this equal to that?"

make a little more sense? :D

yea I know, I know a some c++. I just meant python looks confusing to me, I absolutley hate the syntax.

---

### Post by MaxIBoy on 2009-12-09
That's because you're looking at it through a little window in his forum post, and he's got massive huge lines. 

PROTIP: Style counts! Don't use \n to combine multiple lines of output into a single string. Use multiple print statements where appropriate, or leave the \n in but put them on separate lines of code. If you've got huge strings you should break it up a little. Also, whitespace is your best friend and you should add it wherever possible. Use tabs to line stuff up if you can. This code:
```
print("\n\nIf you purchase low quality paint,", paintunit, "gallon(s) will cover less than", sqfeet, "square feet.\nIf you purchase especially high quality paint,", paintunit, "gallon(s) will cover more than", sqfeet, "square feet.\n\nIf you purchase a darker color,", paintunit, "gallon(s) will cover less than", sqfeet, "square feet.\nIf you purchase a lighter color (such as white or off white),", paintunit, "gallon(s) will cover just about", sqfeet, "square feet.\n\nThere is no exact formula for this part. It requires a bit of human intuition and experience.")
```Could have been written like this: [http://pastebin.com/m63233afa](http://pastebin.com/m63233afa)
Or even better, like this, using tabs to line things up: [http://pastebin.com/m6b487a46](http://pastebin.com/m6b487a46)
This will help you code much faster, and it starts to matter a lot more for big projects. Personally, I think the first chapter of any self-respecting beginners programming guide should be devoted to code style.



Python is a great language, and I hope you find programming to be as rewarding and fun as I do.

---

### Post by earthpigg on 2009-12-09
so, i need more practice. i want to make sure that i ***really know*** the stuff i currently kinda-sorta-know before i move on.

anyone have any simple tasks or number crunching they would like to be automated?

practice for me, time saver for you.

at this point i can:

1 - ask the user questions and take numerical input
2 - do basic "if this is true, then do this... otherwise, do this" statements
3 - manipulate that input
4 - provide output

---

### Post by earthpigg on 2009-12-09
good advice, thanks Max.

and actually... i already kind of knew that. i already do that with <br> when i do html. i dont know what i was thinking when i did that.

---

### Post by earthpigg on 2009-12-09
question for those 'in the know':

right now, im just using gedit with contextual highlighting. 

i code, i hit ctrl+s, then i click on my happy little terminal window, press the up arrow key and press enter to run the script, read any error messages, go back to gedit, and attempt to fix.

at what point will it be more efficient to be using an IDE instead?

---

### Post by MaxIBoy on 2009-12-09
Some easy ones:

[LIST]
[*]Math stuff (i.e. area of circle given radius, surface area of an *n*-sided equilateral prism given *n* and the size, stuff like that.)
[*]Text-based adventure game.
[*]Really stupid shell implementing only "cd," "cat," and "ls."
[/LIST]
The "IDLE" editor provided with the standard Python distribution is great for one-file or two-file projects. I recommend something that supports at least tabs if you have anything with more files than that. If you want a full IDE, I can absolutely recommend SPE ("Stani's Python Editor.") It has an integrated debugger which is really nice! (Although you can run the debugger on its own as well.)

EDIT: One more thing on style. If you have a large, multi-line string that doesn't have embedded variables, use triple-quotes so your string can last multiple lines. (Any odd number of contiguous quotes, single or double, counts as a single large opening/closing quote.) In fact, it may be a good idea to use string formatting instead, for huge strings with very few embedded variables: [http://www.diveintopython.org/native_data_types/formatting_strings.html](http://www.diveintopython.org/native_data_types/formatting_strings.html)

For very, very large strings, consider putting them in text files which are read by your program. This makes it easy to rewrite for other (human) languages as well.

---

### Post by Bölvaður on 2009-12-09
your code is much better than any code I write. But it is only because of comments.... I know how to do really nice comments, but I never do :D

and this is one of the things I get flamed at from others for doing in the opensource application Im doing in android

```

// useless comment about the loop in relation to the if statement
for (int i = 0 ; i > 100 ; i++ )

/* comments about what this actually does
    and lets the next programmer forget that there are no {}
    so he'll surely put some code between
    the for statement and the if statement :)
*/
if ( i % 5 == 0 )
return false;
return true;

```

you just have to love the readability and how concrete it is to avoid all errors in the future if some one randomly puts code somewhere.

---

### Post by earthpigg on 2009-12-09
> **Bölvaður said:**
> your code is much better than any code I write. But it is only because of comments.... I know how to do really nice comments, but I never do :D

i did what the book told me and put most of the comments in before i did a single line of code :D

---

### Post by MaxIBoy on 2009-12-09
That's the way to do it. Here's a quote from one of my favorite programming books, *practical C programming* 3rd edition ( (c) O'Reilly Media, Inc.)
> Understanding what you are doing is the most important part of programming. I once wrote two pages of comments describing a complex graphics algorithm. The comments were revised twice before I even started coding. The actual instructions took only half a page. Because I had organized my thoughts well (and was lucky,) the program worked the first time.

---

### Post by earthpigg on 2009-12-10
wow, nice quote. i won't be afraid to follow the author's example.

well, here's my next little script: clientdays

a good friend is a substance abuse counselor who's company is contracted by the state to help folks out that made some mistakes in their lives.

they charge the state *per day* and sit their with a calendar and calculator on a client's discharge date to figure out exactly how many days to bill... ugh.

user enters the year, month, and day of arrival... then enters the year, month, and day of departure. output is how many days she/he/it was present for.

you can also use it to calculate how many days you spent on this earth if you where to die today :D

next step is for me to figure out how to conjure up a web interface for this.... and maybe earn some cash by putting ads up :D

it is certainly nothing unique, but the fact that i know folks and that i know folks that know folks (etc) that would end up using it would be my angle.

```

#! /usr/bin/python3

"""
clientdays.py
Problem: Find out how many days a something was present prior to its departure.
Target Users: Anyone.
Target System: GNU/Linux
Interface: CLI
Maintainer: earthpigg
License: Public Domain
"""
__version__ = 0.1

# description of program
print("""\n\nclientdays
    \nBy earthpigg
    \nVersion 0.1
    \n\nThis program is designed to help you determine exactly how many days something was present prior to its departure.
    \nBoth the day of arrival and the day of departure will be counted as one full day each.
    \nNeither "partial" days nor hours will not be calculated. It is either a full day or not a day at all.""")

#ask entry year
print("\nWhat year did she/he/it arrive?")
yeararrive = input()

#ask entry month
print("\nWhat month did she/he/it arrive?")
montharrive = input("1-12: ")
int(montharrive)
if int(montharrive) > int(12) or int(montharrive) < int(1):
    print("""Error: month must be betwee 1 and 12. Results will be invalid""")

#ask entry day
print("\nWhat day of that month did she/he/it arrive??")
dayarrive = input()
montharrivedays = int(0)

if int(montharrive) % int(2) == 0:
    montharrivedays = int(31)
else:
    montharrivedays = int(30)

    #screw feb...
if montharrive == int(2):
    montharrivedays = int(28)

if int(dayarrive) > int(montharrivedays):
    print("Error: There are not", dayarrive, "days in this month. Results will not be valid.")
if int(dayarrive) < int(1):
    print("Error: Invalid entry. Results will not be valid.")

#ask exit year
print("\nWhat year did she/he/it depart?")
yearexit = input()

#ask exit month
print("\nWhat month did she/he/it depart?")
monthexit = input("1-12: ")
int(monthexit)
if int(monthexit) > int(12) or int(monthexit) < int(1):
    print("""Error: month must be betwee 1 and 12. Results will be invalid""")
monthexitdays = int(0)

if int(monthexit) % 2 == 0:
    monthexitdays = int(31)
else:
    monthexitdays = int(30)
if int(monthexit) == 2:
    monthexitdays = int(28)

#ask exit day
print("\nWhat day of that month did she/he/it depart??")
dayexit = input()

if int(dayexit) > int(monthexitdays):
    print("Error: There are not", dayarrive, "days in this month. Results will not be valid.")
if int(dayexit) < int(1):
    print("Error: Invalid entry. Results will not be valid.")

#crunch numbers
import datetime

entrydate = datetime.date(int(yeararrive), int(montharrive), int(dayarrive))
exitdate = datetime.date(int(yearexit), int(monthexit), int(dayexit))
totaldays = exitdate - entrydate
totaldays = totaldays.days + int(1)
print("She/he/it was present for", totaldays, "days.")
```

---

### Post by Warpnow on 2009-12-10
I'm also learning python. Recently wrote a basic CLI app that asks you for capital, interest rate, time, and compound periods, and calculates the compound interest. I used it in one of my classes a few times. I wanted it to work backwards, ie, be able to find rate from other data, or time, ect, but never got that far.

Accidently deleted it when cleaning my hard drive. :(

Edit: Actually, I found it:

```

#!/usr/bin/python
#Filename: interest.py
#A = a(1+(b/d))^cd

def interest(a, b, c, d):
	b = b / 100.00
	b = b / d
	b = b + 1
	c = c * d
	total = b**c*a
	print('The Future Value is {0}'.format(total))

a = int(input('What is the Principal?'))
b = float(input('What is the interest rate?'))
c = int(input('How many years will it compound?'))
d = int(input('How many times is it compounded each year?'))
interest(a, b, c, d)	

```

---

### Post by earthpigg on 2009-12-11
next noob question:

trying to find a goto-type function, so i can make a program that loops.

user enters data, numbers crunched, program provides output. then:

"do you want to enter more data or quit?"

if the answer is 'enter more data', i want it to go back almost to the start... the program will provide output that continues to change as it is given more and more data.

google has told me that someone wrote a goto module as a 'joke' for python 2.x, but there isn't one for 3... and, apparently, there is a whole bunch of hate out there at goto functions in programming.

so, why the hate? and, can someone give me a quick down-and-dirty example of how we do goto type stuff in python?

pseudocode:

```
#user enters data

#numbers crunched

#output

#want to enter more data that will modify the output?
   #if no, program is done.
   #if yes, allow user to enter more data.
```

---

### Post by Bölvaður on 2009-12-11
in other languages goto is looked downon... there actually are cases in some programming languages that goto isn't too stupid, but I would assume those languages are pretty much extinct by now.

In C++ on cli programs I use while loop for this type of problem.

So I did something like

```
bool in_menu_loop = false;
while (in_menu_loop){

// main function

//ask if you would like to continue
//and turn in_menu_loop to false if not

}
```


(this link might be helpful.. I havent read it tbh)
[http://www.ibiblio.org/g2swap/byteofpython/read/while-statement.html]("http://www.ibiblio.org/g2swap/byteofpython/read/while-statement.html")

---

### Post by cgb on 2009-12-11
I'm just beginning to learn python myself but a solution I came up with for a goto statement would be as such.  Just a basic version but I'm sure something similar would suit your needs..

```
def testOut():
    first = input("1st number")
    second = input("2nd number to add")
    print first+second
    test = input("enter 1 to exit 2 to repeat")
    if int(test) == 2:
        print testOut()
print testOut() 
```

---

### Post by Bölvaður on 2009-12-11
> **earthpigg said:**
> 
pseudocode:

```
#user enters data

#numbers crunched

#output

#want to enter more data that will modify the output?
   #if no, program is done.
   #if yes, allow user to enter more data.
```



are you talking about something like this?
```




def loop():

#while 'this' is true

int i
int sdf
# take input for i and sdf

# write out number crunching results
print  numbercrunching( i ,sdf)


#want to enter more data that will modify the output?
   #if no, ('this' is not true) go to return.
   #if yes,('this' is true) go another loop
    return



# nbumber crunching
def numbercrunching(int i,int sdf):

#something like   i = i * PI
return  i / sdf^2




```

---

### Post by juancarlospaco on 2009-12-11
Make a Graphical version...

---

### Post by -grubby on 2009-12-11
> **earthpigg said:**
> 
i haven't gone to the trouble to correct the user in every possible given case of illogical inputs. for example: if you tell it you have a room "potato" feet long, it will simply drop back to the terminal with an obscure error message instead of helpfully notifying you that "potato" is not a number.


The error isn't obscure if you know what you're doing :P

But yes, to fix this, look into [exceptions](http://docs.python.org/tutorial/errors.html). If you write some exception code around a statement, you're "catching" the error if it occurs.

I.e:

```

try:
    int("potato")
except ValueError:
    print "That isn't a number!"

```

> **earthpigg said:**
> question for those 'in the know':

right now, im just using gedit with contextual highlighting. 

i code, i hit ctrl+s, then i click on my happy little terminal window, press the up arrow key and press enter to run the script, read any error messages, go back to gedit, and attempt to fix.

at what point will it be more efficient to be using an IDE instead?

Throughout 2 years of Python programming, I've not used an IDE much. Most of my programming, though, is not desktop applications, but web applications, so I test in a browser mostly. 

I've attempted to write some GUI desktop applications, though, and I used Qt-Designer, along with pyuic4 to convert it's UI files to Python files. If that was integrated into an IDE I was using, it would most likely be more convenient.

At the level of experience you're at now, along with the type of projects you're doing, it's clear you don't need an IDE. If you think you need one at some point, I guess you can just try some and decide how you like them.

---

### Post by juancarlospaco on 2009-12-11
HowMuchPaint GUI, *the next [SIZE="1"]de[/SIZE]generation:*

```

#!/usr/bin/python
# Dependencies: sudo apt-get install python python-tk
from Tkinter import *
root = Tk()
root.title('HowMuchPaint')
def lol():
    exit(0)
menuz = Menu(root)
filemenu = Menu(menuz, tearoff=0)
filemenu.add_command(label='Quit', command = lol )
menuz.add_cascade(label='File', menu=filemenu)
root.config(menu=menuz)
label = Label(root, text='HowMuchPaint GUI: The Hello World...')
label.pack(padx=20, pady=20)
root.mainloop()

```

Now put inside the text fields and labels

---

### Post by cmat on 2009-12-11
> **earthpigg said:**
> 
at what point will it be more efficient to be using an IDE instead?

An IDE at any point wouldn't hurt, just the matter of picking the right one. Geany is my favorite one for Python and it's in the repos. It provides features like a sidebar so you can keep track of your variables and functions and you can build your code with a few mouse clicks.

For huge projects geany is great but PyDev (Eclipse) is better.

---

### Post by user1397 on 2009-12-11
> **earthpigg said:**
> so, im 50 pages into "[Python 3 for Absolute Beginners]("http://www.amazon.com/Python-Absolute-Beginners-Experts-Source/dp/1430216328/ref=sr_1_1?ie=UTF8&s=books&qid=1260414358&sr=8-1")" and it felt like i had read enough to construct my own happy little program from scratch.Then you have done what I could not. :(

Good job, keep it up.  (You're awesome for licensing it under public domain too...should be a more common practice.)

---

### Post by earthpigg on 2009-12-11
> **ubuntuman001 said:**
> (You're awesome for licensing it under public domain too...should be a more common practice.)

since they are so simple, trying to enforce any other licensing scheme would be impossible. my two little programs so far are little more than "hello world" programs. *de-facto* public domain already exists.

i use the [wtfpl]("http://en.wikipedia.org/wiki/WTFPL") for [a lot of my stuff]("http://sites.google.com/site/masonux/home/legal-stuff") because i think it's funny and cute (and, incidentally, i have no objections to the terms themselves), but i didn't do that here because i didn't want to go to the trouble to include the text of it.

my stuff so far is little more than creative expression. i haven't created anything i would call "Software" with a capital S. i don't like the CC and restrictive copyleft stuff for my personal hobbyist ventures. if someone wants to use something i wrote or did in a book or something, i would be honored. attributed or not (though my ego would certainly be stroked if it was attributed).

that being said, an acquaintance of mine that actually does really good artwork (like, on paper and stuff. you know, ***IRL***!)... i showed him the CC website and encouraged him to use one of them.

i probably wouldn't even have thought to put that line in the code, except the book told me to, so that it would become a routine/habit for me... cant put that line there without at least spending half a second to think about it, right? which makes sense, so ill go with it.

now that i am thinking about it...

i suppose ill stick with public domain or wtfpl for "super hello world" programs that are mostly for my own learning.

if i where to write something that was a trivial software contribution, i would use the BSD license, request attribution, and have no objections to someone re-licensing it under the GPL... or using it in non-free software. (i have zero objections to video games and toys being proprietary. there will never be a situation wherein i am ***reliant*** on a toy.)

if i where to write something that i felt had any potential of being a non-trivial contribution (ie: something that someone out there could potentially become ***reliant*** upon), i would be sure to use GPLv2 and, again, to *request* attribution.

the main reason to request documented attribution is so i could put it on my resume and have it be verifiable. :D

i guess that sounds reasonable. to me, at least. but, im getting ahead of myself. back to learning python!

---

### Post by aaron_the_dude on 2009-12-13
You helped me out in the past, and i'm using this tutorial, [http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python)

I have to say, I don't quite understand what def and return statements are for.  In the tutorial, it seems almost redundant.

---

### Post by MaxIBoy on 2009-12-13
"def" creates a function.
```
def name_you_want_the_function_to_have (arguments, that, the, function, will, take):
```"return" is used to exit the function and it also is used to specify the "answer" of the function.
```
def three ():
    return 3

def double (number_which_will_be_doubled):
    return number_which_will_be_doubled*2

print (double(three())) #the output is 6

```

---

### Post by -grubby on 2009-12-13
> **MaxIBoy said:**
> double is a reserved word

NameError: name 'double' is not defined

No it isn't.

---

### Post by MaxIBoy on 2009-12-13
Thanks, and corrected. (Yeah, I'm in C mode right now.)

---

