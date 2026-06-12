---
title: "Best Daemon Tool for Ubuntu [Jaunty]"
date: 2009-06-09
forum: The Cafe
---

### Post by Gias Kay on 2009-06-09
Hi,

Just wondering if I can get some names of the best daemon tools for Jaunty in here. So far I've heard of AcetoneISO 2, but I searched it and found some old posts claiming it's not working great under Gnome. So any ideas or suggestions?

---

### Post by LowSky on 2009-06-09
gmount-iso is in the repos, works great

[http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2](http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2)

---

### Post by bulletxt on 2009-06-09
AcetoneISO works perfectly and has a lot of features.

This is the official website where you can get the latest release for Ubuntu:

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)

---

### Post by cariboo on 2009-06-09
```
mount -o loop <any>.iso /mnt
```

):P

---

### Post by Gias Kay on 2009-06-10
Tried gmount-iso and worked great. AcetoneISO looks kinda like a bloatware, they advertize their program being able to "download videos from Pornotube!" What the heck would that have anything to do with a daemon tool?

---

### Post by swoll1980 on 2009-06-10
> **bulletxt said:**
> AcetoneISO works perfectly and has a lot of features.

This is the official website where you can get the latest release for Ubuntu:

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)

+1 for AcetoneISO

---

### Post by swoll1980 on 2009-06-10
> **Gias Kay said:**
>  they advertize their program being able to "download videos from Pornotube!" 

Where do you see that at?

---

### Post by LookTJ on 2009-06-10
> **Gias Kay said:**
> they advertize their program being able to "download videos from Pornotube!"They removed that feature according to the changelog.

---

### Post by binbash on 2009-06-11
you do not need any except mount command

---

### Post by Mistrblank on 2009-06-11
> **cariboo907 said:**
> ```
mount -o loop <any>.iso /mnt
```

):P

+1 vote for this.

---

### Post by praveesh on 2009-07-26
Will these apps emulate an ISO image as a real cd drive (or they just mount the iso image)? . Daemon tools emulate a real cd drive.

---

### Post by AndyCee on 2009-07-26
My vote goes for

sudo mount -o loop <isoname> /mnt

---

### Post by praveesh on 2009-07-26
> **AndyCee said:**
> My vote goes for

sudo mount -o loop <isoname> /mnt

That will mount the iso . But the system will not treat it is a real cdrom. I have a number of iso images of Ubuntu in hard drive. But if I want to install softwares from them, using synaptic, I can't . I need to install real cd. That's the problem.

---

### Post by dicairo on 2009-07-26
> **bulletxt said:**
> AcetoneISO works perfectly and has a lot of features.

This is the official website where you can get the latest release for Ubuntu:

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)

i am totally agree with this AcetoneISO work nice for me:)

---

### Post by praveesh on 2009-07-26
> **dicairo said:**
> i am totally agree with this AcetoneISO work nice for me:)

Does the system treat the iso image mounted using acetoneiso as a real cd rom? If not, there is no need of it. Just right click and click on archive mounter. Done

---

### Post by Viva on 2009-07-26
> **praveesh said:**
> Does the system treat the iso image mounted using acetoneiso as a real cd rom? If not, there is no need of it. Just right click and click on archive mounter. Done

My system recognises it as a cd if I mount it as cdrom0

---

### Post by praveesh on 2009-07-26
> **Viva said:**
> My system recognises it as a cd if I mount it as cdrom0

what tool did you use?

---

### Post by FuturePilot on 2009-07-26
> **praveesh said:**
> what tool did you use?

Just use the same command above but change the mount point.

```
sudo mount -o loop <isoname> /media/cdrom0
```

It will even show up on your desktop as if you had put in an actual CD.

---

### Post by praveesh on 2009-07-26
> **FuturePilot said:**
> Just use the same command above but change the mount point.

```
sudo mount -o loop <isoname> /media/cdrom0
```

It will even show up on your desktop as if you had put in an actual CD.

Yes. The system recognized it as a real cdrom. But, in synaptic, when I tried to add cd rom, after showing, "mounting cdrom :"  it replied "E: Failed to mount the cdrom" . What can be the reason?

---

### Post by AndyCee on 2009-07-29
I actually remember something like that happening when I tried a distro upgrade without burning a CD. Is this what you're trying to do?

---

### Post by praveesh on 2009-08-21
Cdemu does the job very will (it's in the ppa. Go to launchpad.net and search for cdemu. ). It really emulates a real physical cd drive. Iam able to mount an Ubuntu iso image and the synaptic recognises it as a real cd and Iam able to install apps from the iso image. No other softwares or scripts or commands are able to do this. Others might be able to mount the cd (and may be in the /cdrom itself) but the synaptic doesn't recognise it as a real cd rom. More over, there is an applet for the Gnome panel which helps in mounting cds(much similar to the daemon tools). It is the perfect replacement of the daemon tools.

---

### Post by praveesh on 2009-08-21
With cdemu, it is possible to upgrade distro without the need of burning a cd

---

