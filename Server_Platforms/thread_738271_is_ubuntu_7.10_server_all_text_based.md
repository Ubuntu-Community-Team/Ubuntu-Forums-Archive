---
title: "is ubuntu 7.10 server all text based?"
date: 2008-03-28
forum: Server Platforms
---

### Post by AnthonyArde2 on 2008-03-28
I inastalled the server version of ubuntu 7.10 x86, and noticed there is no GUI, is this normal, i`m going to be using this system as a web server, am i able to get a gui for this or do i have to run the computer in a text (DOS) enviroment?

Thanks

Anthony

---

### Post by rickyjones on 2008-03-28
> **AnthonyArde2 said:**
> I inastalled the server version of ubuntu 7.10 x86, and noticed there is no GUI, is this normal, i`m going to be using this system as a web server, am i able to get a gui for this or do i have to run the computer in a text (DOS) enviroment?

Thanks

Anthony

The server version does not have a graphical interface by default. The reason being that most servers, specifically Unix based, run headless daemons that do not need direct input from the user.

You can install a graphical environment if you choose. For example, "apt-get install ubuntu-desktop" will install a graphical environment and programs that you normally get with a desktop installation of the operating system.

-Richard

---

### Post by kerry_s on 2008-03-28
> **AnthonyArde2 said:**
> I inastalled the server version of ubuntu 7.10 x86, and noticed there is no GUI, is this normal, i`m going to be using this system as a web server, am i able to get a gui for this or do i have to run the computer in a text (DOS) enviroment?

Thanks

Anthony

you can install a minimal gui to save you resources.
sudo apt-get install xorg gdm synaptic fluxbox mc

---

### Post by Ch3knraz3 on 2008-03-28
> You can install a graphical environment if you choose. For example, "apt-get install ubuntu-desktop" will install a graphical environment and programs that you normally get with a desktop installation of the operating system.

you can install a minimal gui to save you resources.
sudo apt-get install xorg gdm synaptic fluxbox mc

I am a complete NOOB to Linux .  I just bought a Proliant 1850R.  This is my first time working with a server or a Linux based OS.  I have installed the Server package (though I think I installed it twice).

1. So how do I "apt-get" from my command prompt xxx@xxx :~$   

2. Would I be better off installing the desktop and then apt-get the LAMP piece?

Thanks,

Ch3knraz3:confused:

---

### Post by freebeer on 2008-03-29
you just type it (or copy/paste) at the command prompt.  ie.  Open a terminal window and you'll get a command line prompt then you type:

```

apt-get install ubuntu-desktop

