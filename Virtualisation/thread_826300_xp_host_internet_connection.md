---
title: "xp host internet connection"
date: 2008-06-11
forum: Virtualisation
---

### Post by spur on 2008-06-11
I have virtualbox installed and all works ok (including usb) except intenet.
I have it set to etho and nat and it says its connected and even shows up activity, but it does not actually connect.
My ubunto box is  hardy install and its a wired adsl connection, always on.
I have looked and looked for a solution and all I keep seeing is it works out of the box. well mine must have jumped right out of the box as it doesn't.
I have checked a lot of things. I stopped the network manager, and found no netwrok at all. I tried the different  'drivers' in the vbox set up.
When I  had the same setup with gutsy I did have internet on the host.
Sharing does work. Guest additions installed.
Any ideas any one.](*,)

---

### Post by pytheas22 on 2008-06-11
Just for clarification: you have XP installed inside VirtualBox on a Hardy host?  If so, look at the network settings for XP.  What does ipconfig tell you?  Does it think it has an IP address?  Are you able to set a static IP address?

---

### Post by wolpert on 2008-06-12
I also have the exact problem. I have virtual box on 3 separate 8.04 installs of Ubuntu, with a windows XP image on each. Since recent updates I have no network connection from any of the installs to the outside world. Note that DNS does work fine. No changes were made by me to the individual images and about 3 weeks ago, when I last used them, they were fine.

What should I be looking for?

Thanks

---

### Post by wolpert on 2008-06-12
Let me add abit more details. 

One of the systems has 'pre-release' mode on for software sources. (Kernel 2.6.24-19-generic, 32-bit) and the others are 2.6.24-18, one is 32-bit and one is 64-bit, default software sources.  They've been this way for almost since 8.04 came out.  VirtualBox is on all three, but I 'think' this has been a problem since about 3 weeks ago, since the .18 upgrade.  The VirtualBox module had to be updated after the kernel upgrade occurred before virtualbox worked again... and it 'seemed' to be fine except for not being able to see any other network device. (no ping, no www, etc) but DNS does work. (If I try to ping [www.yahoo.com](www.yahoo.com), the name resolves, but no packets get through.) I assume that's vbox in action for the DNS.

---

### Post by wolpert on 2008-06-12
Okay, just an FYI, it 'does' work, but not with ping. Specifically, www seems to work now. (I had a bunch of updates recently, no idea if that worked or something else flaked out)

Of course, still no ping... IP tables is not running, so that's not it... and my systems are in different physical environments. But I guess I don't need that... just kinda weird.

---

### Post by spur on 2008-06-12
> **pytheas22 said:**
> Just for clarification: you have XP installed inside VirtualBox on a Hardy host?  If so, look at the network settings for XP.  What does ipconfig tell you?  Does it think it has an IP address?  Are you able to set a static IP address?
Yes xp inside a virtual box on Hardy.
Yes it thinks it has an ip.  No static ip address. 
I'm thinking if this was working on gutsy (as is) then why not now? So I'm also thinking it could be something simple that lies in the differences between Gutsy and Hardy.

---

### Post by spur on 2008-06-12
> **wolpert said:**
> Okay, just an FYI, it 'does' work, but not with ping. Specifically, www seems to work now. (I had a bunch of updates recently, no idea if that worked or something else flaked out)

Of course, still no ping... IP tables is not running, so that's not it... and my systems are in different physical environments. But I guess I don't need that... just kinda weird.
I read somewhere that when you have the connections set with NAT you can't ping but you do get your internet connection working. So as long as you have the internet ok I wouldn't worry about 'ping', unless of course its critical for you.

---

### Post by pytheas22 on 2008-06-12
I can confirm the ping thing...my XP virtual machine, using NAT networking, also can't ping, but the rest of the Internet works fine otherwise.

