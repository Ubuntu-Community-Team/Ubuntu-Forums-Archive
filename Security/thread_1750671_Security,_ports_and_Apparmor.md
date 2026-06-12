---
title: "Security, ports and Apparmor"
date: 2011-05-05
forum: Security
---

### Post by Axolotl9250 on 2011-05-05
Hi, I've been using Ubuntu now for a year, and Arch for about half a  year - Ubuntu because I love it for my work. and Arch because it makes  me learn the working of linux (albeit a little bit BSD-ish), without  having to build an entire system from source. Recently I've been  thinking about setting up a server on an old tower for general gaming  and messing about with friends, like minecraft and such. This has turned  my attention to security, both for this potential server and my laptop.  On Ubuntu, I have gufw set to protect my computer, as well as Apparmor  although it's not really enforcing or learning anything yet, I also did a  install of OSSEC-HIDS, but haven't done anything further with it, and I  have chkrootkit and rkhunter and scan my system every few days. 

I'm  not using Apparmor yet because I set it to learn Firefox and generate a  profile, which then stopped it from loading up when it enforced, I  notice there is a broken link in the Disable folder to do with Firefox  and I'm wondering if this has anything to do with it.

I've used  advice from: [https://wiki.archlinux.org/index.php/Security](https://wiki.archlinux.org/index.php/Security) except from  kernel hardening and compiling, as grsecurity and several other options I  considered require recompiling the kernel. 

I've also read the  Ubuntu pages on this, including the main security page. I know the  firewall should prevent a lot of unauthorised traffic for people running  server applications and I've read most of the security wiki too, but I  have a few questions. Mainly if I really need to have the apache stuff  to interact with OSS HIDS (theres no documentation for Arch, and the  Ubuntu documentation tells me to use the web server), or would i need  something else like tiger? Secondly is there any point in me using  SNORT, which was said to be vulnerable to attacks of it's own, If I  already have a HIDS. 

For my future little game tower server I'm  planning on using a minimal linux install, with the minecraft server  software and the hamachi free VNC software, because it makes connecting  to an ip easier, no matter where me and my friends live (we've at uni-  so several digs throughout our years) without messing about with port  forwarding and such and altering our router settings (in fact for our  sky one it's not possible). If anyone has any advice regarding making  this secure, other than what I've already done above - because I will do  mostly the same with it as I've done on my laptop, plus whatever extra  precautions are necessary for a server, then I will gratefully pursue  and research any advice given.

Thanks in advance.
Ben W.

---

