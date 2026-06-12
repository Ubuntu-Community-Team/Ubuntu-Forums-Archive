---
title: "[SOLVED] Envy sucks!"
date: 2008-03-18
forum: Testimonials &amp; Experiences
---

### Post by WFGeppetto on 2008-03-18
I am sorry, and this paragraph should serve as a disclaimer.  I am pretty pissed off right now, and I am going to say what I *think*, rather than what I know.  I am barely competent in the terminal, and I've only been using Ubuntu for about a month, so by many standards, I am a noob.  I am sorry if I am insulting a developer, or wrongly accusing the program, but here goes:

I finally got everything working like I wanted.  I had used the 64 bit Gutsy, but I had so many problems with internet apps, and video, that I switched to 32bit.  I got compiz working great, even with plugins, I had all my internet streaming working great, dvds were perfect, basically everything worked.  I even managed to get AWN working with AWN curves, and functional applets.  It was awesome.

The only thing that didn't work **great** was the Atlantis plugin for compiz.  I think it's just incredibly demanding of the graphics processing.  Anyway, atlantis ran very slowly, so I started looking into finding a driver better than fglrx.  Soon, I had seen my 3rd post about Envy.

Envy is supposed to be the easy way to install the appropriate driver.  1st complaint:  It says you will have to uninstall any changes it makes when ever you want to update Ubuntu.  That's retarded.  I'd rather have half working graphics, than an OS that won't update.

Anyway, I ran it, like an idiot.  It downloaded a new ATI driver, and installed it, then changed my xorg.conf settings (it said 'recommended').  Then prompted me to reboot.  Now, all I get after the boot processes run, is a black screen.  I can't even see my login, so I can't try to change sessions.  I am stuck with recovery mode, and not enough knowledge to fix it.  It seems to boot properly, and everything, just not display.  I can hit the power button, and it shutsdown, and shows 'gnome display shutting down' 'saving system clock' and all that that you are supposed to see on shut down, so I think it's actually running properly, it just doesn't display anything.

Seriously, please do not recommend a program that is so dangerous.  I'm sure Envy works fine for some people, but calling it "the easy way", and suggesting it for use by noobs just isn't cool.  It changes too many important things to be trusted, unless you know how to recover from a command line.  I will never recommend this program, without listing the necessary steps to fix it, if it doesn't work.

At this point, all I can do is post, and try to get help with recovery, but that will suck.  I'd have to reboot, write down my errors, reboot again, run windows, post my error logs, wait for an answer, reboot, try answer, reboot, post results, reboot, etc.  It'll be easier to reinstall the whole shebang, and that just plain sucks!

I hate Envy, and I'm sorry to whomever may take offense to this.

---

### Post by fenian on 2008-03-18
Dude chillax we can fix this.First in recovery mode login with your username and password next enter the following line...

> sudo dpkg-reconfigure -phigh xserver-xorg

next reboot your computer with this command...

> sudo reboot

Also you don't need to reinstall/rerun envy after every system update only after system upgrades,ie;moving from version 7.10 (Gutsy) to version 8.04 (Hardy).

---

### Post by drubin on 2008-03-18
I had the same issue, I had to re-format to get my drivers working again.

I now have limited compiz support(and i am to scared to play with things for fear that it will mess up......... :? )

