---
title: "How to Make XRDP do Beautiful Things for You!"
date: 2009-05-23
forum: The Cafe
---

### Post by infraction on 2009-05-23
I'm posting this in the hope that it will make someone's life easier.  There are not a lot of very firm descriptions of how to make XRDP work out there.  That's probably because pretty much everyone uses VNC, and that makes complete sense.  VNC 'just works'....period.  However, I found myself in a position where my employer black-balled VncViewer from my work box, and suddenly I couldn't connect to my home Ubuntu machine.  Since I'm stuck with WinXP at work, Remote Desktop Protocol seemed the logical choice, as my employer should not have a problem with it.  But as I said, there just isn't much in the way of a road map out there that deals with the specifics of making XRDP work on Ubuntu.  In my small way, I hope with this post to help some folks get XRDP working without going through the trial-and-error process I went through.

First, let me cite some links that were helpful to me, either with basic information, or clues, or suggestions, or just tidbits that made me think and sort this all out:

[http://venturehosting.net/howto-get-xrdp-working-on-ubuntu-610-server/](http://venturehosting.net/howto-get-xrdp-working-on-ubuntu-610-server/)



[http://ubuntuforums.org/showthread.php?t=392184&highlight=xrdp](http://ubuntuforums.org/showthread.php?t=392184&highlight=xrdp)


[http://ubuntuforums.org/showthread.php?t=1077607](http://ubuntuforums.org/showthread.php?t=1077607)



Use these as you will.....I found them helpful, but no single one or any combination got me to a successful conclusion.  But their clues and such were invaluable.  Thanks to all the writers of those posts.


Here's some stuff you need to understand up front..........
I'm running Ubuntu Intrepid, fully updated.  I have a dual monitor setup, something that made all of this a bit more challenging.

There are three (3) pieces to this puzzle:  1) a VNC server.  Doesn't really matter which one as XRDP doesn't particularly care as far as I can see; he just needs a VNC server to serve up your display.  Your choices are:
		tightvncserver
		vnc4server
		vino-server
All are readily available via Synaptic Package Manager.  2)  XRDP.  Again, available via Synaptic.  He handles all of the Remote Desktop Protocol nonsense.  3)  SESMAN....he handles login Ids, passwords, and such.  Again, all are available in Synaptic.

You need to be aware of what ports each of the above VNC servers are listening on. Vnc4server and tightvncserver both listen on port 5901.  Vino listens on 5900 exclusively.

If there is a router in your configuration, you need to know how to forward ports to the IP address of the machine you intend to control remotely (that is, your Ubuntu box).  You are on your own to figure out how to do that....that's beyond the scope of this write-up.

If you are using a firewall on the machine you intend to control remotely, you need to understand how to create a rule that allows access through the port (5900, 5901, whatever) that you end up using for XRDP.  Again, that's beyond the scope of this post.

There are .ini file(s) you need to be aware of.  They are found in /etc/xrdp.  The specific files are:
xrdp.ini
sesman.ini

There is a control shell script for XRDP that you will need.  It is found in /usr/local/xrdp.

'sudo' access will be required as you go through this, so be sure you know how to make yourself sudo.

I used a free third-party service called DynDns to give me a URL to my Ubuntu box that I want to control remotely.  Do the same....you will find it helpful.  But maybe you will want to use some other service....your choice.



So, here we go kids......this is how I made this work.  I have tried all three (3) VNC servers and all worked, save some differences.  Vnc4server and tightvncserver both, when started, spawn a new X session......that may be OK with you, but was not with me.  Also, those two (2) servers were not able to deal with my dual monitor screen real estate.  They simply scrunched my two monitor view down into the space of a single screen.  Now, that was usable, but not what I had in mind at all.  Vino, on the other hand, could deal with my dual monitor display by giving me a scrollable window.  Another benefit was that he did not spawn a new X session, but instead just displayed my existing one......EXACTLY what I was looking for!  Obviously, I settled on Vino as my VNC server.  Choose your server as you see fit.

