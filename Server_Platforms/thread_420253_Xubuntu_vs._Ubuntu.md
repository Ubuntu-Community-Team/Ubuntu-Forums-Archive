---
title: "Xubuntu vs. Ubuntu ?"
date: 2007-04-23
forum: Server Platforms
---

### Post by gigi on 2007-04-23
Hello, 

first I want a tell you what I want to do:
I've got an epia board without any fan. The board has a 800 MHz CPU. So this is a real low end PC, but I only want to use it as a musicbox. The aim is to let the PC run without any monitor or keyboard.

So I want to Install lirc for IR-remote conrol and mdp as the music player. 
My last installation was xubuntu and lirc and mdp works. Then I was trying to instal a xubuntu server, but that thing doesn't exist. Now the installation has to be done again.
But I'm not shure if it makes more sense to install an ubuntu server. 

My open questions:
- Does a server needs less power because the graficcard is only displaying text
- Xubuntu is specially for low end PCs. What about the ubunut server edition? Is it the same like xubuntu without GUI or does it need a more powerfull PC? 
- Is it possible to let mpd, lirc and irexec run on a server without having to login, or do I allyaws need to logon before starting the programs?
- Is it possible to mount automatically an external SATA-Harddisk during startup without logging on?
- Is it possible to start maybe gmpc on a server through an ssh -X session, so the GUI is on another machine or do I need to have the Desktop installed on the server too? Maybe a stupid question but I had problems to let gmpc connect to the remote mpd. This is another question what user or rights do I need to connect to a remote mpd?

Thanks for all hints and helps

---

### Post by ola on 2007-04-23
Hi!
> 
- Does a server needs less power because the graficcard is only displaying text


Yes it does. Generally; the more things you have running, the more resources are used by the system. 

If you install the server version you can install X later via apt-get. You can even grab the meta package (a package that contains a lot of other packages) to install the standard Ubuntu desktop packages called ubuntu-desktop.
 
> - Xubuntu is specially for low end PCs. What about the ubunut server edition? Is it the same like xubuntu without GUI or does it need a more powerfull PC?

The main difference between the ubuntu server edition and the ubuntu desktop edition is that the desktop edition contains Gnome and the server edition contains server programs such as Apache by default. Even though you choose the server edition your can always add and remove programs later (via apt). 

I think that Xubuntu is a Ubuntu desktop but instead of using Gnome for the desktop they use XFCE4 (which use less resources than Gnome). They might have done some customization of the installation as well.

> - Is it possible to let mpd, lirc and irexec run on a server without having to login, or do I allyaws need to logon before starting the programs?

I'm not sure about those exact programs, but in general you can add a startup script to /ect/init.d where you place the lines that starts your application. From that you can make a soft link to for example /ect/rc3.d that run the script you put in /etc/init.d. To get better understanding of this you would probably want to look into Ubuntu Start Up Scripts.

> - Is it possible to mount automatically an external SATA-Harddisk during startup without logging on?

You can probably add the mount points for your SATA-disk to /etc/fstab which is the file that keeps track of your file systems.

> - Is it possible to start maybe gmpc on a server through an ssh -X session, so the GUI is on another machine or do I need to have the Desktop installed on the server too? Maybe a stupid question but I had problems to let gmpc connect to the remote mpd. This is another question what user or rights do I need to connect to a remote mpd?

Yes, to be able to run X or X-programs remote you need to have that specific program installed on your server.

Hope it's to any help! You would probably want to read a little bit about /etc/fstab and start up scripts, but it might be a beginning! Good luck and have a nice day!

Best regards,

Ola

---

### Post by MilesZS on 2007-04-23
EDIT:  ola beat me to it.  His post is also much more helpful, haha.

I can only address part of the issue, but I think it will help:
There is no Xubuntu server edition, because the 'X' portion has only to do with a GUI.  The base of Xubuntu, Kubuntu, and Ubuntu are all the same -- Ubuntu.  The X, K, etc, speak only to the graphical desktop manager.  In other words, since you aren't going to use a GUI, you only need the server edition.  In fact, server edition will work faster on a slower machine, because it doesn't have to use any CPU cycles on a GUI.  

I think I used a lot of text to make a simple point:  If you're doing all your work from the command line, you want the server edition.  

I take no responsibility if you fry the board without a fan ;)

---

### Post by gigi on 2007-04-23
ok, that seems to be enough for me
I'll try the ubuntu server. 
My experience (hope positive) will come back to the board.

Thanks for your help and quick and long answers

regards
gigi

---

### Post by gigi on 2007-04-30
Hi All,

I've installed the ubuntu server and this runs without any problems.
Then I get the package openssh-server to have remote access.

To mount to my external SATA disk automatically I added this line to /etc/fstab
/dev/sda1       /media/icybox   ext3  defaults   0  2


I followed more or less this guide to install LIRC
[http://www.vdr-wiki.de/wiki/index.php/Debian_-_LIRC_Installation](http://www.vdr-wiki.de/wiki/index.php/Debian_-_LIRC_Installation)
It very easy because of the "module-assistant"

To install mpd I used this guide, for me it worked without any problems
[http://zappi.wordpress.com/2006/09/30/wahlt-die-mpd-jetzt/](http://zappi.wordpress.com/2006/09/30/wahlt-die-mpd-jetzt/)

Both programs lirc and mpd were running as deamons in the background after reboot.
After reboot I only had to start irexec as root.

For all other actions I can use the remote control

I still have problems 
- to have a remote connection to mpd on my server.
- to let gmpc run through an ssh session because of the following error 
   Gtk-WARNING **: cannot open display:
I've allready tried on my machine "xhost + 192.168.0.111" and on the server "export DISPLAY=192.168.0.111" but the error still occurs ???

But ncmpc is running in a terminal so everything its ok, but there is still some work to do ;-)


short instruction
==========
install these programs
- openssh-server
- linux-headers-2.6.20-15-generic
- gcc-4.1
- lirc
- lirc-module-source
- module-assistant
- mpd
- mpc
- ncmpc

#dpkg-reconfigure lirc-modules-source "choose streamzap !!!"
#module-assistant -f auto-install lirc-modules-source
add file <home>.lircrc
-------------------------------
begin
  prog = irexec
  button = Red
  config = mpd&
  mode = mpd
  flags = once
end

begin mpd
  begin
    prog = irexec
    button = play
    config = mpc play 0
  end
  begin
    prog = irexec
    button = pause
    config = mpc pause
  end
...
-----------------------------------
configure the file mpd.conf  <see guide>
create the mpd-Database
etc/init.d/mpd restart

---

