---
title: "Does such a distro of linux exist ?"
date: 2011-09-26
forum: The Cafe
---

### Post by rishi_singh on 2011-09-26
I want a distro which i can use easily. I installed ubuntu 10.04 but i cant use wifi and make my windows partition invisible inside ubuntu. I wasted 12 hours on this and still no success :(
Is there any distro which will handle all the basic stuff like running devices and produce a system that is ready for use ? I dont want to spend 12 hours regularly, just trying to make things work and ending up failing all the time. I would rather focus on learning about the os instead of being bogged down by drivers and such.

Any suggestions ? Or should i delete linux and forget it forever. I guess learning mac would be better.

---

### Post by aysiu on 2011-09-26
Probably has less to do with the distro and more to do with the kernel. Linux is notorious for having hardware regressions. A wireless card will work fine in one version, and then the next version it won't connect or will drop signal intermittently or take forever to reconnect after resume from suspend-to-RAM. [quote=rishi_singh]I would rather focus on learning about the os instead of being bogged down by drivers and such.

Any suggestions ? Or should i delete linux and forget it forever.[/quote] Yes, you're better off deleting Linux and forgetting it. As I mentioned before, it's possible that the new version of Ubuntu will support your wireless card out of the box... and then the next version after that will leave you spending 12 hours trying to get it to work again.

Granted, I've had wireless problems in both Windows and Mac OS X, but they tend to be either present or absent. In Ubuntu even if you have a theoretically "supported" wireless card, the constantly changing kernels can give you extremely varied performance/compatibility issues.

---

### Post by drawkcab on 2011-09-26
What hardware are you using?  If it's relatively new stuff then you might need to wait a week or so for the updated kernel in 11.10.

---

### Post by aysiu on 2011-09-26
> **drawkcab said:**
> What hardware are you using?  If it's relatively new stuff then you might need to wait a week or so for the updated kernel in 11.10.
You can see in the actual support thread:
[10 Hours wasted and unable to use wifi.](http://ubuntuforums.org/showthread.php?p=11286002#post11286002)

The current thread is about whether a magical "supports every piece of hardware all the time" Linux distro exists or not. The above-linked thread is for helping the OP with the actual specific problem with Ubuntu.

---

### Post by earthpigg on 2011-09-26
I understand the frustration expressed in the OP, and here's the policy I've come to adopt:

If wifi doesn't work from the LiveCD, I don't install.

If I do install, and then I can't get my video card up and running in 10 minutes or so, I pick another distro/release and try again.


Don't worry about the distro. They are all similar enough that loyalty to one over the other doesn't make much sense. Changing distros only means that you may get a different DE, some different pre-installed software, and a different default theme.

The more I've used Linux, the more solid my conclusion that "Mainstream Desktop Linux is Mainstream Desktop Linux" becomes, and no amount of pretty desktop wallpapers or slightly different package management is going to change that.

---

### Post by rishi_singh on 2011-09-26
> **drawkcab said:**
> What hardware are you using?  If it's relatively new stuff then you might need to wait a week or so for the updated kernel in 11.10.

I have mentioned my hardware below. But i have one question - Can i put a request to the makers of ubuntu to create drivers and such for my system in their future release ?
Are there any companies that can do this for a (reasonable) fee and continue to provide the updated drivers as ubuntu is upgraded ?

PS : I am eager to learn ubuntu, so i can bear the pain for a few more days. After that, i will simply delete it and enjoy my little world of windows and malware. Its painful, but at least i can do basic stuff on windows.

hardware :
1x1 11b/g/n Wireless LAN PCI Express Half Mini Card Adapter
Adapter Type  :  IEEE 802.11 wireless
NetBIOS over TCP/IP  :  Enabled via DHCP
NETBIOS Node Type  :  Hybrid node


Operating System
    MS Windows 7 Home Premium 64-bit SP1

---

### Post by drawkcab on 2011-09-26
> **earthpigg said:**
> I understand the frustration expressed in the OP, and here's the policy I've come to adopt:

If wifi doesn't work from the LiveCD, I don't install.

If I do install, and then I can't get my video card up and running in 10 minutes or so, I pick another distro/release and try again.


Don't worry about the distro. They are all similar enough that loyalty to one over the other doesn't make much sense. Changing distros only means that you may get a different DE, some different pre-installed software, and a different default theme.

The more I've used Linux, the more solid my conclusion that "Mainstream Desktop Linux is Mainstream Desktop Linux" becomes, and no amount of pretty desktop wallpapers or slightly different package management is going to change that.

Sound advice.

---

### Post by polardude1983 on 2011-09-26
One day i decided instead of trying to get linux to work with my usb wifi. I just got a usb wifi that worked automatically with linux. saved me a heck of a lot of trouble.

---

### Post by 3Miro on 2011-09-26
Hm, a distribution that will give you 100% hardware support out of the box. I can think of Ubuntu, on my sister's laptop you can get wifi, 3D effects and everything else right out of the live CD. I should be able to do that on my new System76 laptop (scheduled to come today).

If you want to use an OS, you should first of all get compatible hardware.

---

### Post by aysiu on 2011-09-26
> **3Miro said:**
> 
If you want to use an OS, you should first of all get compatible hardware. You can probably tell from my earlier reply that this has not been my experience at all. I've had "compatible" hardware that works with one release and then is broken for the next release and then works for another. Or suspend will work and wireless won't, and then wireless will work but suspend won't. This has happened on multiple computers.

---

### Post by rishi_singh on 2011-09-26
> **polardude1983 said:**
> One day i decided instead of trying to get linux to work with my usb wifi. I just got a usb wifi that worked automatically with linux. saved me a heck of a lot of trouble.

Yes, but then i dont want to buy a usb wifi just for linux.

---

### Post by 3Miro on 2011-09-26
> **aysiu said:**
> You can probably tell from my earlier reply that this has not been my experience at all. I've had "compatible" hardware that works with one release and then is broken for the next release and then works for another. Or suspend will work and wireless won't, and then wireless will work but suspend won't. This has happened on multiple computers.

In the past several years I have worked with 3 laptops (one needs prop broadcom, one needs prop nvidia, one doesn't need anything) + 4 desktops (mostly nvidia video + AMD CPU). Those belong to me or immediate family. I have used mostly *ubuntu, but also many other distros.

The only hardware regression that I have experienced was with a kernel update once that broke a driver and suspend became iffy once for one of the laptops.

I guess the experience can be different and I am not denying that hardware regressions happen, I just don't think they are that common. OP's case also doesn't seem to be about a regression.

---

### Post by grahammechanical on 2011-09-26
Hi welcome to the forums. You ask:

> Are there any companies that can do this for a (reasonable) fee and continue to provide the updated drivers as ubuntu is upgraded ?


There are plenty of developers right now working to produce drivers. If they did not do this then Linux would not exist.

The problem is there because hardware makers are not willing to reveal details of the hardware to the developers. They do not want to give information that could help their commercial rivals.

Are you willing to buy hardware and give it to a developer so they can test out the drivers? Or do you expect this cost to be met by the developer? New products are coming out all the time.

If it was a law in all the world that computers be sold without an operating system pre-installed then you will notice that Microsoft will be having the same issues as Linux has now.

I remember when this was true in the past. People who purchased the latest Windows found that there were not any drivers for their printers and scanners. Yes, in the past Windows broke their computers. Have you not noticed that with every piece of hardware the maker also supplies drivers for windows? Supposing you were using Vista would you buy a scanner if it only worked with Windows 7 and not with Vista? Yet you do not want to buy hardware that works with Linux.

When Microsoft released Windows Media Center it would not allow anyone to buy the product. Microsoft would only sell (licence) it when it was pre-installed on a machine and the supplier had the responsibility of making sure that the product was fit for sale. This was because Microsoft did not want the bad publicity of people complaining that Windows Media Center did not work on their machine and can they have their money back.

Having used advertising to associate its product with the PC, Microsoft's latest adverts are suggesting that people buy a new computer to get Windows 7. In this way Microsoft avoids the issues that Linux has.

And yet I have been using Ubuntu since 2007 and I am happy with it. and I did not pay anything even to get drivers that work.

You say that you want to learn but you also want an operating system that just works and works like Windows so that you do not have to learn anything.

So, what can anyone teach you?

Regards.

---

### Post by t0p on 2011-09-26
> **rishi_singh said:**
> 
PS : I am eager to learn ubuntu, so i can bear the pain for a few more days. After that, i will simply delete it and enjoy my little world of windows and malware. Its painful, but at least i can do basic stuff on windows

If you really are eager to learn about Linux, why delete your Linux partition? You can keep the Windows partition too, and use it as necessary, and use the Linux partition where possible and generally use it as a test partition. I don't see why it has to be a case of "either one or the other".

---

### Post by Copper Bezel on 2011-09-26
[QUOTe=rishi_singh]1x1 11b/g/n Wireless LAN PCI Express Half Mini Card Adapter
Adapter Type : IEEE 802.11 wireless
NetBIOS over TCP/IP : Enabled via DHCP
NETBIOS Node Type : Hybrid node[/QUOTE]
That's the spec, but not the exact card. (Tells us how the card talks to the network, not how it talks to the motherboard, as it were.) What's the model # on the PC itself? You can usually find the WLAN chipset from that.

[QUOTe=polardude1983]One day i decided instead of trying to get linux to work with my usb wifi. I just got a usb wifi that worked automatically with linux. saved me a heck of a lot of trouble.[/QUOTE]
I had spotty support for the wireless card on my first Ubuntu machine and did this to compensate. Signal strength from the tiny card compared against that of an antenna strung through the display panel was atrocious. Having the unsightly growth attached to my USB port was irritating. Then I would bump it and lose the connection. 

No offense intended, and I'm glad it worked out for you, but while it might be applicable for a desktop rig, I wouldn't suggest this solution for a laptop to someone who had killed my dog.

---

### Post by t0p on 2011-09-26
:(

---

### Post by rishi_singh on 2011-09-27
> **Copper Bezel said:**
> That's the spec, but not the exact card. (Tells us how the card talks to the network, not how it talks to the motherboard, as it were.) What's the model # on the PC itself? You can usually find the WLAN chipset from that.


Realtek Semiconductor Corp.
rtl8192ce - copied this from the driver file. 
I hope this is useful information. I am not an expert at these things, so please bear with me.

---

### Post by Copper Bezel on 2011-09-27
That's very useful! It looks like there's a bug filed for this card [_here_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/686333"). Remind me - are you using the latest release of Ubuntu (11.04) or an earlier one? It looks like the driver for this card was added in the version of the kernel that shipped with 11.04, so it should work out of the box, but according to at least one person, the performance isn't ideal. If it's not working out-of-the-box for you at all on 11.04, I'm not sure what's up.

On earlier versions, the driver needs to be installed manually from the Realtek page.

---

### Post by rishi_singh on 2011-09-27
> **Copper Bezel said:**
> That's very useful! It looks like there's a bug filed for this card [_here_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/686333"). Remind me - are you using the latest release of Ubuntu (11.04) or an earlier one? It looks like the driver for this card was added in the version of the kernel that shipped with 11.04, so it should work out of the box, but according to at least one person, the performance isn't ideal. If it's not working out-of-the-box for you at all on 11.04, I'm not sure what's up.

On earlier versions, the driver needs to be installed manually from the Realtek page.

Deleted 10.04. Did stuff to make its partition visible and usable in win  7. But now i cant instal 11.04 in that partition. It throws up options i  cant understand. Besides, the wifi did not work with live cd for 11.04.

Any linux drivers for my card ?

---

### Post by Copper Bezel on 2011-09-27
Odd. I guess not, then. It should have just worked with the 11.04 LiveCD. The bug report links to the [_driver from the Realtek website_]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") for earlier versions, but you'd have to compile it (a couple of commands from the terminal), and there's no guarantee that your card isn't just being mis-identified somehow, given that it didn't work in 11.04.

---

### Post by earthpigg on 2011-09-27
> **rishi_singh said:**
> Besides, the wifi did not work with live cd for 11.04.

Any linux drivers for my card ?

If you've tried two or three distro's and wifi hasn't worked from the LiveCD, I suggest going back to Windows and trying again in 6 months (or with a different computer).

Linux is great and all, but Windows isn't so horrible that the transition is worth 40 hours of arduous labor.

---

### Post by rjbl on 2011-09-27
> **rishi_singh said:**
> I want a distro which i can use easily. I installed ubuntu 10.04 but i cant use wifi and make my windows partition invisible inside ubuntu. I wasted 12 hours on this and still no success :(
Is there any distro which will handle all the basic stuff like running devices and produce a system that is ready for use ? I dont want to spend 12 hours regularly, just trying to make things work and ending up failing all the time. I would rather focus on learning about the os instead of being bogged down by drivers and such.

Any suggestions ? Or should i delete linux and forget it forever. I guess learning mac would be better.

Hi rishi_singh

You'd get much more out of life if you settled down to exploring the capabilities of GNU/Linux, try Ubuntu 10.04LTS. You seem, from your recent postings, merely to be troll. Wastes people's patience; doesn't make you any friends.

Bye now.

rjbl

---

### Post by Copper Bezel on 2011-09-27
Frankly I'm not certain that he really needs it, man. His main use case for Linux is a [_rather dubious security procedure_]("http://ubuntuforums.org/showthread.php?t=1850171") he's been doing - but I guess you posted on that as well.

As for the frustration, I can understand it; a lot of people end up looking into Linux because someone sold it on them as an easy, magical solution to all their Windows problems. Obviously, it's not; it's another operating system with problems of its own.

It's the same frustration people experience when they try the latest version of Ubuntu from the Ubuntu website, experience a problem, and then come to the forums to have people criticize them for not sticking with the LTS. Well, the LTS isn't what's marketed; what do you expect? 

Ditto this. Sure, Linux *is* easier than Windows - if you're just as familiar with it as you are with Windows, if your hardware is supported, if you don't need applications that are only distributed for Windows, if, if, etc., etc.

Edit: And as earthpigg is saying, if the device works better on Windows, it works better on Windows. If you don't have any pressing need to use Linux on it, why stress?

---

### Post by Shpongle on 2011-09-27
@Copper Bezel , good points.

@ OP , I would say try fedora if you still haven't made up your mind , I have found in certain situations that it supports more than ubuntu out of the box.

---

### Post by 3rdalbum on 2011-09-27
Try a different distribution. I hear good things about Fedora.

Ubuntu is easy if your hardware is supported. It looks like yours isn't yet. Fedora might have the required support for your wifi card.

Alternatively, try downloading the beta of Ubuntu 11.10.

Windows just tends to be complicated in lots of different ways.

---

### Post by Canis familiaris on 2011-09-27
> **rishi_singh said:**
> 
Any suggestions ? Or should i delete linux and forget it forever. I guess learning mac would be better.
I'll suggest this.

---

### Post by rishi_singh on 2011-09-29
> **Canis familiaris said:**
> I'll suggest this.
No, i am diving into linux now.

---

### Post by kvv_1986 on 2011-09-30
Hey! If you want to learn Linux, but you are having so much trouble with your hardware, you should install it in a virtual machine, and you will be just fine!

Learning a mac is a decent option too, provided you know what you want to learn and where to look for it.

---

### Post by Copper Bezel on 2011-09-30
The WiFi problem apparently sorted itself out in a kernel update (initially it was a fresh install from the CD, and the update notification didn't kick in for some reason) so the hardware might be less a problem.

Glad to hear you're staying on, rishi! Particularly if you're really interested in making a learning experience out of it (and thus figuring out what you can break so you can fix it again,) fun and headaches in equal measures await. = D

---

