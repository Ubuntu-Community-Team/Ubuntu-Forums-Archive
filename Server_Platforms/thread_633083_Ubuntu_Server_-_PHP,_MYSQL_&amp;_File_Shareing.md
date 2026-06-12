---
title: "Ubuntu Server - PHP, MYSQL &amp; File Shareing"
date: 2007-12-06
forum: Server Platforms
---

### Post by NuWeb on 2007-12-06
Hello,

Im a 18 year old PHP developer and took on a ICT system of family building company :(

They needs some simple sever requirements:
 1. PHP - To support the little Intranet site I created them
 2. MySql - To use with the PHP system as a database.
 3. File Share - Edit, Save, Manage files from other XP computers.

========

Im NEW to Ubuntu, and noobish on Linux experiance. So can I ask some noob questions:
[B]Will ubuntu server support php, mysql and File Share?
IF not how to i activate them?

Is it hard to install drivers?
Is it compatible with XP networked computers?[/B]

========

The other thing im using a Brand New Windows Vista computer that I formatted for the use of a server. I did have server 2003, but it got a virus within 3 weeks.
So im not doing so well

---

### Post by CyberBob on 2007-12-06
Ubuntu will indeed support php, mysql, and file sharing!

If you have not yet installed the Xubuntu (server) system on the computer in question, you can configure it during installation as a LAMP server: Linux/Apache/MySQL/PHP will all be installed together.

As for file sharing, you simply need to install Samba to connect and see windows computers in a shared network. To do this use the following command:

$ sudo apt-get install samba

(you will be asked for your password by invoking the sudo command, which temporarily gives you super user privileges)

After that, your system should be ready to do what you like ...

Good luck!

---

### Post by NuWeb on 2007-12-06
Ahh nice one. :)

OK. I did a FRESH INSTALL.. **BUT**

It lists things that its starting, they all say OK.
The last one it says is
"Running local boot scripts /etc/rc.local" [ok]

THen nothing?
If i press enter, it asks for user and pass in prompt. Then its all commands, **Is their no GUI?**

---

### Post by TurboRush on 2007-12-06
You do not get a GUI with the server edition... this may answer some questions

