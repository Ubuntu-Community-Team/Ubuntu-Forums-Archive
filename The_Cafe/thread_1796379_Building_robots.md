---
title: "Building robots"
date: 2011-07-03
forum: The Cafe
---

### Post by WinterMadness on 2011-07-03
I would really like to get into this, and browsing through google I cant help but to find a lot of things that are largely unrelated, or perhaps something thats meant for very young kids (such as toy robots that only require basic assembly)

what I want to know is, what kind of information should I research to get into this? I have a decent understanding of programming languages(taking an AI, algorithms & data structures classes this semester), and though I havent taken calculus yet im pretty decent at math. 

I would like to start relatively small, but I want to have a very good understanding of what im even doing at any given moment

so can you guys recommend books and other things I should look into? im not asking how to build Asimo or anything, just the fundamentals :)

dont be stingy with recommendations, this fascinates me and im very willing to dive in real deep.

---

### Post by red_Marvin on 2011-07-03
I'd say get into microcontroller programming,
personally I think the avr by atmel is a nice
architecture, programmable with c and/or asm.
gcc for avr as well as other neccesary linux
tools are available.

You would need a programmer, a suitable power
source and a breadboard etc. This is not
too difficult to set up though.

If you want something more beginner friendly
there is the arduino, which is avr based,
comes on a board with usb and power regulator
and an ide, I don't think you get to work on
the c/asm level though, although you could
reprogram it the normal way as any other avr.
I have not tried it but many seem to like it.

I guess it depends on if you want to work
on the application or the kernel level :)

You should also get the hang of controlling
stuff with digital signals, eg transistors as
switches, how to control or even build H bridges
etc. Controlling a standard hobby servo is an
easy start, once you get the hang of basic
programmimng for the microcontroller you choose.

---

### Post by Grafens on 2011-07-03
I don't know anything about robots myself but these students built a robot for $14 in five minutes.[http://www.eecs.harvard.edu/ssr/projects/progSA/kilobot.html]("http://www.eecs.harvard.edu/ssr/projects/progSA/kilobot.html")
The pdf file on their site gives a list of the research materials that they used. Maybe this will point you in the right direction.

---

### Post by handy on 2011-07-03
I haven't had a look for a while, but I did see a lot of robotic stuff being made that used VIA Pico-ITX mainboards:

