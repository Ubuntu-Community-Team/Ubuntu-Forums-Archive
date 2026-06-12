---
title: "How to install VMware player on Ubuntu 9.04 easy"
date: 2009-05-07
forum: Virtualisation
---

### Post by thomasr on 2009-05-07
Download the "bundle" from [http://www.vmware.com/download/player](http://www.vmware.com/download/player) to your desktop.

Right click on the downloaded file and select properties and select the permissions tab. Check the box labeled "Allow executing file as program.

Done.

Hope this helps someone - drove me crazy until I realized I had to make it executable.

---

### Post by islifeliberty on 2009-05-08
i downlaoded the VMware-Player-2.5.2-156735.x86_64.bundle file......but can u help with the installation pl.....i am using ubuntu 8.04

---

### Post by thomasr on 2009-05-08
Is your cpu a 32 bit or 64 bit processor? The x64 download isv fo 64 bit processors only.

---

### Post by buck2825 on 2009-07-02
ok i can't get this to install 

i ran 

sudo bash VMware-Player-2.5.2-156735.i386.bundle

the script runs fine when i run vmware player from applications - system tools - vmware player

i get an error

Before you can run VMware Player, several modules must be compiled and loaded into the running kernel.  and so on

---

### Post by buck2825 on 2009-07-04
found the solution I will have to post the fix when I'm back at the house.

---

### Post by RadarBat on 2009-07-04
Please post the procedure for installing "VMware-Player-2.5.2-156735.i386.bundle". I tried what thomasr posted, but it didn't work.

EDIT: This is for the "Player" that runs the Virtual Machines that you *have already created*. I need the application that you can "create" a VM and run it.  RB

---

### Post by NoFlags on 2009-07-09
@ buck2825; when are you back to your house? ;)

I got the same error but don't find any solution....

---

### Post by linsidious on 2009-07-15
Could you please post the solution... trying to put this on 8.04 as well and not budging...

Thanks!

---

### Post by thexder31 on 2009-07-30
Here's what I did.

1) Download the bundle from [http://www.vmware.com/download/player/download.html](http://www.vmware.com/download/player/download.html)
2) Enabled the permissions for executable... and double clicked on the file.  That failed.
3) Opened command window, and did sudo <file> and that failed.
4) Did chmod 755 *.bundle
5) Did sudo ./VMware-Player-2.5.2-156735.i386.bundle
6) That launched the installer.  

I haven't tried it yet, I have to get a playable image.  But since no one here appears to have gotten past install, I thought this might help someone.

spd.

---

### Post by ciscovip on 2009-08-14
I have completed the installation. However when I run the program i get prompted for a root password. How did you get around that?

---

### Post by bhavana on 2009-08-15
[FONT=Arial][SIZE=3]:)

[/SIZE][/FONT][FONT=Arial][SIZE=3]Greetings,

I found the solution on [/SIZE][/FONT][SIZE=3][http://stefan.waidele.info/2009/06/02/vmware-player-auf-ubuntu-904-jaunty-jackalope/](http://stefan.waidele.info/2009/06/02/vmware-player-auf-ubuntu-904-jaunty-jackalope/)[/SIZE][FONT=Arial][SIZE=3]. It worked on my system (9.04, 64bit). Its german, so here is the barebone translation:


[/SIZE][/FONT]
[LIST=1]
[*][FONT=Arial][SIZE=3]     Download the newest Version of VM Player ("*VMware-Player- 2.5.2-156735.x86_64.bundle*" in my case) after all that registering and ok-klicking...[/SIZE][/FONT]
[*][FONT=Arial][SIZE=3]     Next we have to make the downloaded file executable: [SIZE=4]**chmod a+x VMware-Player-2.5.2-156735.x86_64.bundle**[/SIZE] (you might rename it before, so you don't have to type all that numbers, I did so)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=3] ... and execute: [SIZE=4]**sudo ./VMware-Player-2.5.2-156735.x86_64.bundle**[/SIZE][/SIZE][/FONT]
[*][FONT=Arial][SIZE=3]     after the graphic (gui) installation you will find VMware Player the menu or you can start it via console: vmplayer (or vmplayer whatever.vmx, if already configured)[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=3] [I][SIZE=2]
May All Beings Be Happy[/SIZE][/I]
[/SIZE][/FONT]

---

### Post by parameter on 2009-08-16
> **bhavana said:**
> you might rename it before, so you don't have to type all that numbers, I did so

You don't have to rename it. Just type the first few characters and then press the tab key. The command line will complete the filename for you automatically.

---

### Post by searcoid on 2010-03-01
> **thexder31 said:**
> Here's what I did.

1) Download the bundle from [http://www.vmware.com/download/player/download.html](http://www.vmware.com/download/player/download.html)
2) Enabled the permissions for executable... and double clicked on the file.  That failed.
3) Opened command window, and did sudo <file> and that failed.
4) Did chmod 755 *.bundle
5) Did sudo ./VMware-Player-2.5.2-156735.i386.bundle
6) That launched the installer.  

I haven't tried it yet, I have to get a playable image.  But since no one here appears to have gotten past install, I thought this might help someone.

spd.

Thanks thexder31! Used step 1, 4, 5, 6 and now all is running smoothly! :D Used a recovery disk to install Vista on the VM, works fine, unlike other VM software I tried. Others were hanging at the beginning of the Vista install, but not this one.

---

