---
title: "How to install virtualbox-4.3 (amd64.deb) in 14.04 x64"
date: 2014-10-06
forum: Virtualisation
---

### Post by ricardo072 on 2014-10-06
Hi All,

I'm using ubuntu 14.04 x64 and I want to install virtual box (the x64 version) and I just got the package "**virtualbox-4.3_4.3.16-95972~Ubuntu~raring_amd64.deb**" from the webSite:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

so I'm not sure how to do it and I do not want to mess my PC, could you please tell me what is the best way to install it properly ? Do I need to install something else first ? it will be the very first time I install this.

Thank you,
Best Regards.

---

### Post by mastablasta on 2014-10-07
have a look here: [https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation)

or here: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
(under debian based)
so assuming you have 14.04 you can copy this into terminal: 
```
deb http://download.virtualbox.org/virtualbox/debian trusty contrib
```

```
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
```

```
sudo apt-get update
```
```
sudo apt-get install virtualbox-4.3
```

and if it's not yet installed:
```
sudo apt-get install dkms
```

You can also do all this in GUI if you prefer. open software center, go to software sources and add the above source, then add the key, then go back to main software center screen, click on update and virtualbox will appear in programs that can be installed. click on it and click install.

then find dkms and install that as well (though I think it might already be installed)

---

### Post by TheFu on 2014-10-07
In most Linux distros, it is a bad idea to install packages directly. This can lead to "APT hell" - and can make your system become unpatchable.

Best to use the repo provide version, if possible.

If you need a newer version for some reason, then find a reputable PPA and use that as mastablasta explains.  It normally isn't so many commands to add a PPA under ubuntu - usually is is just the **add-apt-repository** command, assuming the provider setup their repo properly.  Lots of examples for that on the internet.

---

### Post by SeijiSensei on 2014-10-07
For reasons I've never understood, Oracle doesn't seem to offer a way to use add-apt-repository.  You have to follow the procedure mastablasta outlined of downloading and installing the key manually, then adding an entry to sources.list for the repository.

I use a slightly different method.  Rather than modifying /etc/apt/sources.list, I created a file called oracle-virtualbox-trusty.list in the /etc/apt/sources.list.d/ directory with the line:
```
deb http://download.virtualbox.org/virtualbox/debian trusty contrib
```
that mastablasta uses above.  Files in the sources.list.d directory are appended to sources.list when "apt-get update" is run.  When you add repositories with add-apt-repository, it also places files in this directory.

The VirtualBox packages on Oracle's site include dkms as a dependency; you shouldn't need to add it separately.

---

### Post by ricardo072 on 2014-10-08
Hi, 

Thank you All, -- mastablasta, Thefu, SeijiSensei -- for your feedback and kindness, reading [https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation) I see the following:

-- A 64 bit host CPU is not enough to run 64 bit guests (in contrast to VMWare). The host must also be running a 64-bit OS and have hardware virtualization extensions enabled in the mainboard BIOS.

so I didn't touch my Ubuntu, not yet... and I have the next questions:

- In your opinion, what is the best VMWare or VirtualBox ? (to be honest, I do not really mind what is the best, I just need to be able to run different OSs which they are 64bits, all of them ).
- if so, how can I install VMWare ?
- The "hardware virtualization extensions enabled" in the mainboard BIOS is somehow a painful topic for me.. then, should I choose VMWare? or I have to enable it on the BIOS ?

Thanks.
Best regards.

---

### Post by TheFu on 2014-10-08
VMware makes 6 different virtualization products - each for different requirements. Which are of these are you interested?
There are a few other choices that might make sense, depending on your requirements - Xen and KVM.

IMHO, VirtualBox tries to be easy-to-use while others concentrate on performance and control. For a first-time virtualization user, vbox is not a bad choice.

So ... what do you want these VMs to do? Anything specific?  desktops, servers, something else?

---

### Post by SeijiSensei on 2014-10-09
I suspect any virtualization method that supports 64-bit guests on a 64-bit host will require the proper BIOS settings, but I don't have enough experience with systems other than VirtualBox to know for sure.

Why do you need a 64-bit guest?  For most purposes other than enabling large memory spaces, I doubt the 32-bit versions of anything you might run will have substantially poorer performance than the 64-bit versions.  For instance, most server applications run just fine on 32-bit operating systems.

---

### Post by Sarkozy on 2015-09-29
mastablasta, I just followed your instructions which resulted in installing the i386 (32-bit) version of VirtualBox.  How do I specify the 64-bit version (AMD64) ??  Or is that just not offered anywhere?  Thx for any advice you can provide.

---

