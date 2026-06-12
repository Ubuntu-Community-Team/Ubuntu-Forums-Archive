---
title: "Teaching Computer Class"
date: 2011-04-09
forum: The Cafe
---

### Post by vehemoth on 2011-04-09
I've been asked by a teacher what I would expect to learn in a computer class (yr 13, last year high school). I gave him some ideas but I thought the best people to answer a question like that are you guys, so what do you think?

---

### Post by earthpigg on 2011-04-09
Selecting hardware that is compatible, and assemlbing a computer given a specified budget.

---

### Post by LowSky on 2011-04-09
do your own homework. LOL

---

### Post by vehemoth on 2011-04-09
Lol, nah this isn't homework and it can only be software wise. So far I reckon a look at different licenses and software under those licenses.

---

### Post by Thewhistlingwind on 2011-04-09
I don't know, something like writing a parser for some formal language?

---

### Post by earthpigg on 2011-04-09
> **vehemoth said:**
> Lol, nah this isn't homework and it can only be software wise.

ok.

be able to write simple programs that solve math equations.

[this]("http://ctmason.wordpress.com/2011/03/13/simple-ti-83-program-for-econ-students-elasticity-coefficient-calculator/") would probably be a handy thing to be able to do, for any student entering college next year, no?

teacher could hand out random equations pulled from math, science, and econ text books - and expect the students to be able to write computer programs that instantly solve them by the end of the semester.

instead of just being useful for students that want to be accountants or computer programmers, this is a skill that could legitimately be useful for damn-near any academician. 

or even blue collar folks -- i wrote a similar very simple program in python that tells you how much paint you need to purchase for a room of any given size given 1 or 2 coats and given that the ceiling will or will not be painted.

