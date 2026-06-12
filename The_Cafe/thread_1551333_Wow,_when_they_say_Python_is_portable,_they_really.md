---
title: "Wow, when they say Python is portable, they really do mean portable."
date: 2010-08-12
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-08-12
Well lately I've picked back up on learning python, and I don't like to just sit there and read stuff or do little bits at a time. I learn best when I go through a ton of frustrations which hasn't been much with python, just annoyances when I don't get the syntax right every now and again (C++ put me in fits of rage, python is fun :) ). So I thought the best way to learn the language was to do a project. So I decided to make a program for my chemistry class for various types of tedious calculations (ones that involve looking at the periodic table every time). My friend asked me if he could use it in his chemistry class. Well it worked on Windows!! Yay! I can hold off on learning how to port something once again. I tried it in my Virtualbox of WinXP, and it only took a download of python from the website, and now I can execute them.

Now he wants to know if I can make it more clickable...he wants me to build a gui. Blah...
I don't know any other gui builders that are as easy to use as Visual Studio, and I don't even know how to use arrays in Visual Basic.

Oddly enough the hard part is finding the info...for over 100 elements. Oh and if you're curious, this is the code so far. :D

```

#!/usr/bin/env python

import math

a=0
b=0
c=0
d=0
e=0
f=0
g=0
h=0
i=0
j=0
k=0
l=0
m=0
n=0
o=0
p=0
q=0
r=0
s=0
t=0
u=0
v=0
w=0
x=0
y=1
z=0

question = y

while question == y:
    print "        Chemistry Handbook version 1.0"
    print ""
    print "Enter a number for any operation you wish to perform. All elements are entered with their abbreviations (i.e. 'C' for Carbon)."
    print ""
    print "    1. Mass Calculator"
    print "    2. Something"
    print "    3. Something"
    print "    4. Something"
    print "    etc."
    print ""
    
    option = input("Which operation would you like to perform? ")
    
    #Formula Mass calculator
    if option == 1:
        Ac=227.028
        Al=23.982
        Am=243
        Sb=121.757
        Ar=39.948
        As=74.922
        At=210
        Ba=137.327
        Bk=247
        Be=9.012
        Bi=208.98
        Bh=262
        B=10.811
        Br=79.904
        Cd=112.411
        Ca=40.078
        Cf=251
        C=12.011
        Ce=140.115
        Cs=132.9054
        Cl=51.9961
        Co=58.9332
        Cu=63.546
        Cm=247
        Db=262
        Dy=162.503
        Es=252
        Er=167.263
        Eu=151.965
        Fm=257
        F=18.9984
        Fr=223
        Gd=157.253
        Ga=69.723
        Ge=72.61
        Au=196.96654
        Hf=178.492
        Hs=265
        He=4.002602
        Ho=164.93032
        H=1.0079
        In=114.82
        I=126.90447
        Ir=192.223
        Fe=55.847
        Kr=83.801
        La=138.9055
        Lr=262
        Pb=207.21
        Li=6.941
        Lu=174.967
        Mg=24.305
        Mn=54.938
        Mt=266
        Md=258
        Hg=200.593
        Mo=95.941
        Nd=144.24
        Ne=20.1797
        Np=237.048
        Ni=58.6934
        Nb=92.90638
        N=14.00674
        No=259
        Os=190.21
        O=15.9994
        Pd=106.421
        P=30.9737624
        Pt=195.083
        Pu=244
        Po=209
        K=39.0983
        Pr=140.907653
        Pm=145
        Pa=231.0359
        Ra=226.025
        Rn=222
        Re=186.2071
        Rh=102.9055
        Rb=85.4678
        Ru=101.07
        Rf=261
        Sm=150.36
        Sc=44.955910
        Sg=263
        Se=78.96
        Si=28.0855
        Ag=107.8682
        Na=22.989768
        Sr=87.62
        S=32.066
        Ta=180.9479
        Tc=98
        Te=127.603
        Tb=158.92534
        Tl=204.3833
        Th=232.0381
        Tm=168.93421
        Sn=118.710
        Ti=47.88
        W=183.85
        U=238.0289
        V=50.9415
        Xe=131.29
        Yb=173.04
        Y=88.90585
        Zn=65.39
        Zr=91.224
    
        mass = input("Formula: ")
        print "Atomic mass = ", mass, "grams per mole"
        
    #Element Information
    if option == 2:
        Ac = ['Actinium',1878] #Not real!
        einfo = input("Which element would you like information on? ")
        print "Element Name: ",einfo[0]
        print "Year discovered: ",einfo[1]
        question = input("Return to main menu? [y/n]: ")
    question = input("Return to main menu? [y/n]: ")
    if question != y:
        break

```

---

### Post by RiceMonster on 2010-08-12
Python runs in an interpreter that has been ported to different OS's. Of course it's portable.


As for arrays in Visual Basic, they're not much different than other languages. Same basic concept.

For example:
```
Dim myArray() as Integer = {1,2,3,4,5,6,7,8,9}
```

---

### Post by Legendary_Bibo on 2010-08-12
> **RiceMonster said:**
> Python runs in an interpreter that has been ported to different OS's. Of course it's portable.


As for arrays in Visual Basic, they're not much different than other languages. Same basic concept.

For example:
```
Dim myArray() as Integer = {1,2,3,4,5,6,7,8,9}
```

oh, that is easy. Hmmm...I guess I could build a gui for it, and it would just take a few tweaks of the language and I should be able to get one. Do you know of a program like Visual Studios that actually matches its ease of use? I've only used the free VS, and even then it seems to be quite effective.

---

### Post by RiceMonster on 2010-08-12
Well there is glade for making gtk+ interfaces for python programs. I don't know much about it, though.

MonoDevelop also has an interface designer.

---

### Post by ve4cib on 2010-08-12
Python on Windows ships by default with Tkinter (the Python version of the Tk UI toolkit), so if you want maximum portability in your UI I'd go for that.  The Tkinter package is also available through the Ubuntu repositories (though it is not included by default).

Building a UI in Tk isn't the easiest thing in the world to do, but it's not bad.  Certainly no worse than designing a webpage in HTML + CSS.  You can define a grid for your layout, and you just drop every element (button, label, scrollbar, etc...) onto it through code.

Several years ago I wrote a pretty simple RPN calculator using Python & Tk.  This was my very first attempt at writing a UI in Python, so it's rough around the edges, but it might give you some ideas:

[http://sites.google.com/site/ve4cib/rpncalculator](http://sites.google.com/site/ve4cib/rpncalculator)

Documentation for how to use Tkinter can be found here: [http://wiki.python.org/moin/TkInter](http://wiki.python.org/moin/TkInter)

---

### Post by Legendary_Bibo on 2010-08-12
I'll look into both of your guys' suggestions.

---

### Post by forrestcupp on 2010-08-12
I used to use PyGTK.  Glade makes it easy like Visual Basic.

But honestly, if you're not programming a GUI, any programming language out there is portable.  If you're not programming WinAPI, even a lot of GUI toolkits are portable.

---

### Post by WinterMadness on 2010-08-12
I think netbeans has a python plugin so you can make GUIs and code

---

