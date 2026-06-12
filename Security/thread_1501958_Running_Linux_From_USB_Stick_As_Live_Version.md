---
title: "Running Linux From USB Stick As Live Version"
date: 2010-06-04
forum: Security
---

### Post by TheNewbieGeek on 2010-06-04
My netbook runs Windows CE but I want to run Debian as a live version from my USB flash drive. Does this provide the same amount of security from hackers as installing Debian as the only OS on my netbook. Windows ce would still be on my netbook? Thanks for the replies.

---

### Post by oldfred on 2010-06-05
One example:

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by TheNewbieGeek on 2010-06-05
Thank you but i wanted to know if it's as secure as installing linux to my netbook as the only OS. Currently Windows CE is installed. I would have a live version of Linux on the usb flash drive. It seems as though it wouldn't be as secure. But I needed a how to on that as well.

---

### Post by OpSecShellshock on 2010-06-05
I'm not sure exactly what you mean by "as secure," but it certainly wouldn't have persistent software updates. By that I mean you'd have to manually update whatever you're running every time you boot up as far as I know. Or you'd have to regularly wipe the USB stick and use a newer .iso to boot from. Bit of work, but no big deal. There shouldn't be anything left behind by the live disk after the session's been terminated.

Another thing to consider is that security isn't really a stable state. This gets a bit into the theoretical aspects of the field, but in short, you need to identify what risks you're trying to protect against first, then confirm that they really exist in your specific setup, and then apply protective measures. You aren't, for example, going to have financial transactions hijacked by a Trojan if no Trojans exist for your build, whether you're running a live version or a fully installed version. So what kinds of things are you worried about?

---

### Post by TheNewbieGeek on 2010-06-05
Trojans and spyware are exactly what I was talking about.

---

### Post by bodhi.zazen on 2010-06-05
First, "Trojans and spyware" are almost unknown in Linux, I have not seen any of these things on any of my Linux systems ever and the only way you would get them would be if you installed them yourself.

Second, I think we are wondering what makes you think instlling to a USB sitick is any different from installing to a hard drive? What makes you feel a USB stick is more or less secure? It is not.

Third, Windows is a very limited OS and can not read your Linux file system. In theory it may be possible for malware on windows to affect a Linux partition, but I have not seen such an example "in the wild". Keep your Windows system secure, but, for the most part, Windows malware will not affect Linux.

I suggest you read the sticky at the top of these forums.

---

