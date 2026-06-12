---
title: "GUI Ndiswrapper Tool"
date: 2005-07-20
forum: The Cafe
---

### Post by poofyhairguy on 2005-07-20
Retrix was nice enough to give me what I really wanted for Christmas- a GUI ndiswrapper tool.

I got ahold of an Ubuntu laptop. A screenshot is attached.

Retrix is currently going through the proper channels. I was asked to build a presence for the tool in the forum to improve bug testing.

If people are interested enough, it will get its own third party forum.

Contact me or Retrix about bugs. Here is newest deb:

[http://www.users.on.net/~spohlenz/ubuntu/ndisgtk_0.2-0ubuntu1_i386.deb](http://www.users.on.net/~spohlenz/ubuntu/ndisgtk_0.2-0ubuntu1_i386.deb)

Put in home folder. Install this this command:

> sudo dpkg -i ndisgtk_0.2-0ubuntu1_i386.deb

Then run it this way:

> gksudo ndisgtk

---

### Post by Stormy Eyes on 2005-07-20
I'd do it, but I don't have any Wifi gear. My home network is strictly Ethernet.

---

### Post by poofyhairguy on 2005-08-04
bump

---

### Post by kiddo on 2005-08-04
what if my ndiswrapper is already set up? What should I test?

Okay, here are my first comments:

[list]
[*]The program runs fine, but it needs root privileges (duh).
[*] You need to do something else with the help button.
[*]You need to do a gnome menu entry.
[*]Ndisgtk doesn't check in realtime for hardware plugged or not. It should, if possible.
[*] Removing a driver works. Adding it back does not.
[*] Here is a screenshot:
[/list][img]http://www.imgreactor.com/display/5734/Screenshot-Wireless_Network_Drivers.png[/img]

**Edit:** tried removing and putting back my realtek driver, it did not work. Sad. *"Not a valid driver .inf file"*
Ndiswrapper still works.
 ```
jeff@kitsune:~/Desktop$ sudo ndiswrapper -i /home/jeff/driver-linksys-realtek/NET8180.INF
Installing net8180
jeff@kitsune:~/Desktop$ ndiswrapper -l Installed ndis drivers:
net8180 driver present
```

 
P.s.: thanks for making a .deb

---

### Post by Burgundavia on 2005-08-04
Retrik, it is pretty easy to get stuff into Ubuntu. Contact the MOTUs in #ubuntu-motu on how to get it into Ubuntu.

Corey

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=kiddo]
**Edit:** tried removing and putting back my realtek driver, it did not work. Sad. *"Not a valid driver .inf file"*
Ndiswrapper still works.
 ```
jeff@kitsune:~/Desktop$ sudo ndiswrapper -i /home/jeff/driver-linksys-realtek/NET8180.INF
Installing net8180
jeff@kitsune:~/Desktop$ ndiswrapper -l Installed ndis drivers:
net8180 driver present
```[/QUOTE]


What ndiswrapper are you using? Ubuntus or a compiled one?

---

### Post by kiddo on 2005-08-04
Ubuntu's ndiswrapper, I especially wanted to get rid of the complicated (and unclean, in my taste) compiled one, even if it was newer. I prefer the synaptic way.

ndiswrapper-utils version is 0.12+1.0rc2-1 (hoary)
I have uploaded my chipset driver (discovered a long time ago that taking the driver directly from linksys was no good) here for your testing convenience if you want: [http://public.nanokron.info/upload/NET8180.INF](http://public.nanokron.info/upload/NET8180.INF)

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Burgundavia]Retrik, it is pretty easy to get stuff into Ubuntu. Contact the MOTUs in #ubuntu-motu on how to get it into Ubuntu.

Corey[/QUOTE]

Retrix is working under Oliver Grawert, a Motu.

We just need to help bug test and such.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=kiddo]Ubuntu's ndiswrapper, I especially wanted to get rid of the complicated (and unclean, in my taste) compiled one, even if it was newer. I prefer the synaptic way.[/QUOTE]

Ok. 

Let me file a bug report.

---

### Post by kiddo on 2005-08-04
I hope I was of some help ;) (don't forget to see my previous post, I edited it to include some more stuff for you)

---

### Post by Retrix on 2005-08-04
[QUOTE=kiddo]
**Edit:** tried removing and putting back my realtek driver, it did not work. Sad. *"Not a valid driver .inf file"*
[/QUOTE]

Hi,

Firstly thanks for starting this thread poofyhairguy.
Thanks for revealing a bug kiddo. The program expects the .inf extension to be lowercase. This will be fixed in the next version. For now, renaming the file will work.

Thanks for the ideas everyone.

-Sam

---

### Post by ubuntu_demon on 2005-08-04
good work Retrix
thnx for starting this thread poofy!

I don't own wireless stuff but I think a lot of users would really like this!

Should I recommend this the next time a user has problems with ndiswrapper ?

---

### Post by ssck on 2005-08-04
nice work

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=ubuntu_demon]
Should I recommend this the next time a user has problems with ndiswrapper ?[/QUOTE]

