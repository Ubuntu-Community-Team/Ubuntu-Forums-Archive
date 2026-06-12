---
title: "Request : libnjb and gnomad2"
date: 2005-06-07
forum: Ubuntu Backports
---

### Post by Leszek Tarkowski on 2005-06-07
Anyone who uses creative mp3 players would be glad to seenew versions of those... newest from debian/unstable needs new glibc, so it is really hard now to get those things working.

---

### Post by tristan on 2005-06-07
Just download the FC3 rpms for gnomad2 and libnjb2.1 from [http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)

Convert them to debs using alien, and then dpkg -i those debs. I did this and it works without a problem. Much faster than Gnomad2.5!!

---

### Post by dodongo on 2005-06-07
I know this isn't always the preferred option (in fact, I'm liable to be lynched in this thread for suggesting it), but you could compile these by hand...   I'm reasonably comfortable doing so, and I appreciate the fact it lets me keep up instantaneously with the almost-always-important Gnomad2 updates.

If you take the time to install the dev packages needed by the two programs, it isn't too hard.  A couple symlinks and a shell script later and you're up and running.

-----------------------

OK, and responses like mine are so why people bitch & moan about F/OSS.  I agree, the Gnomad project should be considered for a backport.  Maybe then I won't need my symlinks and shell scripts quite so bad :)  

Let me know if any help is needed in getting this one off the ground.  Lord knows I've done enough troubleshooting on it.  A problem you might encounter while building it (whoever builds it) is that the hotplug.sh script in the libnjb package needs to be run (at least for Gnomad >= 2.7.1 to work) on Ubuntu, but it doesn't seem to be able to run properly.  That's why I just wrote the basic shell script for the launcher:
> 
gksudo "chmod -R a+w /proc/bus/usb"
gnomad2

---

### Post by Leszek Tarkowski on 2005-06-08
Yes, actually i can build it myself, and i did it. 
But you see, my point is that i have friends (yeah, some linux fan does have friends) and i can't recommend ubuntu (at least for one of them which has zen micro) and tell - recompile it...

So that was just idea what is still missing.

---

### Post by dodongo on 2005-06-08
[QUOTE=Leszek Tarkowski]Yes, actually i can build it myself, and i did it. 
But you see, my point is that i have friends (yeah, some linux fan does have friends) and i can't recommend ubuntu (at least for one of them which has zen micro) and tell - recompile it...

So that was just idea what is still missing.[/QUOTE]
 Wow, you have friends *too*?!  :)   

You're exactly right, and I shouldn't have slipped into geek mode unnecessarily.  The reason I like Ubuntu is that I dont *have* to switch to geek mode to get things working, hardly at all anymore.  But it's there for fun when I want it to.  

Anyway, yes, again, I second this motion and offer myself up for testing or troubleshooting or whatever.  It'll be interesting to see if apt-get can install this correctly so I avoid the errors I mentioned.

---

### Post by jdong on 2005-06-08
k; I'm currently redoing Firefox packages.

After I finish that, I'll look at this. is the library (libnjb) necessary? I don't like backporting libraries... What other packages depend on libnjb?

---

### Post by dodongo on 2005-06-08
[QUOTE=jdong]k; I'm currently redoing Firefox packages.

