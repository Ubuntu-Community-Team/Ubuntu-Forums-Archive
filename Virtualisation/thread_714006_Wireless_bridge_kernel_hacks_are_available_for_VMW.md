---
title: "Wireless bridge kernel hacks are available for VMWare, but what about VirtualBox?"
date: 2008-03-03
forum: Virtualisation
---

### Post by Starks on 2008-03-03
Is there a reason as to why VMWare, a relatively closed piece of software, gets all the hacks as opposed to the extremely open VBox?

---

### Post by fjgaude on 2008-03-03
> **Starks said:**
> Is there a reason as to why VMWare, a relatively closed piece of software, gets all the hacks as opposed to the extremely open VBox?

Maybe because vmware has been around for so long, and the hackers understand it enough to offer solutions. :)

---

### Post by scottro on 2008-03-03
You can do wireless bridging with VirtualBox though.  I have a page (more Fedora and ArchLinux oriented, but should be easily translated to Ubuntu) at [http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html) that goes through my adventures with it.

---

### Post by bollix47 on 2008-04-11
> **scottro said:**
> You can do wireless bridging with VirtualBox though.  I have a page (more Fedora and ArchLinux oriented, but should be easily translated to Ubuntu) at [http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html) that goes through my adventures with it.

I saw in another thread where you had a problem getting this howto working with Hardy.  Have you had any luck since then?

I've tried using the tutorial but just can't ping anything from the guest o/s.

Thanks for any guidance.

---

### Post by scottro on 2008-04-11
Actually, no, but the other fellow did.  :)
I haven't had any chance to play with it for awhile, and probably won't for another week or so.

---

### Post by scottro on 2008-04-13
Ok, I just reinstalled Hardy.  

Nope, it doesn't seem to be working.  I tried uninstalling and reinstalling using the tarball from Innotek, but had no joy there either. I  suppose that either Hardy or VB had an upgrade which broke it.  However, it still works without trouble on Fedora and ArchLinux.

So, just for fun, I tried it with NAT.  That works, at least with the Innotek version.  I also found out that I don't actually need bridged host network to use this company's VPN.  (My former company used Nortel, my present company uses Checkpoint.)  So, that's a good thing for me. 

I really have no idea why it's not working on Ubuntu when it works on everything else.

---

### Post by bollix47 on 2008-04-13
Thanks for giving that a try.

I already have NAT working and the browser and all other programs that use the net work fine except for one installer of a program that I unfortunately need.  I was hoping to try the bridge method to see if the problem went away.

The installer is for Amazon Seller Desktop and it insists there's no internet connection even though all other network programs work fine.

Anyway, I will wait until Hardy goes final and if it still doesn't work then I'll try VMware or some other solution.

---

### Post by scottro on 2008-04-13
Folks, please post any updates to this thread.   I tried googling for the solution tonight, but it seems that everything I find either leads to my page or to one of the pages I used in my solution.  It's still working with Fedora and Arch, both of which are pretty cutting edge (Fedora Rawhide) so I think the principles are still sound.  

I'll be short of time for the next few weeks and I'm not all that great at interpreting tcpdump, but sooner or later, I'll try running it and see if that gives me some sort of clue as to why it's stopped working.

---

### Post by scottro on 2008-04-13
Ok, it's working.  
The whole thing is a bit strange.

I turned off apparmor--I'll turn it back on tomorrow and see if it makes a difference, but it's too late tonight. 

Anyway, here is the trick. 
After doing everything else, that is after running parprouted and before starting VirtualBox add the route to tap0.  In other words, after for example

parprouted ath0 tap0 
do
route add -net 192.168.1.0 netmask 255.255.255.0 tap0

Then and only then, start VirtualBox.  It should then work.

---

### Post by bollix47 on 2008-04-14
After adding the route command I can now use tap0 with my XP guest on a Hardy host.

Unfortunately, the above-mentioned installer still thinks I don't have a network connection even though all other network programs work properly.  The installer does work fine on a native Windows computer so I'm a bit confused as to what's causing the problem.

Anyway, with your help I have at least eliminated 1 possible cause and can now advance my investigation into other areas.

Thanks very much for your help with this.

---

### Post by scottro on 2008-04-14
Well, glad it fixed that tap0 issue anyway.  

Thanks for testing it.  I'm sorry it didn't fix the other issue, with Amazon's installer.

---

