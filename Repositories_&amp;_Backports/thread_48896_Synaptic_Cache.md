---
title: "Synaptic Cache"
date: 2005-07-14
forum: Repositories &amp; Backports
---

### Post by ShaneR on 2005-07-14
I got it in my head to give KDE a try on Ubuntu.  Now, I only have dial-up so I knew I was in for a long download.  So, I set up synaptic to download kubuntu-desktop and it's dependencies over night.

I got up this morning, and everthing downloaded except Konversation.  I figured no problem, I can get the package, and then install KDE from the cache.  But, I went into were the cache is stored and only 32 deb pacakages were there.  Well, that ticked me off...

I thought all downloaded files were supposed to be stored in cache?? I do have the synaptic options set correctly.  No big deal for KDE, but if need to do some large system upgrades (and I do...new installation this week), I afriad the same thing will happen.

Anyone have an idea??

---

### Post by ShaneR on 2005-07-15
Not to be a pest, but does anyone have a solution?

The same thing happened last night.  I set it up to download 47 updates to my ubuntu install, it made it 3/4 of the way when my dialup connection failed, and then I had to start from the beginning...which I didn't 'cause it's a pain in the @#@.

If Synaptic is not going to behave the way I expect it should, I'll need to either find another package management system, another distro, or stay with windows.  Anyway, just a litte frustrated...Simply want to keep my system updated.  Sadly, broadband is not an option where I now live (Believe me, I MISS it)

Thanks for the help :)

---

### Post by az on 2005-07-15
Downloaded files _are_ saved directly to the cache.  Even partially downloaded files are in their own directory.

Check out /var/cache/apt/archives to see what is there.

Synaptic is not your problem, here.  You are not downloading the packages.  Check to see that you do not have a zillion incomplete files.

Another option would be for you to get hold of a kubuntu cd.  Add the cd to your repositories and install kubuntu-desktop from that.

---

### Post by ShaneR on 2005-07-15
Thanks, Azz :)

As I stated above, the files are most certianly not in cache.  Except for 30 odd deb files.  No where near the amount the system informed me I had completed download (ie: I believe there were 172 files for Kubuntu-desktop)  I had checked off and on during the prcocess and only one or two were marked failed.

Anyway, I;m not concerned about KDE...the updates, however, are another story.  I'll clear the cache etc and try again tonight.

On a postive note, I'm enjoying Ubuntu greatly :) ...Almost have the girlfriend ready to put it on her system. ;)

---

