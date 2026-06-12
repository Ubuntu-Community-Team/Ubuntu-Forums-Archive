---
title: "New LTSP isntallation"
date: 2011-02-28
forum: Server Platforms
---

### Post by xpertuse on 2011-02-28
I just finished installing LTSP on a 10.04 server.
I tried to log in with a diskless PC.
The logon screens come successfully but when I am putting the user name and password a terminal window opens at the top left of the screen.
I have added a test user with adduser command.
How I am suppose to log in and load the graphical desktop?
Or because I have installed Ubuntu 10.04 server edition I will never get a graphical desktop???

Thanks in advance.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-28
Okay, first, chances are your gonna have to rebuild your images from the ground up, or you could chroot to the LTSP root folder and add packages through there.
To do the chroot, login to the server and type:

sudo su

Then were gonna wanna chroot to the ltsp chroot:

chroot /opt/ltsp/i386 
(/opt/ltsp/amd64 if you built the chroot for amd64 based systems)

Now we have to mount /proc in the chroot:

mount -t proc proc /proc

Now to update apt for our packages:

apt-get update

And finally we install ubuntu desktop:

apt-get install ubuntu-desktop

Now to update our packages:

apt-get dist-upgrade

Heres where you exit the chroot:

exit

Now to update our LTSP kernels:

ltsp-update-kernels

Now unmount /proc:

sudo umount /opt/ltsp/i386/proc

Now update out LTSP image:

ltsp-update-image

To exit sudo just type:

exit

:)

Thats the hard way, if you have nothing to reconfigure in your setup, i recommend to do this:

Create this file:

/etc/ltsp/ltsp-build-client.conf

Within this type:

# For 64-bit clients change this to ARCH="amd64" etc.
ARCH="i386"
# For edubuntu change to FAT_CLIENT_DESKTOP="edubuntu-desktop"
FAT_CLIENT_DESKTOP="ubuntu-desktop"
LATE_PACKAGES="
   gimp
   flashplugin-nonfree
"

Now save the file and run:

ltsp-build-client --purge-chroot

and your done :)
For more help visit:

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

And for more config file options:

[https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)

This should work :)

---

### Post by xpertuse on 2011-02-28
Thank you very much for your answer.
I'll try it first think tomorrow.
To be sure I understand correctly, if I had installed LTSP on an ubuntu desktop and not on a server I wouldn't have to do that. Correct?
After this configuration I will have fat clients instead of thin? I.e. local hardware dependable?

---

### Post by headvampyre@hotmail.co.uk on 2011-02-28
Yeah, if you used ubuntu desktop you wouldnt have to do this, im stabbing in the dark at what i do to change desktop environment, but it should work :) I actually run my LTSP servers off an ubuntu desktop machine, but i used to deploy kubuntu instead of Gnome :)
As for hardware - im not entirely sure, i assume the server still processes everything, just with the added desktop environment, but ill look into that for you. As for hardware dependance, any THIN client should still be capable of running the desktop nvironment locally anyway, which would also take some strain off the server allowing for more clients :) if that doesnt work, just install the dektop edition - it runs fine as a server, aswell as LTSP i run DHCP, DNS, Samba4 and Squid aswell as handling 25 clients at half the load :)

---

### Post by xpertuse on 2011-02-28
Thanks so much. I'll give it a try tomorrow. I am new in Linux and I am trying to experiment a litle bit :).
I tried to implement a thin client environment with XP clients and their images stored in a ubuntu server with no luck... (I couldn't find enough info, I might open a new thread..) So now I want to try out the LTSP!

---

### Post by xpertuse on 2011-03-02
OK. I did what you told me. I think now I have to somehow force my test user to login to the graphical interface. Is that correct? Because I've logged in with my test user and I still get the terminal window...

---

### Post by headvampyre@hotmail.co.uk on 2011-03-02
Try typing startx and see what happens. Post the output on here, it may help.

---

### Post by xpertuse on 2011-03-03
I run it on the server. Correct?
Nothing happened. I got the bellow and the cursor waiting for input...

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux ubuntu-server 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-server root=UUID=9c6d3105-b891-4eeb-adf9-05310018f3ed ro quiet
Build Date: 10 December 2010  05:52:57PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  3 10:20:09 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
resize called 1280 1024
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Symbol map for key <KPDL> redefined
>                   Using last definition for conflicting fields
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

```

---

### Post by HugoSerrano on 2011-03-03
Run it on the client.

---

### Post by xpertuse on 2011-03-03
> **HugoSerrano said:**
> Run it on the client.

How?
I cannot login on the client...

---

### Post by headvampyre@hotmail.co.uk on 2011-03-03
can you type anything in the terminal? I was under the impression that it was going straight to the no-GUI server console instead. If you can type in it - just type "startx".

---

### Post by xpertuse on 2011-03-04
OK, I typed sudo startx and it says "testuser is not in the suboers file. This incident will be reported".

I also run startx and it says:
"user not authorized to run the X server, aborting.
"giving up."
"xinit: No such file or directory (errno 2): Unable to connect to X server"
"xinit: No such process (errno 3): Server error."


Thats all...

---

### Post by headvampyre@hotmail.co.uk on 2011-03-05
Weird :( Did you install ldm-server? If not, install that and run:

sudo ltsp-update-image
sudo ltsp-update-sshkeys

on the server.

---

### Post by xpertuse on 2011-03-05
If I installed ldm-server?
Don't thong so...
How do I do that?
sudo apt-get ldm-server?

---

### Post by headvampyre@hotmail.co.uk on 2011-03-05
yeah, apt-get install ldm-server :)

---

### Post by xpertuse on 2011-03-06
ldm-server was already installed... :(
I did sudo ltsp-update-image --arch i386 and
sudo ltsp-update-sshkeys
I will check if anything happened in Tuesday that I'll be at work....

---

### Post by xpertuse on 2011-03-09
Still no go...

---

### Post by deece803 on 2011-05-07
ok, this is what i did as i had the same problem. at the login screen on the thin client, bottom left corner is the preferences button, click that. Click "select session..." brings you to a drop down menu that says default. From the drop-down menu select "Ubuntu Desktop Edition" then click "change session". then login as normal.

BUT, what i did first before i discovered the preferences option, in the terminal i installed gnome-core (sudo apt-get install gnome-core) while logged in as root. Then i found the preferences option on the login screen, so i'm not sure if the "ubuntu desktop edition session" is available to you without installing gnome-core.

So give the first paragraph a go first and let me know how you go!

Good luck and sorry for not being very good at explaining things!

---

