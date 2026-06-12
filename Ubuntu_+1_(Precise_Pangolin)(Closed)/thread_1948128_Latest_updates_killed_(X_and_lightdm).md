---
title: "Latest updates killed (X and lightdm) ?"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tehowe on 2012-03-27
So, I was away for a week and a half from my desktop and unable to stay right on top of updates. Shouldn't matter, right? But after updating about 669 packages I was greeted with a screen very much like this one.

[IMG]http://i1107.photobucket.com/albums/h395/tehowe42/20120327_001b.jpg[/IMG]

Initially, lightdm didn't load properly and the line reading 'mountall: Plymouth command failed' so as a series of shots in the dark I tried the equivalent of the following

sudo apt-get install ubuntu-desktop
sudo apt-get --reinstall install lightdm
sudo apt-get install plymouth (reporeted latest version already)
sudo apt-get install mountall (reported latest version already)

You see the result above. How do I even go about troubleshooting/fixing this? 

Or am I officially now a Beta 2 ISO tester :/

---

### Post by effenberg0x0 on 2012-03-27
We need any info, so we can guess better.

Press Ctrl+Alt+F6 to Switch to VT6 (Virtual Terminal 6). Login with your Login and Password.

Get Kernel version, Ubuntu Release, your VGA Card brand and model:
```

uname -a
lsb_release -a
lspci -vvvv| grep  'VGA '

```

Regards,
Effenberg

---

### Post by tehowe on 2012-03-27
> **effenberg0x0 said:**
> We need any info, so we can guess better.

Press Ctrl+Alt+F6 to Switch to VT6 (Virtual Terminal 6). Login with your Login and Password.

Get Kernel version, Ubuntu Release, your VGA Card brand and model:
```

uname -a
lsb_release -a
lspci -vvvv| grep  'VGA '

```Regards,
Effenberg

Specs:
AMD Phenom x6 1090t
8GB
Radeon 5850
LUKS alternate install

Also notable: "cat: /proc//environ: No such file or directory" is displayed immediately before my prompt.

Here's the rest, thanks for checking it out...

> uname -aLinux galt 3.2.0-20-generic #33-Ubuntu SMP Tues Mar 27 16:42:26 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
lsb_release -a
```No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu Precise (development branch)
Release: 12.04
Codename: precise

```
lspci -vvvv | grep 'VGA'
```better a pic than to transcribe this... the card is a Radeon 5850, with Catalyst 12.2 installed.  Xorg.conf looks ok btw

[IMG]http://i1107.photobucket.com/albums/h395/tehowe42/20120327_001.jpg[/IMG]


Thanks Effenberg! I'll be up as late as it takes to fix this tonight. And flash my new router. Can you believe my router died while I was away too? This stuff keeps me occupied anyways :)

---

### Post by effenberg0x0 on 2012-03-27
Hi tehowe, one very possible reason to not be able to get to lightdm would be not having a proper VGA kernel module loaded or not having corresponding drivers installed. You mention updating and I see you are running a current kernel, so it reinforces this hypothesis. 

Which drivers were you using before? I'm gonna guess again and say Catalyst? (therefore, when updating the kernel, there's no dkms update to the Kernel Module - making this an ordinary issue, unrelated to Precise.)

If so, this is the URL for the current Catalyst 64-Bit Linux driver:
[http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run)

And this are the install instructions:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.2)

Tell us if you need more instructions, or if I guessed wrong and you were running open source drivers, so we can go from there.

Regards,
Effenberg

---

### Post by cariboo on 2012-03-28
+1  to what effenberg0x0 said, with the last kernel update, on my system the Nvidia driver didn't get built properly. I haven't rebooted since today's kernel update yet, so I don't know if the problem has been resolved.

---

### Post by paul_in_london on 2012-03-28
[COLOR="Red"]****[/COLOR]> **cariboo907 said:**
> +1  to what effenberg0x0 said, with the last kernel update, on my system the Nvidia driver didn't get built properly. I haven't rebooted since today's kernel update yet, so I don't know if the problem has been resolved.

Since the recent upgrade of nvidia-current to [COLOR="Red"]**295.33**[/COLOR] (from xorg-edgers) I've had no further build failure issues using the 3.3 kernel which is available here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/)

---

### Post by tehowe on 2012-03-28
> **effenberg0x0 said:**
> Hi tehowe, one very possible reason to not be able to get to lightdm would be not having a proper VGA kernel module loaded or not having corresponding drivers installed. You mention updating and I see you are running a current kernel, so it reinforces this hypothesis. 

Which drivers were you using before? I'm gonna guess again and say Catalyst? (therefore, when updating the kernel, there's no dkms update to the Kernel Module - making this an ordinary issue, unrelated to Precise.)

If so, this is the URL for the current Catalyst 64-Bit Linux driver:
[http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run)

And this are the install instructions:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.2)

Tell us if you need more instructions, or if I guessed wrong and you were running open source drivers, so we can go from there.

Regards,
Effenberg

You, kind sirs, are brilliant.

Odd that this never happened before though, with Maverick or Oneiric  through various kernel updates. I'm fairly certain I've never used the  --buildpkg flag to install Catalyst in the past, though maybe that made  some difference here.

eg; (for future readers) the instructions** Effenberg0x0** point us to above say to execute the following;

```
sudo sh ./amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/precise
```while I've always

```
sudo sh ./amd-driver-installer-12-2-x86.x86_64.run
```which has me back up and running now, thanks! Though in future I'd try the former approach first.

**On a side note, Paul_in_London**, thanks for posting the 3.3 PPA.  That may be useful esp on my netbook which is having Bluetooth problems  (though I wonder if I shouldn't wait to put the new kernel in until LTS  goes stable...)

---

### Post by paul_in_london on 2012-03-28
> On a side note, Paul_in_London, thanks for posting the 3.3 PPA. That may be useful esp on my netbook which is having Bluetooth problems (though I wonder if I shouldn't wait to put the new kernel in until LTS goes stable...)

This "vanilla" version of the 3.3 kernel (i.e. without any distro-specific patches) has now been released and will probably work ok for you. Not sure off the top of my head which kernel 12.04 will finally "ship with" though.

---

