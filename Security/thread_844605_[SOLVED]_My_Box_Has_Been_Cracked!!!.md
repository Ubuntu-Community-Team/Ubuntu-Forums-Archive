---
title: "[SOLVED] My Box Has Been Cracked!!!"
date: 2008-06-29
forum: Security
---

### Post by HunterThomson on 2008-06-29
I hope I am wrong but I think I am right](*,)

I came here because you all are vary smart when it comes to security:)

The shelds up web sight tells me that these ports are open:

111 sunrpc sun remote procedure call

769

After I first installed I whent there and none were open......
I have not installed any serveses stuff other then ktorrent, tor, privoxy???

rkhunter tells me the following:

Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script text executable

Warning: The command '/usr/bin/whatis' has been replaced by a script: /usr/bin/whatis: POSIX shell script text executable
e
Warning: The command '/usr/sbin/adduser' has been replaced by a script: /usr/sbin/adduser: Bourne-Again shell script text execut$

Warning: The syslog daemon is running, but no configuration file can be found.

Warning: Hidden file found: /usr/man/man8/.isdnctrl_conf.8.gz: gzip compressed data, was ".isdnctrl_conf.8", from Unix, last mod$

And, not now but last time I "ls" the /etc a lot of things and things dealing with group, user, syslog and sudoers were in RED boxes

When I turn on firestarter I pass shelds up as stelth but then when I try to go to ubuntuforums.org or archlinux forums or gmail it never getts there and I have to turn off firestarter to get the page to load??? However, other web sights load with no problem???

What do you think? Should I panic and reinstall?
Or are the ports 111 769 no problem and were probaly opend by some program, just close them and I should not worry about them?

I'll read up on how to make a backup before I reinstall so I have a backup after I set my sys up.... (I just spent all week getting my new archlinux all setup and runing like a champ](*,) )

---

### Post by yopnono on 2008-06-29
[http://ubuntuforums.org/archive/index.php/t-785332.html](http://ubuntuforums.org/archive/index.php/t-785332.html)

---

### Post by HunterThomson on 2008-06-29
> **yopnono said:**
> [http://ubuntuforums.org/archive/index.php/t-785332.html](http://ubuntuforums.org/archive/index.php/t-785332.html)

Thanks for responding:)

I am more conserned about syslog.conf and sudoers and stuff being changed and the new open ports((however these could just be the changes I made when I made new a new sudoer user acount)). I removed firestarter and installed guarddog/setup now I have the ports closed and can still visit ubuntuforums.org and archlinux forums. But how do you think the the ports were opended? Guarddog said that port 111 is a High security risk and is used to relay info about logins and stuff.

edit: I kind of figured the things bing scrips were no big deal because I looked at the scripts and they don't seem to be doing anything they should not:)

---

### Post by joshuachad on 2008-06-29
I think your over analyzing but at least your concious of security. Get to know iptables if you can and that way if you have services need to get out / get in you can lock down access. But to respond you thread said you box was cracked. There is nothing based off of what you posted that suggests that.

---

### Post by yopnono on 2008-06-29
Run this as well.
sudo rkhunter --propupd
then
sudo rkhunter --check --pkgmgr dpkg

---

### Post by HunterThomson on 2008-06-29
> **joshuachad said:**
> I think your over analyzing but at least your concious of security. Get to know iptables if you can and that way if you have services need to get out / get in you can lock down access. But to respond you thread said you box was cracked. There is nothing based off of what you posted that suggests that.

Thankyou all:guitar:

Ya, I want to learn iptables. I was hopping I was just over analyzing.

I titled my thread "My Box Has Been Cracked" to get a quick response:^o

Sorry for bing misleading. However, I realy was woryied about the new open ports....

---

### Post by HunterThomson on 2008-06-29
> **yopnono said:**
> Run this as well.
sudo rkhunter --propupd
then
sudo rkhunter --check --pkgmgr dpkg

Ya, I do run --propupd

I haven't figured out how to set up the pakage manager checksum to work with pacman. But ya that sounds like a really good option:)

---

### Post by HunterThomson on 2008-06-29
I am going to make a backup of all my partitions now. So, if I ever do get cracked/HDD crash/mess things up/ it will be no big deal.

Thankyou all for the fresh air:lolflag:

---

