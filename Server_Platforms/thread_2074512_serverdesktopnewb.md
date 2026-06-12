---
title: "server/desktop/newb"
date: 2012-10-21
forum: Server Platforms
---

### Post by rdeeds on 2012-10-21
i installed the desktop version of ubuntu and am interested in learning about the server side of things. i am new to ubuntu and to linux in general but i find it far batter than windows already and am dying to learn more and more. i would like to eventually host a website on my computer as well, so i know i need to be able to use the server side of it. can anyone help me figure things out? i don't really know anything about it so i don't know what to ask...if anyone can be a friend and possibly all around mentor for ubuntu/linux i would greatly appreciate it.

---

### Post by arrrghhh on 2012-10-22
Well I would start small - which it sounds like you've done.  You can run ALL the same services on an Ubuntu Desktop system as you can an Ubuntu Server edition.  The main difference between the two versions is Ubuntu Desktop includes a point-and-click interface (GUI) and all the applications that go with that GUI, and Ubuntu Server does not.  Command-line only.

So for starters, most do begin with Ubuntu Desktop.  You can run an apache, lighthttpd, whatever web server you want to run on Ubuntu Desktop just as you can for the Server edition.

While I do encourage you to use the command-line tools to start getting used to them, I wouldn't recommend throwing yourself into a command-line only environment right away.  Once you get comfortable with it, spool up a VM of Ubuntu Server and see if you can get it setup to how you like it.  Then you can apply the concept to whatever system is your 'production' system if you will.  That's what I did at least - learned how to get comfy with the Linux command-line utilities/commands before putting myself in a command-line only environment.

Good luck!

---

### Post by Starcruiser322 on 2012-10-22
You CAN install a GUI environment into the server edition using a command like this:
*sudo apt-get install ubuntu-desktop*
keeping in mind that this will consume considerable space on your hard disk.

I recommend you become familiar with the regular desktop environment before you try to work on the server. I saw my CCNA professor freeze once he saw that I was using my command-line server over the school's connection as a DNS server to speed up everyone else in the room...

I also recommend that you find out exactly what is working out of the box and what is not, and ask around to find what you need to download for each that is not working. This especially goes for wireless cards, if you have one.

Get used to using the terminal instead of the GUI. The GUI does not always work, so knowing the equivalent terminal commands can save your system.

---

### Post by arrrghhh on 2012-10-22
> **Starcruiser322 said:**
> You CAN install a GUI environment into the server edition using a command like this:
***sudo apt-get install ubuntu-desktop***
keeping in mind that this will consume considerable space on your hard disk.

[size=4]DO NOT DO THIS!!!![/size]

If you apt-get install the ubuntu-desktop meta-package onto the Server install you've basically installed ALL of the packages necessary for the full blown Ubuntu Desktop system - rendering your Server install quite pointless, as you may as well just install Ubuntu Desktop from the beginning...

Now if you install it with --no-recommends or perhaps go with LXDE - and just install a window manager/desktop environment... Again, if you go with the full ubuntu-desktop package you get OpenOffice, and a lot of other junk that you probably do not want on your server install.  Worst part is you can't easily revert - purging the ubuntu-desktop meta-package will NOT get you back into a state before, unfortunately...

---

### Post by Starcruiser322 on 2012-10-22
Oops, I did mean to put a --no-recommends on there, thanks for pointing that out! If you failed to put that you would have ~1GB extra crap you don't need on a server!
Also, the ubuntu-desktop package isn't very suited for the server anyway, the xubuntu package is much better for the server IMO

---

### Post by rdeeds on 2012-10-22
I have already started trying to learn the command-line. but so far I have only been able to use codes like apt-get install, apt-get clean, apt-get update, apt-get upgrade, and i created a new user. other than that i don't know much about using command line and i can't think of ways to force myself to learn more as i don't do much. i.e. programming or anything. any suggestions on how to learn more commands?

---

### Post by Starcruiser322 on 2012-10-23
There are some useful server commands here:
[http://www.techcuriosity.com/resources/linux/linux_server_administration_commands.php](http://www.techcuriosity.com/resources/linux/linux_server_administration_commands.php)

There's a fairly good list of basic good-to-know commands here:
[http://h30565.www3.hp.com/t5/Feature-Articles/The-16-Linux-Shell-Commands-Every-Desktop-Linux-User-Should-Know/ba-p/3093](http://h30565.www3.hp.com/t5/Feature-Articles/The-16-Linux-Shell-Commands-Every-Desktop-Linux-User-Should-Know/ba-p/3093)

---

### Post by snowpine on 2012-10-23
This guide will get you up and running with basic Ubuntu Server concepts: [https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

---

### Post by rdeeds on 2012-10-23
thank you all for your help

---

### Post by Be1 on 2012-10-24
I advise you to use the info command to learn more about the options. For example:  in the terminal, write: info apt-get 
You will get a description and all the options of this command.
I hope this is usefull but I don't feel that I know enough about Ubuntu that's why I retain myself from contributing to this forum :)

---