Next, let it be known that SESMAN never at any time gave me a problem.....it just worked.  There is some confusion out there as to what port he likes to listen on.  Either 3350 or 3389.  I wimped out and forwarded both to my Ubuntu box, and opened both ports on my firewall.  Done deal.

XRDP needed a little attention.  By default, he likes to listen on port 5910.  Now is where you will need to edit the 'xrdp.ini' file mentioned above, and you will probably need to be 'sudo' to do that.  Do the right thing, and back up that .ini file first!!  Here is what mine looked like after editting (remember I'm using Vino who likes port 5900.......make your changes for the appropriate port that your chosen VNC server likes):

[globals]

bitmap_cache=yes

bitmap_compression=yes

port=3389

crypt_level=low

channel_code=1



[xrdp1]

name=RDP-To-Vino
lib=libvnc.so

username=ask

password=ask

ip=127.0.0.1

#port=-1

#port=5901

port=5900



#[xrdp1]

#name=sesman-Xvnc

#lib=libvnc.so

#username=ask

#password=ask

#ip=127.0.0.1

#port=-1



#[xrdp2]

#name=console

#lib=libvnc.so

#ip=127.0.0.1

#port=5900

#port=5901

#port=5910

#username=na

#password=ask



#[xrdp3]

#name=vnc-any

#lib=libvnc.so

#ip=ask

#port=ask5900

#username=na

#password=ask



#[xrdp4]

#name=sesman-any

#lib=libvnc.so

#ip=ask

#port=-1

#username=ask

#password=ask



#[xrdp5]

#name=rdp-any

#lib=librdp.so

#ip=ask

#port=ask3389



#[xrdp6]

#name=sesman-X11rdp

#lib=libxup.so

#username=ask

#password=ask

#ip=127.0.0.1

#port=-1



You will notice everything is commented out except for the [globals] and [xrdp1] sections.  This is what is working for me.  You will also notice that in the [xrdp1] section, I am using port=5900....that is for Vino, which I've explained is my VNC server of choice.  You need to alter that setting to fit the VNC server you have chosen to use.  And a side note, using 'port=-1', to the best of my knowledge, causes XRDP to listen on its default port, which is 5910 as I mentioned above.


Now that this is done, you should be able to start up the three (3) pieces.  Start them as sudo, or not.  I'm not using sudo, and everything still works fine.  I started things this way.........
first, the VNC server (in my case       'vino-server &'       meaning I started him in the background)
then XRDP and SESMAN, using the start-up script in /usr/local/xrdp......usage is 'xrdp_control.sh start'.

Now, go to a Windows box, start Remote Desktop Connection, point it to the URL you created via DynDns (or whatever), and you will see your Ubuntu desktop magically appear in front of your eyes!!

Should you need to shut down XRDP / SESMAN, you definitely want to use the control script.....usage is 'xrdp_control.sh stop'.  I did not do that once, and it left me with a nearly unusable X session.....not fun.

As of this writing, I've not set things up so that the above three (3) pieces are automatically started at system start-up, but I believe one of the links I listed at the start of this primer does explain how to do that.  We are all on our own on that task at this point.

It is my sincere hope that this has somehow, someway helped someone with using this beautiful application called XRDP.  As said before, information I found was sketchy at best.  My hope is that I've filled in some information gaps, and given our community a little bit better road map for using this application.....I personally am thrilled that this is working, and working so well!!

This is a post-it-and-run kind of deal for me.  I'll place this in the most prominent places I can find, but I won't be back for follow-ups.  Use you head, and you'll be fine.  Discovery is own pleasure anyway, right??  But maybe I've spared you 40 hours of discovery!!   :)   UBUNTU ROCKS!!!!

Happy Computing!

---

### Post by FoolishStar on 2009-09-17
Thank you very much for this post, it has pointed me in the right direction, I'm currently running Ubuntu 8.04.3 and had an issue whereby after installing xrdp with apt I could not pass from the RDP session into sesmen then onto any VNC session.  With the above info I have managed to get into a session, Bash only but never the less a session!

I'm going to post back here when I get into X correctly.

Thanks again!

---

