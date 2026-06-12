---
title: "Simple Test web server"
date: 2008-08-22
forum: Server Platforms
---

### Post by Stupid_newbie on 2008-08-22
YOU will probably laugh at me for this, and be like "YOU ARE CHEATING!" but I don't care, I am stubborn.

I am designing a simple website for a client of mine. he just wants a simple web menu designed for his pizza shop. I told him no problem! (it has become a problem)

Heres the minor problem: I Use Ubuntu more then my XP partition, and I paid for dreamweaver, and dreamweaver creates a "PSUDO" web environment in xp. to use dreamweaver I used wine to emulate the software (even tho Wine Is Not an Emulator)

 I have dyndns point to my ip so that I can test everything remotely just to ensure my changes are working properly. unfortunately when I tried to implement JAVA code into the pages, I get diddily squat! I installed apache, I installed mysql and I also installed php and I cant get my menu codes to work!... I am a noob to this type of web server! 

I tried to install "lamp" as someone on this forum suggested and debian told me to **** off! (not literally)

any help would really really be appreceated.

kevinroche.isa-geek.com is the url

---

### Post by pytheas22 on 2008-08-22
When I visit that URL I don't see any javascript (is that what you mean by "JAVA code?") even in the page source.  How are you trying to serve it?  If you're using includes or something, are you sure that the javascript files are readable by everyone (i.e., they should have at least 755 permissions)?  Otherwise, did you try pasting the javascript directly into the html file?

---

### Post by wirepuller134 on 2008-08-22
What is it your trying to do with the menu?  I also don't see any of the java script.

---

### Post by Stupid_newbie on 2008-08-23
I deleted the Java Code. cause It wasnt working. but it wont run it at all!.. I have been working on the page for a bit now and I will put it back in a few min.

---

### Post by OutOfReach on 2008-08-23
Golden Pizza?
That's what I get when I visit the URL.

---

### Post by Stupid_newbie on 2008-08-23
yes. that is right... the LOGO is like 2mb and I have to change it.. i am just getting the damn menu written up.. I am like new to CSS and Java that I am tempted to just insert a simple menu like it has now and not a Java menu like my old personal web site

---

### Post by windependence on 2008-08-23
There is a BIG difference between Java and Javascript. Javascript is a very widely used scripting language used in web development. Java is an actual programming language by Sun Microsystems. They are not related at all. IF your code really is Java and not Javascript, then you would have needed to install the Java runtime to get it to run. Installing the JDK probably would have been the best approach.

-Tim

---

### Post by Stupid_newbie on 2008-08-23
> **windependence said:**
> There is a BIG difference between Java and Javascript. Javascript is a very widely used scripting language used in web development. Java is an actual programming language by Sun Microsystems. They are not related at all. IF your code really is Java and not Javascript, then you would have needed to install the Java runtime to get it to run. Installing the JDK probably would have been the best approach.

-Tim

fair enough! and thank you for the input, but once again..it is javascript I am trying to run and I get eff all!

---

### Post by pytheas22 on 2008-08-23
> I am tempted to just insert a simple menu like it has now and not a Java menu like my old personal web site

I vote for that.  I don't like using javascript in menus unless there's a good reason.  Javascript often causes more problems that it's worth because it sucks up system resources, has a greater potential to behave unexpectedly in different browsers than straight html/CSS and isn't supported by older browsers.  Also, I have a personal aversion to sites that go overboard with javascript and have stuff popping up or flashing every time I move the cursor.

If you're just dealing with a simple (presumably short and one-dimensional) menu, I'd highly recommend sticking to normal html.  Of course, if you do decide to go with javascript, let us know when you put it back up so we can see if it works.

---

### Post by Stupid_newbie on 2008-08-23
it is back there, I am just working on some new code for the home page.. let me know if the main logo takes a while to load up.. if so im sorry... I believe my u/l bandwidth is capped!

---

### Post by windependence on 2008-08-23
Instead of reinventing the wheel, use a template. Check these out:

[www.oswd.org](www.oswd.org)

Just wanted to save you some work. ;)

-Tim

---

### Post by Stupid_newbie on 2010-07-29
In the End I decided to scrap the Java and just go with a basic menu with location tags. I then never finished the page and lost the data... Oh well, he wasn't going to pay me anyway

thanks all

---

