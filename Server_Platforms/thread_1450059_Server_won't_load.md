---
title: "Server won't load"
date: 2010-04-08
forum: Server Platforms
---

### Post by nipsy on 2010-04-08
I installed ubuntu 8.04 as my server. However when it boots up, it sends me to command lines, as if I should be adding something instead of booting all the way.

How do I get it to boot all the way through, is there something I should type there?

Also we tried installing 9.10 and it wouldn't work at all, kept getting boot errors.

---

### Post by wojox on 2010-04-08
Ahhh there is no gui on the server disk. You can download one if you'd like. You just installed the normal 8.04 server cd right?

---

### Post by nipsy on 2010-04-08
Yes, I simply installed the server edition..where do I go to get the dl for the gui? and once I get that dl, how do I install..

Thanks for your patience, first time trying to make my own server and I've tried everything from Ubuntu 6 to knoppix and back again..

I'm running scsi hard drive if that makes a difference

---

### Post by lisati on 2010-04-08
The server disk does not install a GUI by default, but you can add one if you want. Any preferences?

---

### Post by Vegan on 2010-04-08
The Gnome desktop is the default and its reasonable useful.

I like the CLI as its fast to fix things and less of a nuisance when editing system files.

---

### Post by wojox on 2010-04-08
If you want to install a graphical desktop manager without some of the desktop addons like Evolution and OpenOffice, but continue to use the server flavor kernel use the following command:

```
sudo aptitude  install --no-install-recommends ubuntu-desktop
```

Just run that in your shell and reboot. 

If you have the time and patience, you could always leave it alone and learn the true power of Linux by using just the shell.

---

### Post by nipsy on 2010-04-08
Re-installed ubuntu, ran through entire installation and I still get nothing but the shell. No desktop, just command lines and my user name with flashing curser.

How do I boot into desktop from there and why does it seem like it didn't install all the way?

Do I simply need to reboot?

Maybe I've worked on this too long, was up until 4:30 am, got up at 7, had surgery, came home and I'm still working on this...

Ubuntu has drug me into its addiction:P:P:P

---

### Post by drdos2006 on 2010-04-08
I am assuming that you have a second PC networked to access the server PC. If that is correct you can use Webmin to access the server from your second PC.
Tutorial is here.
Quote:
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

regards

---

### Post by nipsy on 2010-04-08
As I sit on the shell, tried to install desktop got error 

"debconf failed to run"

so I  sudo apt get-install debconf and ran

got message that debconf was already latest version..

running out of ideas to try now..

---

### Post by nipsy on 2010-04-08
> **drdos2006 said:**
> I am assuming that you have a second PC networked to access the server PC. If that is correct you can use Webmin to access the server from your second PC.
Tutorial is here.
Quote:
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood

regards


This is a brand new server connection, I cannot use other PC's to access the server when Ubuntu won't even load.

---

### Post by drdos2006 on 2010-04-08
It is a server, it is designed to be administrated from an external connection. If you must have a GUI, then download and install ebox.
It is based on Ubuntu 8.04 server. 
regards

---

### Post by kevinthecomputerguy on 2010-04-23
[COLOR=black][FONT=Verdana]drdos2006 is 100% right, you should not be physically administering the server (keyboard,mouse,monitor) that develops bad habits. Load up webmin, and manage it remotely.[/FONT][/COLOR]

---

### Post by nipsy on 2010-04-23
Thanks for all the responses and support. We ended up loading 8.04 regular edition and it is working just how we want it to. A personal server. (Using it as our own extreme media center between the 9 working computers in this house)

The reason we didn't want the webmin was because we aren't running as an online server. If there are any ideas of free server programs to put on, please feel free to let us know.

Again, thank you.

---

### Post by kevinthecomputerguy on 2010-05-03
Hey guys-
I uploaded a new version that includes Samba groups (version 3.76)
[http://woodel.com](http://woodel.com)

---

### Post by arrrghhh on 2010-05-03
> **nipsy said:**
> Thanks for all the responses and support. We ended up loading 8.04 regular edition and it is working just how we want it to. A personal server. (Using it as our own extreme media center between the 9 working computers in this house)

The reason we didn't want the webmin was because we aren't running as an online server. If there are any ideas of free server programs to put on, please feel free to let us know.

Again, thank you.

Well if you're running a "server" - there's no need for a GUI.  I have a server that's just for home use (I do have a web server that faces the outside world, but it's just so I can manage the server when I'm away :D)

The GUI is really just another piece of bloat.  If you ever get the urge, try ubuntu-server again.  You'll have to set it up to be accessed via SSH at the very least, but then all you need is a power cable and a network cable... That's all that's going to my server, I love it!!

---