But for a FRESH install of ubuntu, and for a noob it is a great tool, it works for most cases. (provided bandwidth isn't an issue,) 

I personally wont ever use it again though. :(

---

### Post by Oldsoldier2003 on 2008-03-18
> **rubinboy said:**
> I had the same issue, I had to re-format to get my drivers working again.

I now have limited compiz support(and i am to scared to play with things for fear that it will mess up......... :? )

But for a FRESH install of ubuntu, and for a noob it is a great tool, it works for most cases. (provided bandwidth isn't an issue,) 

I personally wont ever use it again though. :(

restricted drivers manager works just fine in most cases.

---

### Post by drubin on 2008-03-18
> Re: Envy sucks!
Quote:
Originally Posted by rubinboy View Post
I had the same issue, I had to re-format to get my drivers working again.

I now have limited compiz support(and i am to scared to play with things for fear that it will mess up......... )

But for a FRESH install of ubuntu, and for a noob it is a great tool, it works for most cases. (provided bandwidth isn't an issue,)

I personally wont ever use it again though.
restricted drivers manager works just fine in most cases.

LOL, thanks, But it was the first thing i tried, (I don't want to steal this thread since currently I am quite alright with my Nvidia drivers that i manually had to install 

Ps 
How could you not install them as a noob, they pop up and gives you nice big buttons to click on :)

---

### Post by WFGeppetto on 2008-03-18
Thanks, first, I agree with rubinboy, but I don't actually know that much, I just needed to put in the rant.

Fenian, alright, I'll write that down, and reboot, and try it.  I don't get to login though, I have to use recovery mode, and it just takes me to the root with a command prompt, but I don't see why it would matter if I login.  Those commands look good, I'll try, and come back, and report my outcome.

Sorry, I knew it was a rant post.  I would change the title to something more docile, but edit won't let me change the topic title. I am chillaxing currently.  See you soon, hopefully from the Ubuntu side of this thing.

---

### Post by WFGeppetto on 2008-03-18
Yeah, before I reboot, I wanna say:

I should have stuck with flgrx, or whatever, it worked fine really.  I shouldn't have screwed with it.  The normal restricted driver works just fine, don't try to fix that which is not broken.

I did, and now it's broken.

*rebooting, trying Fenian's advice, bbs*

---

### Post by drubin on 2008-03-18
What the first command does, Is gives you text based configuration settings for your ubuntu.

Basically will re-configure your stuff to the way you want it working. (NICE cmd to have written down encase you mess things up) 

had to use it many a time trying to get my drivers sorted.

---

### Post by guilly on 2008-03-18
ahhh I'm guessing you forgot to backup your xorg.conf :). Not trying to make fun or anything but it's a lesson we all learn, if your making any sort of configuration changes and are not sure of the outcome BACKUP!!!

---

### Post by drubin on 2008-03-18
> Iahhh I'm guessing you forgot to backup your xorg.conf 

Back in those days. (like a few months ago) I didn't even know what the cp cmd meant :)

---

### Post by WFGeppetto on 2008-03-18
> **guilly said:**
> ahhh I'm guessing you forgot to backup your xorg.conf :). Not trying to make fun or anything but it's a lesson we all learn, if your making any sort of configuration changes and are not sure of the outcome BACKUP!!!

Ok, yeah, I've just learned that lesson.  Actually, I didn't back it up, because Envy made a backup.  I thought about that, but I didn't think about it hard enough to remember where it made the copy, or what it named it.

Fenian, your code helped, sort of.  I can go to my login screen now, but when I log in, it starts, then reverts to the login screen again.  At least I can see something now.  I tried using xclient, and again with just gnome from sessions.  Every time, it starts, then reverts to the login, almost like there is a ctrl-alt-backspace in the end of the program start up.

Weird.  What else can I do?  I can still go back to recovery mode, but I'm not sure where to look for my xorg.conf (the old one), and I'm not sure that that is what I need to do anyway.

---

### Post by drubin on 2008-03-18
```
cd /etc/X11/
ls 

```

that should give you a list of all the files in the folder.  Xorg. is located in there.

Not sure if you need sudo rights though?

---

### Post by forrestcupp on 2008-03-18
Well, it's probably not Envy that sucks.  It's probably more like issues with those drivers, your card, and your system.  All the Restricted Drivers Manager gives you is an older version of what Envy gives you.  If you would have downloaded the drivers from ATI's web site and installed them manually, the same thing would have happened.

And for the record, I've had the same thing happen with drivers installed from the RDM.

The whole purpose for trying to get the newer ATI drivers is so you don't have to use Xgl to run Compiz.  But if you have to use Xgl and older drivers to get it to work, that's what you have to do.

And the reason you have to uninstall every time you upgrade your Ubuntu version is because it doesn't use the Ubuntu supported drivers, so they can't really coordinate their upgrades with it.

---

### Post by WFGeppetto on 2008-03-18
Ok, so, before I reboot, and try this, lemme make sure I know what to do.

I'll cd /etc/x11

then ls

suppose I find something like xorg.conf.back (I have no idea what it should look like, this is a horrible guess), or something else that I can be pretty sure is my old xorg.conf.  If I do, I should delete the current xorg.conf, and rename the one I want, right?

If this is correct, what is the command for delete, and rename?

---

### Post by forrestcupp on 2008-03-18
> **rubinboy said:**
> ```
cd /etc/X11/
ls 

```

that should give you a list of all the files in the folder.  Xorg. is located in there.

Not sure if you need sudo rights though?

Yes, you will need sudo permissions to restore your backup in that directory.

---

### Post by rune0077 on 2008-03-18
Yeah, I could never get Envy to work with my ATI card either. Then I bought a Nvidia card and Envy has been working magic ever since. But yes, it did screw everything up with the ATI card (then again, ATI and Linux does not seem to fit that well together).

> **WFGeppetto said:**
> 
Envy is supposed to be the easy way to install the appropriate driver.  1st complaint:  It says you will have to uninstall any changes it makes when ever you want to update Ubuntu.  That's retarded.  I'd rather have half working graphics, than an OS that won't update.


:) Relax, you can still update the OS, you just can't upgrade from Gutsy to Hardy. There's a big difference between an update and an upgrade - as long as you're still on Gutsy you can update as much as you want.

---

### Post by forrestcupp on 2008-03-18
> **WFGeppetto said:**
> Ok, so, before I reboot, and try this, lemme make sure I know what to do.

I'll cd /etc/x11

then ls

suppose I find something like xorg.conf.back (I have no idea what it should look like, this is a horrible guess), or something else that I can be pretty sure is my old xorg.conf.  If I do, I should delete the current xorg.conf, and rename the one I want, right?

If this is correct, what is the command for delete, and rename?

Be careful of casing.  it is 
```
cd /etc/X11
ls
```
the 'X' should be capitalized.  Then if you have one called xorg.bak, do this:
```
sudo cp ./xorg.bak ./xorg.conf
```to copy that to the xorg.conf.

---

### Post by WFGeppetto on 2008-03-18
> **forrestcupp said:**
> Well, it's probably not Envy that sucks.  It's probably more like issues with those drivers, your card, and your system.  All the Restricted Drivers Manager gives you is an older version of what Envy gives you.  If you would have downloaded the drivers from ATI's web site and installed them manually, the same thing would have happened.

And for the record, I've had the same thing happen with drivers installed from the RDM.

The whole purpose for trying to get the newer ATI drivers is so you don't have to use Xgl to run Compiz.  But if you have to use Xgl and older drivers to get it to work, that's what you have to do.

And the reason you have to uninstall every time you upgrade your Ubuntu version is because it doesn't use the Ubuntu supported drivers, so they can't really coordinate their upgrades with it.

That helps me understand a bit.  I suppose I shouldn't bash Envy so much, but I just shouldn't have used it, and I wish it hadn't been recommended to me.  I suppose the problem is just an issue of drivers in general, but I wish I had been properly warned.

Actually, like I said earlier, I should have known not to mess with it.  Everything was working fine, and I suppose atlantis is just slow on my meager little integrated graphics laptop.

For the record, one issue that may be causing the problem:  I have an AMD64 dual core, but I am running the 32 bit distro.  I often have to use dpkg -i --force-architecture to get many i386 debs to install.  I'm not sure if this has anything to do with it, but I thought it important to mention.

---

### Post by WFGeppetto on 2008-03-18
Thanks Forrest, I'm writing that down, and rebooting.  Bbs, hopefully.

---

### Post by aysiu on 2008-03-18
While I don't agree that Envy "sucks," it is certainly not the first method I'd recommend. If you can use the Restricted Drivers Manager and get good results with it, I would recommend you try that first. Envy would be a backup / last resort method.

---

### Post by WFGeppetto on 2008-03-18
> **aysiu said:**
> While I don't agree that Envy "sucks," it is certainly not the first method I'd recommend. If you can use the Restricted Drivers Manager and get good results with it, I would recommend you try that first. Envy would be a backup / last resort method.

I don't mean to keep posting, and it may seem mindless, but I'd like anyone else that comes in here to know I agree completely.  I hate Envy because I am relatively ignorant, and it just broke my ubuntu.  I am sure it works fine most of the time.

I cannot stress enough the truth of the above quote.  My system was fine, and I went screwing with it anyway.  If you have restricted drivers enabled, and all the bells and whistles ding and blow, then don't mess with your drivers.  The chances are it'll only make things worse.

---

### Post by sdowney717 on 2008-03-18
You can  from terminal or command prompt run it by typing
ENVY - T

Envy has almost always worked for my 9600ATI card.
In fact once you have ati xorg working the way you want, when updating thru ENVY you dont have to have ENVY make any changes to xorg.

ATI proprietary driver changes parts of xorg to look like this:

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"PseudoColorVisuals"	"off"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by WFGeppetto on 2008-03-18
Alright, that seems just a tad bit over my head.  I am no longer worried about getting the proper proprietary drivers working.  I'll be happy to get back where I was, with the restricted drivers.

Ok, I tried to fix the xorg.conf.  I found this file:

xorg.conf_backup_200803181234

I am left to assume that this is the backup that Envy made. I tried Forrest's code:

sudo ./xorg.conf_backup_200...    ./xorg.conf (but with proper syntax, and spelled out)

it returned this:

```
 sudo ./xorg.conf_backup_200803181234 command not found
```
This is not a copy/pasted code, so it may not be perfectly verbatim.

---

### Post by forrestcupp on 2008-03-18
> **WFGeppetto said:**
> Alright, that seems just a tad bit over my head.  I am no longer worried about getting the proper proprietary drivers working.  I'll be happy to get back where I was, with the restricted drivers.

Ok, I tried to fix the xorg.conf.  I found this file:

xorg.conf_backup_200803181234

I am left to assume that this is the backup that Envy made. I tried Forrest's code:

sudo ./xorg.conf_backup_200...    ./xorg.conf (but with proper syntax, and spelled out)

it returned this:

```
 sudo ./xorg.conf_backup_200803181234 command not found
```
This is not a copy/pasted code, so it may not be perfectly verbatim.

Sorry, you must have read it before I edited it.  theres a **cp** after the sudo.  I mistyped, then edited it.

---

### Post by WFGeppetto on 2008-03-18
Downy:  Do you mean, I can run ENVY - T in recovery, and maybe it will revert my xorg.conf for me?

That'd be cool.  Keep in mind, I'm pretty much in the noob catagory here.  I like what you say about keeping Envy out of the xorg.config, but your post (while seemingly simple) is ever so slightly over my head, and I don't want to mess with any of that stuff. I'd just like my old xorg.conf back.  Once I get back going, I'm sticking with the flgrx, or whatever it is.  It worked fine.

Everybody, Thanks so much for coming, and helping.  I'm waiting for another response, before I reboot, and try something else.  Either way, you guys are awesome for coming.  Thanks all around, once I get it going.

---

### Post by WFGeppetto on 2008-03-18
Thanks Forrest!!! I'm trying again...

---

### Post by WFGeppetto on 2008-03-18
Ok, well I think I'm still in trouble with all that.  I ran the sudo cp ,/xorg... it didn't return an error this time, so I 'sudo reboot'.  

Then it booted, and the code on the screen looked normal, but it stopped at a black screen again.  I can input text at this black screen, but it doesn't have a prompt, and code doesn't work, so it must not be a command line.  So, I 'sudo dpkg-reconfigure -phigh xserver-xorg'  and rebooted.  Now, I can get to my login screen, but when I log in, in xclient, or gnome, it starts, and reverts back to the login screen.

Currently, I am in ubuntu, but running Gnome Failsafe.  It works, but naturally all my pretty stuff is gone, and I can't seem to get the other sessions to work.

At least I can copy/paste from/to my terminal now.

My synaptics update is trying to run, but it has an error, it says to run 'sudo apt-get install -f'  I did that, and here is what it returned:

```
wfgeppetto@GPTO:~$ sudo apt-get install -f
[sudo] password for wfgeppetto:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xorg-driver-fglrx
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/12.3MB of archives.
After unpacking 34.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 112462 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/amdcccle', which is also in package fglrx-amdcccle
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Should I run my updates again now, or should I adress this error code? Or, maybe I should do something completely different (monty python style).

---

### Post by WFGeppetto on 2008-03-18
Oooh, I think I know what the current problem is.  It's having errors with that .deb file.  I have had to use 'dpkg -i --force-architecture <debname>.deb' before to get debs installed, because I am running 32bit gutsy, on an AMD64.  Shoud I go and find that file in the terminal, and try that?

(sudo dpkg -i --force-architecture xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_amd64.deb)?

Or, maybe I should try reinstalling xserver in synaptics?

---

### Post by sdowney717 on 2008-03-18
yes, you can run ENVY - t from a command prompt or terminal.

Could it be the ATI driver does not work well with you card ?

Or it could also just be the xorg.conf is messed up. 

you can select older versions of the driver with ENVY.

```

scott@scott-desktop:~$ envy -t
[sudo] password for scott:

OK: All the packages are installed


       +-------------------------------------------------+
       |                                                 |
       |             Welcome to Envy 0.9.10              |
       |                                                 |
       |    Developed by Alberto Milone (aka tseliot)    |
       |                                                 |
       +-------------------------------------------------+


       +-----------------------------------------------------------+
       |    Envy Menu ver.0.9.10                                   |
       |                                                           |
       |    1 - Install the NVIDIA driver                          |
       |                                                           |
       |    2 - Uninstall the NVIDIA driver                        |
       |                                                           |
       |    3 - Install the ATI driver                             |
       |                                                           |
       |    4 - Uninstall the ATI driver                           |
       |                                                           |
       |    5 - Install the ATI/NVIDIA driver Manually             |
       |                                                           |
       |    6 - Clean the Installation of any Nvidia driver        |
       |                                                           |
       |    7 - Restart the Xserver                                |
       |                                                           |
       |    8 - Restart your computer                              |
       |                                                           |
       |    9 - Exit                                               |
       |                                                           |
       |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
       +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:






```

---

### Post by WFGeppetto on 2008-03-18
Alright, now, things are getting a little better.  I used Envy -t to uninstall the driver I previously used.  Then I went to restricted drivers, and re-enabled the graphics driver.  I restarted, as prompted, and now I am running in xclient.  The only problem now, is that I cannot turn my desktop effects back on.

---

### Post by WFGeppetto on 2008-03-18
Alright, I think I've about gotten things back in order.  I used envy to uninstall anything that it would uninstall, then I uninstalled envy, and reinstalled the restricted driver.  I can log into any session again, but now my compiz is screwed.

Output from 'compiz --replace'

```
wfgeppetto@GPTO:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

```

The screen flashes when I run that, and again when I close the terminal.

---

### Post by forrestcupp on 2008-03-19
In a terminal, type:
```
gksu gedit /usr/bin/compiz
```

change the path on the line that is for COMPIZ_BIN_PATH to "/usr/bin" instead of "/usr/local/bin"

Also, change the line that says:
COMPIZ_NAME="compiz"
to
COMPIZ_NAME="compiz.real"

Then save it and try enabling visual effects again.

---

### Post by WFGeppetto on 2008-03-19
Sorry, Forrest.  I really appreciate your help, I actually got someone in IM with me last night, and we tried to fix it.  After about an hour, I had learned a lot, but not made any real noticable progress towards fixing it.  I think part of the problem was that I configured xserver-xorg, and was still running default in Xclient. 

I dunno, I had very little that needed to be backed up, and a very large jump drive. I just got my stuff, and reinstalled.  Now I have the best install so far.  I am meticulously repeating the installs of everything line by line, double checking it all, and it is seriously paying off.

I really do wish I could edit the title of this thread, though.  It's a bit mean, and shortsighted.

---

### Post by Mazza558 on 2008-03-19
I'm inclined to agree with you. I can see how Envy could be useful, but I really don't see what the fuss is about when it's **never, ever** done what it's supposed to do for me.

---