Not yet. Lets get some more testing done. When it is ready, it will be in the Universe.

---

### Post by pailhead on 2005-08-04
[QUOTE=poofyhairguy]Retrix was nice enough to give me what I really wanted for Christmas- a GUI ndiswrapper tool.

I got ahold of an Ubuntu laptop. A screenshot is attached.

Retrix is currently going through the proper channels. I was asked to build a presence for the tool in the forum to improve bug testing.

If people are interested enough, it will get its own third party forum.
[/QUOTE]

Can we get it for AMD64 machines? I've got a 64bit machine and this deb won't install...

---

### Post by Retrix on 2005-08-04
I'm not an expert on building deb packages (this was my first) but I will look into building an architecture independent deb. It is after all just a python program that should work on any platform.

Any particular errors that dpkg gives you?

Cheers,
Sam

---

### Post by blakamin on 2005-08-04
I'll give it a go in about 3 hours... if thats any help.

I'm away from my home network (at work :mad: ) and have just finished a fresh install on a new (to me) laptop, so I'll give it a go the moment I can get some internet access to this lappy... I'm running a dell l400 and a linksys wpc54g (or buffalo airstation, depending what I'm up to)

---

### Post by Retrix on 2005-08-05
[QUOTE=blakamin]I'll give it a go in about 3 hours... if thats any help.

I'm away from my home network (at work :mad: ) and have just finished a fresh install on a new (to me) laptop, so I'll give it a go the moment I can get some internet access to this lappy... I'm running a dell l400 and a linksys wpc54g (or buffalo airstation, depending what I'm up to)[/QUOTE]
 Please note that the current version will not automatically load the ndiswrapper module or run 'ndiswrapper -m' to have it autoload on bootup. This functionality will come in the next version.

---

### Post by blakamin on 2005-08-05
I actually keep getting ```
cannot accss archive: no such file or directory
```
so i might wait for your next version ;-)


after my reinstall... :-P

---

### Post by ubuntu_demon on 2005-08-05
[QUOTE=poofyhairguy]Not yet. Lets get some more testing done. When it is ready, it will be in the Universe.[/QUOTE]
 ok

---

### Post by SKLP on 2005-08-07
nice work :)

---

### Post by Retrix on 2005-08-09
Hi,

I've posted a new version up at [http://www.users.on.net/~spohlenz/ubuntu/ndisgtk_0.3-1_all.deb](http://www.users.on.net/~spohlenz/ubuntu/ndisgtk_0.3-1_all.deb).

Changes include:
 * It should now work on all architectures (packaging issue)
 * Help buttons removed for now (are they necessary?)
 * Modules automatically set to load on bootup
 * Menu icon in System->Administration->Windows Wireless Drivers

Thanks for all the comments so far,
-Sam Pohlenz

---

### Post by mobo on 2005-08-09
Sorry for being a complete newb here but could someone offer some insight as to this error I recieved and what I should do next ?

Unpacking replacement ndisgtk ...
dpkg: dependency problems prevent configuration of ndisgtk:
 ndisgtk depends on ndiswrapper-utils; however:
  Package ndiswrapper-utils is not installed.
dpkg: error processing ndisgtk (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ndisgtk

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=mobo]Sorry for being a complete newb here but could someone offer some insight as to this error I recieved and what I should do next ?

[/QUOTE]

You need ndiswrapper:

> sudo apt-get install ndiswrapper

---

### Post by mobo on 2005-08-09
I did that through synaptics. Then retried the first command and got a different piece of feedback. Something about it being locked..UGH

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=mobo]I did that through synaptics. Then retried the first command and got a different piece of feedback. Something about it being locked..UGH[/QUOTE]

close synaptic.

---

### Post by mobo on 2005-08-09
I rebooted as well. Then retried the first command and it all seemed to go. Now the second command..Hmmm, guess I need a driver file at this point...Any idea where I might find a wlan 1370 for a dell unit..?

---

### Post by mobo on 2005-08-09
I took the inf file from a windows download and put it in the home directory. The ran the second cammand, selected that driver and clicked the appropriate button. However I have the same image as you have posted in the first post saying that the gardware was not present..


Any thoughts ?

---

### Post by Retrix on 2005-08-09
[QUOTE=mobo]I rebooted as well. Then retried the first command and it all seemed to go. Now the second command..Hmmm, guess I need a driver file at this point...Any idea where I might find a wlan 1370 for a dell unit..?[/QUOTE]

Check out [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List).

-Sam

---

### Post by mobo on 2005-08-09
Ok I have the correct drivers in place and the ndisgtk reports so. Now I rebooted and there was still no wireless connection so I ask "what else please and thank you"

---

### Post by Retrix on 2005-08-09
[QUOTE=mobo]Ok I have the correct drivers in place and the ndisgtk reports so. Now I rebooted and there was still no wireless connection so I ask "what else please and thank you"[/QUOTE]

Now is the time to go into your network properties (System->Administration->Networking) and set up your (presumably) wlan0 network interface. You'll probably just need to set an essid, set to dhcp and activate. Good luck.

