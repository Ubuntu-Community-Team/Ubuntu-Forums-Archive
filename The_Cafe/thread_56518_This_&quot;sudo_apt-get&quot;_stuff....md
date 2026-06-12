---
title: "This &quot;sudo apt-get&quot; stuff..."
date: 2005-08-12
forum: The Cafe
---

### Post by xequence on 2005-08-12
Ive heard of this sudo apt-get stuff on here alot, and some other sudo thingys. Im figured out sudo gets you access to the admin stuff... It seems that you can do one command and it will update all your software, is that true? Do you type it into the terminal? Ive also heard about just doing a little phrase to download and install any program. How does it know where the program is located?

Thank you very much in advance. Again the linux community is really helpful :)

---

### Post by TravisNewman on 2005-08-12
it has online repositories where it gets the software. You can't just install anything with apt-get, but you can with dpkg.

See ubuntuguide.org for some basic information on how to use it, and some examples of things you can do with it.

---

### Post by xequence on 2005-08-12
Ok, thank you very much :) The site looks really helpful on first glance  :)

---

### Post by aysiu on 2005-08-12
This is what upgrades all your installed programs

[i]sudo apt-get update
sudo apt-get upgrade[/i]

The way apt-get knows where to find the programs is the /etc/apt/sources.list--it has a list of all the repositories to draw software from.

apt-get also has a graphical version called Synaptic Package Manager.

---

### Post by az on 2005-08-12
You can do anything from the command line.  Everything that you do from the graphical environment is just a way of making the graphical program call up the command line to get the real program to do the job.

This is unix.  Your graphics card and monitor are optional.  That is a very powerful starting point.  Sysadmins can get a great deal of work done without even being in the same city as the server on which they are working.

Just about everyting is a client-server deal.  What you see on your screen is put there by the X server (the graphics server).  Every window that appears is owned by a client application....

Welcome.

---

### Post by xequence on 2005-08-12
> This is unix. Your graphics card and monitor are optional. 

Ill stick with them, thank you very much :P

I love all this stuff, being able to take much more control of the OS then with windows. I just hope I can learn the basics in a good ammount of time. =D

And I also love the way the system (graphically) is so custonizeable.

---

### Post by DJ_Max on 2005-08-12
[QUOTE=xequence]Ill stick with them, thank you very much :P
[/QUOTE]
I believe he was referring to servers, and home networks, where there is no need to waste money on monitors, video cards. (or sound cards or extra keyboards for that matter).

---

### Post by GreyFox503 on 2005-08-13
[QUOTE=xequence]Ive heard of this sudo apt-get stuff on here alot, and some other sudo thingys. Im figured out sudo gets you access to the admin stuff... It seems that you can do one command and it will update all your software, is that true? Do you type it into the terminal? Ive also heard about just doing a little phrase to download and install any program. How does it know where the program is located?

Thank you very much in advance. Again the linux community is really helpful :)[/QUOTE]

I'm pretty new too, but I think I can answer some of this:

1) The 'sudo' command gives you temporary root privileges for exactly the one command in which you use it.  Its great because you can do small administrative things without ever switching to or logging in as root.

2) aysiu is right:

```
sudo apt-get update
sudo apt-get upgrade
```

these will update all the existing packages on your machine.

3) As for that little phrase:  It's very easy to install programs if you they're in one the repositories you're using, especially if you know the package name already.

```
sudo apt-get install *some_program*
```

That will download and install the program and anything it is dependent on.

If you know what you want, but you don't know the exact package name, or just something like "cd burner" then open up Synaptic (System > Administration > Synaptic Package Manager) and search for it.

---

### Post by fng on 2005-08-13
[QUOTE=GreyFox503]If you know what you want, but you don't know the exact package name, or just something like "cd burner" then open up Synaptic (System > Administration > Synaptic Package Manager) and search for it.[/QUOTE]

Or type apt-cache search 'searchterm' in a terminal

---

### Post by Lord Illidan on 2005-08-13
You might also want to look at the Ubuntu Guide, for more info:

[www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by WirelessMike on 2005-08-13
Definitely check out the guide, as Lord Illidan suggests...  If you have alot of superuser/root commands to perform, there are alternatives to typing "sudo" in front of every command (like root terminals).

For the record--  Ubuntu has a Linux kernel, which is a Unix clone, but not actually Unix (nor is it Posix, BSD, etc.).  I'm sure the point is that typical Unix commands work in Linux, though, so if you're familiar at all with Unix, there's not much of a learning curve here.  GNU = Gnu's Not Unix.

---

### Post by az on 2005-08-13
[QUOTE=xequence]Ill stick with them, thank you very much :P

I love all this stuff, being able to take much more control of the OS then with windows. I just hope I can learn the basics in a good ammount of time. =D

And I also love the way the system (graphically) is so custonizeable.[/QUOTE]


My point was not to tell you to get rid of your monitor.

You can update your system graphically by using the synaptic package manager.  My point was just to mention that typing is one command to upgrade your whole system is not a big deal.  The command line is very powerful.

---

### Post by xequence on 2005-08-13
> My point was not to tell you to get rid of your monitor. 

It was just my lame attempt at a joke :P

---

### Post by WirelessMike on 2005-08-13
[QUOTE=azz]The command line is very powerful.[/QUOTE]

Amen to that, brother!  You won't get that kind of utility from the Windows command line.  Oh--  It's useful, but as azz said, our command line is truly powerful!

---

### Post by xequence on 2005-08-13
> Amen to that, brother! You won't get that kind of utility from the Windows command line. Oh-- It's useful, but as azz said, our command line is truly powerful! 

Oh, that is just begging to be made into an image. The linux one beating the crap out of the windows one :P

---

### Post by Brunellus on 2005-08-13
[QUOTE=xequence]Oh, that is just begging to be made into an image. The linux one beating the crap out of the windows one :P[/QUOTE]

Windows doesn't even have a real commandline anymore.  

Command.com seems to be a shadow of itself these days.  

Anyway, how would you even represent two command-lines duking it out?

it'd have to be ASCII art...and I don't have the mad ASCII skills to do that.

---

### Post by xequence on 2005-08-13
[QUOTE=Brunellus]Windows doesn't even have a real commandline anymore.  

Command.com seems to be a shadow of itself these days.  

Anyway, how would you even represent two command-lines duking it out?

it'd have to be ASCII art...and I don't have the mad ASCII skills to do that.[/QUOTE]

Isnt the windows command line the little "run" thingy? And doesent the linux one look like a dos window thingy in windows? I dont know, but heh. It could be really cool :P And iconic. Like people using it in their desktop background, like tux. And there could be many different versions.

---

### Post by Brunellus on 2005-08-13
[QUOTE=xequence]Isnt the windows command line the little "run" thingy? And doesent the linux one look like a dos window thingy in windows? I dont know, but heh. It could be really cool :P And iconic. Like people using it in their desktop background, like tux. And there could be many different versions.[/QUOTE]
 nah.  the windows command line is the old-fashioned C:\ prompt you get when you dig around and look for "COMMAND PROMPT" or something to that effect.

If you really want to see what a real command line interface looks like, hit CTRL+ALT+F1 on your ubuntu box.  Don't worry, you can go back to GUI-land with a CTRL+ALT+F7.....

---

