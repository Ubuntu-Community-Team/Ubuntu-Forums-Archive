---
title: "[SOLVED] Ubuntu Server for an Absoloute Beginner"
date: 2008-10-02
forum: Server Platforms
---

### Post by dESAI on 2008-10-02
Greetings good people,

I've been using Ubuntu for a couple of months now. I love it. But I'm still a beginner, as I have problems using the command lines.

I've just installed Ubuntu Server 8.04, on a test machine.

It was with great disappointment that I discovered the command line interface. I was expecting a GUI.

I now stuck. 

I stress again that I'm a complete noob. I'm not used to working without a GUI.

I am hoping that there is a GUI that I can get access to. If not, I guess I'm going to have to start learning how to work with a terminal interface.


Is there a GUI?

If not, should I try a different version of a Linux Server that does have a GUI?

Can anyone recommend a place where I can learn the basics of using the terminal?

As I'm not good (and not happy) with using command lines, should I forget about using Linux?


Thanks everyone :D

D

---

### Post by mrtomservo on 2008-10-02
Really, the solution here is to learn how to use the terminal.  If you expect to have a functional server, you should expect to be using the terminal.  

You could add a GUI to Ubuntu server...  Check out this post for example:

[http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/]("http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/")

---

### Post by lykwydchykyn on 2008-10-02
I'm sorry, but you don't *have to* restrict yourself to the terminal to have a server, especially if it's a home server or you are a beginner.  That's ridiculous.  Sure, there are a lot of more advanced things that can't be done in a GUI, but let's be fair here.

desai, you can have a GUI very quickly:
```

sudo aptitude install xorg gdm gnome

```
If you don't have a very powerful server, you might install xfce4, fluxbox, jwm, or some other lightweight wm instead of gnome.

You should also look at webmin or ebox for administering your services.  They are both web-based guis, so you can just pull them up in a browser from your workstation to administer your server.

That said, it is a good idea to get comfortable with the command line and config files, especially if this is going to be a production server in a work environment.  But ease yourself into it, by all means.

---

### Post by mrtomservo on 2008-10-02
Lykwydchykyn is absolutely correct.

---

### Post by dESAI on 2008-10-02
> **lykwydchykyn said:**
> I'm sorry, but you don't *have to* restrict yourself to the terminal to have a server, especially if it's a home server or you are a beginner.  That's ridiculous.  Sure, there are a lot of more advanced things that can't be done in a GUI, but let's be fair here.

desai, you can have a GUI very quickly:
```

sudo aptitude install xorg gdm gnome

```
If you don't have a very powerful server, you might install xfce4, fluxbox, jwm, or some other lightweight wm instead of gnome.

You should also look at webmin or ebox for administering your services.  They are both web-based guis, so you can just pull them up in a browser from your workstation to administer your server.

That said, it is a good idea to get comfortable with the command line and config files, especially if this is going to be a production server in a work environment.  But ease yourself into it, by all means.

1,00,000 thanks! I'm so relieved, you have no idea!

Right now I just need to learn how to install software and scripts on this test server. But in the future I will have to maintain one in a professional environment, so I will try to learn the terminal code :)

For now, I have installed gnome, as you recommended :D

I've restarted, next I need to know how to access the GUI.

D

---

### Post by dESAI on 2008-10-02
> **mrtomservo said:**
> Really, the solution here is to learn how to use the terminal.  If you expect to have a functional server, you should expect to be using the terminal.  

You could add a GUI to Ubuntu server...  Check out this post for example:

[http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/]("http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/")

Thanks :)

I've installed gnome. I really am not comfortable using a terminal. So it's going to be really hard for me. But I will try.

:guitar:

---

### Post by Krupski on 2008-10-02
> **dESAI said:**
> Greetings good people,

I've been using Ubuntu for a couple of months now. I love it. But I'm still a beginner, as I have problems using the command lines.

I've just installed Ubuntu Server 8.04, on a test machine.

It was with great disappointment that I discovered the command line interface. I was expecting a GUI.

I now stuck. 

I stress again that I'm a complete noob. I'm not used to working without a GUI.

I am hoping that there is a GUI that I can get access to. If not, I guess I'm going to have to start learning how to work with a terminal interface.


Is there a GUI?

If not, should I try a different version of a Linux Server that does have a GUI?

Can anyone recommend a place where I can learn the basics of using the terminal?

As I'm not good (and not happy) with using command lines, should I forget about using Linux?


Thanks everyone :D

D

Learning the command line is (for some) a fun and rewarding challenge.

If you would rather not be bothered with the CLI, you can always install the "Desktop" version.

The desktop version is (dare I say it) Windows-like (i.e. it has a graphical interface, mouse support, familiar programs like Firefox, etc..)

Linux / Ubuntu SERVER is an OS designed for... servers. In addition to being internally optimized for memory and disk handling, server also lacks a GUI (which is worthless to a server).

Get and try Desktop Ubuntu... I think you'll like it.

-- Roger

---

### Post by jerome1232 on 2008-10-02
The main reason I encoruage the command line on a server is 99.99% percent of your configuration is just editing text files or access a web based gui, and 99% of your tuts on how to configure a server will be giving you command line instructions.

Hence not much of a benefit to using a gui

learn how to navigate the file system, copy, move files from a commandline and learn how to use vi are the main things you will want to learn.

nano will work but I've never seen a linux system that didn't have vi installed.

