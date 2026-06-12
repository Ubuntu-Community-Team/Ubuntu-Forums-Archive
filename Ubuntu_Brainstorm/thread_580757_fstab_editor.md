---
title: "fstab editor"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by autocrosser on 2007-10-19
I've ran into this several times now...have setup a computer for someone & later they want to add another hard-drive--Sounds simple to me, but when I talk him/her thru it--finding the UUID--proper defaults & information, well, let's say the normal answer is---"why is this so hard?? when we installed it, everything was done already"

Mac OSX has a editor called "Drive Utility" (catchy name--yes;)  ) that partitions, labels & creates the fstab files--all rolled into one.

I would like to see something similar based around gparted--I think that all that would be needed would be a dialog or tab that offered the function.

---

### Post by chrisccoulson on 2007-10-19
A graphical tool already exists for configuring fstab...

[http://flomertens.free.fr/disk-manager/]("http://flomertens.free.fr/disk-manager/")
 It doesn't partition and label, but it does detect the addition of new partitions and notifies you at login.

---

### Post by carac on 2007-10-19
> **autocrosser said:**
> I've ran into this several times now...have setup a computer for someone & later they want to add another hard-drive--Sounds simple to me, but when I talk him/her thru it--finding the UUID--proper defaults & information, well, let's say the normal answer is---"why is this so hard?? when we installed it, everything was done already"

Mac OSX has a editor called "Drive Utility" (catchy name--yes;)  ) that partitions, labels & creates the fstab files--all rolled into one.

I would like to see something similar based around gparted--I think that all that would be needed would be a dialog or tab that offered the function.



I subscribe to this idea - I have just spent 10 minutes fixing something like that manually - obviously now with UUIDs the manual mode is too complex for the average user !!!

---

### Post by Ceemee on 2007-10-19
Its Got my vote.

---

### Post by zolookas on 2007-10-19
Looks like Disk manager is a very good utility, so ubuntu could just include it.

---

### Post by chrisccoulson on 2007-10-19
disk-manager is quite good. I used it on Feisty and Gutsy. Setting up my NTFS partition was a breeze.

---

### Post by Zdravko on 2007-10-19
Yepp. Nice feature.

---

### Post by autocrosser on 2007-10-19
I just looked at Disk Manager & am d/l it now--I would love to see it & gparted rolled together--would be a great utility........

---

### Post by unixhead on 2007-10-19
This is one the most useful features in OS X. Go for it.

---

### Post by m0eman on 2007-10-19
Agreed, this would be handy to have by default.

---

### Post by Zdravko on 2007-10-19
Yes, by default would be perfect.

---

### Post by teasum on 2007-10-23
Another agreement here.

---

### Post by Shootfast on 2007-10-23
Wasn't disk manager included in Dapper but removed from Edgy? I seem to remember some outcry about that a while back

---

### Post by FXEF on 2007-10-23
> **Shootfast said:**
> Wasn't disk manager included in Dapper but removed from Edgy? I seem to remember some outcry about that a while back

Yes, Disk Manager is in 6.06 LTS, however I find that editing fstab in gedit to be simpler for me.

FXEF

---

### Post by SonicSteve on 2007-10-23
It might have even been removed from Dapper and present in Breezy. Anyway where ever it was it wasn't able to change the FSTAB. I remember it had functions that made it sound like it would mount them but it never did.

---

### Post by SonicSteve on 2007-10-23
> **FXEF said:**
> Yes, Disk Manager is in 6.06 LTS, however I find that editing fstab in gedit to be simpler for me.

FXEF

I don't find it easier by any stretch of the imagination, but I manage without it. I would also like to say that I would love to see this process simplified. There is no doubt that many people these days are adding hard drives to their computers. Under windows it isn't much of an issue. I remember though when I first started learning about Ubuntu that I added a hard drive and I didn't understand why I couldn't access it. Then after mounting it I didn't have R/W access. Although that was valuable experience it would likely have sent someone with less experience running and screaming from Linux. Let's not take these people for granted.

---

### Post by FXEF on 2007-10-23
> **SonicSteve said:**
> I don't find it easier by any stretch of the imagination, but I manage without it. I would also like to say that I would love to see this process simplified. There is no doubt that many people these days are adding hard drives to their computers. Under windows it isn't much of an issue. I remember though when I first started learning about Ubuntu that I added a hard drive and I didn't understand why I couldn't access it. Then after mounting it I didn't have R/W access. Although that was valuable experience it would likely have sent someone with less experience running and screaming from Linux. Let's not take these people for granted.

Maybe gedit is not easier but works for me. This link will explain how to auto mount disk or partitions.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

This explains two different methods:
1) Mounting partitions with a script
2) Mounting partitions manually

I perfer mounting manually method, but that's just my personal choice. The script method may work best for some users. 

FXEF

---

### Post by screaminj3sus on 2007-10-23
Definately agreed, although ubuntu automagically detects my windows drive it doesn't always work right. Just recently I had a lot of "fun" in fedora 7 and suse 10.3 because they basically try and force me to install grub onto my windows drive so I unplugged it during install (When I install to the windows drive they don't like to boot at all, I like the way ubuntu doesn't try and **** with my vista drive at all because grub makes vista not boot at all) and I had to maually edit the fstab file to get the windows drive to mount. In ubuntu I also had to unplug it during the beat because the install would freeze, but it still automatically detected it when I plugged it back in unlike fedora/suse. This could still be a very usefull tool to have though.

---

### Post by Bou on 2007-10-23
> **chrisccoulson said:**
> A graphical tool already exists for configuring fstab...