(i suggest using python for this, not BASIC or C or C++ or C# or C%##+.)

---

### Post by vehemoth on 2011-04-09
Interesting. Our curriculum sucks over here. Our "programming" class at this school is web design with html css and basic javascript. This class is near the bottom of the heap with the peeople in it, so maybe not programming. I was thinking basic work in blender, what do you think about that? is it a good idea?

---

### Post by earthpigg on 2011-04-09
I think very basic programming, as i described, is more likely to be more useful for more students when compared to making pretty pictures appear on a screen.

Any of your teachers ought to be able to teach themselves basic python in a week or two. Hell, I have no reason to doubt that you *yourself* could do that over spring break. You've taken Algebra 1, right?

If you wanted to go the pretty pictures route, though, I'd suggest gimp over blender. It would mesh well with your school's existing emphasis on making web pages.

---

### Post by Thewhistlingwind on 2011-04-09
> **earthpigg said:**
> I think very basic programming, as i described, is more likely to be more useful for more students when compared to making pretty pictures appear on a screen.

Any of your teachers ought to be able to teach themselves basic python in a week or two. Hell, I have no reason to doubt that you *yourself* could do that over spring break. You've taken Algebra 1, right?

If you wanted to go the pretty pictures route, though, I'd suggest gimp over blender. It would mesh well with your school's existing emphasis on making web pages.

Agreed, on all points, another idea is that you could try some really amateur computer forensics, if nothing else knowing 3+ utilities to recover your data is always a useful trait.

---

### Post by vehemoth on 2011-04-09
I understand that, however this class is below the web design clas, and I don't know whether the othe members of the class could cope. I did the webdesing course last year and saw other class members struggle with it. I don't think a lot of the people in this class would be able to do that sort of thing.

---

### Post by earthpigg on 2011-04-09
> **Thewhistlingwind said:**
> ...another idea is that you could try some really amateur computer forensics, if nothing else knowing 3+ utilities to recover your data is always a useful trait.

ooo, nice! photorec, dd, and we're having a forensic party!

will come in handy when your friend or girlfriend accidentally deletes pictures on her camera.

you know that software telling you that something is 'permanently' deleted is usually lying to you, right? if not, wouldn't it be fun to learn why?

and how the FBI busts people even when they "Empty Recycle Bin" the evidence?

---

### Post by earthpigg on 2011-04-09
man, threads like this make me want to be a teacher.

given 1 school year, i would have my kids picking parts, putting computers together, installing operating systems, setting up local area network multimedia servers, and  writing programs to do their homework for them.

i'd also have those able to do so growing ridiculous facial hair so they could be like me.

is that worth wasting 2 years on a union-mandated-but-otherwise-worthless high school teaching credential in California?

---

### Post by Thewhistlingwind on 2011-04-09
> **earthpigg said:**
> man, threads like this make me want to be a teacher.

given 1 school year, i would have my kids picking parts, putting computers together, installing operating systems, setting up local area network multimedia servers, and  writing programs to do their homework for them.

is that worth wasting 2 years on a union-mandated-but-otherwise-useless high school teaching credential?

Theres only one problem, 90% of students are apathetic. And they'll break the parts. Which the school won't fund.:popcorn: Trust me, the kids who are worth having will gravitate this way one path or another.

EDIT: As for the OP, consider yourself lucky, I've still got four years to go.

---

### Post by earthpigg on 2011-04-09
> **vehemoth said:**
> I understand that, however this class is below the web design clas, and I don't know whether the othe members of the class could cope. I did the webdesing course last year and saw other class members struggle with it. I don't think a lot of the people in this class would be able to do that sort of thing.

making very simple programs that execute formulas is easier than web design stuff. 

```
#! /usr/bin/python3

"""
howmuchpaint.py
Problem: Find out how much paint user will need to paint a certain room.
Target Users: Me, anyone
Target System: GNU/Linux
Interface: CLI
Maintainer: Chris Mason <mason.christopher.thomas@gmail.com>
License: Public Domain
"""
__version__ = 0.1


# description of program
print("\n\nhowmuchpaint \nBy Chris Mason \nVersion 0.1\n\nThis program is designed to help you determine how much paint to purchase in order to paint all four walls and perhaps the ceiling of a given room with a given type of paint.")


# want to think 'per bucket' or 'per gallon'?
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
    # light covors more

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

is any of that math or those concepts to much for a senior in high school?

---

### Post by vehemoth on 2011-04-09
> **Thewhistlingwind said:**
> Theres only one problem, 90% of students are apathetic. And they'll break the parts. Which the school won't fund.:popcorn: Trust me, the kids who are worth having will gravitate this way one path or another.

EDIT: As for the OP, consider yourself lucky, I've still got four years to go.

Man that's gotta suck, hope you have better subjects than me. And for me it's actually two years, I'm doing a subject a level up

---

### Post by vehemoth on 2011-04-09
> **earthpigg said:**
> making very simple programs that execute formulas is easier than web design stuff. 

```
#! /usr/bin/python3

"""
howmuchpaint.py
Problem: Find out how much paint user will need to paint a certain room.
Target Users: Me, anyone
Target System: GNU/Linux
Interface: CLI
Maintainer: Chris Mason <mason.christopher.thomas@gmail.com>
License: Public Domain
"""
__version__ = 0.1


# description of program
print("\n\nhowmuchpaint \nBy Chris Mason \nVersion 0.1\n\nThis program is designed to help you determine how much paint to purchase in order to paint all four walls and perhaps the ceiling of a given room with a given type of paint.")


# want to think 'per bucket' or 'per gallon'?
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
    # light covors more

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

```is any of that math or those concepts to much for a senior in high school?

Saddly, yes. Computing is considered one of those subjects you do when you don't want to do a lot of work. Maybe it's worth a try anyway, It's not like those guys weren't gonna fail anyway.

---

### Post by Thewhistlingwind on 2011-04-09
> **vehemoth said:**
> Man that's gotta suck, hope you have better subjects than me. And for me it's actually two years, I'm doing a subject a level up

Worse, I have one class that asks me for any specific talents, the rest are pretty ordinary.

And it's great, when you think about it that means I get four years of free room and board to hone my art and learn how to get it out there. I'm always looking to win the game early though. :D

---

### Post by earthpigg on 2011-04-09
> **vehemoth said:**
> > is any of that math or those concepts to much for a senior in high school?Saddly, yes. Computing is considered one of those subjects you do when you don't want to do a lot of work. 

I'm not sure I agree with you.

For high school seniors such as myself back in the day, doing the absolute bare minimum to graduate and join the Marines? yes, clearly.

But I did the above without a day of university education, and 8 years after having failed basic high school math. The point isn't how smart I am, the point is how *not* smart I am. I'm clearly no genius, far from it. I picked up a book titled "Python for Morons" or similar.

I think any high school senior that ought to actually *be* a high school senior, and that *wants* to do it can do even better than I did 2 years ago after being a professional bullet stopper for 8 years. (the code is sloppy.)

So: call it an "honors" course or an "AP" course.

---

### Post by vehemoth on 2011-04-09
> **earthpigg said:**
> I'm not sure I agree with you.

For high school seniors such as myself back in the day, doing the absolute bare minimum to graduate and join the Marines? yes, clearly.

But I did the above without a day of university education, and 8 years after having failed basic high school math. The point isn't how smart I am, the point is how *not* smart I am. I'm clearly no genius, far from it. I picked up a book titled "Python for Morons" or similar.

I think any high school senior that ought to actually *be* a high school senior, and that *wants* to do it can do even better than I did 2 years ago after being a professional bullet stopper for 8 years. (the code is sloppy.)

So: call it an "honors" course or an "AP" course.

Yeah I suppose, Anything has got to be better than the brief writing and word documents that we are currently doing.

---

