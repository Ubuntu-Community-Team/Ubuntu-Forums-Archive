---
title: "nvidia-current ripped with recent 3.5.0-7 updates"
date: 2012-08-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-08-02
Just upgraded one install, ripped out nvidia-current and now cannot re-install it:

```

dale@dale:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-12
E: Unable to correct problems, you have held broken packages.
dale@dale:~$ 

```

---

### Post by ventrical on 2012-08-02
I now have Commadore 64 screen ! :) lol

---

### Post by ventrical on 2012-08-02
This fix will not work - even on rollback of kernels.

[http://ubuntuforums.org/showpost.php?p=12065592&postcount=19](http://ubuntuforums.org/showpost.php?p=12065592&postcount=19)

---

### Post by Harry33 on 2012-08-03
Yes, your screen looks awesome!
Happy with Unity?

Now to the issue with nvidia-current.

This error here:
The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-12

It means you have not installed any package that would provide the virtual package xorg-video-abi-12.
However, that is provided by the correct (for xserver 1.12) xserver-xorg-core and all correct video drivers (like xserver-xorg-video-vesa).
Check which version of xserver you have, is it 1.12 or the new 1.13?

Perhaps it is easier to first disable the proposed repo, so the new xserver 1.13 will not get accidentally installed.

---

### Post by ventrical on 2012-08-03
> **Harry33 said:**
> Yes, your screen looks awesome!
Happy with Unity?

Now to the issue with nvidia-current.

This error here:
The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-12

It means you have not installed any package that would provide the virtual package xorg-video-abi-12.
However, that is provided by the correct (for xserver 1.12) xserver-xorg-core and all correct video drivers (like xserver-xorg-video-vesa).
Check which version of xserver you have, is it 1.12 or the new 1.13?

Perhaps it is easier to first disable the proposed repo, so the new xserver 1.13 will not get accidentally installed.

I have the 1.12

---

### Post by dino99 on 2012-08-03
no problem here with xserver-xorg 1.12.1.902 & nvidia-current (quantal-proposed off)

---

### Post by ventrical on 2012-08-03
> **dino99 said:**
> no problem here with xserver-xorg 1.12.1.902 & nvidia-current (quantal-proposed off)

  I have the xserver-xorg-core 2:1.12.99.902...

Is there a difference?

---

### Post by ventrical on 2012-08-03
Anyway to resolve this ?

thanks

---

### Post by Harry33 on 2012-08-03
> **ventrical said:**
> I have the xserver-xorg-core 2:1.12.99.902...

Is there a difference?

There is a difference indeed.
You are running xserver 1.13 rc2 there (=1.12.99.902).
So downgrade to the 1.12.1.902 (aka xserver 1.12.2 rc2). :guitar:

---

### Post by ventrical on 2012-08-03
> **Harry33 said:**
> There is a difference indeed.
You are running xserver 1.13 rc2 there (=1.12.99.902).
So downgrade to the 1.12.1.902 (aka xserver 1.12.2 rc2). :guitar:

 Thanks Harry33. A nice fix indeed. Works even more snappier now.

Just s side note to anyone else that may run into this problem. After downgrading , don't forget to:

sudo apt-get install ubuntu-desktop 

from terminal because this process will  ripp a lot of other modules that actually run the desktop.

  I will write a comment later on this in regards to newer people comming on board to Ubuntu and how we can teach them  and convince them that Ubuntu is more user friendly than other commercial software packages. :) lol

---

### Post by eliasv on 2012-08-05
Hey everyone. I have also had this problem, with the exact same versions of packages involved.

When I force the downgrade of the packages xserver-xorg-core & xserver-common (these seem to be the only packages with the relevant versions, is that correct?) lots of other important packages are removed, as described.

The problem is that if I now try to install ubuntu-desktop it just fails in synaptic with unmet dependencies:

"ubuntu-desktop:
 Depends: xorg but it is not going to be installed"

...and if I try from the terminal it just updates xserver-xorg-core & xserver-common again.

Am I doing something wrong here? I am okay with waiting, I'll just have to put up with using a lower resolution on my external monitor until I can install the nvidia packages again. :(

In fact, I'd be fine with not using the nvidia drivers at all, but I can't figure out how to force nouveau to use custom EDID, doesn't seem to work for some reason... That is a separate issue, though! :)

Cheers,

Eli

---

### Post by Harry33 on 2012-08-05
> **eliasv said:**
> Hey everyone. I have also had this problem, with the exact same versions of packages involved.

When I force the downgrade of the packages xserver-xorg-core & xserver-common (these seem to be the only packages with the relevant versions, is that correct?) lots of other important packages are removed, as described.

The problem is that if I now try to install ubuntu-desktop it just fails in synaptic with unmet dependencies:

"ubuntu-desktop:
 Depends: xorg but it is not going to be installed"

...and if I try from the terminal it just updates xserver-xorg-core & xserver-common again.

Am I doing something wrong here? I am okay with waiting, I'll just have to put up with using a lower resolution on my external monitor until I can install the nvidia packages again. :(

In fact, I'd be fine with not using the nvidia drivers at all, but I can't figure out how to force nouveau to use custom EDID, doesn't seem to work for some reason... That is a separate issue, though! :)

Cheers,

Eli

If you downgrade xserver-xorg-core and xserver-common, you also need to downgrade all video and input drivers you have installed in order to match the correct ABI of the xserver.

This is the general rule. Note, that I do not know your exact problem because you did not mention what is your xserver version before the downrade process and how did it function + where did you install it from in the first place.

---

### Post by eliasv on 2012-08-05
Hi, thanks for the quick response :).

I didn't post the version numbers because, as I meant to convey (sorry for not being clear), they were the same as the version Ventrical had installed, and then downgraded to, i.e.:

