---
title: "After the last update (kernel 4.13.0-26)crashed"
date: 2018-01-16
forum: Security
---

### Post by ubu112 on 2018-01-16
I have an Acer Aspire One AOA150 with Lubuntu 16.04.2 LTS.

After update,I rebooted and I had just black screen with strange lines,later 3/4 black screen and 1/4 regular screen,but nothing can be done.

I'm not an expert, I fund @Pilot6 solution [https://askubuntu.com/questions/9454...d-update-16-04]("https://askubuntu.com/questions/945403/how-to-downgrade-kernel-after-bad-update-16-04")

I deleted the 4.13.0-26 kernel and then : sudo apt install linux-generic.

Now,I'm working with the previous kernel and everything is fine.

If I'm not wrong, this was the Meltdown patch and,obviously,I need it.

I'd like to understand if ,the next time,this kernel will be updated?if I did well to delete the malfunctioning kernel.

How could I have a functioning Meltdown/Spectre patch?

Thank you

---

### Post by TheFu on 2018-01-16
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown) is the most correct/current info that I know.
> The Rolling HWE kernel for Ubuntu 16.04 will go to 4.13 early, instead of also fixing 4.10 HWE kernel. 

There is also a _sticky thread_ in the security subforum here about this stuff.

---

### Post by vasa1 on 2018-01-16
>  I have an Acer Aspire One AOA150 with Lubuntu 16.04.**_2_** LTS.What does```
lsb_release -d
```show you now?

I get```
$ lsb_release -d
Description:    Ubuntu 16.04.**_3_** LTS
$
```

---

### Post by TheFu on 2018-01-16
I saw that too vasa1.  Looked up support info ...  There is the kernel for the .2 which doesn't have support anymore and there is the rest of the supported packages, which appear to get the full 5 yrs of support.  Confusing?  It is to me.  Basically, the v4.13 kernel is what we all need to get onto. My 16.04.3 machine is running v4.10.x of the kernel now.  I'd been delaying any patches to let others _find all the issues_ first. ;)

---

### Post by ubu112 on 2018-01-16
@The Fu,@vasa 1,First of all,thank you for your answers.

Yes,I made a mistake:

> user@AOA150:~$ lsb_release -d
Description:    Ubuntu 16.04.3 LTS
user@AOA150:~$ uname -r
4.10.0-42-generic

If I understand well, have we to wait and see if the next update works?

Have you the same kernel (4.10.0-42)?

If I'm not wrong,the best info come from "wiki".

I read all the "Meltdown and Spectre" sticky,and It's not clear to me,if the next update  applies to 32bit and 64 

bit.This because I'm still using an old 32bit.

Thank you

---

### Post by TheFu on 2018-01-16
I've not seen any timeframe for 32-bit kernels to be fixed.
In short, just patch weekly and you'll get the updates quickly enough.

---

### Post by ubu112 on 2018-02-13
@The Fu,sorry if I'm disturbing you.

I patched weekly as you suggested to me but the kernel is always the same.

Now,I discovered that 4.13.0-26 appear to be affected by a bug - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1743111](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1743111)

On Wiki I read:

