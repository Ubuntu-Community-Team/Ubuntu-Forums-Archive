---
title: "Turn one computer into more of them"
date: 2005-04-05
forum: The Cafe
---

### Post by UbuWu on 2005-04-05
After seeing [this](http://www.userful.com/) , I saw [this](http://www.ltn.lv/~aivils/) website. Has anybody tried this with Ubuntu? It looks a bit complicated to setup, but I think it can potentially save a lot of money.

---

### Post by totalshredder on 2005-04-05
[QUOTE=UbuWu]After seeing [this](http://www.userful.com/) , I saw [this](http://www.ltn.lv/~aivils/) website. Has anybody tried this with Ubuntu? It looks a bit complicated to setup, but I think it can potentially save a lot of money.[/QUOTE]
Sounds like a good idea; but I'd end up having too much fun closing other people's windows. 
Them "Who did that!"
Me "Must have been that bob kid"

It could be good if the computers aren't used often; and you wanted to place them in every room, like at your own home. But if you planned on more than one person using it... good luck my friend.

Luke

---

### Post by az on 2005-04-05
You can have as many X sessions running as you like.  You would need a video card for each monitor.  It is a pain to set up.  But it can be done out-of the box with any Xwindows system.

---

### Post by Jad on 2005-04-05
but you will need to have a very good hardware.

---

### Post by jdong on 2005-04-05
[QUOTE=Jad]but you will need to have a very good hardware.[/QUOTE]
Untrue. I have set up Ubuntu based FreeNX systems with relatively little. The central server was a 1.2GHz Athlon with 512MB RAM, and it was handling 10 users simultaneously running GNOME.

The clients basically ran a minimal install of Ubuntu, with an X server and an NX client.

---

### Post by TravisNewman on 2005-04-05
[QUOTE=azz]You can have as many X sessions running as you like.  You would need a video card for each monitor.  It is a pain to set up.  But it can be done out-of the box with any Xwindows system.[/QUOTE]
 yes, but can you have an independent keyboard and mouse?

---

### Post by jdong on 2005-04-05
Sure, if you have a nice USB hub & usb input devices.

But seriously, get separate thin-client systems... They don't need to be any more powerful than a basic Pentium I.

---

### Post by UbuWu on 2005-04-05
[QUOTE=panickedthumb]yes, but can you have an independent keyboard and mouse?[/QUOTE]

That is the whole thing that ruby backport page is about. You can use one computer with several graphic cards with monitors connected to them and have a seperate keyboard and a mouse for alk of them and you probably won't even notice that you are using the same computer during every day use.

---

### Post by TravisNewman on 2005-04-05
Yeah I know. I was replying to azz saying that you could do this with vanilla xorg. I don't really see the point of ruby if this is already included, but I've never heard of it being included... but yeah, thin clients would be much better, but not as cheap ;)

---

### Post by Brunellus on 2005-04-05
naive question:  would it be possible to have a hydra-headed thin-client using this system

as in, one box that acts as a client to a fat server--with lots of displays & keyboards sprouting out of it?

Even without my (mis)understanding of the concepts, the multiple displays idea strikes me as a great way for libraries to increase the number of catalogue terminals they make available, say.

---

### Post by Jad on 2005-04-06
I'm shocked, yet another reason to respect linux.
I'll try to set it up and see how it works.

---

### Post by UbuWu on 2005-04-06
[QUOTE=Jad]I'm shocked, yet another reason to respect linux.
I'll try to set it up and see how it works.[/QUOTE]

Keep us updated...  ;)

---

### Post by nad on 2005-04-07
Am I to understand that the Ruby patch is applied to the current Hoary kernel, or do I still need to patch my sources and roll my own? The Hoary multiseat package seems to supply only config tools!

I currently have a local multiuser setup. Four GeForce cards, monitors, keyboards and mice. No stability problems. Works like a charm. I understand that a main reason that the patch has not gone mainstream is security. Event device handling is still being worked on.

---

### Post by UbuWu on 2005-04-07
[QUOTE=nad]I currently have a local multiuser setup. Four GeForce cards, monitors, keyboards and mice. No stability problems. Works like a charm. I understand that a main reason that the patch has not gone mainstream is security. Event device handling is still being worked on.[/QUOTE]

Can you tell us how you did this?

And what does the multiseat package do?

---

### Post by nad on 2005-04-07
Glad to see interest in expandng the possibilities of the pc!

There is a HOWTO at tldp.org. Look for XFree local multi-user.