[http://www.via.com.tw/en/initiatives/spearhead/pico-itx/](http://www.via.com.tw/en/initiatives/spearhead/pico-itx/)

If you search Scroogle for via pico-itx robotics you'll find plenty to go on with I think, like:

[http://robots.net/article/2511.html](http://robots.net/article/2511.html)

[http://www.engadget.com/2008/08/22/via-shows-off-epia-pico-itx-based-robots/](http://www.engadget.com/2008/08/22/via-shows-off-epia-pico-itx-based-robots/)

[http://forums.trossenrobotics.com/showthread.php?t=1312](http://forums.trossenrobotics.com/showthread.php?t=1312)

---

### Post by ve4cib on 2011-07-03
[Robotis](http://www.robotis.com/xe/) is a company from Korea that makes robots and robot parts/kits.  The prices range quite a lot from kit to kit, but you can get a microcontroller (programmable in C), and a few servo motors for not too much.

A CM-5 microcontroller and a couple of servos (AX-12s are cheap) would give you a decent way to get started with a basic robot.  It might be a little expensive though.

(I'm currently doing my master's in computer science, focusing on robotics at the University of Manitoba.  We use Robotis parts and kits for a lot of our research, so they're not just cheap toy robots.  I can personally vouch for their quality.)

Typically robots don't have vast amounts of processing power, so any kind of embedded systems programming is always helpful.  Real-time systems programming is also good, since robots interact with the real world directly.  If you can't get the timing of the walking gait on a bipedal robot right then it will just fall over.

Like Red_Marvin said, Atmel AVR boards are nice to work with.  The Robotis CM-5 uses at AtMega128.  If you're interested, I've got a (very unstable, still in-progress) Google Code project on the go to write a multi-tasking OS for the AtMega128 CPUs [here](http://code.google.com/p/frigos/).  Feel free to read through the horribly messy code if you want.  (I haven't had a chance to work on it in a little while, but it's not abandoned yet.)

Controlling motors in a robot is usually done in one of two ways in my experience: generating PWM (pulse-width modulation) signals directly on an I/O pin, or sending data over a serial/USB/ethernet connection.

Sending data over a direct connection is pretty simple, and not terribly exciting.  Just look up whatever data format the motor expects, and transmit it.  Nothing complex there.

PWM is an interesting exercise for any programmer to try to do though.  Basically, you need to create a pulse with a specific frequency to set the position of the motor.  Different frequencies = different motor position.  If the PWM signal is noisy (i.e. the frequency isn't stable) the motor will jitter back and forth, instead of staying in a nice, stable position.

Once you can control the motors, the next job is orchestrating them to do something useful.  This area is called "motion planning."

Motion planning is simply determining what positions the motors need to be and, and how fast they need to be moving, at any given moment.  So if you want to walk, you need to lift the hip and the knee of one leg simultaneously, then lean forwards, extending that leg, and place the foot back down.  Repeat with the other leg.  And over, and over.

After basic motions you can start having fun with inputs.  Sensors come in all sorts: proximity, thermal, cameras, microphones, etc...  The type of robot you want to make will influence what kinds of sensors you want to use.  Personally I like a standard, colour camera.

Vision processing (the OpenCV library is great for that) is a field of its own, but it's heavily used in robotics.  Identifying objects, determining where they are, and then planning & executing a motion to interact with that object is ultimately the goal of most robots.

I realize I've been a little vague, and rambled a bit.  So if you have any specific questions feel free to ask them.

And now, here's a video of a robot doing stuff:

[http://youtu.be/_p3pguWNhY8](http://youtu.be/_p3pguWNhY8)

(This is the robot I'm working on right now in the lab at school.  Made by... you guessed it: Robotis.)

---

### Post by Tux Aubrey on 2011-07-07
I have been playing with Arduino for around six months and, for me, it has been a great introduction to electronics, programming and learning to design control systems.  You could check out some of the robotics supply shops on line for different ideas - [http://www.australianrobotics.com.au/](http://www.australianrobotics.com.au/) is one I know.  The main[Arduino forums]("http://arduino.cc/forum/") also have lots of discussion about robotics and relevant issues like sensors, motors, navigation and wireless communications.

Have fun!

---

### Post by wishyjr on 2011-07-07
not being funny, but have you considered a Lego 'Mindstorm' kit? great for a fun robot project and there is a buzzing community. might be cheaper than other (more serious) kits too.

---

### Post by handy on 2011-07-08
> **Tux Aubrey said:**
> I have been playing with Arduino for around six months and, for me, it has been a great introduction to electronics, programming and learning to design control systems.  You could check out some of the robotics supply shops on line for different ideas - [http://www.australianrobotics.com.au/](http://www.australianrobotics.com.au/) is one I know.  The main[Arduino forums]("http://arduino.cc/forum/") also have lots of discussion about robotics and relevant issues like sensors, motors, navigation and wireless communications.

Have fun!

Thanks for the heads up on the Australian Robotics site Tux Aubrey. 

I find the robotics thing interesting but I don't really have anything but learning to do with a "robot" that I built.

With what I've seen on the Australian Robotics site, I have had the possibilities of what I can do expanded greatly due to the practicalities of the prototyping tools on hand via the Arduino & related products. 

I've ordered a few of their books & a kit or two & am looking forward to learning what looks like their cut down version of the "C" programming language.

Apart from the occasional half hearted look at Python, I've not really done any programming or script work since 1995, so this should be a gentle way back into it, with a reason to do it. I want to be able to measure & log soil temperature & moisture in my wife's 9 raised veggie garden beds & automatically control their irrigation appropriately.

If I polish that up & know what I'm doing, I expect that there will be a number of other people in the local area who may want to use a similar system.

I'm looking forward to the arrival of the package next week. :)

---

### Post by Tux Aubrey on 2011-07-08
> **handy said:**
> 
Apart from the occasional half hearted look at Python, I've not really done any programming or script work since 1995, so this should be a gentle way back into it, with a reason to do it. I want to be able to measure & log soil temperature & moisture in my wife's 9 raised veggie garden beds & automatically control their irrigation appropriately.

If I polish that up & know what I'm doing, I expect that there will be a number of other people in the local area who may want to use a similar system.

I'm looking forward to the arrival of the package next week. :)

That's a great start!  You are a couple of decades ahead of where I was when I started with Arduino programming (Fortran on punch cards in the 1970s).  I found lots of sites that really helped me get into Arduino programming and hardware using a "recipe book" approach and lots of cut and paste.  Look at John Boxall's [tronixstuff]("http://tronixstuff.wordpress.com/") site for some great tutorials and references.  There are many others.  Don't be afraid to start with the very simple "blinking led" projects in the beginners' sections.

My first "real life" Arduino project was a greenhouse controller (documented on my blog - link below).  It was painful but rewarding and I now feel confident to move onto some bigger projects.

---

### Post by handy on 2011-07-09
> **Tux Aubrey said:**
> 
That's a great start!  You are a couple of decades ahead of where I was when I started with Arduino programming (Fortran on punch cards in the 1970s).  

I feel better already! :)

> **Tux Aubrey said:**
> 
I found lots of sites that really helped me get into Arduino programming and hardware using a "recipe book" approach and lots of cut and paste.  Look at John Boxall's [tronixstuff]("http://tronixstuff.wordpress.com/") site for some great tutorials and references.  

Wow, terrific site, thanks Aubrey.

If I had of known about that earlier I may have only bought 2 instead of 3 books. <doh!>  I've only looked at the table of contents of the 39 lessons, the progression of subjects looks to be well thought out.

> **Tux Aubrey said:**
> 
There are many others.  Don't be afraid to start with the very simple "blinking led" projects in the beginners' sections. 

Yes, my intention it to start at most basic & gradually work my way through increasingly more difficult projects. My only concern is that my memory isn't so good these days, so I'll certainly be looking back at what I've done a lot in an effort to try & embed it the language in my mind.

> **Tux Aubrey said:**
> 
My first "real life" Arduino project was a greenhouse controller (documented on my blog - link below).  It was painful but rewarding and I now feel confident to move onto some bigger projects.

Painful, as in getting to know the cut down version of the "C" language that the Arduino uses? Or in applying the most effective hardware to the problems at hand?

I suspect all of the above.

I had a look at your blog yesterday, I'm thoroughly impressed by what you have accomplished.

---

### Post by ve4cib on 2011-07-09
> **handy said:**
> Painful, as in getting to know the cut down version of the "C" language that the Arduino uses?

I'm curious what you mean by this.  I've never worked with Arduino boards myself, but I've used other boards with Atmel chips, and I've never run into a "cut down version of C."

Are you talking about specific libraries that you can't use?  Or something else?

---

### Post by handy on 2011-07-09
> **ve4cib said:**
> I'm curious what you mean by this.  I've never worked with Arduino boards myself, but I've used other boards with Atmel chips, and I've never run into a "cut down version of C."

Are you talking about specific libraries that you can't use?  Or something else?

It is a language called Processing, which is used for quite a number of creative things. 

This should hopefully answer your questions:

[http://www.openprocessing.org/](http://www.openprocessing.org/)

---

### Post by red_Marvin on 2011-07-09
Processing is the language for arduinos, however avr chips are programmed
with c and or assembler and it is the gnu utils we are talking about, not
any limited proprietary hobby version.

Arduinos are to my knowledge fully open, and it should be no trouble
writing c/asm for them, but you would loose the option of programming them
over usb, unless you write your own bootloader, or somesuch...

---

### Post by Tux Aubrey on 2011-07-09
> **handy said:**
> 
Painful, as in getting to know the cut down version of the "C" language that the Arduino uses? Or in applying the most effective hardware to the problems at hand?

Yes! Not having either an electronics or programming background, I had to start from scratch.  Six months ago, I had never used a soldering iron in anger and can now construct even (fairly) complex kits or Arduino "shields".  I do still struggle with both the programming and the hardware side but now only make about a dozen stupid mistakes per project.  That's quite satisfying in a peculiar way and, if I was younger, I would probably be learning all this very quickly.  So far I have learned that capacitors explode if you put them in backwards.

---

### Post by handy on 2011-07-09
> **Tux Aubrey said:**
> Yes! Not having either an electronics or programming background, I had to start from scratch.  Six months ago, I had never used a soldering iron in anger and can now construct even (fairly) complex kits or Arduino "shields".  I do still struggle with both the programming and the hardware side but now only make about a dozen stupid mistakes per project.  That's quite satisfying in a peculiar way and, if I was younger, I would probably be learning all this very quickly.  So far I have learned that capacitors explode if you put them in backwards.

:lolflag: I'll keep that in mind!

I'm reading through all of the 39 tutorials on the tronixstuff site to prime my brain so it is somewhat ready for the package that will arrive in a few days via the post. 

I'm up to lesson 6, & am becoming more familiar with the way the code is written.

From past experience I know that I like to be able to modify code written by others, to suit my needs or just to experiment with, it is much easier than having to start from scratch when you don't really know what you are doing... :) <stating the obvious again I know...>

---

### Post by handy on 2011-07-10
> **ve4cib said:**
> I'm curious what you mean by this.  I've never worked with Arduino boards myself, but I've used other boards with Atmel chips, and I've never run into a "cut down version of C."

Are you talking about specific libraries that you can't use?  Or something else?

There is more specific info' on the ATMEL AVR micro-controller chips used here:

[http://arduino.cc/en/Main/ArduinoBoardDuemilanove](http://arduino.cc/en/Main/ArduinoBoardDuemilanove)

Apparently the bootloader uses C header files.

"Processing" is a C like programming language, which is one of the reasons why I call it cut down C. The other one is the limitations Processing has in comparison to C. 

Though those limitations are inconsequential for the purpose of programming the Arduino prototyping systems.

---