> [COLOR=#333333][FONT=&amp]No fix is currently available for Meltdown on 32-bit x86; moving to a 64-bit kernel is the currently recommended mitigation[/FONT][/COLOR]

I'm not an exspert at all,what do you think can I do now? can I hope to have a new kernel?

Thank you

---

### Post by ubu112 on 2018-04-29
As I said in the post #1,I had an issue with kernel 4.13.0-26 and I followed the @pilot6 suggestion, I mean I deleted it.

I patched weekly but I still have the same kernel 4.10.0-42.

Is this correct or what have I to do?

Thank you

---

### Post by deadflowr on 2018-04-29
I see you installed the linux-generic package
for what it's worth that package brings in the 4.4 kernels which are obviously a lower version number than 4.10.
Since the bootloader loads the newest available version number by default that means it'll always load the 4.10 kernel over the 4.4 kernel unless you manually select a 4.4 kernel.
look at
```
dpkg -l linux-*
```
to see what kernels and whatnots related to kernels are installed.

---

### Post by ubu112 on 2018-04-29
@deadflowr, thank you for your answer.

This is the result:

```
Voluto=U (non noto)/I (installato)/R (rimosso)/P (rimosso totale)/H (in attesa)
| Stato=Non/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(nessuno)/R (reinstallazione richiesta) (Stato,Err: maiuscolo=grave)
||/ Nome           Versione     Architettura Descrizione
+++-==============-============-============-=================================
ii  linux-base     4.0ubuntu1   all          Linux image base package
ii  linux-firmware 1.157.17     all          Firmware for Linux kernel drivers
ii  linux-generic  4.4.0.122.12 i386         Complete Generic Linux kernel an
ii  linux-headers- 4.10.0-40.44 all          Header files related to Linux ker
ii  linux-headers- 4.10.0-40.44 i386         Linux kernel headers for version 
ii  linux-headers- 4.10.0-42.46 all          Header files related to Linux ker
ii  linux-headers- 4.10.0-42.46 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-112.13 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-112.13 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-116.14 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-116.14 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-119.14 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-119.14 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0-122.14 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-122.14 i386         Linux kernel headers for version 
ii  linux-headers- 4.4.0.122.12 i386         Generic Linux kernel headers
rc  linux-image-4. 4.10.0-28.32 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.10.0-30.34 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.10.0-32.36 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.10.0-33.37 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.10.0-35.39 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.10.0-37.41 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.10.0-38.42 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-40.44 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.10.0-42.46 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.13.0-26.29 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-109.13 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-112.13 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-116.14 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-119.14 i386         Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-122.14 i386         Linux kernel image for version 4.
rc  linux-image-4. 4.8.0-36.36~ i386         Linux kernel image for version 4.
rc  linux-image-4. 4.8.0-53.56~ i386         Linux kernel image for version 4.
rc  linux-image-4. 4.8.0-54.57~ i386         Linux kernel image for version 4.
rc  linux-image-4. 4.8.0-58.63~ i386         Linux kernel image for version 4.
rc  linux-image-ex 4.10.0-28.32 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.10.0-30.34 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.10.0-32.36 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.10.0-33.37 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.10.0-35.39 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.10.0-37.41 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.10.0-38.42 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.10.0-40.44 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.10.0-42.46 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.13.0-26.29 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-109.13 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-112.13 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-116.14 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-119.14 i386         Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-122.14 i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.8.0-36.36~ i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.8.0-53.56~ i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.8.0-54.57~ i386         Linux kernel extra modules for ve
rc  linux-image-ex 4.8.0-58.63~ i386         Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.122.12 i386         Generic Linux kernel image
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
user@AOA150:~$ 

```
Now,can you,please,be so kind  to explain to me what this mean,because I'm not an expert.

I mean I'd like to know if everything is correct,if I have to do something and if will I have a new kernel?

Thank you

---

### Post by deadflowr on 2018-04-29
Basically you followed pilot6's advice and what happened is exactly what pilot6 said would happen.
Ubuntu 16.04 can install two different kernel series 4.4 or a rolling kernel 
(originally the rolling kernel was 4.8, then upgraded to 4.10 and now is at 4.13; in the future it will be 4.15)
The first kernel (4.4) is from the original kernel series used in 16.04.
The second (the rolling) is part of the hwe or hardware stack enablement.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

When you removed the 4.13 kernel packages, that removed the hwe version of the linux-generic packages.
So when you reinstalled the linux-generic package you actually installed a different linux-generic package than what was installed.
So instead of bringing in the 4.13 kernels, it now brings in the 4.4 kernels.

Fret not, because the 4.4 kernel can be booted into and this can be fixed.
But to do so you need to do it manually at startup.

When you startup the machine during boot up, the machine should show the BIOS screen (it usually tells you what machine it is; It might be Dell or a Lenovo, or if generic it might say Intel or AMD)
But whatever it says what you need to do wait for that screen to disappear and then hit either the Shift key or the ESC key.
You need to hit the key immediately when that BIOS screen goes blank, and you might need to do some quick tapping of the key so you don''t miss the window that needs open

When successful, you will get the Ubuntu boot menu (grub) 
In here what you'll do is go down to the second line marked as Advanced Options.
Click on this and go down to the first option that shows a 4.4 kernel
(It should say something like  "Ubuntu, with linux 4.4.0-122-generic (on /dev/sdX)" since 4.4.0-122 is the latest 4.4 kernel you have.)
Now yo can just select and you'll boot into that 4.4 kernel.

Now, what you can do is test it out and see how well it works for you.
If it works well enough for you then you can just keep running the 4.4 kernels
and remove the 4.10 kernel packages you have installed.
Once you remove those, then the system will boot into the 4.4 kernels on their own,since they would be the only kernels.

And if it doesn't perform as you would like, you can try and reinstall the hwe packages and get back to the 4.13 kernels again and see if those work.

But I would test the 4.4 kernels first before doing anything else.

Hope it makes sense and gets you going in a workable way.
Good luck.

---

### Post by ubu112 on 2018-04-30
@deadflowr,sorry,as I said I'm not an expert,so I have some doubts:

When I had problems with the kernel 4.13.0-26 I deleted it and I typed:

```
[COLOR=#111111][FONT=Consolas]sudo apt install linux-generic[/FONT][/COLOR]
```

Pilot6 said:

> That will install the latest kernel and kernels will be upgraded

But, I didn't have upgrades,why? maybe for the bug  described in my post #7? or,what else?

Now,I'm working fine with kernel 4.10.0-42,that was the kernel before the malfunctioning 4.13.0-26, so I chose that one.

When you said:

> [COLOR=#000000]So when you reinstalled the linux-generic package you actually installed a different linux-generic package than what was installed[/COLOR]

Do you refer to the 4.10.0-42? because I don't understand why I have to delete it.

I tried kernel 4.4.0-122 and it seems to work fine.

If I also delete kernel 4.10.0-42, what advantages can I have?

Thank you

---