btw vi (vim) and nano are both commandline text editors, nano being easyier vi(m) being advanced.

With that being said feel free to run your server in anyway you please, this is just my advice :)

cheers.

---

### Post by Krupski on 2008-10-02
> **jerome1232 said:**
> The main reason I encoruage the command line on a server is 99.99% percent of your configuration is just editing text files or access a web based gui, and 99% of your tuts on how to configure a server will be giving you command line instructions.

I personally love the command line. I come from the days of home built wirewrapped computers, Commodore PET, Radio Shack Color Computer on up to today.

I learned computers on a command line, so I am comfortable there.

Some people, however, just want a DESKTOP that runs what they click on.

One of the reasons that MS Windows is so popular is that "any old dummy" (no insult intended to anyone) can use the computer without so much as knowing how to type "DIR" on a command line.

Lots of us love the command line... others are scared to death of it.

Ubuntu (and Linux in general) needs really to have two versions... a "hacker's delight" command line server and a "Runs out of the box GUI desktop".

In the world of Windows, what's the ratio of GUI users to command line users? Probably 99% GUI users... and Linux needs to appeal to the _majority_ if it ever wants to break out of it's niche.

---

### Post by dESAI on 2008-10-02
> **Krupski said:**
> Learning the command line is (for some) a fun and rewarding challenge.

If you would rather not be bothered with the CLI, you can always install the "Desktop" version.

The desktop version is (dare I say it) Windows-like (i.e. it has a graphical interface, mouse support, familiar programs like Firefox, etc..)

Linux / Ubuntu SERVER is an OS designed for... servers. In addition to being internally optimized for memory and disk handling, server also lacks a GUI (which is worthless to a server).

Get and try Desktop Ubuntu... I think you'll like it.

-- Roger

I've got 8.04 installed on my desktop, I love it! But I need a test server I can use for developing and testing a php script called Clip-bucket. The programmer will need remote access to the server.

I'm not a programmer, so I really need a GUI.

But it sounds like there is a GUI, that will meet my needs. I installed gnome, now I just need to know how to launch the GUI :D

---

### Post by dESAI on 2008-10-02
No that I've installed a Gnome GUI on the server, can someone please tell me how I can launch it?

Thanks all :)

---

### Post by dESAI on 2008-10-02
> **mrtomservo said:**
> Really, the solution here is to learn how to use the terminal.  If you expect to have a functional server, you should expect to be using the terminal.  

You could add a GUI to Ubuntu server...  Check out this post for example:

[http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/]("http://www.linuxquestions.org/questions/ubuntu-63/gui-for-ubuntu-server-463053/")

Thanks :) I've added the GUI, now I just need to know how to launch it. The link you provided has a way to launch it, but it's not working for me.

/etc/init.d/gdm start

---

### Post by jerome1232 on 2008-10-02
try:
```
startx
```

---

### Post by dESAI on 2008-10-02
> **jerome1232 said:**
> try:
```
startx
```

thanks, but it didn't work :(

it says i need to be root

---

### Post by MystaMax on 2008-10-02
```
 sudo startx 
```

OR

```
 sudo /etc/init.d/gdm start 
```

After entering one of the commands above, it'll ask for your password.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dESAI on 2008-10-02
> **MystaMax said:**
> ```
 sudo startx 
```

OR

```
 sudo /etc/init.d/gdm start 
```

After entering one of the commands above, it'll ask for your password.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

command not found :(

---

### Post by lykwydchykyn on 2008-10-02
Are you sure:
 - your xorg/gdm/gnome install went through without errors?
 - you're typing in lower case?

If nothing else, if gdm is installed it should launch on boot by default.  Have you tried restarting? (not the best method, but it works).

---

### Post by dESAI on 2008-10-02
> **lykwydchykyn said:**
> Are you sure:
 - your xorg/gdm/gnome install went through without errors?
 - you're typing in lower case?

If nothing else, if gdm is installed it should launch on boot by default.  Have you tried restarting? (not the best method, but it works).

Hey :)

Yes, I tried restarting. No luck.

I repeated the install and saw there was one error.

Next I booted with my desktop CD. Browsed to the folder, but it was not in there.

I'm now installing the full Ubuntu desktop on the machine. I was really not comfortable with the terminal like that. Normally I would persevere, but I don;t have time right now. 

I was really not expecting a CLI :D I've only worked in w2003 servers up to now.

So. Hopefully, I can either set it up to run the php script on it directly, or I can make a virtual server. 

I will read up on it all. Hopefully find some nice "installing ubuntu server" tutorials somewhere.
Or maybe get someone to install a server for me later.


Should I make another thread asking what is the best way to get a nice php dev environment setup?

1,000,000 thanks for your help :D 

Peace.

D

---

### Post by MystaMax on 2008-10-02
here ya go:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by dESAI on 2008-10-02
> **MystaMax said:**
> here ya go:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

And all this time I was just searching for the start of the path.

Thanks :D

---

### Post by jerome1232 on 2008-10-02
Actually you can use the desktop version the only differences are:


One comes with a desktop enviroment, the other doesn't

The server edition has a kernel optimized for being a server, you can install the server kernel in the desktop version.

Other than that they are identical, they both have access to the same software.

---

### Post by Ed1000 on 2008-10-04
Have you considered installing "webmin" for remote server administration?

[www.webmin.com](www.webmin.com)

---

