---
title: "ubuntu firewall"
date: 2009-03-08
forum: Security
---

### Post by itlarson on 2009-03-08
if you type "Ubuntu firewall"  into Google the first two results say there is no firewall on Ubuntu.  Am I correct in my understanding that this is old info, and that Ubuntu has iptables running in the background by default?

---

### Post by kevdog on 2009-03-08
iptables/netfilter is running in the background, however by default there are no firewall rules other than to accept all incoming/outgoing/forwarding connections.  This may sound dangerous, however by default there are no listening processes or servers.

---

### Post by itlarson on 2009-03-08
So do I have to set anything?  I'm only doing stuff like web browsing, music streams, bit torrent and flash player.

---

### Post by kevdog on 2009-03-08
That's an open ended question.  Depends how you access your security risk.  To use all of those programs by default, nothing will be blocked by the firewall -- they will all function.  If you need to restrict access however (ie in a torrent like application), you may want to set up a few iptables rule.  It really just depends.

---

### Post by ushills on 2009-03-09
I find ufw configured through gufw really simply and easy to create rules.

---

### Post by byStanderone on 2009-03-09
...have been using firestarter as gui for the iptables. works fine and user friendly...after a few minutes of orientation.

---

### Post by lovinglinux on 2009-03-09
Since you use torrent which require an open port to listen to, I would recommend using [moblock]("http://ubuntuforums.org/showthread.php?t=803183") (ip blocklist) plus Firestarter or UFW. If you are willing to learn iptables commands, then you can disable Firestarter/UFW and use the built-in scripts from [moblock]("http://ubuntuforums.org/showthread.php?t=803183") to create the iptables rules.

Six months ago, when I started with Linux, the whole iptables were too scary. But now I'm running my own rules using [moblock]("http://ubuntuforums.org/showthread.php?t=803183") scripts an it works like a charm.

---

### Post by itlarson on 2009-03-09
Is there somewhere where I can find out what rules to create and how to create them?  I installed firestarter, but don't know what to do with it.

---

### Post by OrangeCrate on 2009-03-09
> **itlarson said:**
> Is there somewhere where I can find out what rules to create and how to create them?  I installed firestarter, but don't know what to do with it.

Here are links to two sources that should answer any questions you might have...

Configuring Firestarter:

[http://books.google.com/books?id=M66WOfYoULYC&pg=PA180&lpg=PA180&dq=configure+firestarter&source=web&ots=aTj1xQZB1l&sig=hIRWRbp_JUQiHx5YTxnPa8TAGp0&hl=en&sa=X&oi=book_result&resnum=9&ct=result](http://books.google.com/books?id=M66WOfYoULYC&pg=PA180&lpg=PA180&dq=configure+firestarter&source=web&ots=aTj1xQZB1l&sig=hIRWRbp_JUQiHx5YTxnPa8TAGp0&hl=en&sa=X&oi=book_result&resnum=9&ct=result)

Firestarter documentation:

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by bodhi.zazen on 2009-03-09
And for ufw :

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

and iptables 

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

If you are looking for a GUI, I suggest gufw and / or guarddog.

guarddog has excellent built in help.

---

### Post by itlarson on 2009-03-09
Thanks.

---

