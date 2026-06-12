---
title: "Am I at Risk?"
date: 2011-04-07
forum: Security
---

### Post by josephmills on 2011-04-07
hi there I am new to ubuntu and really like it,But am a bit confused about software sources. When I add a repository is like I am connecting to a data base some where? or is it different? Also I tried to add a repository following this web page [http://www.clshack.it/en/installa-su-ubuntu-tutte-le-applicazioni-di-backtrack-4.html](http://www.clshack.it/en/installa-su-ubuntu-tutte-le-applicazioni-di-backtrack-4.html)

after adding the repository I tried to update and and could not. Something about the key not being good?:confused: ```
W: GPG error: http://archive.offensive-security.com pwnsauce Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEF51A0A571327DB
```but when I go to synaptic package manager I see a bunch of programs that are from backtrack-linux when I try to install one of them I can install some but not others and there is a page that says  something about it being a dangerous program (see pic) how do I "Undo" what I have done and is my machine at risk? Thank you for your time

---

### Post by wilee-nilee on 2011-04-07
When taking a screen shot use the timer to get a clean picture or the select area to grab, a screen shot like that is not very helpful.

As far as backtrack if it was me I would just full install it on a thumb large enough, mixing it in with Ubuntu may not be the best of ideas the way your doing it. I believe most of the programs for backtrack are already in the regular repos anyway.

You also if your have a setup you can't afford to loose anything with might consider cloning it, before you break it.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by josephmills on 2011-04-07
> **wilee-nilee said:**
> When taking a screen shot use the timer to get a clean picture or the select area to grab, a screen shot like that is not very helpful.
 sorry about that here is a new pic 

and thanks for the link

---

### Post by wilee-nilee on 2011-04-07
When you install a third party you will get a warnings at times, not a big worry if you know what your installing, and that is a beautiful screen shot.:)

Here is 0trace the website.
[http://seclists.org/fulldisclosure/2007/Jan/145](http://seclists.org/fulldisclosure/2007/Jan/145)

---

### Post by BkkBonanza on 2011-04-07
For things like backtrack, for a relatively new user, I would highly suggest making a live "flash stick" or cd and booting with that. You're going to use it to explore things that could really muck up your ubuntu system, and unless you like fixing things a lot, using a seperate boot image will make life better.

You can go adding keys to your install so that packages go in without warnings but that's not such a great idea. Once you add a key you are saying that you trust that user - and the bottom line is you ask yourself "do you really trust that user for all time for every file they may provide". Well, I know I don't. It's bad enough having to trust Ubuntu as a source, but then trusting random net users is just pushing it too far. How would you verify that some some hacker didn't put their files up and claim to be so-and-so with some key. 

This is why booting a clean system image for these uses is good and why backtrack make a suitable image available for you to test on.

---

### Post by josephmills on 2011-04-07
> **BkkBonanza said:**
> For things like backtrack, for a relatively new user, I would highly suggest making a live "flash stick" or cd and booting with that. You're going to use it to explore things that could really muck up your ubuntu system, and unless you like fixing things a lot, using a seperate boot image will make life better.

You can go adding keys to your install so that packages go in without warnings but that's not such a great idea. Once you add a key you are saying that you trust that user - and the bottom line is you ask yourself "do you really trust that user for all time for every file they may provide". Well, I know I don't. It's bad enough having to trust Ubuntu as a source, but then trusting random net users is just pushing it too far. How would you verify that some some hacker didn't put their files up and claim to be so-and-so with some key. 

This is why booting a clean system image for these uses is good and why backtrack make a suitable image available for you to test on.

thank you so much for all of this info and your honesty I really appreciate it so once again thanks. I am very new to all of this and it is a bit overwhelming at point's but I am learning so much. In the past few years when I first started getting into computers. I never learned as much as I have in the past 4 months or what ever it has been scents I burned that ubuntu iso. I started going to the local linux user groups and also the local hackerspace. I am luck to have that in my city. But I do have a big problem. After trying to uninstall the backtrack source by going to Software Sources-- Other Sources and removed the offensive-security one. And bam I lost wireless. I then went to termanal to try to see what was going on. and got to ```
rfkill list  hp wifi: Wireless lan Soft blocked no hard blocked yes
```  I tried to use ```
rfkill unblock all 
``` and nothing happens I have also tried ```
rfkill unblock wlan
``` Is there a way to unblock this? Also ifconfig shows no wlan0. I don't know what happened ,but should I reinstall ubuntu and lose some files(not a big deal) thanks again

---

### Post by BkkBonanza on 2011-04-07
I don't think this could happen due to removing a software source but perhaps along the way you also removed a package (from that source?). If so, then likely your problem is that some package needed for wifi is now not installed. It's pretty hard for me to know. Just guessing. If you have some idea what package may have been removed then you could try reinstalling it. You may need net access for that though.

Another thing with wifi is that the hardware can get turned off in some cases (usually laptops have a button) so it's worth making sure it's not that. I seem to recall that rfkill is temporary and a reboot should fix that. You can do some basic checks with,

sudo ifconfig -a

which should at least show the interface. You could post output here.

If the itnerface does show up then you can try restarting networking,

sudo /etc/init.d/networking restart

If the interface doesn't show up then you have driver or hardware issues to fix. That would depend on your adapter model, which driver you need, and loading the driver (with modprobe maybe, though now many (most) drivers get detected automatically).

---

### Post by josephmills on 2011-04-07
sorry about the delay I was fighting to stay awake. After doing some research some funny things started happening on my computer (random pop-ups) even when I I had the cat5 cable disconnected. As I could not get my wlan0 driver to work. I sure it is a user error. But now I know that I will never ever ever put more repo's on my computer's. So yes I took the easy way out and am re-installing ubuntu 10.10 after having headaches with suse and slack. I think that I once said that ubuntu is not user friendly while I am eating my words right now. thank you for all your help again.

---

