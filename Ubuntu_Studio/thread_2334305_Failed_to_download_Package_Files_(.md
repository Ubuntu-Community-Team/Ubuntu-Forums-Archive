---
title: "Failed to download Package Files :("
date: 2016-08-18
forum: Ubuntu Studio
---

### Post by javierdl on 2016-08-18
Hi all,

I get this error message when accepting to download update files:

[IMG]https://sites.google.com/site/javierwebfolio/_/rsrc/1471532578683/temp/Failed%20to%20download.jpg[/IMG]

The advise to check my Internet connection really does not help much. If there was a problem with my Internet connection I wouldn't be able to post this on the first place ;)
Should I go to Settings? (lower left corner) If so, what should I be looking for?

Thanks guys :)

JDL

---

### Post by QIII on 2016-08-18
Hello!

Please use the terminal and issue the following command:

```
sudo apt-get update && sudo apt-get upgrade
```

and post back the results between code tags.

---

### Post by javierdl on 2016-08-18
Thanks for helping QIII :)
Here it is:

```
javier@javier-Predator-G3-710:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for javier: 
Hit:1 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Ign:5 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial InRelease
Ign:6 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease               
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]      
Hit:8 [http://ppa.launchpad.net/minetestdevs/daily-builds/ubuntu](http://ppa.launchpad.net/minetestdevs/daily-builds/ubuntu) xenial InRelease
Ign:9 [http://repo.vivaldi.com/snapshot/deb](http://repo.vivaldi.com/snapshot/deb) stable InRelease                    
Hit:10 [http://repo.vivaldi.com/snapshot/deb](http://repo.vivaldi.com/snapshot/deb) stable Release                     
Hit:11 [http://ppa.launchpad.net/minetestdevs/stable/ubuntu](http://ppa.launchpad.net/minetestdevs/stable/ubuntu) xenial InRelease    
Hit:12 [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial InRelease
Ign:13 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial Release
Hit:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease             
Ign:15 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 Packages
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Hit:18 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                    
Ign:19 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main i386 Packages
Ign:20 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main all Packages
Hit:21 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release           
Ign:22 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en_CA
Ign:23 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [371 kB]
Ign:25 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:26 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:15 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 Packages
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [367 kB]
Ign:19 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main i386 Packages
Ign:20 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main all Packages
Get:30 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [319 kB]
Ign:22 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en_CA
Ign:23 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en
Get:31 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [316 kB]
Ign:25 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:26 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:15 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 Packages
Ign:19 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main i386 Packages
Ign:20 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main all Packages
Ign:22 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en_CA
Ign:23 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en
Ign:25 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:26 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:15 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 Packages
Ign:19 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main i386 Packages
Ign:20 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main all Packages
Ign:22 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en_CA
Ign:23 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en
Ign:25 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:26 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:15 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 Packages
Ign:19 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main i386 Packages
Ign:20 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main all Packages
Ign:22 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en_CA
Ign:23 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en
Ign:25 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:26 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main DEP-11 64x64 Icons
Err:15 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 Packages
  404  Not Found
Ign:19 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main i386 Packages
Ign:20 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main all Packages
Ign:22 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en_CA
Ign:23 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main Translation-en
Ign:25 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:26 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial/main DEP-11 64x64 Icons
Fetched 1,563 kB in 4s (342 kB/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
javier@javier-Predator-G3-710:~$ 



```

---

### Post by QIII on 2016-08-18
Ok.  

This is a "teach a man to fish..." moment.  :)

What does the "Failed to fetch " line near the bottom suggest to you?  Do you know what 404 means?

Your clue is there.  If you see it, let me know.

This is probably an easy fix.

---

### Post by javierdl on 2016-08-18
Thanks QIII I do appreciate the fishing lesson actually :)
It would suggest to me that either the file is not were it was anymore, or the address is wrong. Either way the address needs fixing, either to point to the right and existing file, or simply to correct the address. I would think is probably the former.
Am I close?

---

### Post by QIII on 2016-08-18
So ...

In the first command I gave you, the "&&" effectively means "... if the first completes, then move on to the second ..."  The first failed, so it did not move on.

However, if you were to run ```
sudo apt-get upgrade
```  (or dist-upgrade, or apt instead of apt-get, etc) right now, you would get updates for the packages that could be found.

The 404 on the PPA might indicate a number of things:  The maintainer has moved the PPA to a different URL, the maintainer of the PPA has it down for the moment to update, the maintainer of the PPA has abandoned and removed it, etc.

If you disable the PPA in your sources.list (via the terminal or GUI), I'd bet dollars to doughnuts the issue would disappear.   That would let you update.  You could investigate what is going on with the PPA at some other time.


(By the way, this is one of those cases that explains why so many of us ask folks to use the terminal when we are trying to help.  Some people get from that the impression that you have to be a programmer to use Linux.  This isn't programming.  It's asking the OS a question.  To get good diagnostics from Windows, I often ask people to run commands at the cmd prompt.  Same thing.  In this case, what I got back from your feedback was not only the exact nature of the error, but the very URL that was causing the problem!)

---

### Post by javierdl on 2016-08-18
Not surprisingly to you I suppose: it worked! ;)
It took a while to go through the whole process, I guess it had lots to catch up.

So, should I infer this the way it'll be done every time? Or I'm not fishing yet?

---

### Post by QIII on 2016-08-18
Good to hear.

If you left the PPA disabled, you are good for now.  You can check periodically to see if it's available or if it has moved.

Happy fishing!

---

### Post by howefield on 2016-08-19
Just to add that if you visit the failed repository, you'll see that there is no Xenial repository.

[http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu/dists/](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu/dists/)

It stops at Utopic. Just be aware that if you have software installed on your machine from when the repository was active, it won't get any updates.

---

### Post by javierdl on 2016-08-19
howefield,  Thanks. Then, how to identify what software was coming from that PPA?
I thought it came with the original installation of Ubuntu Studio.

---

### Post by howefield on 2016-08-19
> **javierdl said:**
> howefield,  Thanks. Then, how to identify what software was coming from that PPA?

Well going to the [launchpad ppa]("https://launchpad.net/~i-nex-development-team/+archive/ubuntu/stable") page and filtering by release to the "Overview of published packages"  Looks like one package called "*i-nex*"

> I thought it came with the original installation of Ubuntu Studio.

I doubt a ppa would be included with any flavour of Ubuntu out of the box, it has to have been installed post installation of the operating system. PPAs come and go (as this one has) and in any event, there is no Xenial repository so why include a non existent repository ?

---

### Post by javierdl on 2016-12-06
Thanks for your reply howefield :)

---

