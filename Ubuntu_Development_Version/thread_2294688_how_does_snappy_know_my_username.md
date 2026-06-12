---
title: "how does snappy know my username?"
date: 2015-09-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-09-12
I just realized while working in cli  that snappy knows my user name at ubuntuforums and presents it as such:

```

ventrical-desktop login:

```

I downloaded the raw image through terminal and used both 'disks' and mkusb to restore the image to hdd and usb. So how did this raw image figure out my ubuntuforums username and is it a security risk?

Regards..

---

### Post by QDR06VV9 on 2015-09-12
I was hoping someone else would pick that up..
Kind of Disturbing, but I'm sure The security part will be down played with another term.
Regards

---

### Post by zika on 2015-09-12
> **ventrical said:**
> I just realized while working in cli  that snappy knows my user name at ubuntuforums and presents it as such:

```

ventrical-desktop login:

```

I downloaded the raw image through terminal and used both 'disks' and mkusb to restore the image to hdd and usb. So how did this raw image figure out my ubuntuforums username and is it a security risk?

Regards..At least two possible answers are below and I suppose there are several more...
1. User **ventrical** answered to that already: [http://ubuntuforums.org/showthread.php?t=2286066&p=13354306#post13354306](http://ubuntuforums.org/showthread.php?t=2286066&p=13354306#post13354306) ... ;)
or
2. that &#8222;ventrical-desktop&#8220; does not have anything to do with **ventrical** here as I supose You nickname Your machines also like that... ;)

Security risk? No, I do not think so... ;)

---

### Post by QDR06VV9 on 2015-09-12
> **zika said:**
> At least two possible answers are below and I suppose there are several more...
1. User **ventrical** answered to that already: [http://ubuntuforums.org/showthread.php?t=2286066&p=13354306#post13354306](http://ubuntuforums.org/showthread.php?t=2286066&p=13354306#post13354306) ... ;)
or
2. that „ventrical-desktop“ does not have anything to do with **ventrical** here as I supose You nickname Your machines also like that... ;)

Security risk? No, I do not think so... ;)
All Good Points.
Thanks zika):P

---

### Post by ventrical on 2015-09-12
> **zika said:**
> At least two possible answers are below and I suppose there are several more...
1. User **ventrical** answered to that already: [http://ubuntuforums.org/showthread.php?t=2286066&p=13354306#post13354306](http://ubuntuforums.org/showthread.php?t=2286066&p=13354306#post13354306) ... ;)
or
2. that „ventrical-desktop“ does not have anything to do with **ventrical** here as I supose You nickname Your machines also like that... ;)

Security risk? No, I do not think so... ;)

..yes .. i see that perhaps.. but I still have to log on with 'ubuntu' password so does not make sense to me atm.

Regards..

---

### Post by The Cog on 2015-09-12
Sounds like ventrical-desktop is the machine name. Could that have been picked up from a DHCP server that previously saw a machine called ventrical-desktop at that MAC adddress?

---

### Post by ventrical on 2015-09-12
> **The Cog said:**
> Sounds like ventrical-desktop is the machine name. Could that have been picked up from a DHCP server that previously saw a machine called ventrical-desktop at that MAC adddress?

That could be perhaps. I am currently typing this message from snappy installed on USB where I had logged in with my SSO and cli says ```
 amd64_ubuntu@localhost: 
``` which is the right prompt.

---

### Post by QDR06VV9 on 2015-09-12
This needs more info here i login with runrickus
But name my machines "Me" and i am usually behind a VPN.
Checking my old install logs now to verify.

---

### Post by ventrical on 2015-09-12
> **runrickus said:**
> This needs more info here i login with runrickus
But name my machines "Me" and i am usually behind a VPN.
Checking my old install logs now to verify.

