---
title: "Potential Major Fan issue..."
date: 2012-10-06
forum: Security
---

### Post by Gazucha on 2012-10-06
Hi all,

a couple of weeks ago I started a thread after my fan started going mental...

[http://ubuntuforums.org/showthread.php?t=2061475](http://ubuntuforums.org/showthread.php?t=2061475)

the thread was closed due my having a trivial fan problem, however,

...since that time, the Ubuntu 11.10 system that I had been using, has absolutely refused to let me get back on line, whether it be wifi, 3G etc. (I'm now on the same computer but using a different Linux). At first, I lost even the Ubuntu connection icon - as well as the page which requires the sim code  to connect- although after a run through recovery mode, the icon is back yet it still won't allow me to type in the pin code needed to connect. 

So Game Over Ubuntu...(again!)
 
Just so you know, I even changed the fan but hey, the problem is still there.

 Is it normal for a fan to disable your internet connections?

Anyways.
 unfortunately, right now I don't have much time to hang around and resolve this. 

When I do have time, I shall follow the advice on this site regarding security such as here...

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

what would be nice to know is, "can the Ubuntu system be repaired or has it been cyber-knobbled and needs to be erased?" 

Any help and advice would be greatly appreciated.

To me, it would appear that some dark-side entity has entered my computer and fiddled with things. Then again, maybe we should just keep an eye on those fans?

Love to you all,

~Gaz

---

### Post by Ms. Daisy on 2012-10-06
I don't see anything that makes me concerned about security in what you describe.

Are you sure your hard drive is healthy? I'd recommend checking it with gparted. You may also make sure you've got the proper wireless driver.

---

### Post by greatsirkain on 2012-10-06
Random data loss sounds like a dying hard drive to me but your main problem is just lack of internet? So lets start there:

```
iwconfig
```
to display wireless details (I'm sticking with wireless because that's what I use)

```
sudo iwlist scan
```
Scans for wireless networks

Make sure you've the basics covered, connecting to the right network etc, wifi shouldn't require a sim code, that would only be needed if you were connecting through a mobile phone or 3g mobile internet dongle and as far as I know the dongles all come pre-loaded with the software you need & update automatically, more details about exactly how you're connecting might help


> some dark-side entity has entered my computer and fiddled with things
Sith lord with a netbook? A randy David Icke? The man trying to shut you down for the reptilian overlords?...We can sort those guys out after your internet's working again. :P

---

### Post by lisati on 2012-10-06
Data loss *could* be a symptom of a hardware failure that's also causing your fan to work overtime and/or messing with your connectivity.

---

### Post by Gazucha on 2012-10-07
Maybe I should add that the fan only runs nuts when I am (sorry, was) online, and only  with Ubuntu. All other times it is ok.
 The Hard Drive was new 9 months ago and works perfectly well with Linux Mint.

---

### Post by cariboo on 2012-10-07
> **Gazucha said:**
> Maybe I should add that the fan only runs nuts when I am (sorry, was) online, and only  with Ubuntu. All other times it is ok.
 The Hard Drive was new 9 months ago and works perfectly well with Linux Mint.

That means absolutely nothing, it could be that Mint is installed on a different part of the hard drive that isn't affect by a hard drive problem.

Check the drive to make sure it isn't going defective.

As for your fan spinning faster that normal, what were you doing on the internet when the fan spooled up? Flash is well know to use a lot of resources, and as resource usage goes up, hardware components heat up causing the fan to spin faster.

---

