---
title: "update blew out Nvidia-Current - thrown back to 2D"
date: 2012-06-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-06-28
The newest nvidia graphics drivers (302.17) is now available from the official Quantal repos.

Here:
[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/302.17-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/302.17-0ubuntu1)

No do not try to install this one. It will break your graphics.
This is because it has been built against the old xserver 1.11 ABI (xorg-video-abi11).

It should have been built against the newest xserver 1.12 ABI (xorg-video-abi-12).

---

### Post by dino99 on 2012-06-28
yes DO NOT INSTALL

and it wants to install a bunch of unneeded xserver-xorg-video-xxxx

---

### Post by philinux on 2012-06-28
It just landed.

apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 302.17-0ubuntu1
  Version table:
     302.17-0ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages

---

### Post by philinux on 2012-06-28
> **Harry33 said:**
> The newest nvidia graphics drivers (302.17) is now available from the official Quantal repos.

Here:
[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/302.17-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/302.17-0ubuntu1)

No do not try to install this one. It will break your graphics.
This is because it has been built against the old xserver 1.11 ABI (xorg-video-abi11).

It should have been built against the newest xserver 1.12 ABI (xorg-video-abi-12).

Indeed 
```
/# apt-cache policy xorg-video-abi-12
N: Unable to locate package xorg-video-abi-12

```

However it only wants to install itself nothing extra.

```
Calculating upgrade... Done
The following packages have been kept back:
  oss-compat
The following packages will be upgraded:
  nvidia-current
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 58.7 MB of archives.
After this operation, 1,229 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


```

---

### Post by ventrical on 2012-06-29
Which one do I choose to restore my nvidia driver?

---

### Post by lucazade on 2012-06-29
is this screnshot a fake? :confused:
never seen so much different drivers in that dialog!

---

### Post by ventrical on 2012-06-29
It's the real deal .. at least according to what jockey is reporting.

---

### Post by lucazade on 2012-06-29
oh good gosh... jockey is becoming worse every release.

---

### Post by terry_gardener on 2012-06-29
> **ventrical said:**
> Which one do I choose to restore my nvidia driver?

open the terminal and install the nvidia-current package. 

you might need to use the nvidia-xconfig command to reconfigure xorg 

the way i fixed my last nvidia problem is to purge nvidia current and then reinstall nvidia-current and ran nvidia-xconfig to get it working again. 

i don't tend to use jockey in dev releases

---

### Post by terry_gardener on 2012-06-29
also my jockey screen has also got a very long list of drivers

---

### Post by 3vi1 on 2012-06-29
Ran into the same problem.  Due to the new xorg, it doesn't look like everything needed to fix it (particularly, a new nvidia-current compiled against the new ABI) is in the repos at the moment:  :\

```
evil@saturn:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11 but it is not installable
                  Recommends: nvidia-settings (>= 302.17) but 295.33-0ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by 3vi1 on 2012-06-29
Learned this one the hard way.  :)  But, glad it's not specific to me.  Rolling back....

---

### Post by jbicha on 2012-06-29
The very long list of jockey drivers is temporary as jockey is being refactored; it won't look like that when Ubuntu 12.10 is final.

---

### Post by ventrical on 2012-06-29
> **3vi1 said:**
> Ran into the same problem.  Due to the new xorg, it doesn't look like everything needed to fix it (particularly, a new nvidia-current compiled against the new ABI) is in the repos at the moment:  :\

```
evil@saturn:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11 but it is not installable
                  Recommends: nvidia-settings (>= 302.17) but 295.33-0ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

```


Thanks 3vi1. Thats exactly it ! :)


Guess we will have to wait it out then ?

---

### Post by ventrical on 2012-06-29
> **jbicha said:**
> The very long list of jockey drivers is temporary as jockey is being refactored; it won't look like that when Ubuntu 12.10 is final.

Thank you Jeremy for that clarification.

---

### Post by sammiev on 2012-06-29
I like it as you can test different drivers installed. Hate to see it go myself.

---

### Post by ventrical on 2012-06-30
I just do not get it , that the nvidia driver works on the other installs on the same machine but this one is coming up with the xorg error.

---

### Post by Cheltspy on 2012-06-30
If you still have your old nvidia driver in your apt cache, this is how I restored the old driver on 3.5.0-2.

check these still apply
sudo apt-get remove xserver-xorg-video-nouveau
sudo apt-get install dkms


sudo dpkg -i --force-depends '/var/cache/apt/archives/nvidia-current_295.53-0ubuntu2_i386.deb'
sudo update-grub

---

### Post by Thomas1477 on 2012-06-30
> **Cheltspy said:**
> If you still have your old nvidia driver in your apt cache, this is how I restored the old driver on 3.5.0-2.

check these still apply
sudo apt-get remove xserver-xorg-video-nouveau
sudo apt-get install dkms


sudo dpkg -i --force-depends '/var/cache/apt/archives/nvidia-current_295.53-0ubuntu2_i386.deb'
sudo update-grub

Thank you, this worked for me.:p

---

### Post by ventrical on 2012-06-30
Where can I download this:


nvidia-current_295.53-0ubuntu2_i386.deb

 I recall on this 'install' I experimented with:


NVIDIA-Linux-x86-295.20.run  durng Precise testing.

and so perhaps that is why  this install is slightly borked.

---

### Post by mc4man on 2012-06-30
> **ventrical said:**
> Where can I download this:


nvidia-current_295.53-0ubuntu2_i386.deb

 I recall on this 'install' I experimented with:


NVIDIA-Linux-x86-295.20.run  durng Precise testing.

and so perhaps that is why  this install is slightly borked.

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.53-0ubuntu2/+build/3596776](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.53-0ubuntu2/+build/3596776)

---

### Post by ventrical on 2012-06-30
@mc4man and Cheltspy,

Thanks a million! :)

That saved me a lot of time  and data. This particular install started with Oneric Alpha1 and now it has upgraded to quantal alpha2. I have to give kudos to the ubuntu Braintrust, the devs, for making these rolling release processes so exceptionally streamlined.

---

### Post by tokyobadger on 2012-07-02
```
sudo apt-get remove xserver-xorg-video-nouveau
sudo apt-get install dkms


