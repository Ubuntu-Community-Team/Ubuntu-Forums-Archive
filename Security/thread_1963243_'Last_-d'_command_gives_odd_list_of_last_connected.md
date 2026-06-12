---
title: "'Last -d' command gives odd list of last connected users"
date: 2012-04-22
forum: Security
---

### Post by FrancoisD on 2012-04-22
Hello
I'm using a desktop machine, am the unique user, and am not using any remote logins. When I check which users were last logged in using the ['last -d' command]("http://manpages.ubuntu.com/manpages/lucid/fr/man1/last.1.html") to check for any remote logins, the output seems odd. It lists the correct username 'ubuntuhome' but gives the connection as coming not from the local address, but from 'aircrack.ng.org.'  I've appended the output of 'list -d' below. 
The term 'aircrack.ng.org' listed in non-local connections, is btw also the name of WEP password cracking software. 
Should I be concerned, or is there be a simple explanation for this?
Btw I have several security tools installed, such as Arpwatch, Wireshark, and Darkstat; could any of these be causing a false alarm?
Any help much appreciated 
D

usermachine:~$ last -d
 ubuntuhome   pts/1        aircrack.ng.org  Sun Apr 22 10:17   still logged in
 ubuntuhome   pts/0        aircrack.ng.org  Sat Apr 21 17:12   still logged in
 ubuntuhome   tty7         aircrack.ng.org  Sat Apr 21 17:10   still logged in
 reboot   system boot  aircrack.ng.org  Sat Apr 21 17:10 - 10:27  (17:17)
 ubuntuhome   pts/7        aircrack.ng.org  Sat Apr 21 12:23 - crash  (04:46)
 ubuntuhome   pts/7        aircrack.ng.org  Sat Apr 21 12:23 - 12:23  (00:00)
 ubuntuhome   pts/4        aircrack.ng.org  Fri Apr 20 11:47 - crash (1+05:22)
 ubuntuhome   pts/3        aircrack.ng.org  Fri Apr 20 09:36 - crash (1+07:33)
 ubuntuhome   pts/2        aircrack.ng.org  Tue Apr 17 17:29 - crash (3+23:40)
 ubuntuhome   pts/1        aircrack.ng.org  Tue Apr 17 17:25 - crash (3+23:44)
 ubuntuhome   pts/0        aircrack.ng.org  Tue Apr 17 17:20 - crash (3+23:49)
 ubuntuhome   pts/2        aircrack.ng.org  Fri Apr  6 11:04 - 11:04  (00:00)
 ubuntuhome   pts/1        aircrack.ng.org  Fri Apr  6 10:52 - 10:07 (3+23:15)
 ubuntuhome   pts/0        aircrack.ng.org  Fri Apr  6 10:51 - 10:07 (3+23:16)
 ubuntuhome   tty7         aircrack.ng.org  Fri Apr  6 10:50 - crash (15+06:19)
 reboot   system boot  aircrack.ng.org  Fri Apr  6 10:49 - 10:27 (15+23:38)
 ubuntuhome   pts/0        aircrack.ng.org  Tue Apr  3 09:56 - 10:16  (00:20)
 ubuntuhome   pts/1        aircrack.ng.org  Mon Apr  2 19:58 - 08:56  (12:58)
 ubuntuhome   pts/0        aircrack.ng.org  Mon Apr  2 11:06 - 08:57  (21:50)

---

### Post by unspawn on 2012-04-22
To find out if this is a name resolution glitch run 'last -ai' instead.

---

### Post by strask on 2012-04-23
Yeah if you look at the reboot lines it seems like your system thinks that aircrack is the local host name.

---

### Post by FrancoisD on 2012-04-25
> **strask said:**
> Yeah if you look at the reboot lines it seems like your system thinks that aircrack is the local host name.

Hmm... The local host name seems to resolve fine using any other means. And why should it resolve to a site of well-known wifi WEP-cracking software -- which is not installed on my system? Doesn't that seem a bit odd? 
Re using 'last -ai,'; I'm not on the same machine here, so can't send the output from 'last -ai' but when I tried it on the machine in question it didn't seem to say anything informative.
A 'last -d' on all other machines on the network gives 0.0.0.0 on all interfaces.
Any other thoughts?
Any help much appreciated.
D

---

