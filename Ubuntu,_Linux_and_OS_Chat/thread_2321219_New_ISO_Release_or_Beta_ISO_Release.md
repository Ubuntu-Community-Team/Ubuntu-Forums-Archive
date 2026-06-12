---
title: "New ISO Release or Beta ISO Release"
date: 2016-04-21
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2016-04-21
Hey All,

Is there away to tell if an ISO download is the actual new release or a beta release.
I assume that a beta release would say beta somewhere is that correct.
Just want to be sure as this is my first time to download a brand new release and didn't want the beta release.

Here is the link I used for my Lubuntu ISO new release.

[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

Thanks.

---

### Post by slickymaster on 2016-04-21
> **poorguy said:**
> Hey All,

Is there away to tell if an ISO download is the actual new release or a beta release.
I assume that a beta release would say beta somewhere is that correct.
Just want to be sure as this is my first time to download a brand new release and didn't want the beta release.

Here is the link I used for my Lubuntu ISO new release.

[http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/)

Thanks.

That's the final release.

---

### Post by poorguy on 2016-04-21
Hey slickymaster,

That is what I needed to know as  this is my first new release phase since becoming a Linux user.

Thanks

---

### Post by Laui on 2016-04-21
When is the Release of Lubuntu 16.04?

---

### Post by slickymaster on 2016-04-21
Merged two similar threads

---

### Post by grahammechanical on 2016-04-21
It never says Alpha or Beta but Development branch in brackets. Run this command

```
lsb_release -a
```

if you get this

> graham@sdb7-Dev:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


You are on the release. Yesterday it was saying (development branch). Grub uses this file to get its OS labels. So, one day it will be show "development version." and then when the lsb_release file is updated it will show plain old Ubuntu 16.04 LTS.

Regards.

---

### Post by poorguy on 2016-04-21
Hey [COLOR=#000000]grahammechanical,

Thanks for that and I will check that out.

Thanks[/COLOR]

---

### Post by Eva_Bouwman on 2016-04-21
Beta release says beta, just have been installing Kubuntu Beta 16.04 on two devices. It is becoming very nice. Needs some tweaks but for sure do-able to install and work with it. I did for a week but always looking for more challenges, now mint Xfce :D

Wish you lot's of fun, with the possibilities we are offered :D

---

### Post by poorguy on 2016-04-21
Hey [COLOR=#000000]grahammechanical,[/COLOR]

[COLOR=#000000]Ran the terminal command you sent and it came back with the same as you posted so I have the final release if I am understanding what you posted.
I haven't installed it yet I have only ran it from DVD.

Thanks

[/COLOR]

---

### Post by poorguy on 2016-04-21
> **Laui said:**
> When is the Release of Lubuntu 16.04?

I was under the impression from what I read and saw that today was the final release date for them all but don't quote me on that.
I downloaded Ubuntu Mate and Lubuntu and both download sites had nothing posted as to it being a beta or developmental release.

---

### Post by poorguy on 2016-04-21
Ok so this is what I show in the terminal.

```
lubuntu@lubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
```

So this is a final release if I understand what I read from above.

---

### Post by slickymaster on 2016-04-21
> **poorguy said:**
> Ok so this is what I show in the terminal.

```
lubuntu@lubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
```

So this is a final release if I understand what I read from above.

Yes it is.

---

### Post by poorguy on 2016-04-21
> **slickymaster said:**
> Yes it is.

Then this also must be a final release to.

```
ubuntu-mate@ubuntu-mate:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
```


Hey slickymaster,

I know I'm a problem but this is my 1st time at this final release thing so now I know what to expect.

I really do appreciate all of the help from everyone.

Thanks and very much appreciate everyone"s help.

The poorguy

---

### Post by slickymaster on 2016-04-21
> **poorguy said:**
> Then this also must be a final release to.

```
ubuntu-mate@ubuntu-mate:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
```


Hey slickymaster,

I know I'm a problem but this is my 1st time at this final release thing so now I know what to expect.

I really do appreciate all of the help from everyone.

Thanks and very much appreciate everyone"s help.

The poorguy

Exactly.

---

### Post by ipselute on 2016-06-15
You can check ISO release date against the official release calendar for xenial: [https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule](https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule). This is best way to locate an ISO date in an Ubuntu time interval (and see what stage it belongs to).

---