[http://ubuntuforums.org/showthread.php?t=621478](http://ubuntuforums.org/showthread.php?t=621478)

---

### Post by NuWeb on 2007-12-06
lol. You think it whould mention somewhere that its just all command line.
Thats no use to me, i need tick boxes.

Looks like its back to Win Server 2003 :(

---

### Post by buntunub on 2007-12-06
sudo aptitude install ubuntu-desktop

sudo aptitude install kubuntu-desktop

sudo aptitude install xubuntu-desktop

sudo aptitude install fluxbuntu-desktop

Whats so hard about that? You want to setup and configure a LAMP server, and you think its going to be mindlessly easy in either Linux or Windows?.. LOL!!!!

---

### Post by koenn on 2007-12-06
> **buntunub said:**
> sudo aptitude install ubuntu-desktop

sudo aptitude install kubuntu-desktop

sudo aptitude install xubuntu-desktop

sudo aptitude install fluxbuntu-desktop

Whats so hard about that? You want to setup and configure a LAMP server, and you think its going to be mindlessly easy in either Linux or Windows?.. LOL!!!!
last time I checked, "sudo aptitude install ubuntu-desktop" (and variations thereof)  installs a complete default ubuntu desktop system i.e. with all bells and whistles (openoffice, wall papers, media player, ...). Not really a smart thing to do on a server, imo. 


see post #10 in [http://ubuntuforums.org/showthread.php?t=621478](http://ubuntuforums.org/showthread.php?t=621478)

---

### Post by NuWeb on 2007-12-06
Yeh it is mindlessly easy in Windows Server 2003, but windows is slow and vunerable. Which is why i was looking for alternative.

Also "whats so hard about that" you just install lots of desktops that are pointless!!!, none of them are for server management.
That is not what I need.

You seem to be angry at me not useing UBUNTU, but thats down to the OS not being compleated with GUI.
As i thought it did, as it did not say otherwise... Shame

---

### Post by kazuya on 2007-12-06
well, if you use xubuntu or even ubuntu, it may include some other bell's and whistles stuff. It still performs optimally for you. Who says when doing server stuff, you may not need those items for certain tasks or functions. a default Ubuntu install is lacking in a lot of bloat. What is on there is small enough..

Now, there are other linux distros that may do this server role for a very low-powered machine with only {64MB RAM} or 128MB RAM -  vector linux / Zenwalk {both are slack-based}, archlinux {mainly command line driven},etc; mepis anti-x {based on fluxbox}

Or you can try  some of the BSDs - these are reputable as well...

For you, I would recommend the above ones  {Mint xfce edition} also comes to mind.

What is your PC Specs? How m uch RAM, Hard drive space?, etc.., processor, etc.? 

PS: Feel free to stick with windows server if that is what you know, but you may be very impressed like many others here after persisting..

The additional things you do not like on there could be removed afterwards if you so choose...

Another distro like Fedora {free form of Redhat} or Centos may be more to your appeal.These are some of the big players business wise, but they are all essentially the same when it comes to functionality..

---

### Post by koenn on 2007-12-06
> **NuWeb said:**
> ...but thats down to the OS not being compleated with GUI.
As i thought it did, as it did not say otherwise... Shame
An operating system's main purpose is to facilitate and coordinate communication between programs and hardware. A GUI is just another program, but with the specific purpose of 
- creating windows, borders, buttons, ... for other programs, and
- provide a "point and click" environment for the user. 
A server without GUI makes perfect sense - the MS approach of having servers with GUI's is the exception rather than the rule. 

As you say yourself : windows is slow and vulnerable. It doesn't occur to you that slow may have something to do with the overhead of a GUI, and vulnerable may have something to do with the complexity of integrating a GUI in an Operating System  (and, quite possibly, the fact that GUI's allow for untrained sysadmins to set up a server with out of the box 'always works' defaults that create security holes all over the place) ? 

Nevertheless, you can install a GUI on a Linux server and propably install some administrator tools, or use web apps for system administration.

---

### Post by kazuya on 2007-12-06
> **NuWeb said:**
> Yeh it is mindlessly easy in Windows Server 2003, but windows is slow and vunerable. Which is why i was looking for alternative.

[COLOR="Red"]Also "whats so hard about that" you just install lots of desktops that are pointless!!!, none of them are for server management.
That is not what I need.[/COLOR]

You seem to be angry at me not useing UBUNTU, but thats down to the OS not being compleated with GUI.
As i thought it did, as it did not say otherwise... Shame

You do not need all of them you may need one of them. These are the popular gui choices. When you work in window server, you are using something similar to icewm desktop gui or window manager..So doing :
sudo aptitude install xubuntu-desktop

would get you the light-weight xfce gui desktop and some few reqd components and applications of it. This is not a bad thing; This is choice. Having one of these things helps you with using SAMBA {file sharing}, etc.

You do not have to use Ubuntu as there are many other equivalents. You do get a lot of help here though when you ask the question(s) with an open-mind to a different methodology of doing what you used to do one way.

Best of luck though. We are all still learning. In addition, the short-comings you find and report lead folks to listen and improve on whatever may be lacking; But you cannot improve system without having even tried to understand the reasoning for why it is done differently. you may invent a new way that others may start to utilize.

---

### Post by buntunub on 2007-12-07
> **NuWeb said:**
> lol. You think it whould mention somewhere that its just all command line.
Thats no use to me, i need tick boxes.

Looks like its back to Win Server 2003 :(

My response was based upon yours. You indicated in this response that you need tick boxes. You get those with MySQL GUI and others within the Ubuntu Desktop via Synaptic. You then went on later to say that you are frustrated in the lack of a GUI. Simply install Ubuntu Desktop and you get all that, same as with Windows Server 2000+, no different. It is not easy to setup/configure a LAMP server in either environment unless you have done it many times before and know your precise setups for that environment (each environment is completely different, one from another, and requires different setups).

I honestly could care less if you use Ubuntu or not. Trust me on this one. If you love Windows then more power to ya! If you want to use Linux, it wont come with any support at all, and figuring things out is 100% your responsibility. They say that Linux IS user friendly, its just extremely picky about who its friends are.

---