### Post by ricojonah on 2009-10-26
Thanks for this guide! I've been searching around quite extensively for information on how to implement xrdp with Ubuntu.

---

### Post by Circa Lucid on 2009-12-10
Dude, I just got RDP access to Karmic and it runs a heck of a lot better than Remote Desktop Viewer. All I did was:
```
cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak
nano /etc/xrdp/xrdp.ini
[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1

[xrdp1]
name=RDP-To-Vino
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=5900

service xrdp start
```

Thanks for everything!

---

### Post by benjaminsuman on 2009-12-10
Trying to run Synaptic or perform any other administrative function through the menus will error out using the default xrdp settings.  You get the error message:

"Unable to copy the user's Xauthorization file"

---

### Post by Steve1961 on 2010-01-02
This does seem to work pretty well on karmic, and much faster than vnc.  I've accessed it remotely by tunnelling it through ssh and its still quite speedy.  On karmic the service also seems to start automatically when booting as well.  However, the rdesktop client on windows 7 doesnt work with it and throws up a protocol error.  This seems to be a known issue.

---

### Post by juancarlospaco on 2010-01-02
Use SSH or FreeNX my young padawan...

---

### Post by Steve1961 on 2010-01-02
> **juancarlospaco said:**
> Use SSH or FreeNX my young padawan...

I do use ssh, but it isnt the best when you want to see a full desktop, and as I maintain my kids machines remotely that's what I need.  NX is great when it works properly, but I've had mixed expereinces with it.  xrdp seems just as fast as NX so its all good.  The more ways we have of accessing Linux boxes remotely the better - and lets face it VNC is a dog

---

### Post by jrssystemsnet on 2010-02-10
If anybody's still looking, I've got a fully-documented install procedure at [http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing) which:

* explains what xrdp actually does (and doesn't do)
* sets up xrdp to map to Vino to control the currently logged in local user's session
* sets up xrdp to map to TightVNC to control an arbitrary vnc-only (non-local) session
* shows you how to configure Vino
* shows you how to configure TightVNC
* shows you how to work around the keyboard mapping bug between xrdp and TightVNC
* shows you how to automatically start your TightVNC session outside the local user log-in process

[IMG]http://ubuntuwiki.net/images/d/df/Xrdp_login.png[/IMG]

Once you're done, you have a working xrdp server that lets you choose at the time of connection whether you want to connect to the local user session or the arbitrary tightvnc session you've set up... just choose "Active Local Login" or "New Session" after connecting via RDP and you're off to the races.

---

### Post by lipinski on 2010-03-02
jrsystemsnet:

Great tutorial/Wiki.  That was very helpful.

One critique - you mention uninstalling tightvncserver.  But, you don't mention which one to use/install (if not installed).  I had only tightvncserver installed - don't remember if I uninstalled the default, or whatever a long time ago.  But, when I removed tightvncserver - I didn't have a VNC server package at all.  And you didn't mention which one works with your setup.

All in all, I actually prefer tightVNC, and just fixed the Keyboard problem.  

Thanks again - this works better than just straight tightvncserver<->tightvncclient than I was using before.  No more small font issues and blurry screen - that I couldn't resolve with a standard tightvnc setup.

---

### Post by jrssystemsnet on 2010-03-17
> **lipinski said:**
> One critique - you mention uninstalling tightvncserver.  But, you don't mention which one to use/install (if not installed).

The **apt-get install vino** part under "Installing Packages" should replace the original Xvnc if it's been uninstalled.

---

### Post by Whammy on 2010-12-03
> **benjaminsuman said:**
> Trying to run Synaptic or perform any other administrative function through the menus will error out using the default xrdp settings.  You get the error message:

"Unable to copy the user's Xauthorization file"
How do you get around this?

---

### Post by jzaruba on 2011-01-13
How come I get **only one keyboard layout** offered when connecting via xrdp? I have set up two, US and CZE Qwerty, but they're both disabled and "US 105-ke" is used.

At least for me the pop-up for administration operations seems to work fine. It did not with plain 'sudo apt-get install xrdp', so thanks for the wiki/guide again. :)

---

