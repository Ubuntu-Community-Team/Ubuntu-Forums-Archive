---
title: "Issues with 12.10 and NVidia"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Djalmahal on 2012-09-20
When I try Ubuntu without installing only "nomodeset" works, otherwise the display is just garbled.

Now I installed 12.10 on a partition, when I let it boot up it comes up with noveau failed to idle channel 2/3.
I had to update grub manually and now there is no option for "safe mode". I tried editing the grub command with "nomodeset" and "--nomodeset" but both are not recognized. So now when I boot it up it never goes out of textmode and i never get to the log in screen. 
I'm sure once I get to the proper desktop enviroment I can permantly fix it by installing the nvidia driver, but how do I get there?

Thanks for any tips.

---

### Post by dino99 on 2012-09-20
other users already had the same issue, and most works around by removing "splash" from the boot line.

---

### Post by BigSilly on 2012-09-22
Does anyone know if this bug is likely to be fixed for the final release? I don't expect it will be for the next beta. It's no problem to me to delete the words "splash" from the boot options, but to a flipping massive wodge of users out there it's going to cause a serious problem. They're just going to see a glitchy broken OS, and move on.

I found a couple of related bug reports, but there doesn't seem to be any interest in this issue from the devs in those particular reports. Surely they are aware of this problem? I've tried it on both Nvidia and ATI GPU's, on both DVD' and USB's, and the issue is pretty prevalent in all situations.

---

### Post by dino99 on 2012-09-22
Actually all the packages (> 20000) are into the rebuilt queue, to take advantage of the new gcc that fix around 92 issues itself. So that huge task will need some time to end. But we surely get less trouble then.

):P

---

### Post by mc4man on 2012-09-22
> **BigSilly said:**
> Does anyone know if this bug is likely to be fixed for the final release? I don't expect it will be for the next beta. It's no problem to me to delete the words "splash" from the boot options, but to a flipping massive wodge of users out there it's going to cause a serious problem. They're just going to see a glitchy broken OS, and move on.

I found a couple of related bug reports, but there doesn't seem to be any interest in this issue from the devs in those particular reports. Surely they are aware of this problem? I've tried it on both Nvidia and ATI GPU's, on both DVD' and USB's, and the issue is pretty prevalent in all situations.

There was a little interest here (I based on nvidia/nouveau as that's what I have), though nothing much of late
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518)

Using nomodeset to get a live session isn't an acceptable option for most as the live session is terrible, removing splash could be explained in release notes though whether they would do so I don't know
(if not fixed I'd just get rid of splash on the live image, never amounted to much in Ubuntu anyway
At least here, once installed, with nouveau the boot up splash doesn't work anyway , it does for nvidia drivers for all of a couple of sec.'s

---

### Post by BigSilly on 2012-09-22
> **mc4man said:**
> There was a little interest here (I based on nvidia/nouveau as that's what I have), though nothing much of late
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518)


Thanks for the link there. So it's a Nouveau bug in the kernel. Bugger. Hope it gets fixed for the final release! It's been marked as High Importance, but I suppose that doesn't necessarily mean it will be sorted in time.

The Live CD works well for me as long as I delete splash from the boot options. If I put in nomodeset the Live session is really poor, with a terrible resolution and awful performance generally. When it runs well though, Quantal looks fantastic indeed. :)

---

### Post by mc4man on 2012-09-22
> **BigSilly said:**
> Thanks for the link there. So it's a Nouveau bug in the kernel. Bugger. 
That was just a guess by me based on some searching & what is observed here. Whether actually Ubuntu's issue I guess we MAY see..

As you've seen the nomodeset is only good for installing, anyone using that to try the live session pre install would be quite disappointed in most cases

---

### Post by randomizer101 on 2012-09-23
Possibly related to this bug as well: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041637)

Although this one affects both the live session and an installed environment. Oddly enough it's only marked with a Normal priority, but I'd think that a bug affecting so many users which is going to severely hamper the users' experience until they've installed binary blobs (which in my experience they won't be prompted to do because they appear to be using a generic VESA device) would be a little more important than that.

---

### Post by sacridex on 2012-09-24
> **dino99 said:**
> Actually all the packages (> 20000) are into the rebuilt queue, to take advantage of the new gcc that fix around 92 issues itself. So that huge task will need some time to end. But we surely get less trouble then.

OT: When will this happen? Will the packages be updated or reinstall required?

BTT: Having the same issue with 9600gt. ^^

---

### Post by cariboo on 2012-09-24
> **sacridex said:**
> OT: When will this happen? Will the packages be updated or reinstall required?

BTT: Having the same issue with 9600gt. ^^


There was an experimental rebuild this past weekend, and a call was put out to fix packages that wouldn't build, so I would expect we should start seeing the newly rebuilt packages within the next couple of days.

FYI, this email from Martthias Klose:

> This weekend a test rebuild of quantal quetzal did start for the amd64, i386 and
armhf architectures. The test rebuild is now finished for the main and
restricted components, and continues with the universe and multiverse components.

Results can be seen at
[http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20120922-quantal.html](http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20120922-quantal.html)

The archive for the test rebuild is
[https://launchpad.net/ubuntu/+archive/test-rebuild-20120922](https://launchpad.net/ubuntu/+archive/test-rebuild-20120922)

Please help fixing the build failures for the final release.

Note that an upload won't show up in the superseded sections, if it is uploaded
to quantal-proposed, but didn't propagate yet to quantal.

  Matthias


---