sudo dpkg -i --force-depends '~/Downloads/nvidia-current_302.17-0ubuntu1_amd64.deb'
sudo update-grub
```
worked but now gives me this
```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11 but it is not installable
E: Unmet dependencies. Try using -f.
```
and if I follow that I get
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  nvidia-current
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
After this operation, 182 MB disk space will be freed.
Do you want to continue [Y/n]?
```
anyone crack this?
BTW the 302.17 drivers are noticeably better than the 29x.xx for me

---

### Post by dino99 on 2012-07-02
you should have read: [http://ubuntuforums.org/showthread.php?t=2012098](http://ubuntuforums.org/showthread.php?t=2012098)

---

### Post by tokyobadger on 2012-07-02
> **dino99 said:**
> you should have read: [http://ubuntuforums.org/showthread.php?t=2012098](http://ubuntuforums.org/showthread.php?t=2012098)
Yep I probably should have - doesn't detract from the fact that display looks way nicer with 302.17 - guess I'll downgrade until the package is built against the correct abi

---

### Post by mc4man on 2012-07-02
> **tokyobadger said:**
> Yep I probably should have - doesn't detract from the fact that display looks way nicer with 302.17 - guess I'll downgrade until the package is built against the correct abi
It looks here that it's was compiled for 1.12 (xorg.log - "compiled for 1.12.1.902, module version = 1.0.0") just packaged wrong

So a quick test here - 
downloaded the ..deb > extracted to file, deleted the .deb package
Opened Debian/control, edited to xorg-video-abi-12, saved, deleted the backed up control file (~control

Then repackaged & installed, works fine - screens
Ex. command(s)
dpkg -b  /home/doug/Downloads/nvidia-current_302.17-0ubuntu1_i386

dpkg -b  /home/doug/Downloads/nvidia-current_302.17-0ubuntu1_amd64

---

### Post by wildmanne39 on 2012-07-02
Threads merged be request.

---

### Post by mc4man on 2012-07-02
Is being rebuilt now for abi-12

---

### Post by paul_in_london on 2012-07-02
> **mc4man said:**
> Is being rebuilt now for abi-12

It's upgradeable now (although I'm using xorg-edgers anyway so it's basically the same thing):

```
paul@quantal-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 302.17-0ubuntu2
  Candidate: 302.17-0ubuntu2
  Version table:
 *** 302.17-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status
     302.17-0ubuntu1~xedgers~quantal1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main amd64 
```

---

### Post by VinDSL on 2012-07-02
> **paul_in_london said:**
> It's upgradeable now (although I'm using xorg-edgers anyway so it's basically the same thing)[...]
I just upgraded the edgers nvidia-current to 302.17-0ubuntu2 but was rather nervous about it, due to the recent abi-11 snafu.

Before rebooting (didn't want to have a nasty surprise in the morning, before work), I would swear that nvidia-current was missing from the edgers repo.

Let me check again...

Yep, it's AWOL.  Must be the same.  ;)

```
vindsl@Zuul:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 302.17-0ubuntu2
  Candidate: 302.17-0ubuntu2
  Version table:
 *** 302.17-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/restricted i386 Packages
        100 /var/lib/dpkg/status
     302.17-0ubuntu1~xedgers~quantal1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main i386 Packages

```

---

### Post by balloons on 2012-07-03
Yep, installed, rebooted, stable for now. I was on nouveau but noticed a nasty workspace switching bug this morning. Nice to be able to jump ship over to the blob for a bit and see how it's going.

---

### Post by ventrical on 2012-07-03
> **guitara said:**
> Yep, installed, rebooted, stable for now. I was on nouveau but noticed a nasty workspace switching bug this morning. Nice to be able to jump ship over to the blob for a bit and see how it's going.


Honestly , guitara, it healed itself right before my eyes.! I have never seen workspace switcher work so .... err.. ummm punchy !:)

---

### Post by balloons on 2012-07-03
> **ventrical said:**
> Honestly , guitara, it healed itself right before my eyes.! I have never seen workspace switcher work so .... err.. ummm punchy !:)

LOL -- ventrical same experience! I was so excited it was snappy, I tried VT switching. Heh, still broken (SLOW!) :-) But for that moment, I was on cloud nine.

---

### Post by ventrical on 2012-07-03
> **guitara said:**
> LOL -- ventrical same experience! I was so excited it was snappy, I tried VT switching. Heh, still broken (SLOW!) :-) But for that moment, I was on cloud nine.


Well as Mark said once in one of his interviews, 'we'll rock your world' or something like that. lol

So far, it's still working in tip top shape, as it should be.

---

