---
title: "Server or Desktop?"
date: 2006-04-16
forum: Server Platforms
---

### Post by Axrst on 2006-04-16
Hi.

I was using linux back in '95. But now, I have forgot the most of things i used to do then...

I need a server for our new wireless network, and I was told that ubuntu is a good, stable and friendly linux. So, i decited to install it. 

My questions are:

Should I have to install server (I need basic networking server services) or desktop? Security is not a priority at this time, because we will use the server when I'm ready to manage it.

I mean, I would like to have server, but if i need, to be able to run xwindows.  I read somewere to do:

sudo aptitude install ubuntu-desktop

ok, but then, how do i run the x?

Or, is more preferable to make a normal, desktop installation and start then, making some changes to the system to make it run like a server? Installing the xwindows after the server install, is installing all the easy tools that has the desktop version?

Sorry for my "newbie - mode" :-P

Chris.

---

### Post by cilynx on 2006-04-16
To the best of my knowledge, the only difference is that 'server' doesn't install the GUI.  Installing 'ubuntu-desktop' on top of a 'server' install will take you to the same point you would, have been had you done the 'desktop' install in the first place.  It will automagically set up GDM and drop you to a graphical login.  It's pretty much up to you which way you want to go.

---

### Post by chrisjs162216 on 2006-04-16
Yes, the Desktop version is just a GUI version of the Server version.  I just installed KDE without many problems by simply typing sudo apt-get install xserver-xorg and after it finishes, type 'sudo apt-get install kde' (ot gnome) but try to make sure you have a high speed internet connection, it's about 200 megs I think....or is it a total of 200 once installed?  Maybe it's 50 Megs to download.....

I think it's 50 Megs to download :)  Regardless, simply let it install through the night, because it takes a while.

---

### Post by Axrst on 2006-04-17
Thanks for your answers.

I want to boot my machine in console mode, and if I need to run X, to be able to do it (and of course after that to be back to console). Is this possible, and how?

The package of Gnome is not included in server iso? Do I have to download it? I think that must be in the desktop (install cd).

Chris.

PS. I didn't find a very usefull tool I used back in '90s. Midnight Commander. Is somewhere or, is there any other program like this?

---

### Post by cilynx on 2006-04-17
Gnome is not installed when you do a 'server' install.  The packages are still on the CD and are available in the online repositories.

Man, 'mc'....that brings back memories.  Yeah, it's still around.  Just install the 'mc' package and you're there.  I doubt you'll need it though.  Graphical file management has come a long way on *nix since the 90's..

Gnome and console are not mutually exclusive.  First off, you can run terminals inside of Gnome.  Secondly, you can alway get back to a real VC by doing a ctrl-alt-F1 or whatever F# console you want.  By Ubuntu default, 1-6 are VC's.  7 is where your GUI is running.

---

### Post by peanut butter on 2006-04-17
i think he ment is that he dosn't ant a gui hogging system resources. tell me if im wrong. ihave  actuallywondere if there is a way to not start x on startup.

---

### Post by Axrst on 2006-04-18
[QUOTE=peanut butter]i think he ment is that he dosn't ant a gui hogging system resources. tell me if im wrong. ihave  actuallywondere if there is a way to not start x on startup.[/QUOTE]

