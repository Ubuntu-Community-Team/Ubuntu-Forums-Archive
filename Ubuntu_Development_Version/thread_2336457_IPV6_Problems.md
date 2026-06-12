---
title: "IPV6 Problems"
date: 2016-09-08
forum: Ubuntu Development Version
---

### Post by VMC on 2016-09-08
I've noticed that the current Yakkety and current Xenial both have problems with IPV6.


For example, using wget:
'wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)'
Output:
--2016-09-08 08:31:47--  [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
Resolving dl.google.com (dl.google.com)... 2607:f8b0:4007:80b::200e, 216.58.217.206
Connecting to dl.google.com (dl.google.com)|2607:f8b0:4007:80b::200e|:443... 
Then it stops output.

If I then force IPV4:
'wget -4 [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)'
The download starts immediately.

This also happens using 'zsync'. I have no way of forcing ipv4 on zsync.

Futhermore:

'ping6 [www.google.com]("http://www.google.com")'
Output:
PING [www.google.com(lax28s01-in-x04.1e100.net)]("http://www.google.com(lax28s01-in-x04.1e100.net)") 56 data bytes
...
Output stops, with no further response.

Where as:
ping [www.google.com]("http://www.google.com") , I get an immediate response.

I disabled IPV6 using this method found [here]("http://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04") and [here]("http://ask.xmodulo.com/disable-ipv6-linux.html") .
 
To see if IPV6 is enabled, from a terminal type: 'ifconfig' , and 'ip addr list'. Look for **inet6** outputs.

Regarding the kernel, [ArchWiki]("https://wiki.archlinux.org/index.php/IPv6#Disable_IPv6") has more information:

Adding to the kernel line "**ipv6.disable_ipv6=1**" , disables the IPV6 from the kernel.  Now 'zsync' , 'wget' work as expected.

 I'm unsure what programs need IPV6 , as stated in [ArchWiki]("https://wiki.archlinux.org/index.php/IPv6#Disable_IPv6").

I have no issue downloading from the browser with IPV6 enabled.

Several years ago, this came up:[https://ubuntuforums.org/showthread.php?t=1776372&highlight=IPV6+Problems](https://ubuntuforums.org/showthread.php?t=1776372&highlight=IPV6+Problems)
I haven't had any problems until this year with Yakkety and current Xenial.

Please tell me your experiences.

---

### Post by zika on 2016-09-09
Or leave it all as it was by default and edit /etc/gai.conf...

---

### Post by VMC on 2016-09-09
Thanks for hint. I found out now why newer Xenial and current Yakkety updates and downloads fail:

Reading this, explains it all:[http://terokarvinen.com/2016/prefer-ipv4-on-ubuntu-16-04-lts-xenial-etcgai-conf-precedence-ffff0096-100](http://terokarvinen.com/2016/prefer-ipv4-on-ubuntu-16-04-lts-xenial-etcgai-conf-precedence-ffff0096-100)
There was a bug reported last year.

---

