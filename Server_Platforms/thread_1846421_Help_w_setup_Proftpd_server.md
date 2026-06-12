---
title: "Help w/ setup Proftpd server?"
date: 2011-09-19
forum: Server Platforms
---

### Post by ReturnPrivacy on 2011-09-19
Hi all,
I'm running Ubuntu 10.04, and tried to install Proftpd-basic and Gadmin-proftpd. I used software search for Proftpd, and it found it.(proftpd-basic) I installed it. I saw a tutorial that said to NOT use Ubuntu software center to get Gadmin-proftpd, and to download the "i386" file and install it. So I downloaded the file "gadmin-proftpd-dbg_0.4.2-1_i386.deb" and tried to install it. I got an error as it was installing saying "Error: Dependency is not satisfiable: gadmin-proftpd (=1:0.4.2-1) and it stops. What does this mean? Can anyone help me with this? Thank you.

---

### Post by ReturnPrivacy on 2011-09-19
Hi again,
I figured it out...kind of. I went in and uninstalled both proftpd and gadmin-proftpd, but that wasn't enough. I also had to remove ALL of the proftpd config files I found in /etc/ and anywhere else I found them, and there were ALOT of them. (I did a file search for anything that had proftpd in the name) Then I reinstalled proftpd and gadmin-proftpd and they installed.
Now if I can just get it figured out for my setup.
Thanks. You can call this one SOLVED (mostly)...LOL):P

---

