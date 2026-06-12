---
title: "[SOLVED] &amp;quot;HOW&amp;quot; Block a Big List of IP Ranges With IPtables"
date: 2008-05-17
forum: Security
---

### Post by HunterThomson on 2008-05-17
I would like to use the blocklists from [http://www.bluetack.co.uk](http://www.bluetack.co.uk) or other web sights in iptables. Is there a way to use a .txt of IP ranges in iptables? Or what would I have to do? I could maybe write a perl script to extract out all the text or extract out just the iptables to make a new list with no words..... Have any ideas or is there a thread about this that I have just not found? I would be thankful for any help.

---

### Post by yomaoni on 2008-05-17
you might want to look at a program called iplist

[http://sourceforge.net/projects/iplist](http://sourceforge.net/projects/iplist)

might help you.

---

### Post by HunterThomson on 2008-05-17
> **yomaoni said:**
> you might want to look at a program called iplist

[http://sourceforge.net/projects/iplist](http://sourceforge.net/projects/iplist)

might help you.

Cool I installed the 64AMD Gusty .deb and installed. Looks like exactly what I was looking for:) However, I installed it and the two dependency's and restarted. BUT, when I try to start the program it asks me for my password and  I type it in but then it doesn't start, nothing happens??? I am in KDE maybe it will work if I boot up into Gnome. I'll mess around and get it to work. Thank you though. I see no reason why I should allow the DOD or known cracker IP's to connect to my computer. Just one more layer of protection.

---

### Post by yomaoni on 2008-05-17
Indeed,  I found this about a month ago and tested it on a machine with a public and it was interesting to see what could not connect and what could.  Anyways you might look at the IP tables listing, it has some interseting stuff in there.  

Have fun.

---

