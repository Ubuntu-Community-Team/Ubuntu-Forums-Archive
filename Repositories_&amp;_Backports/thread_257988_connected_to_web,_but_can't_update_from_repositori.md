---
title: "connected to web, but can't update from repositories"
date: 2006-09-15
forum: Repositories &amp; Backports
---

### Post by theinvertedweb on 2006-09-15
I have a fresh install of Dapper x86, and am connected to the Internet (i'm posting from the Dapper machine), but i can't seem to update any packages through apt. (or the synaptic package manager).  i have a notification saying that i need 116 updates, and when i mark and then apply, i get the following errors:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_3.1.9ubuntu7.1_i386.deb)
  Connection failed [IP: 195.248.90.23 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060725_all.deb)
  Connection failed [IP: 195.248.90.23 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20060725_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_6.06+20060725_all.deb)
  Connection failed [IP: 195.248.90.23 80]

yadda yadda yadda for all 116 packages.  Does anyone have any advice or course of action to resolve this?

oh yea, and i have already gone through the forum for ideas, i've reinstalled apt after following another thread, but that hasn't fixed the issue.

---

### Post by andiii on 2006-09-15
Are you online through a proxy or sth.?

Synaptic has it's own Network Settings.. but it should be alright, because you have the lists that tell you to update..

---

### Post by theinvertedweb on 2006-09-15
i'm not sure about a proxy, but possibly (i'm new to this office, so i'm not quite sure how the network is set up yet), how can i fix things if i am behind a proxy?

I don't think i am behind any proxies. i was able to get into my router and i have nothing blocked or anything like that.  i have a router set up in the back that connects each person's desk, then i have a switch on my desk in order to connect all the machines that i get to use.  the windows and mac machines are fine and can update, email, web, everything, but the ubuntu machine can get on the web and do all that cool stuff, just can't connect to repositories.  can't upgrade, update, or add new apps.

does anyone have any suggestions that might help me figure out my issue?  i tried:

sudo apt-get update
sudo apt-get upgrade

and both failed:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


i'm totally confused, any help?

---

### Post by budman21901 on 2006-09-15
I am having the same exact problem.  Instead of making a new topic i figured i would just report here.  I have updated my sources list, and no matter what i do everything fails.  I think its my router blocking somehow, but i dont know how to fix it.  Are there ports i need to forward or something.  Please help!!    

Router - Netgear prosafe vpn firewall model fvs318

`````````````````````````````````````````````````````
Errors

[PHP]http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Connection failed [IP: 195.248.90.54 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz: Connection failed
http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz: Connection failed
http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz: Connection failed
http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz: Connection failed [IP: 195.248.90.54 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz: Connection failed [IP: 195.248.90.54 80][/PHP]

`````````````````````````````````````````````````````````

 My sources list 

[PHP]deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse[/PHP]

---

### Post by budman21901 on 2006-09-15
I never figured out the problem with dapper 6.06.  I just installed edgy eft knot3, and everything works perfectly.  Still don't explain why dapper is locking out the repositories though.

---

### Post by theinvertedweb on 2006-09-18
I haven't been able to figure this out either.  it seems that my router is open to all traffic, so i don't know what could be blocking the repos... any suggestions?

weird coincidence, i have the same router as you  ;)

---

### Post by firstc624 on 2006-09-20
i know for me i often get an error saying i can't fetch to to the security.ubuntu.com repo and the us.archive.ubuntu.com repo.

the way i have worked around it for since i can't figure out how to make dapper do it, is i manually go to the web pages