1.12.99.902 => 1.12.1.902

The packages were installed (and the nvidia packages uninstalled) by an update a few days ago, again, as it was for Ventrical.

I downgraded the packages from within synaptic, as Harry33 and Ventrical described, but this also removed:

* 'ubuntu-desktop'
* 'xorg'
* 'xserver-xorg'
* all the 'xserver-xorg-input' packages, and all the 'xserver-xorg-video' packages.

It seems I am unable to downgrade these, and they just get removed. If I try to reinstall any of these packages I get either dependency errors, or it will just upgrade 'xserver-xorg-core' and 'xserver-common' again.

Unfortunately nvidia-current-updates can't install with the new version, but it seems that I can't figure out how to get the downgrade to work without it removing loads of packages.

Do you think I should just wait for the dependency issues to be resolved for nvidia-current-updates?

---

### Post by Harry33 on 2012-08-05
> **eliasv said:**
> Hi, thanks for the quick response :).

I didn't post the version numbers because, as I meant to convey (sorry for not being clear), they were the same as the version Ventrical had installed, and then downgraded to, i.e.:

1.12.99.902 => 1.12.1.902

The packages were installed (and the nvidia packages uninstalled) by an update a few days ago, again, as it was for Ventrical.

I downgraded the packages from within synaptic, as Harry33 and Ventrical described, but this also removed:

* 'ubuntu-desktop'
* 'xorg'
* 'xserver-xorg'
* all the 'xserver-xorg-input' packages, and all the 'xserver-xorg-video' packages.

It seems I am unable to downgrade these, and they just get removed. If I try to reinstall any of these packages I get either dependency errors, or it will just upgrade 'xserver-xorg-core' and 'xserver-common' again.

Unfortunately nvidia-current-updates can't install with the new version, but it seems that I can't figure out how to get the downgrade to work without it removing loads of packages.

Do you think I should just wait for the dependency issues to be resolved for nvidia-current-updates?

The packages you mentioned are meta packages. No need to downgrade them.
They do not contain actually contain anything important.
They only depend on other packages that are considered packages Ubuntu should have. Fir example, if you use nvidia-current, you only need one more video driver (xserver-xorg-video-vesa). Instead, the meta package xserver-xorg installs all input and video drivers on your system.

Please, disable the proposed repository (QQ) and xorg-edgers PPA first.
Then, install nvidia-current with synaptic. Also see that all xserver packages and input and video drivers are QQ versions and not consider local or obsolete (by synaptic).

---

### Post by eliasv on 2012-08-06
Thanks for the clarification :). I'll try what you said and see if it works.

If I don't post any other messages, please anyone reading the thread assume that it worked with no problems ;).

Cheers,

Eli

---

### Post by ventrical on 2012-08-06
Yes .. the trick in all this was disabling the "proposed' repositiory.

I also had to:

sudo apt-get install nvidia-current
sudo apt-get install ubuntu-desktop
sudo update-grub

---

### Post by ventrical on 2012-08-06
I guess the next logical question would be .. what then , if any, is the significance of the 'proposed' repository?

---

### Post by mc4man on 2012-08-06
> **ventrical said:**
> I guess the next logical question would be .. what then , if any, is the significance of the 'proposed' repository?
Can't say I can put significance to proposed but useful it is. Packages can go there awaiting other ones or go there for some user testing.
(in releases proposed packages afford an opportunity to pass or fail verification of bug(s) the package(s) are to fix.

So here on this particular nvidia laptop I'm fully updated, though atm the only thing from proposed installed is some xserver packages 

*for this hardware & use case nouveau is better performing in a ubuntu session than nvidia drivers, in GS could go either way

---

### Post by ventrical on 2012-08-06
Thanks for the clarification.

reagards, ventrical

---

### Post by cariboo on 2012-08-06
> **mc4man said:**
> Can't say I can put significance to proposed but useful it is. Packages can go there awaiting other ones or go there for some user testing.
(in releases proposed packages afford an opportunity to pass or fail verification of bug(s) the package(s) are to fix.

So here on this particular nvidia laptop I'm fully updated, though atm the only thing from proposed installed is some xserver packages 

*for this hardware & use case nouveau is better performing in a ubuntu session than nvidia drivers, in GS could go either way

My experience is exactly the opposite, I noticed a distinct drop in performance going from the current Nvidia driver to nouveau, and the maximum resolution I get is only 1620X1020, I normally run at 1920X1080.

---

### Post by mc4man on 2012-08-07
> **cariboo907 said:**
> My experience is exactly the opposite, I noticed a distinct drop in performance going from the current Nvidia driver to nouveau, and the maximum resolution I get is only 1620X1020, I normally run at 1920X1080.
As usual it's always about the hardware. Atm only have a 13" laptop *Dell 1300m/nvidia 8400m. So 12.10 is the 1st. time nouveau beats out nvidia on that laptop in unity/compiz
(for some reason at some point during a session with nvidia there is always some break in compiz performance & the upclock reaction time in adaptive mode has suffered since 11.10/compiz 0.9.x & 2.XX.+ drivers

The 8400m supports vsync in nouveau so overall there is no tearing, either on the Desktop or in video's ect. (& on a 13" no real use for vdpau which that chip barely supported anyway.

On the other hand on my desktop which  I gave to  my son I'd only use nvidia.. or if I had a newer laptop would likely also use nvidia.

I thought this was an interesting take on, whether all that relevant
 to down the road Ubuntu wise don't know.
[http://smspillaz.wordpress.com/2012/06/08/on-the-future-of-graphics-drivers/](http://smspillaz.wordpress.com/2012/06/08/on-the-future-of-graphics-drivers/)

---

