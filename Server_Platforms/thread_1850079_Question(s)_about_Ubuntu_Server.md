---
title: "Question(s) about Ubuntu Server"
date: 2011-09-25
forum: Server Platforms
---

### Post by Mistertuxedopants on 2011-09-25
hello,

I currently have Ubuntu Server 11.04 installed. I enjoy the command line and use it to program all the time. I have never used server tho, i have always used to desktop. I am still getting used to server. What i want to know is:

Is there a way to install the desktop part and only switch to it when I need to. basically I want it to be server and only switch to desktop temporary. when it boots it boots in to the command line.

if that makes any since?

thanks
MTP

---

### Post by haqking on 2011-09-25
> **Mistertuxedopants said:**
> hello,

I currently have Ubuntu Server 11.04 installed. I enjoy the command line and use it to program all the time. I have never used server tho, i have always used to desktop. I am still getting used to server. What i want to know is:

Is there a way to install the desktop part and only switch to it when I need to. basically I want it to be server and only switch to desktop temporary. when it boots it boots in to the command line.

if that makes any since?

thanks
MTP

you can install the desktop with:

```
sudo apt-get install ubuntu-desktop
```

if you edit your grub and find this:

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
```

and change to 

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash text&#8221;
```

then update 

```
sudo update-grub
```

this will then only boot into CLI/Console mode

Edit: actually thinking about it you say you have server 11.04, it might be a little different for the grub entries, not sure on that one

see here to suit 11.04 [http://ubuntuguide.net/add-a-grub2-entry-for-ubuntu-booting-into-consolecommand-line](http://ubuntuguide.net/add-a-grub2-entry-for-ubuntu-booting-into-consolecommand-line)

---

### Post by Mistertuxedopants on 2011-09-25
i am sorry, i am a n00b when it comes to this.. i still don't understand

---

### Post by haqking on 2011-09-25
> **Mistertuxedopants said:**
> i am sorry, i am a n00b when it comes to this.. i still don't understand

didnt you say you love the command line and program ?

anyways...if you want to install the desktop then as i said above

```
sudo apt-get install ubuntu-desktop
```

thats it.

If you dont want to boot into the DE everytime then edit your grub as outlined above.

---

### Post by Mistertuxedopants on 2011-09-25
so once i install desktop as you said and change the file ubuntu server will still boot up as it originally did?

My next question is

lets say i am working away in the console and i need to get into the desktop environment, how do i get there?

---

### Post by haqking on 2011-09-25
> **Mistertuxedopants said:**
> so once i install desktop as you said and change the file ubuntu server will still boot up as it originally did?

My next question is

lets say i am working away in the console and i need to get into the desktop environment, how do i get there?

```
etc/init.d/gdm start
```

---

### Post by haqking on 2011-09-25
> **haqking said:**
> ```
etc/init.d/gdm start
```

however you can always just boot into the GDM and then drop to a console with ctrl+alt+f1-f6

then ctrl+alt+f7 to return to GDM when you want

---

### Post by Mistertuxedopants on 2011-09-25
Yea, I prefer the console/CLI to boot first, I will try your command to get me into the GUI. Let say i am in the GUI finish up what i was doing can i go back to the Console by doing etc/init.d/gdm stop?

Oh, and thank very much for all your help

---

### Post by haqking on 2011-09-25
> **Mistertuxedopants said:**
> Yea, I prefer the console/CLI to boot first, I will try your command to get me into the GUI. Let say i am in the GUI finish up what i was doing can i go back to the Console by doing etc/init.d/gdm stop?

Oh, and thank very much for all your help

yeah though not the cleanest way to do things.

you will need to append sudo to the action aswell.

no worries

---

### Post by Entilza on 2011-09-26
> **Mistertuxedopants said:**
> Yea, I prefer the console/CLI to boot first, I will try your command to get me into the GUI. Let say i am in the GUI finish up what i was doing can i go back to the Console by doing etc/init.d/gdm stop?

Oh, and thank very much for all your help

You can also run "startx" at the command line without running gdm it will not restart itself after logging out of the gui which I think you are looking for.

---

### Post by Mistertuxedopants on 2011-09-27
> **Entilza said:**
> You can also run "startx" at the command line without running gdm it will not restart itself after logging out of the gui which I think you are looking for.

hey, 

this is interesting. How do I go about using this startx. Could you please give me an example please

---

### Post by haqking on 2011-09-27
> **Mistertuxedopants said:**
> hey, 

this is interesting. How do I go about using this startx. Could you please give me an example please

if you are at cli and Xserver is configured then just:

```
startx
```

just type it and it will being a new X (graphical session)

similar to the gdm start option

---

### Post by Mistertuxedopants on 2011-09-27
> **haqking said:**
> if you are at cli and Xserver is configured then just:

```
startx
```just type it and it will being a new X (graphical session)

similar to the gdm start option

so for this to work i would need ubuntu-desktop installed.

How do i know if xserve is configured correctly?

and when i want to end the graphical session what is command for that stopx (shot in the dark)

thanks!

---

### Post by Mistertuxedopants on 2011-09-27
anybody?

---

### Post by haqking on 2011-09-27
> **Mistertuxedopants said:**
> anybody?

startx will start the Xserver, if it is not set up it will tell you so and then you can configure it.

to end the graphical sessoin you can log out or drop to a console/runlevel

using X to start then stop doesnt really work like that.

if i was you i would use what i suggested before

```
etc/intit.d/gdm start
```

```
etc/init.d/gdm stop
```

if you want a command to do it.

I mean you could use kill with x.

but its kind of weird way to do things.

set it not to go into gui

gdm start

then gdm stop if you need to

---

