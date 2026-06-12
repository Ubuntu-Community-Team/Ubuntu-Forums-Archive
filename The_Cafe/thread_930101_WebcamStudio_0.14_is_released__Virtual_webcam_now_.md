---
title: "WebcamStudio 0.14 is released : Virtual webcam now available for GNU/Linux!"
date: 2008-09-25
forum: The Cafe
---

### Post by patrickballeux on 2008-09-25
Hi people,

WebcamStudio for GNU/Linux 0.14 is now available on sourceforge.net

[CENTER][http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/")[/CENTER]


This software will let you create a virtual webcam like ManyCam does for Windows users.  There is a bunch of features and it is compatible with Flash site (using Flash 10)

I need more testers to validate the stability and make sure that is works well.

You do not need any webcam as you can simply broadcast your desktop, images or movies as a virtual webcam.

The project tries to give a fun and easy solution for the non-geek user to be able to broadcast in their own style.


Read the wiki for installation, you'll need the vloopback module from the Flashcam project to broadcast in a virtual webcam.  But without you can at least see the results in the preview display.

Thank you for your help!

Patrick Balleux
WebcamStudio for GNU/Linux creator

---

### Post by binbash on 2008-09-26
I was looking for this kind of software since 1999.I tested the application, it works perfect here (THO i didn't test it on IMs) .The only part i do not like is the java part ;)

---

### Post by jeyaganesh on 2008-09-26
Is it possible to spy other computers by installing this software? I am just asking in curiosity.:)

---

### Post by patrickballeux on 2008-09-26
Hi binbash,

Thank you for your comment.  It is appreciated.

It is done in Java because I am a good java coder and also, the graphics manipulations are so easy to do in Java using the Java2d libraries.  So it makes only one dependency instead of multiple dependencies with other kind of libraries.

Anyway, it is more a matter of taste than anything else :)  

Have you look in the options, you can apply the GTK style, making it blending with other GTK applications?

The next release will be awsome...  Keep looking on the wiki (or youtube) as I post regularly some preview of what's coming...

Patrick

---

### Post by patrickballeux on 2008-09-26
No, you cannot spy on others computer.

It creates a virtual webcam to broadcast on the internet.

Also, you are able to broadcast your desktop to show other what you are doing...

Pat

---

### Post by quinnten83 on 2008-09-26
please tell me this will work with IM's...

---

### Post by binbash on 2008-09-26
> **patrickballeux said:**
> Hi binbash,

Thank you for your comment.  It is appreciated.

It is done in Java because I am a good java coder and also, the graphics manipulations are so easy to do in Java using the Java2d libraries.  So it makes only one dependency instead of multiple dependencies with other kind of libraries.

Anyway, it is more a matter of taste than anything else :)  

Have you look in the options, you can apply the GTK style, making it blending with other GTK applications?

The next release will be awsome...  Keep looking on the wiki (or youtube) as I post regularly some preview of what's coming...

Patrick

YEs i can apply gtk style, that part rocks.BUT the GUI needs something cleaner.

Please send me a PM if you want me to test something special.

---

### Post by patrickballeux on 2008-09-26
It should as it is creating a V4L device using the vloopback driver from the Flashcam project.

I know that it is working with camstream as I use it for testing and with Flash site (using Flash 10, Flash 9 was giving me some trouble on amd64)...

It should work with aMSN and Skype, but I'll have to check compatibility as I did not validated.

---

### Post by patrickballeux on 2008-09-26
Hi binbash,

Just using it, trying different things and reporting what is not working will be great.  Please do so on the Sourceforge.net project as it will be easier for me to follow issues.

Thanks, and spread the word around!  The more, the merrier!

Also, I have a channel on Youtube and an account on blogTV.com where a do recording and live shows from time to time to show what is coming in the next release...

