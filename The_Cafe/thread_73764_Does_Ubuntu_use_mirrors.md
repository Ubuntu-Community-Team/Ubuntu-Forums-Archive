---
title: "Does Ubuntu use mirrors?"
date: 2005-10-10
forum: The Cafe
---

### Post by Dr. Nick on 2005-10-10
I guess this may be the best place to post this, It doesnt pertain to any particular ubuntu, just in general, but feel free to move it if desired

Does Ubuntu use mirrors for network apt-get updates, I was just curious as I was updating and barely getting 10K on my connetion. Im not complaining just curious if it was a bad mirror site or if traffic always pick up when a new version is nearing. Im not even sure this is a Ubuntu problem, may be my provider. It just seems like with how fast Ubuntu is growing the bandwidth demands would be very high.

Any comments?

---

### Post by mattheweast on 2005-10-10
AFAIK there are two mirrors, one in Europe and one in the US. You should be using the closest one to you automatically.

If it's not working too well (they should be fairly fast), you can try using an unofficial mirror (although of course this runs the risk of not being correctly synched with the main mirrors, depending on who runs the mirror). For more information see the [Archive Wiki Page]("https://wiki.ubuntu.com/Archive")

---

### Post by ubuntu_demon on 2005-10-10
during installation your /etc/apt/sources.list is adapted for the location you specify. I don't know how much official mirrors are out there.

---

### Post by Hobbsee on 2005-10-10
there seem to be a whole heap...

There's definetly an au (australian) mirror, and a few in asia...so there's likely to be similar numbers in the rest of the world.

---

### Post by mattheweast on 2005-10-10
See the wiki page I posted above for a complete list of all unofficial mirrors. There are only two official mirrors, archive.ubuntu.com and us.archive.ubuntu.com. Everything else with archive.ubuntu.com in the url point at those AFAIK.

---

### Post by Dr. Nick on 2005-10-10
Thanks for the link, I had all mine set up right just had a lousy connection:KS 
I tried again this morning and its about 4x faster so Im ok now :)

---

### Post by xequence on 2005-10-10
In someones review of ubuntu they showed them getting 500 KBPS speeds. Ill have to try it out to see, since I upgraded my internet to 3 Mbps :P

---

### Post by asimon on 2005-10-10
> **mattheweast]There are only two official mirrors, archive.ubuntu.com and us.archive.ubuntu.com.[/quote]
Yes, archive.ubuntu.com and us.archive.ubuntu.com are currently the same:
```
 said:**
> 
Everything else with archive.ubuntu.com in the url point at those AFAIK.
Wrong:
```
de.archive.ubuntu.com.  600     IN      A       141.76.2.3
fr.archive.ubuntu.com.  600     IN      A       213.186.33.37
```
Not everything, only some like gr.archive.ubuntu.com.


BTW, number and traffic of mirrors is quite interesting. It gives an idea how popular *buntu is. For example in the last days SUSE has many problems with their server infrastructure. [ftp.gwdg.de allone delivers more than 4TB everyday (around 3500 sessions every moment), 9/10 of that suse linux traffic](http://lists.opensuse.org/archive/opensuse/2005-Oct/0708.html). Not bad, suse never had a bigger storm on their distro. As I read from those poor sever admins on opensuse mailing list I wondered how much traffic ubuntu/kubuntu 5.10 will be generating when they get released.

---

