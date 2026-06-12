---
title: "NVidia 295.33 is out"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xebian on 2012-03-23
You can get it here

[http://www.nvnews.net/vbulletin/showthread.php?p=2538961](http://www.nvnews.net/vbulletin/showthread.php?p=2538961)

---

### Post by dino99 on 2012-03-23
> **xebian said:**
> You can get it here

[http://www.nvnews.net/vbulletin/showthread.php?p=2538961](http://www.nvnews.net/vbulletin/showthread.php?p=2538961)

not only, xorg-edgers ppa already have it. And it works natively with kernel 3.3 but require xserver 1.12 also.

---

### Post by xebian on 2012-03-23
> **dino99 said:**
> not only, xorg-edgers ppa already have it. And it works natively with kernel 3.3 but require xserver 1.12 also.

Mine works fine with older version and 3.3.0 

```
ii  xorg                                              1:7.6+12ubuntu1                            X.Org X Window System
ii  xorg-docs-core                                    1:1.6-1ubuntu2                             Core documentation for the X.org X Window System
ii  xserver-xorg                                      1:7.6+12ubuntu1                            X.Org X server
ii  xserver-xorg-core                                 2:1.11.4-0ubuntu7                          Xorg X server - core server

```

---

### Post by VinDSL on 2012-03-26
Gotta say...

295.33 is working GREAT on this Linux 3.3 machine!  It's the icing on the cake.

I don't know what they did, but this machine is much more responsive now -- a pleasure to use (again).  ;)

---

### Post by VinDSL on 2012-03-26
> **dino99 said:**
> xorg-edgers ppa already have it. And it works natively with kernel 3.3 but require xserver 1.12 also.
I used the x-swat PPA.

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```

Doesn't require xserver 1.12 ;)

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-mar-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-mar-2012-1.png")[/INDENT]

---

### Post by zombifier25 on 2012-03-26
Just one curious question... can I revert to the open source, built-in nVidia driver if this one doesn't work? (since I regularly play games on Wine and the open source driver works fine, while the NVidia driver will give an "out of range" error on some games like Bejeweled 3. However, the open source one refuses to play with Plymouth, while the proprietary will display a nice boot screen)

---

### Post by dino99 on 2012-03-26
vanilla is a second choice as ubuntu devs tweaks the driver for better settings

---

### Post by emptythevoid on 2012-03-26
I updated to 295.33 a few days ago, and since then, my rock-solid 10.04 setup kicked me to the login screen twice.  No warning, no nothing.  I've tried looking through the logs to find something that might indicate what happened, and I haven't seen anything yet.  The new driver is the only major change.  I'm going to keep an eye on it to see if it happens again, but I would like to know how to roll back to a slightly older version (I updated to 295.33 from the x-swat ppa), but it will not let me "force version" on the nvidia-current package.  Any suggestions, or has anyone else had this issue?

---

### Post by emptythevoid on 2012-04-02
Well, I'm going to answer my own question.  Apparently the Xswat PPA does not keep older versions of the Nvidia driver, so I cannot roll back to previous versions using the "force version" option (except for the default version that comes with 10.04).  I *was* able to enable this repository and install the 280.13 driver.  So far so good.
[http://www.ubuntuupdates.org/ppa/nvidia-vdpau?dist=lucid](http://www.ubuntuupdates.org/ppa/nvidia-vdpau?dist=lucid)

---

### Post by jasonsmith01 on 2012-04-02
> **VinDSL said:**
> 

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-mar-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-mar-2012-1.png")[/INDENT]

VinDSL I'm desperately trying to setup conky like you have done. Would you mind if I pm you or start another thread? Ps sorry for the off topic post

Edit: Going to try this out.  [http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)

---

### Post by VinDSL on 2012-04-02
> **jasonsmith01 said:**
> VinDSL I'm desperately trying to setup conky like you have done. Would you mind if I pm you or start another thread? Ps sorry for the off topic post

Edit: Going to try this out.  [http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)
There's a link in my sig, to a great tutorial, which explains my Conky code.  

Also, it's probably the best tutorial on the web, explaining how Conky works, in general.

You might give that a try (if you haven't already)...

Also, there is no limit to the amount of help available in [The Big Conky Thread](The Big Conky Thread), so called. ;)

---

### Post by jasonsmith01 on 2012-04-02
> **VinDSL said:**
> There's a link in my sig, to a great tutorial, which explains my Conky code.  

Also, it's probably the best tutorial on the web, explaining how Conky works, in general.

You might give that a try (if you haven't already)...

Also, there is no limit to the amount of help available in [The Big Conky Thread](The Big Conky Thread), so called. ;)

Awesome, thank you very much.

---

