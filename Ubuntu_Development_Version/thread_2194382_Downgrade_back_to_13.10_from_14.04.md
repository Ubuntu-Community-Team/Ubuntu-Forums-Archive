---
title: "Downgrade back to 13.10 from 14.04"
date: 2013-12-18
forum: Ubuntu Development Version
---

### Post by ch1mp on 2013-12-18
Hey,

I recently upgraded to 14.04, with the intention of staying with trusty and following the phablet progress. In the main everything is fine but I have understanble problems every now and again (which I'm reporting). I'd rather not do a clean install of 13.10 again and have to set up all my stuff again from scratch (virtual machines, lots of local dev sites in apache, databases, software etc. etc.). If I get rid of the trusty sources and then do apt-get update && apt-get upgrade will that be enough to put me back in line with 13.10?

Thanks in advance for any help,

Tom.

---

### Post by howefield on 2013-12-18
Thread moved to the "*Ubuntu+1*" forum

---

### Post by ajgreeny on 2013-12-18
No, I don't think you can do that; there is no downgrade pathway so you will have to backup everything and start again with a clean installation.

---

### Post by ch1mp on 2013-12-18
Ok! There's nothing really major so I'll probably stick with it then, thanks though, good to know if I come across something showstopping that I need to do a clean install to go back.

---

### Post by Elfy on 2013-12-18
I always find it best to have at least 2 installs - I tend to keep the previous version around as well - just for those days ... 

The partition trusty is on used the raring one, saucy is on the quantal one - saucy will end up being the U version when it starts

---

### Post by kansasnoob on 2013-12-18
> **ch1mp said:**
> Ok! There's nothing really major so I'll probably stick with it then, thanks though, good to know if I come across something showstopping that I need to do a clean install to go back.

Have you read this:

[http://ubuntuforums.org/showthread.php?t=2181769](http://ubuntuforums.org/showthread.php?t=2181769)

For the most part if you avoid "[proposed updates]("http://ubuntuforums.org/attachment.php?attachmentid=248134&d=1385562613")" you should survive :)

I would however recommend making frequent backups of anything important to some external media just in case things go kablooey.

And be sure to read the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes") when they're available!

---

### Post by kansasnoob on 2013-12-18
> **Elfy said:**
> I always find it best to have at least 2 installs - I tend to keep the previous version around as well - just for those days ... 

The partition trusty is on used the raring one, saucy is on the quantal one - saucy will end up being the U version when it starts

+1!

I'm still using 12.04 LTS as my stable release, and I always boot into it to perform any actions where security is a primary concern (like on-line banking).

---

### Post by PJs Ronin on 2013-12-18
With the price of HDs being so ridiculously low for desktop systems (no wonder the NSA can grab so much data, sorry metadata) there's no real reason to overwrite/remove old partitions/installs.   I simply clone (rsync) my current production to a new partition and start U+1ing.  If it all turns south I simply revert back to the previous partition and carry on until the boffins fix U+1.   Naturally, all my data is on a separate HD.

---

### Post by sorenimpey on 2013-12-18
To answer your question it is trivial to downgrade if you have a working knowledge of apt/dpkg and bash. You may have to fix packages via chroot. In the worst case scenario you will have to manually hack your dpkg lists due to broken dependency hell. All of this is eminently doable and you may learn alot in the doing. (I've rolled back servers multiple times due to annoying driver/kernel bugs.)

[http://askubuntu.com/questions/49869/how-to-roll-back-ubuntu-to-a-previous-version](http://askubuntu.com/questions/49869/how-to-roll-back-ubuntu-to-a-previous-version)

---

### Post by nanog on 2013-12-18
That was not my first post, BTW. This is my long-term account...I somehow logged in with my U1 account.

---

### Post by rrnbtter on 2013-12-19
Greetings,
I have been using Trusty as my only system since Saucy went Final. I like using the dev version because of the thrill of each update, experiencing each new advance or disaster. Happily I've only had to total re-install once. I have a pretty good partition arrangement so it's at best a thirty minute ordeal to reinstall.  Another caveat of the dev versions is that software devs are rarely in sync with the cycle so quite often particular items don't work even though the system is ok. This is one of the reasons that I have quit using Vbox and have my Win on an alternate HD, WINE can also be a problem and quite a few others.  If this post makes you feel nervous I would sugget that you stick with the finalized versions. Else, go for it and don't forget to report errors.

---

