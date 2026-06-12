---
title: "Do repositorys  go 'offline'?"
date: 2005-11-24
forum: Repositories &amp; Backports
---

### Post by Paul Casey on 2005-11-24
Does it happen that repositories go down, or become temp. not available because of network or otherwise?  My repository list was working fine. Then, with no changes to it (that I'm aware of) it becomes unable to connect.  Does this happen to others?  (otherwise the network connection is ok and internet, such as this forum are reachable)

--------------------------------------
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
--------------------------------------------------------------

---

### Post by carlosqueso on 2005-11-24
I had the same problem, maybe the server is acting stupid and there's no one to fix it because it's thanksgiving in the US?

---

### Post by Xian on 2005-11-24
The US mirrors have for some reason had a history of failures. If it were my box I would edit the /etc/apt/sources.list file and delete the 'us' prefix from the listed repos, leaving you with 'archive.ubuntu.com'.

---

### Post by carlosqueso on 2005-11-24
Beautiful....thanks for the help xian.  Now if I could just use "apt-get beer" and it'd work....

---

### Post by simon.schmidt on 2005-11-24
well, at least you can "apt-get moo"

---

### Post by az on 2005-11-24
It would be interesting to see the ammount of bandwidth these ubuntu repositories move.

---

### Post by aysiu on 2005-11-24
The us.archive.ubuntu.com repositories have been giving people trouble.
Look at the first link in my sig.

---

### Post by Paul Casey on 2005-11-27
thanks for the help.  will try the edit of us out of the listings.  thanks to all.

---

### Post by Paul Casey on 2005-11-27
[QUOTE=azz]It would be interesting to see the ammount of bandwidth these ubuntu repositories move.[/QUOTE]
 
That would be interesting... It'd be great to see a chart page where we could see growth of Ubuntu network traffic.   Something besides the counter on Distrowatch.

---

### Post by dudus on 2005-11-27
The repos in brazil 'br.archive.ubuntu.com' and so on are down now and then. I think it's not a metter of trafic at all

---