```

Couldn't be simpler!  :D

Since you've got the server edition already installed, you only need to type the above to get a desktop, so why go through a re-install of the desktop version?

---

### Post by tubasoldier on 2008-03-29
you will more than likely have to put a sudo before the apt-get command.
So it would look more like:
```
sudo apt-get install ubuntu-desktop
```

By the way, in my opinion, the text mode is much more powerful than a GUI. You can only point and click in a GUI, similar to what little children do when they want something. In the text mode you can learn to speak the language and accomplish multiple tasks with a few sentences rather than a lot of pointing.

---

### Post by Ch3knraz3 on 2008-03-30
I really appreciate your answers. Thanks so much!

> By the way, in my opinion, the text mode is much more powerful than a GUI. You can only point and click in a GUI, similar to what little children do when they want something. In the text mode you can learn to speak the language and accomplish multiple tasks with a few sentences rather than a lot of pointing.

Your point is well taken, A CLI is always more powerful than a GUI, for an expert user.  I would expect that after a certain point I will use nothing but the CLI.  However, I would suggest that children begin to learn their parent's language by pointing to what they want and receiving feedback from the parents.  Asking them to carry on an intelligent conversation on the telephone out of the womb isn't realistic.  At this point I am a child and beginning to learn the language.  Being able to switch back and forth between GUI and CLI will be less frustrating and should speed up the learning curve for me.  Also my objective is to do web development in an AMP environment so setting up the environment is just a step on the path.  It's kind of like a one night layover in Paris on my way to a summer in Italy.  I really need to learn Italian.  I need just enough French to find a bathroom, a restaurant, a taxi, and the hotel.  Of course any analogy breaks down after a bit but I think you get my point.

> ...
Couldn't be simpler!
...
you will more than likely have to put a sudo before the apt-get command.
So it would look more like:

Code:
sudo apt-get install ubuntu-desktop

Ok. It could have been simpler...:lolflag:

After a couple of sidetracks...
Like figuring out how to get into the recovery console so I could edit the sudo and group files...

I was finally able to execute a sudo command from the initial command prompt.

I decided I wanted to try XORG so I tried the suggested:
# sudo install xorg gdm synaptic fluxbox mc

It started apt-getting and then asked for the Gutsy CD.  I just happened to have made one for another reason so I had one at least. But now it keeps asking for it over and over again even though it is in the drive.

So I think I will abort the install (if I can figure out how) and try the apt-get ubuntu-desktop suggestion.

If anyone has any other ideas...

Thanks,
Ch3knraz3
:guitar:

---

### Post by forceofnature on 2008-03-30
I am not the expert here but you will need to identify your repositories or maybe you can try this If they have been identified already.

sudo apt-get update

---

### Post by kerry_s on 2008-03-30
dude, you need to start from scratch. 
use debian it's way better for a server.
net installer-> [http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

at the package selection part, check the server stuff you want, up/down arrows & space bar to move and select, tab to get to continue.

if you leave the desktop checked, you'll have a server with full desktop.

---

### Post by igknighted on 2008-03-31
I must respectfully disagree with the advice given here.

First, there is some merit to installing the GUI in your situation, but consider carefully what you are getting into.  By installing the 'ubuntu-desktop' package, you will get many daemons and other programs running that will have absolutely nothing to do with your server, and are nothing but security risks (anything running that isn't needed could have a security flaw, so since it isn't doing anything useful why run it?).  There is an alternative to simply dumping everything that would be on a base install (ubuntu-desktop) of the desktop version, and that would be similar to what kerry_s said.  However, fluxbox is confusing to configure, so you might wish to consider installing a simpler to use graphical environment, but without all the extra desktop applications/daemons.  I would recommend the 'kde-core' package, because there is a nice simple GUI to turn down all the cpu intensive things that would needlessly bog down a server (easier than trying to do it in gnome or xfce manually).

Second, I would ask you to consider very closely if you REALLY want a GUI, or if it just seems that way because of long-held habits from other OS's, or coming from a world of desktop computing.  I ask this because a server usually isn't a machine that you can sit down in front of, often they sit in rooms and are connected to remotely.  In this case, a web-based configuration tool (such as webmin... sure its controversial amongst the hardcore server folk, but its what most people new to servers are really looking for when they ask for a GUI).  Coming from windows, or the desktop world in general, the thought is that you have an application on your computer that you pull up and make changes.  But since the applications we are dealing with on servers (mysql, apache, postfix, etc.) were often on machines that were physically inaccessible, there was never a need to write a GUI.  So when you fire up your nice GUI on your server, you will still have to pull up a terminal or a web browser to make any changes... and you can get this exact same interface from your normal desktop (even if it is windows using an ssh program like putty), so why tax the server with the GUI?

Third... stop.  Don't install yet.  Do some research.  Look at other distributions (Debian was suggested, for example).  Read the forums and how-tos and ask questions before doing.  This way when you are ready to try something, you wont be stumbling in the dark.  To get your research started, let me recommend CentOS (the free version of the industry standard Red Hat Enterprise Linux).  It comes on a DVD or 5 CD set (there's a liveCD, but you don't want it), but it gives you some great options with the GUI installer.  Select the package groups 'server' and 'server-gui' to get the Red Hat server tools (and if you want, select 'customize package selection now' to determine exactly which server features are installed).

---

### Post by hyper_ch on 2008-03-31
I'd also recommend Debian as server...

and having a gui on a sever is sort of pointless... well, on a true server...

All configuration is done by editing text files and whether you edit a text file in a gui environment or in a cli environemnt is just about the same...

But the most important question is:

What do you want your server to do?

---

### Post by Ch3knraz3 on 2008-03-31
> **kerry_s said:**
> dude, you need to start from scratch. 
use debian it's way better for a server.


I'm not opposed to that...

> **igknighted said:**
> First, there is some merit to installing the GUI in your situation, but consider carefully what you are getting into.

It seems as though I haven't done enough thinking...

> **igknighted said:**
>  Second, I would ask you to consider very closely if you REALLY want a GUI, ...  I ask this because a server usually isn't a machine that you can sit down in front of, often they sit in rooms and are connected to remotely.  In this case, a web-based configuration tool (such as webmin...) ... from your normal desktop (even if it is windows using an ssh program like putty), so why tax the server with the GUI?

Remote administration is fine by me too.  I hadn't thought about that because right now both servers I bought are sitting on the workbench in my home office.  Both servers have RILOE cards though I probably don't even  need that for remote admin.

> **igknighted said:**
>  Third... stop.  Don't install yet.  Do some research.  Look at other distributions (Debian was suggested, for example).  Read the forums and how-tos and ask questions before doing.  This way when you are ready to try something, you wont be stumbling in the dark.

> **hyper_ch said:**
> But the most important question is:
What do you want your server to do?

I am afraid I have hijacked the OP's question.  So I will do some more research and perhaps start my own post with my specific objectives and hardware resources.

Thanks again, you all have been really great.  The strength of the community is one of the major reasons I started with Ubuntu rather than any of the other distros mentioned.

Ch3knraz3
2 + 2 = 5 for large values of 2 or small values of 5

---

### Post by BillGod on 2008-03-31
to answer your question on how to get it to quit asking for the cd.  I have to introduce you to a few things first.

apt-get is the package installer for debian/ubuntu
apt-get uses the file /etc/apt/source.list  The file contains all locations for installing software.  The first of which is the cd.  

Ubuntu does not let you log in as root (by default. you can change this if you wish)  to run commands as root start the command with "sudo" first.  It will ask you for your password then run the command as root.

If you want to remove the option to get it from a cd do this.

sudo nano /etc/apt/source.list
type in your password.

the very first lines in the file start with 
deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 

put a # in front of deb then ctrl-x to exit.  It will ask you to save the file.  

then run sudo apt-get update (this will reload the repositories for all your packages)

now when you run sudo apt-get install MYPACKAGE it will no longer look on the cd for MYPACKAGE

---

