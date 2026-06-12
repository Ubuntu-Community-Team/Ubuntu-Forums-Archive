---
title: "Not a Support Request, just some personal observations"
date: 2014-07-18
forum: Ubuntu, Linux and OS Chat
---

### Post by EnglishElectricAndy on 2014-07-18
It's just coming up to the 1st aniversary of my first ever use of a Linux distribution, Xubuntu 13.04 to be exact. "Wow" I thought, "This is great, so much faster and more straightforward than Windows". I didn't realise that it had a short lifespan in terms of support but any way I rode with it, followed this and other forums with great interest and hunger to learn. Upgrading to 13.10 went reasonably smoothly though Xscreensaver became a bit glitchy after a reboot but I lived with it as it wasn't a complete showstopper.

Now I come to Xubuntu 14.04...

Oh dear, what has happened to that wonderful system I first came across 12 months ago... ? My swap partition vanishes after a reboot: tumblerd hogs up to 99% of my CPU and my ~/.thumbnails is filled up with stuff that I've long since deleted or moved to an external drive. Oh, and Ubuntu Forums keeps logging me out without my permission!

I've worked in many industries where Hutbers Law has been applied with surprising efficiency!

As stated, this is not a support request.

---

### Post by bapoumba on 2014-07-18
> Oh, and Ubuntu Forums keeps logging me out without my permission!
We've seen that among Staff and users. What type of network are you using ? Your own, public, wifi, ethernet, that type of things.

We have no answer for now but try to find some common situation. Thanks (and apologies).

---

### Post by EnglishElectricAndy on 2014-07-18
Hello bapoumba

I've just had to re-log in to get back here, the unexpected logging out seems to happen when I navigate away from the thread I've started or replied to.

I will admit that I haven't got the most robust of connections at the moment, using a 3G mobile phone network via a dongle (Huawei E585) that doesn't need a USB connection because it uses WIFI to connect to my computer.

---

### Post by d-cosner on 2014-07-18
Even though this is not a support question and I do understand your frustration, here are a couple ideas. Have you tried just using the 14.04 Live CD to see if it runs alright with your hardware? The reason I ask this is because you had upgraded before, upgraded a second time and maybe the problems would be fixed with a clean install?

You mentioned you had an external hard drive, you could back up your data, Firefox profile etc and do a clean install if 14.04 works well from the Live CD. I know doing this can be an inconvenience especially if you have added applications you like but a clean install might be easier than trying to figure out all the things that might have gone wrong from the upgrade.

You did not ask for support but if you are having hardware issues with14.04 we are here to help. If you were to get 14.04 up and running you would not have to worry about upgrading for a long time. I have no idea why you are getting logged off the forum but already it has been mentioned that this is happening to others as well so someone certainly will look into it.

---

### Post by EnglishElectricAndy on 2014-07-18
Hi d-cosner

I'm not feeling frustration, perhaps bewilderment. I've learnt so much over my first 12 months of using a Linux distro, how to handle partitions using Gparted, how to create my own bootable USB or DVD, even becoming less fearful of typing stuff into the terminal (and trying to understand the basics of what is happening). I'm just not sure how Xubuntu 14.04 is an improvement on my previous experience, hence my reference to Hutbers Law.

---

### Post by Bucky Ball on 2014-07-18
Upgrade via the Update Manager can be problematic, especially if you've added repos and not turned them off. Was this the case? I'd probably backup and do a clean install. 

(For the record, I have installed Xubuntu 14.04 LTS on three or four machines and it has been running faultlessly on all of them. As for short support, I stick with LTS versions (long-term support), three years for Xubuntu.)

Good luck.

---

### Post by d-cosner on 2014-07-18
[h=1][Hutber's law]("https://en.wikipedia.org/wiki/Hutber%27s_law")[/h]                                           Hutber's law states that "improvement means  deterioration". It is founded on the cynical observation that a stated  improvement actually hides a deterioration.             

Now I get it! :)

---

### Post by QIII on 2014-07-18
Another source of pain is proprietary drivers.  Between PPAs and proprietary drivers, the probability of a significant emotional event when upgrading from version to version increases dramatically.

+1 for fresh installations.  They sweep out the attic.

---

### Post by Bucky Ball on 2014-07-18
> **QIII said:**
> 

+1 for fresh installations.  They sweep out the attic.

+1 for this. I like a clean attic! With LTS releases, at least it only needs to be swept out every few years, which also suits me! ;)

---

### Post by QIII on 2014-07-18
I wonder if that Hutber fellow is the type who would prefer a surrey and a nag in the carriage house to a Cadillac in the garage...

---

### Post by Cliff_Simonds on 2014-07-18
> **EnglishElectricAndy said:**
> Oh, and Ubuntu Forums keeps logging me out without my permission!

I had that problem too...till I turned on history in firefox and set the "selfdestructing cookies" add-on to "never" for the forums in ubuntu. in windows had to put forums cookie on the save side of ccleaner.

---

### Post by buzzingrobot on 2014-07-19
> **EnglishElectricAndy said:**
> My swap partition vanishes after a reboot...

Strange. What signals swaps disappearance? "swapon -s" displays partition currently used for swap, and that should be the partition shown in /etc/fstab. 

"swapoff" disables swapping.  

If, by chance, you've been adjusting the so-called swappiness factor, maybe back off that altogether.

 >  tumblerd hogs up to 99% of my CPU and my ~/.thumbnails is filled up with stuff that I've long since deleted or moved to an external drive.



Is "tumblerrd" a daemon related to the Tumbler blogging system? 

Trashing files moves files from their current location the Trash directory. What happens when you use a file manager to drag files from on drive to another depends on the file manager's setup. "mv" in a terminal certainly cleanly moves everything.

---

### Post by pretty_whistle on 2014-07-19
> **Cliff_Simonds said:**
> I had that problem too...till I turned on history in firefox and set the "selfdestructing cookies" add-on to "never" for the forums in ubuntu. in windows had to put forums cookie on the save side of ccleaner.

Glad you mentioned that.  I had Firefox set to dump everything and not remember history.  Now I fixed it.  :)

---

### Post by WinEunuchs2Unix on 2014-07-19
Gotta love Intel Moore's law of doubling processing power/RAM every year (paraphrasing).

Gotta watch out for Murphy's law!!!

---

### Post by Cliff_Simonds on 2014-07-20
Lot's of people think that cookies are the "Devils Work" and set their browsers to clear "everything" on closing, but personally I find certain ones( more info at AboutCookies.org), very helpful when surfing  especially when it comes to logins and my search engine set up. And the problem with clearing the browser is that one has to reload everything every visit to a site, which in turn uses more bandwidth and time loading. I,ve tried the "Paranoid" way a while and it sucked up my prepaid mobile broadband euros. I live alone and I'm not a criminal so I don't see why I "always" have to delete everything; maybe once a month or so and my DNS cache when I can't get to known sites, like omgubuntu.uk.

---