The ruby (backstreet ruby for 2.4.x kernels) kernel patch allows interception of events  from multiple keyboards to be bound to specific virtual terminals. The latest XFree and Xorg Xservers are now including this ability with the isolateDevice config file option. Older X servers need to be additionally patched. Basically, you craft an X config file to bind specific mice, graphics cards and monitors to their own screen layouts. Of course there is more to it than this. One accepted method is to alter the hotplug subsystem to automatically create your added devices, then you supply symlinks and binding instructions to the device addresses with config files. Keyboards are another matter. They are handled through the ruby patch. Using a 2.6.x kernel, the controlling terminal is assigned the use of virtual terminals 1-17. The next x screen is number 18, etc. The second keyboard, VT1, is automatically bound to the second x screen, VT18. This is of course oversimplified, and yes I've read that this method should work with up to 16 layouts!

What the multiseat package does I don't know. I will try it out this weekend. As far I have researched, it makes it easier to find and configure the several config files you need. If some one knows, please post. I will contact the package maintainer for further info. I have been doing this for several months now the hard way. Patching pristine kernel source and X servers and rolling my own distros based on debian. If ubuntu can do this out of the box the world will be a better place.

I will continue to monitor this thread and offer any help and advice I can. Good luck.

Dan M

---

### Post by Burgundavia on 2005-04-07
Having used Userful's system, I will say it is quite nice. The local library runs them.

Corey

---

### Post by nad on 2005-04-07
A quick review of the Userful Free Trial Download indicates that they may be in violation of the GPL. Unfortunately, the EULA and NDA I was required to agree to forbids me from discussing the contents of the software ;-).

I have filed a license violation notification with the FSF.

Dan M

---

### Post by nad on 2005-04-07
Sorry for the bad form in replying to my own post. I was a little hasty in noting the license violation. It is all the rage these days.

In as much as all the software that Userful distributes is in binary form, I can not determine it's heritage. The list of supplied drivers however looks amazingly similar to the XConsortiums' list of drivers. Only three copyright notices are included. All noting that the deb packages were debianized by alien and copyright Userful. They clearly refer to the xserver as Xorg. Therefore, I assume that the graphics drivers are also MIT licensed. I can not believe that one company has come up with some 2-3 dozen of their own working compatible drivers.

Although this makes the drivers and xserver free to distribute as you wish, the lack of attribution is in clear violation of the MIT license and unethical.

Dan M

---

### Post by sgbeamer on 2005-04-16
I've been trying to do this in my very limited spare time for a couple of months.  I can get 2 screens going but I'm having trouble separating the keyboards and mice even with the udev rules.  I have tried in Ubuntu and in Fedora Core 3 on a spare hard drive.   I also downloaded the Userful trial and had no luck getting that to work because if froze up when configuring (on 2 different boxes).  I am running a brand new box from Monarch with the following hardware:

Althon 64 3.0 GHz
1G RAM
Dual NVidia cards with Nvida drivers (MX4000 AGP and FX5500 PCI) 128 Mb each
200G SATA drive

If anybody gets theirs working, please let me know.

---

### Post by nad on 2005-04-16
I have no trouble doing this with a ruby patched 2.6.0 kernel, debian sarge and the XFree86 x server. I am still playing with the later kernels and patches and xorg.

The full fledged desktop environments are throwing all sorts of dependency problems. I get a broken gnome desktop. However, the simpler window managers work like a charm.

The xorg x server is also causing problems. Some cards will initialize properly with the isolateDevice option. Some will initialize only without the iD option, reading the address from the busID conf line.

I am using devfs with the modified input.rc and input.agent scripts with hand configured kbd.conf and mouse.conf files. I don't think udev is quite up to it yet, besides, I have a stable configuration without it. Remember, everybody using the system has to plug their devices into the one box and with 2 ps/2 and 6 usb ports being used there isn't much left. Adding a hub and couple of more devices isn't a problem. udev will be great when it can manage automagic plugins from a thin client. This is the future. Right now I have a system stable enough for a computer teaching lab, conference table setup, other public venues, etc without the added expense of the thin clients. And yes, with 4 four port graphics cards and additional usb hubs you should be able to get 16 xservers from one box. If you would like to donate the cards, I will send you a picture of it running ;-)

Dan M

---