After I finish that, I'll look at this. is the library (libnjb) necessary? I don't like backporting libraries... What other packages depend on libnjb?[/QUOTE]
 Yes, libnjb is (unfortunately) a dependency of Gnomad2.  libnjb is the library for the Nomad JukeBox.  A list of projects using libnjb is available [here](http://libnjb.sourceforge.net/?section=projects).  This includes:


    * Gnomad 2
    * NomadSync
    * Xnjb
    * GnomeDAP
    * KIO::Slave
    * kiozen 
    * perlnjb
    * njstream
    * Python-libnjb
    * KZenExplorer
    * Linspire Lsongs

According to my search in Synaptic, none of these packages that might conflict exist in the Ubuntu APT repositories.  This doesn't strike me as a library that's going to cause mass pandemonium if it's released, but of course, the final call is up to you.

PS - Is there a place to find a changelog for the Firefox packages?

---

### Post by jdong on 2005-06-08
ok. I'll have to look into kioslave though, whether or not KUbuntu is affected by this.

---

### Post by vassie on 2005-06-14
I have converted both gnomad2-2.7.1-1.FC3.i386.rpm and libnjb-2.1.2-1.FC3.i386.rpm to deb's and installed them, but when I start gnomad2 I get the following

```
gnomad2: error while loading shared libraries: libnjb.so.5: cannot open shared object file: No such file or directory
```

Can anyone help?

Thanks

Ben

---

### Post by vassie on 2005-06-14
I've just tried gnomad2.7.0 and it works fine :D

Ben

---

### Post by tristan on 2005-06-14
Thanks vassie/ben, you just saved me the trouble of telling you to use 2.7.0 (or to make a symlink for libnjb.so.5). :) 

How do you find the speed of the new Gnomad2? It's **much** faster for me.

---

### Post by vassie on 2005-06-14
I installed it last night but my Zen Micro still had the new "Plays For Sure" firmware, I've bought it into work today and downgraded the firmware, I will try it tonight and let you know
Ben

---

### Post by vassie on 2005-06-15
Hot Dog!!!

Well firstly 2.7 works!! 2.5 would not see my Zen Micro, and 2.6 would not install (dependant on newer libc6), this one does work, and is very fast, my next job now is to remove Windows XP from my PC :)

Ben

---

### Post by tristan on 2005-06-15
Good to hear that Gnomad2 has pushed you over the edge into XP removal! Good luck...

---

### Post by vassie on 2005-06-15
I dual booted for a while, when removed XP, but had trouble with my Zen, so when I put XP back on, now I'm dual booting again, but now XP is going, hopefully forever!
The only thing I am going to miss will be a DVD9 to DVD5 program like DVD Shrink, I know I can use it via WINE, but i'd rather not!
Ben

---

### Post by dodongo on 2005-06-15
[QUOTE=vassie]I dual booted for a while, when removed XP, but had trouble with my Zen, so when I put XP back on, now I'm dual booting again, but now XP is going, hopefully forever!
The only thing I am going to miss will be a DVD9 to DVD5 program like DVD Shrink, I know I can use it via WINE, but i'd rather not!
Ben[/QUOTE]
 Welcome aboard then, Ben!  Gnomad2 was one of the major hurdles for me adopting Linux.  Through troubleshooting and developer's updates, it's gotten to be a pretty slick little program.  The other program that had me holding out was an audio editor (GoldWave), which, as it turns out, <B>does</b> run in Wine. 

Wine isn't for the weak-of-stomach sometimes, but when things Just Work in it, it's great.

Good luck!

-Chuck

---

### Post by bennettg on 2005-06-19
I followed the instructions earlier in the thread to use alien and converted rpms into debs ans then dpkg -i the debs,

when i go into synaptic i see that they (gnomad2 and libnjb) are installed but gnomad will not run (i even tried running as root)

can anyone help a noob?

---

### Post by tristan on 2005-06-19
[QUOTE=bennettg]I followed the instructions earlier in the thread to use alien and converted rpms into debs ans then dpkg -i the debs,

when i go into synaptic i see that they (gnomad2 and libnjb) are installed but gnomad will not run (i even tried running as root)

can anyone help a noob?[/QUOTE]

Hi bennetg

So when you say won't run, do you mean the gnomad2 interface won't even come up, or does it come up then crash, or that it comes up but you can't connect to your nomad?

Try running it from the shell **sudo gnomad2** and tell me what the output says.

---

### Post by bennettg on 2005-06-20
sorry.  i had 2.7.1 installed whcih did not run.   i tried 2.7.0 and it works like a charm.  

goodbye bill gates

---

### Post by tristan on 2005-06-20
[QUOTE=bennettg]goodbye bill gates[/QUOTE]

At this rate he'll be bankrupt in 6 months. Poor bloke :).

---

