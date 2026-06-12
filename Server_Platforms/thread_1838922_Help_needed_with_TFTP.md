---
title: "Help needed with TFTP"
date: 2011-09-04
forum: Server Platforms
---

### Post by wolfgangmcq on 2011-09-04
I am trying to install Ubuntu over a network with TFTP. The idea is that you can just boot a computer, hit F2 or whatever, and Ubuntu gets installed automagically, along with a bunch of custom configuration files. I found several tutorials on the Internet, explaining how to do this. None of them work. I am having the exact same problem every time: TFTP *just **won't** work!*

More specifically: TFTP runs fine, no errors, I can see it running when I pgrep it, but when I run a port scan on the computer, TFTP doesn't appear in the list. I have tried this with at least 3 different TFTP servers, 3 or 4 configurations each, and several tutorials, on 2 different computers (both IBM Thinkcentres running Ubuntu Maverick, if that helps) with **exactly** the same problem. I have tried seeing if it's a firewall problem--no luck. First, all the other ports that I use work just fine. Second, I even tried twiddling with ufw to see if that was the problem, and it *still* didn't work.

I have gone looking all over the Net to find a solution, and I'm just about at the end of my rope! I'm pretty good at fixing computer problems, even really weird ones, but this one's got me mystified. I've been trying different things for several months, on and off, and I really need to get this working.

Thank you in advance for your help.

---

### Post by konsole on 2011-09-05
If you can pgrep tftpd but not scan it then you're either not using udp to scan or your firewall is blocking it.

You need to be able to regularly transfer files with a tftp client before you move onto any of the pxe stuff.

---

### Post by wolfgangmcq on 2011-09-06
I know I need TFTP--that's where I'm getting stuck. Why won't TFTP appear when I run a port scan?

---

### Post by wolfgangmcq on 2011-09-15
Perhaps I should clarify. The problem is more with TFTP than network booting. I have tried several TFTP servers, and all exhibit the same problem: they appear to be running just fine, but they cannot be accessed at all, and the port does not appear in a port scan. I am having this problem with no other server.

---