[http://us.archcive.ubuntu.com](http://us.archcive.ubuntu.com)  & [http://security.ubuntu.com](http://security.ubuntu.com)

then i try to update again and it all goes thru just fine.  

hope it works for ya

First_c

---

### Post by budman21901 on 2006-09-22
theinvertedweb, I don't think its router although it is a coincidence.  This problem is now popping up here more often.  It's not fixed, but i thought i would list what i tried with dapper for process of elimination.

* Tried endless source lists.  
* Tried removing apt-get and all depencies, and reinstalling.
* Tried installing apt-get from source.  
* Tried installing dapper without router. (Router elimination)  
* Tried edgy sources for installing apt-get.  

I tried everything in dapper.  I have no clue what it could be.  I installed Edgy, and everything worked perfectly.  I thought it was apt-get, but i will be damned if i could get it working.  What's funny is you can access the repository via browser, but apt-get can not get to them, so you know they are active.  Definantly a problem that should be on top of the list.  Especially when it happens straight from installation.  Good luck.

---

### Post by Peacepunk on 2006-09-22
FYI / Other bug ?

Posted 3 minutes before: Synaptic (dapper) looks for a file that is NOT in the repository - same same but different, you can't download existing files and I can't upgrade because the file doesn't exist.

A corrupted list of files on ubuntu servers maybe ?

---

### Post by samkon on 2006-09-22
let you copy to your own sources.list in to other directory first. Then let you try;
```

wget http://ubuntu-tr.com/download/sources.list

sudo cp sources.list /etc/apt/sources.list

sudo apt-get update
```

I don't know that you may have problems about language or other. Becouse I took this sources.list from a Turkish site that helps ubuntu users as here in Turkey.

if you will have any problem about your new sources.list that I prefered to you. let you move your own sources.list back..

good luck..

---

### Post by soaro77 on 2006-09-22
I am having the exact same problem. Just installed Ubuntu yesterday and it says I need updates but I get the exact same errors. I tried going through the apps and selecting the ones I want to install and get this error for everything. I can connect just fine through Firefox. If I paste the URL from the package into Firefox it will download it. But Synaptic won't for some reason. The network settings are exactly the same as Firefox and I am not going through a proxy or anything. I just have a router out to the Internet that has a built in firewall. It allows all outgoing requests. I don't know what to do. I've used Linux for years but am new to Ubuntu. I would appreciate any help or suggestions anyone might have on how to get this working.

---

### Post by jnk0906 on 2006-09-22
I have also had this problem with the 6.06 and the 6.06.1 releases of desktop and server.  All methods of updating the software with the APT compatible applications have generated the errors.  

I have been able to install 5.10 (Breezy) and perform an upgrade by changing the sources.lst file.  If you change the references from "breezy" to "dapper" and run the SUDO APT-GET UPDATE command followed by the SUDO APT-GET UPGRADE command, the system will alert you that a newer version is available.  During the upgrade, it appears as though a newer version of APT is installed because you can now run SUDO APT-GET UPDATE again and get all of the Dapper upgrades.  There are a few Breezy components that are no longer supported, but I have not had any issues...other than taking a long time to actually perform the upgrade.

It would sure be nice if the problem would be recognized and fixed, but it seems to occur for anyone behind a NAT firwall or some proxy servers...which I would think is a large percentage of users.

---

### Post by soaro77 on 2006-09-22
How do I do this? Are you saying I need to download and burn a CD for an older version of Ubuntu and install it instead of the current version and then upgrade it?

Ugh, I suppose I can do that but geez what a pain that will be.

---

### Post by Ausus on 2006-09-23
Hi all,

I have the same problem.
Cant update from [http://za](http://za).............
Every thin else seems ok

This was a week a go when i did a fresh install.

regards

---

### Post by shailbond on 2006-09-23
hey i had similar problem and this is how itis to be fixed. On terminal type sudo gedit /etc/apt/sources.list to open and edit the file. open another terminal or system>administration>network tools. inthe open file wherever you find a web address e.g archive.ubuntu.com  , security.ubuntu.com replace it with ipv4 address. So your entry will look like now 
  deb [http://123.123.123.123/ubuntu](http://123.123.123.123/ubuntu)  ...... .
instead of

  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) ....

. where 123.123.123.123  is the address u obtain when u ping respective web addresses.

Same way u can connect ur GAIM or evolution by giving ipv4 addresses in place  of web addresses.  
  However firefox is all right . You dont need anything foe that.  

Hope this works. Happy computing

---

### Post by jnk0906 on 2006-09-23
> **soaro77 said:**
> How do I do this? Are you saying I need to download and burn a CD for an older version of Ubuntu and install it instead of the current version and then upgrade it?

Ugh, I suppose I can do that but geez what a pain that will be.

Unfortunately, yes... that is what I had to do.  The new version seems to set name resolution priority to IPv6, which my home router does not support.  As a result, any external named addresses fail to resolve to their IP address before the timeout occurs.  I am not a developer, so I could be off base here, but this is my observation with several iterations of installations using the server and desktop versions of 5.10, 6.06, and 6.06.1.

The next post suggests using the numbered IP address, but I recommend against this for a couple of reasons.  First, it may change and you will need to remember which name you used to acquire the IP address.  Second, the named address may be load balanced over several servers and using the IP address directly will prevent you from taking advantage of the load balancing and automatic server selection if the server fails.

It really is up to the Ubuntu developers to release a new version with this fixed... such as 6.06.2.

---

### Post by soaro77 on 2006-09-23
OK, you are right, I think that is the problem. I installed 5.10 and it was able to update just fine. Unfortunately for me when I tried adding other programs it uninstalled my desktop and I ended up with it booting to the command prompt instead of xwindows. This is for my wife so she really needs to run xwindows (she isn't command line prompt saavy...hehe). So now I am back to installing the 6.06.1 version. At least that installed and was working nicely except for the updater. 

I'll try using the IP addresses for now just to get things working until the devs get this fixed. That should at least get it going for now. I'll just comment out the original lines so I still have them once it is fixed. I'll report back if this works so others having this problem will know what to do until this is fixed.

I'm a developer but I really have no idea how or where to fix this. Otherwise I would. But I also don't want to mess too much with the distribution. Other than this problem it seems very nice (much better than any Windows version I have ever installed).

---

### Post by andybb on 2006-09-23
The problem is solved here!

[http://thread.gmane.org/gmane.linux.ubuntu.user/76867/focus=80212](http://thread.gmane.org/gmane.linux.ubuntu.user/76867/focus=80212)

It says,
[I]
From: laroetman <ulist <at> gs1.ubuntuforums.org>
Subject: Re: Synaptec connection problem
Newsgroups: gmane.linux.ubuntu.user
Date: 2006-06-13 03:00:46 GMT (14 weeks, 4 days, 15 hours and 36 minutes ago)

I had the same problem.  Tried removing that line "proxy::http::false",
and that fixed the problem!  That doesn't make sense to me though... 
That's a major bug, and why does it not seem that everyone else is
having the same problem?  Crazy!

-- 
laroetman
[/I]

---

### Post by andybb on 2006-09-23
arg! i posted all the wrong stuff!

what i mean quote was
[I]
From: Tired <ulist <at> gs1.ubuntuforums.org>
Subject: Re: Synaptec connection problem
Newsgroups: gmane.linux.ubuntu.user
Date: 2006-06-12 17:35:08 GMT (14 weeks, 5 days, 1 hour and 9 minutes ago)

You may have the same problem I did.  Check /etc/apt/apt.conf.  Is there
a proxy entry there?  Some like "Proxy::http::false"?  (I don't have the 
exact syntax in front of me.  If so, remove that line.  I believe it's
telling apt to connect through a proxy named "false", which of course,
doesn't exist.

This fixes the problem for me as well. I saw the line, but incorrectly
surmised that it was turning off http proxy. This is a problem on the
base install of the "desktop" CD and at least the "LAMP" option of the
"server" CD. I'd think a lot of people would be complaining about this.

-- 
Tired
[/I]

---

### Post by soaro77 on 2006-09-23
Yep, that is the problem. I removed that line from apt.conf and it is working fine now. Thank you very much for finding this. I was getting very frustrated with this. Someone really should make that posting a sticky in the forums. As more people install the latest version of Ubuntu, they are going to hit this problem.

---

### Post by saule on 2006-09-26
During the install, the installer told me that some lines were commented out in /etc/apt/sources.list because the URL were not reachable.
I ignored the message but then I had all kind of errors when loading packages or updating repositories.
Finally I found out in one of the forum that the error was caused by a wrong entry in /etc/apt/apt.conf, namely the line 
Acquire::http::Proxy "true";
was causing a problem. I removed it and it solved the issue.

Hope this helps !

---

### Post by bigken on 2006-09-26
I got round this by adding my dns server addresses to **/etc/resolv.conf**
and also adding them to my router ;)

Router as Domain Name Server. 
dns1 XXX.XX.XXX.XX
dns2 XXX.XX.XXX.XX

Router as Default Gateway.
Gateway XXX.XXX.XXX.XXX (IP Address:)

hope this helps

---

### Post by darquillity on 2006-10-12
Hey guys,

I had the same problem and came to this forum to find an answer.

...... but I managed to sort it out :D 

All I did was forward port 3128 (as this is the port setup for the proxy settings in the updater's settings).

Hope that helps someone.

:mrgreen:

---

### Post by ozooha on 2007-08-16
> **saule said:**
> During the install, the installer told me that some lines were commented out in /etc/apt/sources.list because the URL were not reachable.
I ignored the message but then I had all kind of errors when loading packages or updating repositories.
Finally I found out in one of the forum that the error was caused by a wrong entry in /etc/apt/apt.conf, namely the line 
Acquire::http::Proxy "true";
was causing a problem. I removed it and it solved the issue.

Hope this helps !

What if one doesn't have the file /etc/apt/apt.conf?
How do I resolve this?
OZooHA

---

### Post by Seisen on 2007-08-16
You can always create the file here is what mine says

```
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";

```

---

### Post by ozooha on 2007-08-16
> **Seisen said:**
> You can always create the file here is what mine says

```
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";

```

Dude I really appreciate your help with this file but this did not help me
at all.
Any thing else which I have missed or need to know to resolve this
apt-get update mess?
OZooHA

---

