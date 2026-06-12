---
title: "ssh graphics problem"
date: 2011-11-16
forum: Server Platforms
---

### Post by eklikeroomys on 2011-11-16
Halo,

I'm using ssh to graphically work on a server. We're using electronics design and simulation software. I have no problem viewing most of the GUI on my local Ubuntu 10.10 machine. There is only one application that causes my system to hang every time I open it. This application is used for plotting waveforms. Is there a way to make the application operate normally without making my system hang? I'm now forced to use another plotting tool although it is more convenient and sometimes necessary to use the standard one. 

I prefer ssh over the remote desktop viewer. I'm really not sure what causes the hang, my suspicions are that it might be something to do with the graphics of the application.
Is there any way to force it to work properly?

Thank you.

---

### Post by eklikeroomys on 2011-11-16
It seemed like the problem was caused by Java applications, so I installed the OpenJDK Java 6 Runtime package but this doesnt seem to fix the problem....

---

### Post by Jonathan L on 2011-11-16
> I'm using ssh to graphically work on a server. We're using electronics design and simulation software. I have no problem viewing most of the GUI on my local Ubuntu 10.10 machine. There is only one application that causes my system to hang every time I open it. This application is used for plotting waveforms. Is there a way to make the application operate normally without making my system hang? I'm now forced to use another plotting tool although it is more convenient and sometimes necessary to use the standard one. 

I prefer ssh over the remote desktop viewer. I'm really not sure what causes the hang, my suspicions are that it might be something to do with the graphics of the application.
Is there any way to force it to work properly?Hi Eklikeroomys

Tricky without a bit more information ... but I'll have a guess!

Can you run any graphical application on the remote machine and have it display on your own computer?  xclock for example? 

The easiest way of doing this is to connect to your server with X forwarding enabled.  (You connect to your server with -X, which says to the server's ssh software: "please pretend to be an X11 display and send the X11 commands back to me"):
```
ssh -X username@servername

```See [man ssh]("http://manpages.ubuntu.com/manpages/lucid/man1/ssh.1.html").  (There are alternatives, which might be called "direct X11", but the ssh method is easy and good.  If you want to have direct X11, see [http://ubuntuforums.org/showthread.php?t=1623135](http://ubuntuforums.org/showthread.php?t=1623135))

Is that any use?

Kind regards,
Jonathan.

---

### Post by eklikeroomys on 2011-11-16
Hi Jonathan,

I already understand the ssh setup as you've explained above, the only difference is that I use ssh -Y username@servername. And I am successfully capable of running **most** graphical applications on the remote server. It is only certain applications which cause problems, and these are the ones that I am trying to get to work. 

I am not certain whether this has something to do with Java Runtime, graphics stack overflow, or how to make it work.

Thank you!

---

### Post by aeiah on 2011-11-16
does seem like a java problem. perhaps try using the non-free java locally, at least for a test?

can you poke around on the server and see what version of java it uses, or what java libraries the software relies on for drawing the gui?

if the server has vnc you could always put up with that. you can tunnel through ssh to make it secure.

---

### Post by eklikeroomys on 2011-11-16
Halo aeiah,

Well I am able to use vnc, but I dont like it. I like having the GUI open on my local desktop without working on the vnc desktop. 

On my machine: java version "1.6.0_20"
On the server: java version "1.6.0_05"

Could this be the issue?
How can I test the java on my machine?

---

### Post by Jonathan L on 2011-11-17
Hi again Eklikeroomys

> I already understand the ssh setup as you've explained above, the only difference is that I use ssh -Y username@servername. And I am successfully capable of running **most** graphical applications on the remote server. It is only certain applications which cause problems, and these are the ones that I am trying to get to work. [...]Ah good: as I said, I was guessing: it's clear that you have most of everything in place.

> There is only one application that causes my system to hang every time I open it. What's the application? Do you know whether you can get any java application to work and draw?  Or perhaps only some other applications.  Do you get any error messages at all?  And _which_ system hangs: the server (by which I mean the place where the app is running) or the client (by which I mean the one with the display) ?  Can you be more specific about the symptoms?  (Display freezes but computer still going, for example.)

Idea 1: Do you know if it gets as far as trying to open the X display?  You should be able to see these with xlsclients or a network trace (tcpdump or similar).

Idea 2: There are some subtleties to the way which ssh -Y works.  You might consider trying a direct X11 connection to your display.  (Ie, DISPLAY as client:0.0, xhost +server and so on) Do you know how to do that?

As your server is speaking X11 to your client, it doesn't matter what version of java you have on your client as you're not using it.  In any case I don't think the tiny difference of java versions would cause anything at all.

Kind regards,
Jonathan.

---

### Post by Jonathan L on 2011-11-17
Hi again Eklikeroomys

> How can I test the java on my machine?It's not an exhaustive test, but it's a great confidence check: download this demo from Sun (now Oracle), compile it and run it:
```
sudo apt-get install openjdk-6-jdk
wget http://download.oracle.com/javase/tutorial/2d/geometry/examples/ShapesDemo2D.java
javac ShapesDemo2D.java 
java ShapesDemo2D

```(NB if you've not compiled java programs: don't change the filenames.)

As this java program speaks X to your display, it makes no difference what java you have on your local machine.

My versions, on the server:
```
$ **java -version**
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.10) (6b20-1.9.10-0ubuntu1~10.04.2)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)
$ **javac -version**
javac 1.6.0_20
```This is from a 10.04 desktop client, ssh -Y to a 10.04 headless server (25 ms away!).

Produces the image attached (550 x 100 pixels): redraws if you resize it.

If for some reason you don't want to compile it yourself, I'll send you the class files, but of course you shouldn't be running programs from strangers!

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2011-11-18
I wouldn't think the java version on the client matters at all.  The application is running on the server and simply sending its screen output over ssh using the X protocol.

Can you actually sit at the server physically and run the application successfully?  Can you run it with elevated levels of debugging (a "verbose" mode) to see if you can diagnose any problems?

---