I never noticed any problems with my virtual machine about three weeks ago, so I'm not sure if it was caused by a bad update.  Or I may just not have noticed, as I don't use the virtual machine very often.  Also I'm on Hardy 64-bit with the open-source edition of Virtual Box (the one available through Synaptic).  If you're using the closed-source edition from the vbox website, it might make a difference.

As for solving the problem with being unable to get network access, I don't know what else you could try.  I was originally thinking that the problem could be with XP's setup, but that doesn't sound like it's the case.  The only thing I might try is apt-get remove --purge VirtualBox and reinstall, or at least recompile the kernel modules.  Or try using the open-source edition if you're on the closed-source one now, or vice versa.

---

### Post by spur on 2008-06-12
Thanks for your replies.
I have reinstalled with the version latest version from sun. Everything else works very well including seemless and usb. I need the usb more than the internet so am unwilling to risk that. I tried the different 'drivers' for the eth0 as well, still no luck. It just doesn't make sense. I've also switched off all xps and Ubuntus firewalls. I did check and eth0 is the correct one. :)
It is interesting that, in the host, when I click on status it shows up that packages are received and sent. So some activity. Questions; are they going someplace not expected, like to itself and back, or just to the host and no further?

---

### Post by spur on 2008-06-12
I have continued searching for a solution and have found some references to dns problems. Maybe someone who understands this side of things more can explain how this could or could not be the source of the problem.

---

### Post by pytheas22 on 2008-06-13
> Questions; are they going someplace not expected, like to itself and back, or just to the host and no further?

You could install Wireshark on the Ubuntu host to watch the packets.  Do you see them going out over your real interface, and do you see a response coming back in?  Maybe they're being passed from the virtual machine to the host but for some reason are dying there, or maybe the responses are coming back in to the host by for some reason not being passed back in to the virtual machine.

---

### Post by spur on 2008-06-13
I did install wireshark, but couldn't make out what the response meant. I will run it again and copy the response and post it maybe some one can make out what it means.

---

### Post by pytheas22 on 2008-06-13
Basically if you send a request for google.com in your virtual machine, you want to see a packet with destination 64.233.187.99 or similar (Google's IP address) being sent out to your router.  Then you want to see a packet with origin 64.233.187.99 coming back in.  But post a screenshot if you can't tell what's going on.

---

### Post by spur on 2008-06-13
I got this screen shot I hope it helps. (Attachment) It does not seem over clear, but is readable, sorry.
:lolflag:

---

### Post by pytheas22 on 2008-06-13
It looks like the DNS name is not being resolved for either cm2.zonelabs.com or message.real.com...so I would say that DNS is to blame.  Can you access websites in your virtual machine if you put an IP address in the address bar instead of the domain name?  You can find the IP address of any website by using the host command on Ubuntu, e.g. "host google.com"

You could also try running Wireshark on the Ubuntu host at the same time to see what's going on that end and rule out problems with passing packets between the host and the virtual machine.

---

### Post by spur on 2008-06-13
Yes that gets me to the Google site. So it is the DNS. I did have an idea it might be. So how do I get that fixed?

---

### Post by pytheas22 on 2008-06-13
At least you finally know the problem.  First of all, make sure that Windows has the right IP address for your DNS server.  If you type ipconfig /all it should list the DNS that it's using.  It needs to be the same as whichever address you get when you type "cat /etc/resolv.conf" in Ubuntu--probably the local IP of your router.

Beyond that, there is a lot of discussion of this issue and its various causes/solutions if you search around for stuff like "virtualbox dns can't resolve."

Let us know whether you find a solution or not.

---

### Post by spur on 2008-06-13
Beautiful, that enabled me to fix.
FYI:
ipconfig showed nothing for dns suffix.
cat /etc/resolv.conf gave me two different numbers xxx.xxx.x.x and xxx.xxx.xx.xxx
I went into "network connections' on xp and right click properties and Internet protocol tcp/ip properties, then entered the numbers from above in the boxes for preferred DNS server and alternate DNS server. The tested it with firefox and it worked.

---