Exactly. I want (if it's possible) to not start X at boot time. Only if I need it to run it, and close it when I'm done, without shuting down my pc. Any ideas on it?

Chris

---

### Post by Axrst on 2006-04-18
[QUOTE=cilynx]Gnome is not installed when you do a 'server' install.  The packages are still on the CD and are available in the online repositories.[/QUOTE]

Thanks, I'm installing it now.

[QUOTE=cilynx]Man, 'mc'....that brings back memories.  Yeah, it's still around.  Just install the 'mc' package and you're there.  I doubt you'll need it though.  Graphical file management has come a long way on *nix since the 90's..[/QUOTE]

Yeah. mc rulez :p 

As I said in my previus post, I' ll need it, because I dont want my system to start with X. It's loss of resources. I prefer to boot to console mode, doing my work there, and, if I need it, to run it. Is this possible and how?

Thanks,

Chris.

---

### Post by cilynx on 2006-04-18
Basically, you don't want to run a display manager.  Back in the day, you had to type 'startx' to get it running, and when you logged out of the GUI, that was it, you were on a console.  Then XDM, GDM, KDM, etc.. came along.  I don't know how off the top of my head, but you need to disable your display manager.  That way, you can start and stop X when you want.

---

### Post by Digital Alchemist on 2006-04-18
I recently installed Ubuntu with the server option and then installed xubuntu ([link to wiki]("https://wiki.ubuntu.com/Xubuntu")) in one of the servers here at work (currently using as a test server), and I have to say, it works great and **fast**.


PS: Dont install GDM or KDM if you want to boot to a text login and do startx to enter XFCE.

---

### Post by jinacio on 2006-04-18
[QUOTE=Digital Alchemist]I recently installed Ubuntu with the server option and then installed xubuntu ([link to wiki]("https://wiki.ubuntu.com/Xubuntu")) in one of the servers here at work (currently using as a test server), and I have to say, it works great and **fast**.


PS: Dont install GDM or KDM if you want to boot to a text login and do startx to enter XFCE.[/QUOTE]

imho XFCE is the way to go for a light and fast desktop, and it is very usable, recommended!

---

### Post by Axrst on 2006-04-19
I finally found what to do.

You have to change the runlevels. Allthought was very diferent from what I new, I finally figured out the right way.

Well, in **/etc/rc2.d/** you must rename the file **S13gdm** in anything you want (eg **.S13gdm**)

That file runs **../init.d/gdm** and without it, you boot in console mode. Then, if you want you run **startx** to start the Xwindow system, and if you want to go back to the console, you simply logout.

Chris.

---

### Post by dannysauer on 2006-04-19
[QUOTE=Axrst]Well, in **/etc/rc2.d/** you must rename the file **S13gdm** in anything you want (eg **.S13gdm**)[/QUOTE]

Kinda.  Ubuntu uses System V style init scripts (as do most modern Linuxes), where you have a folder full of scripts, and folders for each runlevel.  In each runlevel folder are symlinks to the actual script in init.d.  Symlinks start with an S to start and a K to stop.  The number after the script specifies the starting order, because they're launched basically as "for F in S*; do $F; done" and the numbers force a sort order.

So, to stop somthing from running, you want to remove the script in each relevant runlevel (and typically the K script, as there's no sense stopping a script at shutdown if it wasn't started).  There are a few frontends which make it easier, including "sysv-rc-conf".  Just "apt-get sysv-rc-conf" and then run sysv-rc-conf.  It doesn't remove the K links, for some reason, but it does get you a nice clean little curses interface to what's otherwise a minor pain from the command line.  Webmin has a runlevel manager, too - and webmin can be kinda handy on a headless server, if you often admin said server from a machine with a web browser.

Renaming the script to start with something other than an S will also stop it from running, but really isn't the "right" way. ;)

---

### Post by gymsmoke on 2006-04-20
It would be really helpful if you would spec which version of Ubuntu you are working with... "Server" install option  isn't in 5.10, so my assumption is you're talking about Dapper.. They've recently added a LAMP install to the menu...

My personal thoughts are, if you want a server, install a server.  Administer the system as an administrator, not as a user.  Add GNU Screen if you want virtual terminals, but leave the X server off.  Unless your box is physically able to handle the resources required to run both as a server and a workstation (yikes)... I would use the server for what it was intended for.

---

### Post by Axrst on 2006-04-20
Thanks for your answers, they're very interesting.

I use Dapper. Allthought my machine _is_ able to handle the resources required to run both as a server and a workstation, I also would like a server only version. But sometimes I need, to browse the internet, to use GUI for some task, and I want to be able to.

The other thing I'm  missing is a command line multi tool like Midnight Commander. I installed it after some time, but It canot draw lines, (i tryied enought options in ./configure) and is anoying. I need a tool that can edit easyly (no other vi ](*,)  ), copy, move, rename, exctrect etc with the ease of the GUI. Any ideas?

Chris.

---

### Post by jinacio on 2006-04-21
[QUOTE=Axrst]
The other thing I'm  missing is a command line multi tool like Midnight Commander. I installed it after some time, but It canot draw lines, (i tryied enought options in ./configure) and is anoying. I need a tool that can edit easyly (no other vi ](*,)  ), copy, move, rename, exctrect etc with the ease of the GUI. Any ideas?
[/QUOTE]

Did you download the src from somewhere? why not just "sudo apt-get install mc"?

it works fine here...

---

### Post by Axrst on 2006-04-22
[QUOTE=jinacio]Did you download the src from somewhere? why not just "sudo apt-get install mc"?

it works fine here...[/QUOTE]

It's says: "couldn't find package mc".

So, I downloaded the source, and did the rest with no good results.

Chris

---

### Post by rso on 2006-06-09
I think bum might be easier to use, see:

[http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html)
you can install it with:

sudo apt-get install bum

you need gnome to disable gnome though (;

---

### Post by viniosity on 2006-06-12
I've got the opposite issue: I installed the desktop off the live cd and now I want to free up some memory b/c I'm using it as a server.  Are there packages I should uninstall or is there any easy command to run to get it to not start x at boot?

---

### Post by LordHunter317 on 2006-06-13
You can stop X by running 'sudo /etc/init.d/gdm stop'.  Remove the symlink in /etc/rc2.d to prevent it form running at boot.

But if you never use X, it won't really consume that much in resources.  Moreso than other applications, but not much (because it has locked pages that can never be paged out).

---

### Post by DanielArdelian on 2006-06-14
[QUOTE=Axrst]It's says: "couldn't find package mc".

So, I downloaded the source, and did the rest with no good results.

Chris[/QUOTE]

mc (Midnight Commander) is in the Universe repository. You have to edit /etc/apt/sources.list to activate that, then do an apt-get update, then apt-get install mc.

If mc doesn't look good on the screen or through an SSH client, try starting it with "mc -a".

---

### Post by Indifferent on 2006-06-14
I installed the server first, then Xubuntu and it boots to the console. I have to manually start the GUI, which is what I also wanted.

---

### Post by popper on 2006-07-28
> **DanielArdelian said:**
> mc (Midnight Commander) is in the Universe repository. You have to edit /etc/apt/sources.list to activate that, then do an apt-get update, then apt-get install mc.

If mc doesn't look good on the screen or through an SSH client, try starting it with "mc -a".

thanks, that might help.

a question though given that you start with the server iso
[http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/ubuntu-6.06-server-powerpc.iso](http://www.mirrorservice.org/sites/releases.ubuntu.com/6.06/ubuntu-6.06-server-powerpc.iso) it seems strange that MC wasnt included as standard.

its been a very long time since i learned linux and cant remember a shell/cli editor that is def included in all the platforms or its load/edit/save&quit commands, anyone care to refresh the new readers of this thread so they dont need to jump about looking for the answer?.


mc is good for the cli , does worker exist in the universal (ppc) area or am i going to have to compile it?.

on that note what is the command to setup a working compiler

sudo apt-get install ? , and is it included in the base or do we need to add the universe and edit it by hand before we get that far?.

---

### Post by popper on 2006-07-29
apparently to install a compiler its
sudo apt-get install build-essential
and to install the headers its
sudo apt-get install linux-headers-$(uname -r)

anything else iv missed

and worker , a great gui filemanager by the way, is also in the universe once you edit the file.

---

