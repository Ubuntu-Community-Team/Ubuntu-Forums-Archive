---
title: "unattended upgrades nonsense"
date: 2017-05-08
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-05-08
It appears that the default is to daily check & upgrade in the background. The issue here is that there is no indication that upgrades are taking place & the system will allow a restart during such activity. This can lead to an inconsistent state or even loss of ability to reboot successfully (that just happened here.
I think it's highly advised to disable this during dev..

---

### Post by wildmanne39 on 2017-05-08
> **mc4man said:**
> It appears that the default is to daily check & upgrade in the background. The issue here is that there is no indication that upgrades are taking place & the system will allow a restart during such activity. This can lead to an inconsistent state or even loss of ability to reboot successfully (that just happened here.
I think it's highly advised to disable this during dev..

+1 These upgrades caused me the same kind of trouble on Saturday.

---

### Post by mc4man on 2017-05-08
During dev you'd certainly want to be involved/aware of all updates/upgrades rather than silently. Here I also prefer to do so thru synaptic to keep an organized & straightforward history rather than overwrought logs in /var. 

So am setting top option to never but because there's no guarantee that's as intended am also  removing the unattended-upgrades package altogether.

---

### Post by VMC on 2017-05-08
> **mc4man said:**
> It appears that the default is to daily check & upgrade in the background. The issue here is that there is no indication that upgrades are taking place & the system will allow a restart during such activity. This can lead to an inconsistent state or even loss of ability to reboot successfully (that just happened here.
I think it's highly advised to disable this during dev..

Yea, I just got a unattended upgrade crash. I tried reporting, but didn't work.

---

### Post by ventrical on 2017-05-08
same here..

It also affects boot time with systemd with apt-update-service.

Setting to 'never' fixes for now.

---

### Post by jbicha on 2017-05-09
Yes, I mentioned this bug months ago. Maybe it should be a sticky post or mentioned in a sticky post?

[https://ubuntuforums.org/showthread.php?t=2346439](https://ubuntuforums.org/showthread.php?t=2346439)

---

### Post by wildmanne39 on 2017-05-09
I am not an expert at this but I went into the file and added # to the beginning of:

```
#//	"${distro_id}:${distro_codename}-updates";
#/	"${distro_id}:${distro_codename}-proposed";
#//	"${distro_id}:${distro_codename}-backports";
```
is that sufficient to stop the upgrade like I think without causing issues?
Thanks

---

### Post by harry332 on 2017-05-09
The prolonged booting time with apt-update-service does not go away even if the package unattended-upgrades is removed.
The network-on checking during boot is done (even without unattended-upgrades) because of the new changes in the apt packages (from version 1.4.1ubuntu2 to version 1.4.2).
You get the short boot time back only by downgrading apt packages back to the version 1.4.
There is a bug report about this new setup:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1686470](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1686470)

---

### Post by ian-weisser on 2017-05-09
That bug report has a lot of good discussion already! And even an upload.
Looks like this will be FIX RELEASED in 17.10 soon.

---

### Post by ventrical on 2017-05-09
> **harry332 said:**
> The prolonged booting time with apt-update-service does not go away even if the package unattended-upgrades is removed.
The network-on checking during boot is done (even without unattended-upgrades) because of the new changes in the apt packages (from version 1.4.1ubuntu2 to version 1.4.2).
You get the short boot time back only by downgrading apt packages back to the version 1.4.
There is a bug report about this new setup:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1686470](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1686470)

@harry323,

Good eye harry!  I sort of thought that was the case. Thanks for making it clear. It is sort of like hijacking the PC during boot-time.  I think we can do without it in dev.

---

### Post by ventrical on 2017-05-09
> **jbicha said:**
> Yes, I mentioned this bug months ago. Maybe it should be a sticky post or mentioned in a sticky post?

[https://ubuntuforums.org/showthread.php?t=2346439](https://ubuntuforums.org/showthread.php?t=2346439)

Yes I put that here:

[https://ubuntuforums.org/showthread.php?t=1970289&page=11&p=13643375#post13643375](https://ubuntuforums.org/showthread.php?t=1970289&page=11&p=13643375#post13643375)

---