Visit : [http://www.blogtv.com/People/patrickballeux](http://www.blogtv.com/People/patrickballeux)

Have fun!

---

### Post by david_lynch on 2008-09-26
> **binbash said:**
> I was looking for this kind of software since 1999.I tested the application, it works perfect here (THO i didn't test it on IMs) .The only part i do not like is the java part ;) I like that it's written in java. That makes for better compatibility across releases, since it's not so tightly tied to system libs and kernel version. BTW binbash, some of the coolest software I use is java based - e.g. azureus (now vuze), the lotus notes 8.5 client, and others. 

Java: write once, run everywhere!

---

### Post by patrickballeux on 2008-09-26
Hi David, 

WebcamStudio for GNU/Linux is more write once, run on Linux only!

For now, it is incompatible with Windows or OSX because of the calls I do to the vloopback module using the JNA...

Eventually, I'll look to port it, but my first goal is to provide a fun solution for Linux users since we did not have anything like this for us.

---

### Post by patrickballeux on 2008-09-26
I've posted some more videos of what will be available in the next release...  Go see the wiki in the Example pages, or on blogTV where I do some live show from time to time...

[http://www.blogtv.com/People/patrickballeux]("http://www.blogtv.com/People/patrickballeux")

(There are also recordings to view if I am not online!)


Have fun!

---

### Post by binbash on 2008-09-26
> **david_lynch said:**
> I like that it's written in java. That makes for better compatibility across releases, since it's not so tightly tied to system libs and kernel version. BTW binbash, some of the coolest software I use is java based - e.g. azureus (now vuze), the lotus notes 8.5 client, and others. 

Java: write once, run everywhere!

Yes i agree with write once run everywhere BUT it is SLOW.Anyways lets stick to the application instead of java talk : ) Application is great i had more time to test.GTK style applies well.Please make the gui cleaner

---

### Post by david_lynch on 2008-09-26
> **patrickballeux said:**
> Hi David, 

WebcamStudio for GNU/Linux is more write once, run on Linux only!

For now, it is incompatible with Windows or OSX because of the calls I do to the vloopback module using the JNA...

Eventually, I'll look to port it, but my first goal is to provide a fun solution for Linux users since we did not have anything like this for us.
That's fine, linux is all I ever run anyway, except for some occasional mac usage. But java still makes porting a lot easier, that's for sure.

---

### Post by david_lynch on 2008-09-26
> **binbash said:**
> Yes i agree with write once run everywhere BUT it is SLOW.
Nah, you're stuck in the past if you think java is slow. It used to be really bad that way, but times have changed. The lotus notes 8.5 client is a java app, built on eclipse, and it starts up much faster (and is snappier) than the compiled, native windows version. IBM did a lot of performance work on it, but it goes to show that java code can be very fast if it's written correctly.

---

### Post by patrickballeux on 2008-09-27
I would add that Java 6 has a lot of features to use accelerated process now like native application.  WebcamStudio is using one of the feature in the Java 2D libraries wich give me access to the graphic card memory, making the compositing a lot faster then in the main memory.

You just have to know what to use and how to use it and you can be on par with a C++ application on a lot of processing.

Doing the same thing in C++ would have required a lot more knowledge and libraries.  You have to keep in mind that where you save in C++, you can loose on the complexity of the code (compared to java...).

Anyway, this is not the point of that thread...  Let's have fun!

---

### Post by binbash on 2008-09-27
I have one question (or suggestion) i am using Desktop as "output source" is there a way to let the software follow the mouse? Most windows applications does this.

---

### Post by Vadi on 2008-09-27
"Linux technologies that are not **avaialble** under Microsoft Windows." typo.

---

### Post by patrickballeux on 2008-09-27
> **binbash said:**
> I have one question (or suggestion) i am using Desktop as "output source" is there a way to let the software follow the mouse? Most windows applications does this.
For now, no it is not possible because there is no way to know (in java) the mouse position on your desktop.  Yeah, I know, Java could provide this kind of info.

Anyhow, there is still a way to do this by using recordMyDesktop as the X11 grabber, and saving live to a file pipe (See the wiki for using recordMyDesktop).

And then, you can use the file pipe as a source and show that in your webcam.

Actually, it works so well with recordMyDesktop that This is what I recommend.  The internal destop is available because it is easy to activate and available.

This is still a feature that I look to integrate one day.

Patrick

---

### Post by patrickballeux on 2008-09-27
> **Vadi said:**
> "Linux technologies that are not **avaialble** under Microsoft Windows." typo.

Thanks, I don't know why I always do that typo...  I am cursed with this word :)

---

### Post by binbash on 2008-09-27
Thanks for your kind and fast reply Patrick ;) I will check out the wiki

---

### Post by crirus on 2009-10-07
> **patrickballeux said:**
> Hi people,

WebcamStudio for GNU/Linux 0.14 is now available on sourceforge.net

[CENTER][http://webcamstudio.wiki.sourceforge.net/](http://webcamstudio.wiki.sourceforge.net/)[/CENTER]


 Patrick Balleux
WebcamStudio for GNU/Linux creator


Hello

I have a question about this scenario:

Your software installed on a linux server website.
A web interface to control it's settings.
Users visit the site, login, configure this remote virtual webcam, set their accounts for major streaming flash sites (ustream, justin.tv etc)
They push a button and start broadcasting their local source, through the server, through your software on flash sites?

How possible this is?

Thank you
Cristian Rusu

---

### Post by patrickballeux on 2009-10-12
The what you are looking for is Red5, not webcamstudio

---

### Post by dioltas on 2010-01-19
Hey, just came accross your software, and I really like it.

I'm using it under Arch linux with KDE. I didn't think there was software like this for linux. Good job!

Just wondering, does it create a virtual device in /dev that I can use as a source for programs like skype?

---

### Post by Mehall on 2010-01-19
> **david_lynch said:**
> Java: write once, run everywhere!

It may no longer be the slow, cumbersome beast it once was, but one old adage remains true:

Jave: write-once, debug everywhere.

---

