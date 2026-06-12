---
title: "Connection problems ?"
date: 2005-06-01
forum: Ubuntu Backports
---

### Post by bored2k on 2005-06-01
Strange problem. Backports supposedly are empty. I can't find apps like azureus, beagle, etc. In other words, I have them ON, but they are nowhere to be seen.

```
# apt-get install beagle
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package beagle

apt-get install azureus
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package azureus

```

---

### Post by hda on 2005-06-01
I just found out that the Packages.gz files on the backport mirrors are empty. Check the /var/lib/apt/lists directory.

Who can solve this problem?

---

### Post by ShaneAu on 2005-06-01
[QUOTE=bored2k]Strange problem. Backports supposedly are empty. I can't find apps like azureus, beagle, etc. In other words, I have them ON, but they are nowhere to be seen.

```
# apt-get install beagle
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package beagle

apt-get install azureus
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package azureus

```[/QUOTE]
 What does 'apt-get update' give you (regarding ubuntu backports)?

Edit: Ahr huh... I see, I see. Well my mirror (MirrorMAX) syncs frequently and it seems to be the first effected (maybe).

The last Sync it did:

> 
receiving file list ... done
hoary-backports-staging/bleeding/binary-amd64/Packages.gz
hoary-backports-staging/bleeding/binary-i386/Packages.gz
hoary-backports-staging/bleeding/binary-powerpc/Packages.gz
hoary-backports-staging/main/binary-amd64/Packages.gz
hoary-backports-staging/main/binary-i386/Packages.gz
hoary-backports-staging/main/binary-powerpc/Packages.gz
hoary-backports-staging/multiverse/binary-amd64/Packages.gz
hoary-backports-staging/multiverse/binary-i386/Packages.gz
hoary-backports-staging/multiverse/binary-powerpc/Packages.gz
hoary-backports-staging/restricted/binary-amd64/Packages.gz
hoary-backports-staging/restricted/binary-i386/Packages.gz
hoary-backports-staging/restricted/binary-powerpc/Packages.gz
hoary-backports-staging/universe/binary-amd64/Packages.gz
hoary-backports-staging/universe/binary-i386/Packages.gz
hoary-backports-staging/universe/binary-powerpc/Packages.gz
hoary-backports/bleeding/binary-amd64/Packages.gz
hoary-backports/bleeding/binary-i386/Packages.gz
hoary-backports/bleeding/binary-powerpc/Packages.gz
hoary-backports/main/binary-amd64/Packages.gz
hoary-backports/main/binary-powerpc/Packages.gz
hoary-backports/multiverse/binary-amd64/Packages.gz
hoary-backports/multiverse/binary-i386/Packages.gz
hoary-backports/multiverse/binary-powerpc/Packages.gz
hoary-backports/restricted/binary-amd64/Packages.gz
hoary-backports/restricted/binary-i386/Packages.gz
hoary-backports/restricted/binary-powerpc/Packages.gz
hoary-backports/universe/binary-amd64/Packages.gz
hoary-backports/universe/binary-i386/Packages.gz
hoary-backports/universe/binary-powerpc/Packages.gz
hoary-extras-staging/bleeding/binary-amd64/Packages.gz
hoary-extras-staging/bleeding/binary-i386/Packages.gz
hoary-extras-staging/bleeding/binary-powerpc/Packages.gz
hoary-extras-staging/main/binary-amd64/Packages.gz
hoary-extras-staging/main/binary-i386/Packages.gz
hoary-extras-staging/main/binary-powerpc/Packages.gz
hoary-extras-staging/multiverse/binary-amd64/Packages.gz
hoary-extras-staging/multiverse/binary-i386/Packages.gz
hoary-extras-staging/multiverse/binary-powerpc/Packages.gz
hoary-extras-staging/restricted/binary-amd64/Packages.gz
hoary-extras-staging/restricted/binary-i386/Packages.gz
hoary-extras-staging/restricted/binary-powerpc/Packages.gz
hoary-extras-staging/universe/binary-amd64/Packages.gz
hoary-extras-staging/universe/binary-i386/Packages.gz
hoary-extras-staging/universe/binary-powerpc/Packages.gz
hoary-extras/bleeding/binary-amd64/Packages.gz
hoary-extras/bleeding/binary-i386/Packages.gz
hoary-extras/bleeding/binary-powerpc/Packages.gz
hoary-extras/main/binary-amd64/Packages.gz
hoary-extras/main/binary-i386/Packages.gz
hoary-extras/main/binary-powerpc/Packages.gz
hoary-extras/multiverse/binary-amd64/Packages.gz
hoary-extras/multiverse/binary-i386/Packages.gz
hoary-extras/multiverse/binary-powerpc/Packages.gz
hoary-extras/restricted/binary-amd64/Packages.gz
hoary-extras/restricted/binary-i386/Packages.gz
hoary-extras/restricted/binary-powerpc/Packages.gz
hoary-extras/universe/binary-amd64/Packages.gz
hoary-extras/universe/binary-i386/Packages.gz
hoary-extras/universe/binary-powerpc/Packages.gz
wrote 1396 bytes  read 293840 bytes  11140.98 bytes/sec
total size is 2434929299  speedup is 8247.40


It re-downloaded all the Packages.gz files, which do indeed seem to be empty.