Honestly... I have to go along with your profile pic :) is about where I am at right now :)regards.. edit..WOW.. I updated to core 90 then rebooted.I went to cli and now I have ```
ventrical-Canterwood-ICH5 login 
``` as a prompt! Now I know why they call it snappy personal :) This pc is a lenovo T61 laptop. It is like snappy was made for this machine :) it is so fast. regards.. edit.. The scary thing is that I do not use the username 'ventrical' in my SSO and snappy was not installed like regular distro installs so it is very strange indeed.

---

### Post by QDR06VV9 on 2015-09-12
> **ventrical said:**
> Honestly... I have to go along with your profile pic :) is about where I am at right now :)regards.. edit..WOW.. I updated to core 90 then rebooted.I went to cli and now I have ```
ventrical-Canterwood-ICH5 login 
``` as a prompt! Now I know why they call it snappy personal :) This pc is a lenovo T61 laptop. It is like snappy was made for this machine :) it is so fast. regards.. edit.. _**The scary thing is that I do not use the username 'ventrical' in my SSO and snappy was not installed like regular distro installs so it is very strange indeed**_.
Yes Indeed here is my install process until it becomes more usable. [https://www.maketecheasier.com/ubuntu-snappy-what-you-need-to-know/](https://www.maketecheasier.com/ubuntu-snappy-what-you-need-to-know/)
So now I am scratching my head and smiling having no idea whats going on:D

---

### Post by grahammechanical on 2015-09-12
If I guess right, do I get a cookie? :)

ICH5 = I/O Controller Hub version 5

[https://en.wikipedia.org/wiki/I/O_Controller_Hub](https://en.wikipedia.org/wiki/I/O_Controller_Hub)

Canterwood = Intel 875 chip set

[http://www.computerworld.com/article/2580834/computer-hardware/intel-to-ship-canterwood-chip-set--new-3-ghz-pentium-4.html](http://www.computerworld.com/article/2580834/computer-hardware/intel-to-ship-canterwood-chip-set--new-3-ghz-pentium-4.html)

ventrical = name recorded in the BIOS as part of some motherboard security feature?

Something is picking up information from the BIOS. It gets the time and date from the BIOS. Why not other stuff?

Regards.

[URL="https://en.wikipedia.org/wiki/I/O_Controller_Hub"]


[/URL]

---

### Post by ventrical on 2015-09-12
> **grahammechanical said:**
> If I guess right, do I get a cookie? :)

ICH5 = I/O Controller Hub version 5

[https://en.wikipedia.org/wiki/I/O_Controller_Hub](https://en.wikipedia.org/wiki/I/O_Controller_Hub)

Canterwood = Intel 875 chip set

[http://www.computerworld.com/article/2580834/computer-hardware/intel-to-ship-canterwood-chip-set--new-3-ghz-pentium-4.html](http://www.computerworld.com/article/2580834/computer-hardware/intel-to-ship-canterwood-chip-set--new-3-ghz-pentium-4.html)

ventrical = name recorded in the BIOS as part of some motherboard security feature?

Something is picking up information from the BIOS. It gets the time and date from the BIOS. Why not other stuff?

Regards.

[URL="https://en.wikipedia.org/wiki/I/O_Controller_Hub"]


[/URL]

You really scaring me now :) A whole bag of cookies for you.;)

---

### Post by grahammechanical on 2015-09-13
It is not so long ago that Microsoft in an attempt to stop people installing Windows on more than one machine came up with a system that deactivated Windows if a major hardware component was changed. So, something in an OS is able to work out what is recorded in the BIOS/UEFI boot system. We just do not think about it too deeply.

Here is a scary thought. Pulling a label out of the BIOS and publishing it as a terminal prompt is one thing, But what if it is a BIOS password?

---

### Post by ventrical on 2015-09-13
> **grahammechanical said:**
> It is not so long ago that Microsoft in an attempt to stop people installing Windows on more than one machine came up with a system that deactivated Windows if a major hardware component was changed. So, something in an OS is able to work out what is recorded in the BIOS/UEFI boot system. We just do not think about it too deeply.

Here is a scary thought. Pulling a label out of the BIOS and publishing it as a terminal prompt is one thing, But what if it is a BIOS password?

Of course conventionally that is suppossed to be protected but most any undocumented interrupt vector can be exploited. BIOSes are made to be read. The passwords are encrypted so there is a deterrent there.

I do think it is a bug, however, that while logging in to unity8/snappy-personal that the actual characters are briefly shown in the dialog box.  I mean .. that is part of why we are here.. to test and report these things.

As for Microsoft ....the BSOD ... after a hardware change .  That is malware of the highest order. I try to not dare to look back at that 15 years of madness.

Regards..

---

### Post by flocculant on 2015-09-13
> **ventrical said:**
> ..

I do think it is a bug, however, that while logging in to unity8/snappy-personal that the actual characters are briefly shown in the dialog box.  I mean .. that is part of why we are here.. to test and report these things...

You got bug number - would be interesting to see what they say :)

