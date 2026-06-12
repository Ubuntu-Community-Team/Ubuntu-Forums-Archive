---
title: "How to update/upgrade the 13.04 daily builds"
date: 2012-12-10
forum: Ubuntu Development Version
---

### Post by levomac on 2012-12-10
Hi, 
Please tell me the method to update/upgrade the daily build as there are no software sources and adding any repository ends with an error .
Is there some other command to add package lists or do we need to add quantal sources ? if yes then how??!!
Please advise,
thanks.
What's the 'W' here,W is not my copm or account name
here's the result of apt-get update
sudo apt-get update

Err [http://archive.canonical.com](http://archive.canonical.com) raring InRelease                              
  
Err [http://archive.canonical.com](http://archive.canonical.com) raring InRelease                              
  
Err [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                    
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                    
  Could not resolve 'archive.canonical.com'
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring InRelease                          
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring InRelease                         
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed InRelease
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-proposed Release.gpg
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/InRelease](http://archive.ubuntu.com/ubuntu/dists/raring/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/raring-updates/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/raring-backports/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/raring-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/raring/InRelease](http://archive.canonical.com/ubuntu/dists/raring/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/InRelease](http://extras.ubuntu.com/ubuntu/dists/raring/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-proposed/InRelease](http://archive.ubuntu.com/ubuntu/dists/raring-proposed/InRelease)  

W: Failed to fetch [http://archive.canonical.com/dists/raring/InRelease](http://archive.canonical.com/dists/raring/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/raring/Release.gpg](http://archive.canonical.com/ubuntu/dists/raring/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/dists/raring/Release.gpg](http://archive.canonical.com/dists/raring/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring-security/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring-proposed/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ventrical on 2012-12-10
The best way to update the daily build is to use the tool zsync. You can download it from the repositories:

sudo apt-get install zsync

 Once you have this you can go to the directory where the .ISO file is and, in terminal,

zsync -i ./raring-desktop-i386.iso [http://cdimage.ubuntu.com/daily-live/current/raring-desktop.i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/raring-desktop.i386.iso.zsync)

If your ISO file differs then just use the appropiate .iso file that you are using , ie., amd64 bit.

For more on this just click the link below with the Sudo Code Quick Grabber.

---

### Post by serdotlinecho on 2012-12-10
Could you share your /etc/apt/sources.list? And please wrapped with the code tags. Click on the hashtag symbol and insert the output :)

```
~$ cat /etc/apt/sources.list
```

---

### Post by levomac on 2012-12-10
double post sorry

---

### Post by levomac on 2012-12-10
> **serdotlinecho said:**
> Could you share your /etc/apt/sources.list? And please wrapped with the code tags. Click on the hashtag symbol and insert the output :)

```
~$ cat /etc/apt/sources.list
```
here you go
```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha amd64 (20121209)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring universe
deb-src http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb-src http://archive.ubuntu.com/ubuntu raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb-src http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb-src http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb http://archive.ubuntu.com/ubuntu raring-proposed universe restricted main multiverse
deb http://archive.canonical.com/ raring partner
deb-src http://archive.canonical.com/ raring partner
deb-src http://extras.ubuntu.com/ubuntu raring main
```

---

### Post by grahammechanical on 2012-12-10
It would be my guess that "W" = Warning!

Update: I have just updated my Raring install without any errors messages and I have the same repositories as you do. My sources.list looks the same as your one.

You say this:

> there are no software sources

Where are you looking? How can there not be any software sources?

When we started testing Raring Ringtail we started off with an install of 12.10 and we used a certain command to change the quantal software sources to raring software sources. From that we update daily and get, over time, a 13.04 install. At first we did not have Raring repositories for 'extras.' and that always gave an error but it has now been resolved.

Regards.

---

### Post by zika on 2012-12-10
This looks to me as a network problem of some kind. I've glanced through Your /etc/apt/sources.list and it looks (on glance) OK. Are You behind some proxy, firewall or something like that that could prevent Your computer from accessing these addresses given in that file? Try accessing them in browser just to check...

---

### Post by grahammechanical on 2012-12-10
Looking again at your sources list I see this:

> # deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha amd64 (20121209)]/ raring main restricted

That is the daily image from 09/12/2012. The last image I tried was 20121207 and it failed like the other 3 images I tried with an error message of "unable to find a medium containing a live file system."

So, I would not be surprised if this issue that you have was a bug. I have lost the confidence I once had in the daily ISO images of the development branch.

I guess that I must now download the 20121210 (today's) image. Perhaps I will at last get an install of Raring and may be it will have the same problem as yesterday's image that you have found.

Update: Today's image (201210) has the same error - "unable to find a medium containing a live file system." as the other images I have tried. So, I cannot confirm if a fresh install of Raring has a bug that leaves out the Software Sources.

My problem has nothing to do with my machine. My 12.04.1 disk runs fine and installs as well.

Regards.

---

### Post by rrnbtter on 2012-12-10
Greetings,
to update the daily iso use the procedure in post #2.
However it sounds to me [and I could be wrong] that you are trying to boot the disk and or usb which ever it is and update the software sources. 

The software sources should be updated after the system has been installed. If you are only trying the system and not testing I would suggest that you leave the "proposed" unchecked in the Update manager.  

Given that you have compatible hardware it should be smooth sailing. 13.04 is a delight!
rrnbtter

---

### Post by alphacrucis2 on 2012-12-10
> Err [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg
**[COLOR="Red"]Could not resolve 'archive.canonical.com'[/COLOR]**

Looks like a DNS problem to me. Is your internet access even working from your raring install?

---

### Post by levomac on 2012-12-11
@grahammechanical, zika, rrnbtter, alphacrucis2

Thank you all for your response.
Well the method of upgrading the 12.10 by adding raring sources works fine for me, infact I had this set up till 9/12/12 when I installed the daily build for that day.

The quantal upgraded to raring install works fine ,no issues except that update/upgrade are quiet slow.But the fresh install of daily build pops up with that error.(of course I was updating an installed system and not a live usb etc:))
When I tried updating with the software updater it said that the current install is fully updated.
I am using an employer provided wifi with a proxy but the network work  nicely as in browsing etc ,besides the upgraded install updates ok.
So I guess its a daily build issue or some bug with that specific day build as I have now again reinstalled quantal and upgraded it to raring.

So if anyone has tried a newer daily build, may be they can inform better.

Regards

---

