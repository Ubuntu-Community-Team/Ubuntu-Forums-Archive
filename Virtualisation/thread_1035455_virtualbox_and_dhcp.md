---
title: "virtualbox and dhcp"
date: 2009-01-09
forum: Virtualisation
---

### Post by PuK84 on 2009-01-09
I have a really bizarre problem using virtualbox. Im running kubuntu intrepid with KDE4 (maybe thats the problem ;)) and the VM works with only a slight problem. I can load network shares, surf net, etc however the IP is one designated by virtualbox.

When i set up a relay using dhc3relay it gets the IP from the dhcp server, but i can not access the net or any network shares so even though it has the right ip its like its isolated from everything. 

Any ideas on how to fix it?

Also, i have tried using IPs for webpages and it doesn't work and neither do the network shares so its not a DNS problem.

---

### Post by Jose Catre-Vandis on 2009-01-09
You need to have a good read of the help pages in VirtualBox about  "Host Interfaces" which is hard to set up but works OK once done. Also check my sig for a couple of howtos on host interface and wireless networking with Virtualbox.

By default VBox provides its own subnet with a NAT providing access to the internet, so won't see anything on your local area other than shared folders you setup.

---

### Post by PuK84 on 2009-01-09
HowTo looks awesome. i will try it when i get home (at work at the moment). i will let you know what happens :D

---

### Post by PuK84 on 2009-01-11
ok. i tried what your howto suggested and it proceeded to kill the network settings for the pc. kept saying it couldn't find tap0. this is what i put in but i sorta found the formatting of the howto a bit confusing.

also, when you wrote name.mynetwork.loc next to uml_proxy_arc i really had no idea what you meant.

this is what i wrote to kill the settings.

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#virtual network devises
auto tap0
iface tap0 inet dhcp
tunctl user puk
uml_proxy_arp 201.150.194.17
uml_proxy_ether eth0

#network bridge interface
auto br0
iface br0 inet dhcp
bridge_ports eth0 tap0
bridge_maxwait 0


any suggestions?

---

### Post by Jose Catre-Vandis on 2009-01-12
What's that IP address you are using, is it your internal LAN addressing or your internet IP? ARIN whois tells me its owned by LACNIC in Montevideo?

---

### Post by bodhi.zazen on 2009-01-12
What version of Virtualbox are you using ?

The latest release, the PUEL version, from the virtualbox web site, not the OSE from the ubutntu repositories, SIGNIFICANTLY CHANGED networking and bridged networking now works "out of the box" without additional configuration.

See the sticky, ie the mega thread, for how to configure a bridged network card, both with the old and new ways.

---

### Post by Jose Catre-Vandis on 2009-01-12
> **bodhi.zazen said:**
> What version of Virtualbox are you using ?

The latest release, the PUEL version, from the virtualbox web site, not the OSE from the ubutntu repositories, SIGNIFICANTLY CHANGED networking and bridged networking now works "out of the box" without additional configuration.

See the sticky, ie the mega thread, for how to configure a bridged network card, both with the old and new ways.

Here is the link to that bit :)
[http://ubuntuforums.org/showthread.php?t=346185](http://ubuntuforums.org/showthread.php?t=346185)

Thanks for the heads up **[COLOR="Red"]bodhi.zazen[/COLOR]**

Hmmm, will try this out. Interestingly VBox is not updating me to 2.1, as 2.06 tells me I am on the latest version? If they have sorted this out, this will be a fantastic improvement :D

---

### Post by bodhi.zazen on 2009-01-12
Thanks for the link. And yes it is a lot easier (although a manual bridge is geekier).

---

### Post by Jose Catre-Vandis on 2009-01-12
The upgrade is a fairly painless affair, you have to uninstall VBox2.0* first, but VBox2.1 picks up all your old settings and converts to the new format. I have only one VM out of 7 that didn't come across but with good reason (my own doing not VBox's)., so all is well. The host interface set up is now a breeze.

I booted up my opengeu VM and I was able to mount an nfs share just as if it was a real machine. Brilliant!

---

### Post by PuK84 on 2009-01-14
updated to the version on the virtualbox website and that fixed all my problems and was no pain in upgrading. settings auto-magically were brought accross. thanks for everything :D

---

### Post by Jose Catre-Vandis on 2009-01-16
Hi Puk, glad you got it all sorted. Please mark thread as solved.

---

### Post by garydauphin on 2009-04-11
Ok, I still don't get it, but I am an Ubuntu Newbie.

I use Vbox 2.1x

it has Ubuntu loaded and all is working well, including network.

In bridged networking, it is getting a 10.0.2.x address, where as my real machine is in the subnet 10.0.1.x.

I would like both the booted OS and the VM to get individual 10.0.1.x addresses.

Isn't there a simple way to do that?

email me at: [email]digitalmus@aol.com[/email], please

---

