---
title: "Give me a program to make"
date: 2008-04-08
forum: The Cafe
---

### Post by saj0577 on 2008-04-08
Hey,

Im currently learning python and looking for someone who needs a basic program making. The reason is i can follow tutorials no problem but i find that the real learning is when making something and fixing problems.

So if anyone got any programs you want making let me know

Saj

---

### Post by Linuturk on 2008-04-08
I've been looking for a terminal based fianancial management application. Basically, gnucash on terminal only so I can login remotely and access my finances without having to use a graphical interface.

---

### Post by Bungo Pony on 2008-04-08
It might be beyond your abilities, but I need a good little program to send and recieve files through the serial port. I was using Cutecom until I found out it's a piece of junk - I can't recieve files with it. Not a good thing to discover when your laptop's hard drive is failing and getting files off is extremely time-sensitive. I had to boot into Windows and use Telix.

Just something simple using Zmodem is all I ask.

Oh yeah, and Minicom sucks too.

---

### Post by saj0577 on 2008-04-08
Okay then. Il give it a go cheers. :D

Saj

---

### Post by SZF2001 on 2008-04-08
For the love of God, make some wireless drivers, make them universal.

I don't care what YOU want, it's what **I** want!

(I'm just kidding)

Seriously you should make some game where you bounce balls around and you can change the gravity against the corners of the box the ball is in or something.

---

### Post by saj0577 on 2008-04-08
KK Cheers. lol thats the goal eventualy get some drivers working bu tthat will take time. Im learning :)

Saj

---

### Post by bobbocanfly on 2008-04-08
Something simplish to start off with is a Rot 13 encoder/decoder or a Bubblesort algorithm. Both are pretty easy in Python.

---

### Post by saj0577 on 2008-04-11
> **bobbocanfly said:**
> Something simplish to start off with is a Rot 13 encoder/decoder or a Bubblesort algorithm. Both are pretty easy in Python.

Anyone got any help on this one. I have googled around and its all just examples of the code which does not help (unless your a copy and paster) where as I want to understand whats going on each step of the way.


Cheers
Saj

---

### Post by Zdravko on 2008-04-11
> **saj0577 said:**
> 
So if anyone got any programs you want making let me know
You can take a look at a project I am currently trying to shape: [http://ubuntuforums.org/showthread.php?t=750344](http://ubuntuforums.org/showthread.php?t=750344)
It is about a free web hosting service for us ;)

---

### Post by Steveway on 2008-04-11
You could sign up at project euler and try to solve the problems there.
It's pretty funny and you really get to learn things.

---

### Post by saj0577 on 2008-04-11
> **Steveway said:**
> You could sign up at project euler and try to solve the problems there.
It's pretty funny and you really get to learn things.


Link please so i can find out more.


Saj

---

### Post by Steveway on 2008-04-12
> **saj0577 said:**
> Link please so i can find out more.


Saj

Sure, here: [http://projecteuler.net/](http://projecteuler.net/)

---

### Post by hessiess on 2008-04-12
fix Blendrs .x exporter

---

### Post by elmer_42 on 2008-04-12
I think that is too advanced for him. Hell, I am about the same level as him, but I gave up earlier than he.

---

### Post by BluntBox on 2008-04-12
> **Steveway said:**
> Sure, here: [http://projecteuler.net/](http://projecteuler.net/)

Oooh, glad I read this thread, some good late night problem solving to be had there!

---

### Post by Ioky on 2008-04-12
you can help up out to make the game I am making

---

### Post by BanskuZ on 2008-04-12
I'm having the same problem as well. I just discovered wxPython and I would love to do something, but I'm lacking ideas! I know I could code useless calculators, but I hate creating things that nobody will ever use. It's so pointless and boring.

---

### Post by rastari on 2008-04-12
there should be more interesting and useful programs for programmers to cut there teeth on more people would get to an advanced level that way as most people get bored with the early simple programs and give up, any ideas on helping people learn how to program the practical way it'd help this guy as well

---

### Post by elmer_42 on 2008-04-12
Wow. That Project Euler link looks awesome! I am going to seriously try that when I get home.

---

### Post by saj0577 on 2008-04-12
What about we all work together and make a big project, and help each other out that way we may be able to create something useful and learn along the way with peer support?

Saj

---

### Post by elmer_42 on 2008-04-12
That's a good idea, but then every part would have to be modular. That's a good thing, but makes it harder to code. What program would be made, though?

---

### Post by az on 2008-04-12
Here is my suggestion for a relatively easy program.

It would be great to make a USB live cd installer.

Basically, the USB image for a live cd can be made this way:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch#head-78b0db78435f28e95edbd38e14148a42c1dc4e00](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch#head-78b0db78435f28e95edbd38e14148a42c1dc4e00)

But then, to "burn" the image to usb stick, you need to run

sudo zcat usbimage.gz > /dev/sdc1

Making a self-extracting archive in linux is super-easy:

[http://gnubie.blogspot.com/2006/04/uhow-to-how-to-create-self-extracting_22.html](http://gnubie.blogspot.com/2006/04/uhow-to-how-to-create-self-extracting_22.html)

It would be great to make a self-extracting stub that can run 
sudo lshw -C disk short

and take the output and find USB drives.  Then offer the user the choice of what drive to write the image to.  The user would pick the USB drive that they want to put the image on, and then the installer would unzip the image to the first partition.

If you have never booted from the USB drive before, it needs to have an MBR written to it.  That too is simple and could be handled by the script.  

More advanced features would be to make the script offer to create a separate partition on the device for the space left over after the image is written to it.  You can use that partition for a persistent home.

---

### Post by elmer_42 on 2008-04-12
That seems a more suitable task for a shell script if you ask me. I mean, you could do it in Python, but you would probably just end up running the same commands you would run in the terminal.

---

### Post by swoll1980 on 2008-04-12
a lexmark 5270 driver

---

### Post by CostaRica on 2008-06-07
AmigoI too late to say that I have been trying to make an ERP for my store in python and wxGlade for a long time? I Am too making progress in this areas but still need some help.  It IS a really inreresting project since I already have the data model, know how to connect to PostgreSql and it would be the GUI and signals part I would need help with. We can buiLd it together and learn in the process from one another.

---

### Post by banjobacon on 2008-06-07
How about a plugin to improve? The [Quod Libet plugin for Musicbrainz lookup]("http://www.sacredchao.net/quodlibet/wiki/Plugins") works well, but it doesn't apply the date or genre tags.

---

### Post by Changturkey on 2008-06-07
+1 for Music Brainz. Or make a Youtube Video Downloader/Converter (to Ipod/MP3 Players). I dunno?

---