### Post by opensensesolutions on 2005-04-21
for those who are too busy to do-it-yourself by following a guide like
[http://www.tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/](http://www.tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/) , check out
my company at [http://groovix.com](http://groovix.com)  for multi-user computers.

Userful's apparent violation of the MIT license, if what Dan says is correct, is very troubling.  If they can't even give credit to someone else's code that they are trying to profit from, it makes you wonder what other code including GPL code they are using without properly redistributing the modified source code.

Unlike Userful, everything we do it open source, not to mention a lot cheaper.  Instead of charging $100 PER USER upfront plus another $30/user/year just for the software license, we offer our software standalone with support for only $50/year for as many users as you want.  We also sell high quality hardware (Antec quiet cases, DFI motherboards, etc.) directly from our site.  Currently we use Debian, but we are working on offering Ubuntu in the next few weeks.  Our company started at the same time and with a lot of the same goals as Ubuntu, and now Ubuntu has done a lot of our work for us.   Once we switch to Ubuntu, we might be able to release some easy to use Ubuntu packages for those who wish to create a multi-user setup themselves.  I'll be sure to post some more as Ubuntu support develops.  In the mean time I'd be happy to answer any questions you might have about multi-user setups.  You can also send me email 
at [email]ubuntuforums@groovix.com[/email] in case I don't check this forum all the time.

---

### Post by mslibrary on 2005-05-08
Hello,

I was looking for Groovix @ $50/year with 1 year support but can't find it anywhere on your site.  I see updates for $50/year and support for $99/year, but no software.  Where is it?

Can I download it and try it out first?  Where is the source code?


Thank you!

---

### Post by opensensesolutions on 2005-05-18
Sorry for the confusion mslibrary, here is a direct link to the updated description:
[http://opensensesolutions.com/catalog/product_info.php?cPath=22&products_id=30](http://opensensesolutions.com/catalog/product_info.php?cPath=22&products_id=30)
That includes a DVD, updates, and standard support for 1 year.
We do not currently have a free trial download as the bandwidth would be very expensive, and it will not work on most people's systems anyways without modification.
The source code for everything is on the DVD.  We have also made the key scripts available separately for DIYers at
[http://groovix.com/linuxconsole.html](http://groovix.com/linuxconsole.html)
All the interesting advancements that we've made are all there.

If you don't have the specific hardware that we support and don't plan on buying new hardware anytime soon, I'd highly recommend you start creating a multi-user setup yourself from scratch using:
[http://www.tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/](http://www.tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/)
or waiting until we are ready with an add-on for ubuntu to enable multiple users.
We are working on Ubuntu/Kubuntu support now, but there are many issues to be resolved.  Ubuntu has become very different than standard Debian Sid.  
We have just announced a new mini desktop system using Ubuntu, 
[http://ubuntupc.com/products.html](http://ubuntupc.com/products.html)
but there is no multi-user support yet (definitely by Breezy but hopefully sooner)
If you have any other questions, you can email us directly for a quicker response as we only check these forums occasionally.
Thanks,
Mike

[QUOTE=mslibrary]Hello,I was looking for Groovix @ $50/year with 1 year support but can't find it anywhere on your site.  I see updates for $50/year and support for $99/year, but no software.  Where is it? Can I download it and try it out first?  Where is the source code? Thank you![/QUOTE]

---

### Post by DaJL on 2005-06-04
Could this work with a TV out. 
I have a gforce2 that currently works with something like this:

```

Section "ServerLayout"
    Identifier  "Layout0"
    Screen 0 "Screen 0"
    Screen 1 "Screen 1" RightOf "Screen 0"
    InputDevice "Mouse0" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "ATIRemote" "CorePointer"
EndSection

```

But I would like to be able to have someone control the TV  while another works on the computer simultaneously.

I want:

1-  TV is to be able to control freevo with the ATIRemote which is seen as /dev/input/mouse1. 

2- The keybord and mouse for use on the normal monitor.

So I need these two server layouts to run simultaneously:

```

Section "ServerLayout"
    Identifier  "Layout1"
    Screen 0 "Screen 0"
    InputDevice "Mouse0" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

Section "ServerLayout"
    Identifier  "Layout2"
    Screen 1 "Screen 1"
    InputDevice "ATIRemote" "CorePointer"
EndSection

```

Can I get this to work since the tv-out and the monitor out are both on BusID  "PCI:1:0:0"   or do I need to put in another video card?

---

### Post by SunBurnt on 2005-11-04
The hydra setup is the best idea for closely grouped workstations, single workstation thin clients would be for remote single users.

How about pxe booting a diskless hydra setup PC from a server?

Goes as far as you can to eliminate hardware, & puts all software on the server thus reducing IT people & effort to service the setup.

The Groovix setup seems to be HD based (I'm not sure), so it reduces the hardware & service, but not as much as diskless booting from a server.

This is what I'm looking to do, anyone interested post back & we'll share ideas.

---