I just did a manual sync and it didn't do anything (nothing had changed to sync):

> 
receiving file list ... done
wrote 98 bytes  read 290831 bytes  34226.94 bytes/sec
total size is 2434929299  speedup is 8369.50


So it must be a problem with the main server :( - OR they are simply updating a few things and it will be back to normal very soon. But I'm not 100%. Have to wait for confirmation on that. If it is then when the other mirrors sync they will stop working the correct way also.

- Shane.

---

### Post by bored2k on 2005-06-01
[QUOTE=ShaneAu]What does 'apt-get update' give you (regarding ubuntu backports)?[/QUOTE]
 Nothing.

---

### Post by vagabond on 2005-06-01
Same problem here.  I just formated and reinstalled hoary.  No FF or Gaim in backports.  Just the FF1.0.2 patched upgrade from security and a Gaim patch.

Have my apt-cache from the previous install backed up; I just don't want to install them all manually.  Bad timing for my reinstall.

---

### Post by Mez on 2005-06-01
Indeed, I've just triex an rsync, and they do seem to be blank

I think this si soething to do with jdong trying to implement signing/server side Packages.gz etc etc as he said he was trying to do (as I'm noticing Release an Release.gpg (in the wrong place but there still)

But I dont know... I guess we'll have to wait till a dev gets ehre and can tell us or can roll it back

---

### Post by Mez on 2005-06-01
==============================================================================
TOPIC: make update no longer required
==============================================================================

== 1 of 1 ==
Date: Tues 31 May 2005 20:05
From: John Dong

Issue a svn up, you guys, Packages.gz has been deprecated in favor of doing
so on the Server's side! YAY!!
 This should make conflicts very rare, and should speed up your development,
too!
 the Makefile no longer updates Packages.gz, and a svn update should remove
these files from your repository.
 If you find a good reason to generate these, do ./update_list.sh ...
update_list.bsd.sh is what the server calls, because BSD's paths are
different than Linux's.
 Let me know if you run into any issues.




==============================================================================

---

### Post by tzutolin on 2005-06-01
[QUOTE=ShaneAu]What does 'apt-get update' give you (regarding ubuntu backports)?

Edit: Ahr huh... I see, I see. Well my mirror (MirrorMAX) syncs frequently and it seems to be the first effected (maybe).

The last Sync it did:



It re-downloaded all the Packages.gz files, which do indeed seem to be empty.

I just did a manual sync and it didn't do anything (nothing had changed to sync):



So it must be a problem with the main server :( - OR they are simply updating a few things and it will be back to normal very soon. But I'm not 100%. Have to wait for confirmation on that. If it is then when the other mirrors sync they will stop working the correct way also.

- Shane.[/QUOTE]


i just tried the mirror from umn.edu, and everything seems to be ok. i can see azureus, sun-jre... etc. :-k

---

### Post by ShaneAu on 2005-06-01
[QUOTE=tzutolin]i just tried the mirror from umn.edu, and everything seems to be ok. i can see azureus, sun-jre... etc. :-k[/QUOTE]
 That's because it probably hasn't synced yet.

---

### Post by jdong on 2005-06-01
Very peculiar.... There seems to be nothing wrong with the script, but I'm trying to find the problem here.

---

### Post by ShaneAu on 2005-06-01
[QUOTE=jdong]Very peculiar.... There seems to be nothing wrong with the script, but I'm trying to find the problem here.[/QUOTE]
 Mine just did a sync (again) and it's fine now:

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)

Seems to be ok.

Change anything jdong? Or did it fix it's self?

---

### Post by jdong on 2005-06-01
I did a manual packages.gz recreation.

I'm looking at my update_list.bsd.sh script, and the only thing that I could find wrong could be:

1) gzip wasn't referred to by full path (was in /usr/bin), so it probably didn't work.
2) dpkg-scanpackages may have had trouble calling dpkg-deb, because dpkg-deb isn't in cron's path, either (just "/bin").

So, I decided to give full paths to everything plus I added an explicit PATH= statement, so I hope things work out now.

---

### Post by Mez on 2005-06-01
lets hope it works :D

---

### Post by ShaneAu on 2005-06-01
[QUOTE=Mez]lets hope it works :D[/QUOTE]
 Seems to be fine now, I did a couple of manual syncs and it's keeping the packages.gz. :).

---

### Post by tzutolin on 2005-06-01
i just did an update but got this message: 

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

and this:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by ShaneAu on 2005-06-01
[QUOTE=tzutolin]i just did an update but got this message: 

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

and this:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)[/QUOTE]
 I can't seem to replicate that problem, sorry. Try again? Hopefully this will all start to run smoothly soon.

---

### Post by tzutolin on 2005-06-01
[QUOTE=ShaneAu]I can't seem to replicate that problem, sorry. Try again? Hopefully this will all start to run smoothly soon.[/QUOTE]
 Thanks Shane! :-)

I just updated again and now everything is fine :-)

Best Regards,
tzutolin

---

### Post by jdong on 2005-06-01
The problem seemed to be that mirrors would rsync while the packages.gz generation wasn't complete.

As a result, I modified the update script to use a 3-stage, tempfile process that puts in the actual Packages.gz file in virtually an instant.

---