-Sam

---

### Post by MetalMusicAddict on 2005-08-09
Man, This is so sick. I just got my 60gig laptop drive back from RMA. Im gonna swap out the 30 in my Dell laptop and do a clean install of Hoary just to give this a try. Too cool. Hope it gets in the repo. ;)

Just so Im not mistaken; This will install the driver then I configure the card in the Network Preferences like normal and Ndiswrapper will load at start-up. Right?

---

### Post by mobo on 2005-08-09
And I thought my days frustrations were over....There is only the modem and ethernet connection there.. No wlan of any sort..

---

### Post by SKLP on 2005-08-09
This or something like this should IMHO be included in breezy+1.

---

### Post by mobo on 2005-08-09
I found the last remaining piece of the puzzle.

sudo gedit /etc/modules

Add ndiswrapper to the end of this, save and close. When your machine reboots, it will find the Wireless Adaptor and start it up. 


Thanks to all, I now get to fully experience the power of open source and perhaps even make the switch for good.

---

### Post by MetalMusicAddict on 2005-08-12
Ok. I just tryed this on a Dell Inspiron 2200 with a fresh install of Breezy Colony-2 using the bcmwl5.inf. I took the upgrades that Synaptic offered after install, then rebooted.

**-**I used this: [http://www.users.on.net/~spohlenz/ubuntu/ndisgtk_0.3-1_all.deb](http://www.users.on.net/~spohlenz/ubuntu/ndisgtk_0.3-1_all.deb) version.

**-**Installed with the "Install .DEB with Right-click" script found on the fourms.

-Ran "gksudo ndisgtk" to launch the app.

**-**Installed the driver just fine but after a reboot it didnt show in the Network config GUI. So I "sudo modprobe ndiswrapper" to run ndiswrapper. Then it came up.

**-**Then like mobo said "sudo gedit /etc/modules" Add ndiswrapper to the end of this, save and close." I also had to manually config the "/etc/network/interfaces". Reboot.

**-**Configure away.

I have a spare drive now so if you need something tested I dont mind. ;)

---

### Post by mobo on 2005-08-12
Glad you have it as well. In addition there is also a thread in relation to the touchpad issue locate here so feel free...
[http://www.ubuntuforums.org/showthread.php?t=52920](http://www.ubuntuforums.org/showthread.php?t=52920)

---

### Post by MetalMusicAddict on 2005-08-12
[QUOTE=mobo]Glad you have it as well. In addition there is also a thread in relation to the touchpad issue locate here so feel free...
[http://www.ubuntuforums.org/showthread.php?t=52920](http://www.ubuntuforums.org/showthread.php?t=52920)[/QUOTE]
Thanx. That was annoying. ;)

---

### Post by mobo on 2005-08-12
Just repaying for some assistance i recieved. You should also bookmark this page:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by greenwom on 2005-08-12
I just installed Hoary on a new (old) Latitude LS, I'll give this a wirl and see how it goes.  I've already gotten a Linksys WPC11 working on my sony but have yet to get it up and running on the Latitude so...  Looks like fun

 \\:D/

---

### Post by Retrix on 2005-08-18
Hi,

I've just uploaded the latest version to [http://users.on.net/~spohlenz/ubuntu/ndisgtk_0.4-1_all.deb](http://users.on.net/~spohlenz/ubuntu/ndisgtk_0.4-1_all.deb). Changes include:
 - a button to load the network configuration tool
 - automatically loads the ndiswrapper module and sets it to load on boot

Whilst these improvements are relatively small, I think they will make a significant difference in terms of ease of use. I would be particularly interested in hearing how people on new installs go.

Again, thanks for all the feedback,
Sam Pohlenz

---

### Post by MetalMusicAddict on 2005-08-18
Cool. Ill try it on the Colony-3 release today. I did a fresh install last night. ;)

---

### Post by greenwom on 2005-08-20
I tried it on the Latitude LS and no luck, not the GUI's problem.  I had to compile ndiswrapper from source. (Still doesn't work).  GUI looks good

---

### Post by Retrix on 2005-08-23
Thanks to my SoC mentor, Oliver Grawert, ndisgtk is now in the Breezy Universe repositories. If you are running Breezy, its now a simple matter of enabling universe and running 'sudo apt-get install ndisgtk'. Thanks again to everyone for all the feedback. If you have any more, please don't hesitate.

---

### Post by poofyhairguy on 2005-08-23
[QUOTE=Retrix]Thanks to my SoC mentor, Oliver Grawert, ndisgtk is now in the Breezy Universe repositories. If you are running Breezy, its now a simple matter of enabling universe and running 'sudo apt-get install ndisgtk'. Thanks again to everyone for all the feedback. If you have any more, please don't hesitate.[/QUOTE]

awesome.

---

### Post by Hammer93 on 2010-03-25
Hello i used this today to try and get my sony vaio linked to the  net but ive installed it correctly i get to configure network but it doesnt say wlan0 just eth0 and ppp0 any help

p.s ndisgtk says that my wifi dongle is present and ive installed the drivers

---

