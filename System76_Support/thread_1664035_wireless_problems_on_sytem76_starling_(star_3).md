---
title: "wireless problems on sytem76 starling (star 3)"
date: 2011-01-10
forum: System76 Support
---

### Post by lapedestrienne on 2011-01-10
I must be doing something dumb...

I've been having problems with my starling for a couple months now. I crashed it by mis-installing a grub update, so did a clean reinstall of the OS. However the disk I borrowed from a friend contained an older version of Ubuntu (8.10 maybe?), and I couldn't get it to connect to the internet. I figured it was the OS not playing nice with my wireless card, so did yet another clean reinstall, this time using netbook remix 10.10. Oops, I know, I shoulda stuck with the 10.4 originally on the machine. Could this be my problem?

I went into Users/Groups and enabled wireless access for all users, then rebooted. The wireless light blinks orange when the computer boots, then goes dead. The machine recognizes available networks and tries to connect, but it just gives me that little blue circle-y image and then, after several minutes of trying, tells me I am disconnected and offline. Right now I have a four bar connection and my Macbook is online just fine, but the starling refuses to connect.

I am almost totally reliant on my computer's wireless--I don't have internet service at home, so am always using wifi out in the world. It'll be a couple days before I can get to an ethernet cable at someone else's house. What are folks' recs? Should I wipe it clean again and put 10.4 back on? Should I wait until I can hook up to a wired connection and check for updates? Any other ideas? 

tia.

---

### Post by lapedestrienne on 2011-01-10
erg. bet this is it (from knowledge76):

** Wifi Information **

 After attempting to restore my [Star4]("http://knowledge76.com/index.php?title=Star4&action=edit") netbook using the recommended [10.04 Luicd Lynx]("http://releases.ubuntu.com/lucid/") netbook image I had trouble with my Wifi. 
I experienced problems such as: 
 
[LIST]
[*] Wifi not connecting / constantly asking for AP password
[*] Wifi connecting (pulling a DHCP lease) but not routing packets
[/LIST]
 As it turns out I did not have a wired connection available to me  when I restored so I couldn't perform updates (As I assume System76 does  before shipping the system).  Update your system with a wired  connection and then Wifi works as expected. 
   Kernels   2.6.32-21-generic Broken Installed from CD   2.6.32-27-generic Works Installed after update (On 5-Jan-2011)   [Matt Price's PPA Package]("https://launchpad.net/%7Ematt-price/+archive/mattprice") Fixes -21 kernel Extra unmaintained download  If you can't get to a wired spot then you can also download Matt  Price's PPA that will install just the updated Wifi driver to allow you  to do a full update.  NOTE: This package hasn't been updated since  March-2010 so I would only use it to update the mainline Ubuntu kernel. 
   Retrieved from "[http://knowledge76.com/index.php/Restoring_Your_Netbook](http://knowledge76.com/index.php/Restoring_Your_Netbook)"

---