[http://flomertens.free.fr/disk-manager/]("http://flomertens.free.fr/disk-manager/")
 It doesn't partition and label, but it does detect the addition of new partitions and notifies you at login.

I opened a [thread]("http://ubuntuforums.org/showthread.php?t=429281&highlight=%5BIDEA%5D") in the Gutsy idea pool proposing to include disk-manager by default, and was planning to open a new one here. Could you guys give me a hand and help me expose the rationale behind this?

---

### Post by autocrosser on 2007-10-23
> **Bou said:**
> I opened a [thread]("http://ubuntuforums.org/showthread.php?t=429281&highlight=%5BIDEA%5D") in the Gutsy idea pool proposing to include disk-manager by default, and was planning to open a new one here. Could you guys give me a hand and help me expose the rationale behind this?
 
 
Hi Bou---
 
That is why I opened the thread here---I like the way OSX has it setup & think that We should be able to "blend" Disk Masnager & Gparted together to have the same amount of functionability.....

---

### Post by Bou on 2007-10-23
> **autocrosser said:**
> That is why I opened the thread here---

Cool, mind if we open a [spec]("http://ubuntuforums.org/showthread.php?t=409519") and link it here then? That should be the ideal way to propose stuff.

> **autocrosser said:**
> We should be able to "blend" Disk Masnager & Gparted together to have the same amount of functionability.....

Agreed, but I think that's a bit out of scope here... the Ubuntu devs can hardly add new features to DM, I think you should rather contact the DM developer and suggest him to add that feature. Ubuntu can include DM in the default install, and that's about it.



EDIT: I just opened a spec and a new, more specific [thread]("http://ubuntuforums.org/showthread.php?p=3614064#post3614064"). Hope you don't mind.

---

### Post by autocrosser on 2007-10-23
> **Bou said:**
> Cool, mind if we open a [spec]("http://ubuntuforums.org/showthread.php?t=409519") and link it here then? That should be the ideal way to propose stuff.



Agreed, but I think that's a bit out of scope here... the Ubuntu devs can hardly add new features to DM, I think you should rather contact the DM developer and suggest him to add that feature. Ubuntu can include DM in the default install, and that's about it.



EDIT: I just opened a spec and a new, more specific [thread]("http://ubuntuforums.org/showthread.php?p=3614064#post3614064"). Hope you don't mind.


That's great--I'll take a look at the spec & thread in a bit---I've E'd the dev of DM--We also need to contact the Gnome devs of Gparted & see what they think---If we can get a blend of the two it would make a great app...


Bou--I've cross-posted our threads---Bou's post is:   [http://ubuntuforums.org/showthread.php?t=588816](http://ubuntuforums.org/showthread.php?t=588816)

I will contact the Gnome devs tonight (Pacific time) & send a second E to DM's dev.....

---

### Post by veratyr on 2007-10-24
+1

---

### Post by Denis on 2007-10-24
I agree. Ubuntu really needs a graphical tool to configure fstab.

---

### Post by mikedoth on 2008-01-28
Disk management and a Samba front end and I'll put it back on my desktop. Needless to say I was pissed when it was removed the first time.

---

### Post by cszikszoy on 2008-01-28
Is Disk Manager similar to PySDM?  (Python Storage Device Manager?  All I'm getting on the Disk Manager website is 404 errors, so I can't really see what it is, but PySDM works very well for me, I'd definitely recommend it.

It's available in the repositories.

---

### Post by maybeway36 on 2008-01-28
Does it contain support for mounting CIFS shares? Because it really should. Windows can do it (Map Network Drive).

---

### Post by zekopeko on 2008-01-28
> **mikedoth said:**
> Disk management and a Samba front end and I'll put it back on my desktop. Needless to say I was pissed when it was removed the first time.

if i remember correctly it wasn't up to ubuntu but gnome. they removed it because it was unmaintained.

---

### Post by mikedoth on 2008-01-28
I'm still a fan but it's the stuff that drives away new users and quick. I stuck it out but have since moved on to greener pastures with PCLINUXOS-Gnome Edition but wouldn't mind coming back some day.

---

### Post by vikari_metal on 2008-01-30
Another agreement here.

---

### Post by oponek on 2008-02-02
[https://blueprints.launchpad.net/ubuntu/+spec/disk-manager](https://blueprints.launchpad.net/ubuntu/+spec/disk-manager)

---

### Post by autocrosser on 2008-02-03
Also take a look at:  [https://blueprints.launchpad.net/ubuntu/+milestone/hardy-alpha-5](https://blueprints.launchpad.net/ubuntu/+milestone/hardy-alpha-5)

:guitar:

---

### Post by sicofante on 2008-06-15
I'm truly amazed by Ubuntu sometimes, in the wrong way. I just can't believe I had to dig in Google searching for a utility to permanently mount my partitions. People saying that manually editing fstab is easy can't see beyond their own geeky nose. A modern desktop operating system asking users to edit such a complicated configuration file by hand deserves no place in most homes and offices.

The funny thing is Disk Manager is no longer being developed but works fine in Hardy. Who and why made the decision not only to exclude it from default install but also from the repositories? Such a dumb move.

---

### Post by autocrosser on 2008-06-15
You are not alone--take a look at: [http://brainstorm.ubuntu.com/search?keywords=fstab&ordering=mostvotes](http://brainstorm.ubuntu.com/search?keywords=fstab&ordering=mostvotes)

There has been enough talk that I believe something will be done---Question is: When?

---

### Post by sicofante on 2008-06-15
Well, thanks for the link. Actually, that brainstorm site is full of common sense. If Ubuntu devs just followed requests on that site...

---

### Post by Gina on 2008-06-15
I too thought this was totally ridiculous!! :(  Earlier versions showed all your drives and partitions - that was fine.  Why hide partitions?  I really don't know!

---