---

### Post by QDR06VV9 on 2015-09-13
> **flocculant said:**
> You got bug number - would be interesting to see what they say :)

I also would like to know how they reply.

My CPU Info "Dual core Intel Core i3-2330M (-HT-MCP-)"

Info from Intel
> Intel® Identity Protection Technology is a built-in security token technology that helps provide a simple, tamper-resistant method for protecting access to your online customer and business data from threats and fraud.  Intel® IPT provides a hardware-based proof of a unique user&#8217;s PC to websites, financial institutions, and network services; providing verification that it is not malware attempting to login.   Intel® IPT can be a key component in two-factor authentication solutions to protect your information at websites and business log-ins.
I know it is me just missing information, But none the less curious.

---

### Post by ventrical on 2015-09-13
It's also like the TPM or UEFI for that matter. Uhh....mm.. my point was that I notice these little things come up which are strange because we are not actually performing an install as in the convention sense , entering our username and password on a hard install of ubuntu.

Regards..

---

### Post by ventrical on 2015-09-13
> **flocculant said:**
> You got bug number - would be interesting to see what they say :)

No. I am sure there is one out there.  It happens during the SSO login in the browser.  It may not be unity8 or snappy core that is the problem but more likely the browser.

Regards..

Edit:

 I guess I'll rephrase it to a question.

Is anybody seeing their password characters  show up in the SSO login dialog box while running  the snappy-personal image ? If so - should we worry about it?

Regards..

---

### Post by ventrical on 2015-09-13
Sent a request on the snappy-devel list about this issue.

---

### Post by grahammechanical on 2015-09-13
> Is anybody seeing their password characters  show up in the SSO login  dialog box while running  the snappy-personal image ? If so - should we  worry about it?

I see that. There is a noticeable delay in the character turning to an asterisk. I did not notice it at first as I have to look at the keyboard when typing. :) It does not happen with the login screen. Not that I remember.

---

### Post by ventrical on 2015-09-14
> **grahammechanical said:**
> I see that. There is a noticeable delay in the character turning to an asterisk. I did not notice it at first as I have to look at the keyboard when typing. :) It does not happen with the login screen. Not that I remember.

Thanks for confirming this. I have no idea if it is a security risk but .. if somebody was looking over my shoulder .. then ...:)

regards..

---

### Post by ventrical on 2015-09-17
ubuntu-desktop 15.10 /lubuntu .. etc.. WRITES the username/machinename to BIOS/Firmware and/or UEFI during the installation process.. If you have a working snappy-personal system on USB or hdd and swap it into a machine that previously had an install of any ubuntu flavour of 15.10 , update it, then it will grab the username and whatever else that was written to firmware by the last installation.

Regards..

---

### Post by QDR06VV9 on 2015-09-17
> **ventrical said:**
> ubuntu-desktop 15.10 /lubuntu .. etc.. WRITES the username/machinename to BIOS/Firmware and/or UEFI during the installation process.. If you have a working snappy-personal system on USB or hdd and swap it into a machine that previously had an install of any ubuntu flavour of 15.10 , update it, then it will grab the username and whatever else that was written to firmware by the last installation.

Regards..
Yep! +1

---

