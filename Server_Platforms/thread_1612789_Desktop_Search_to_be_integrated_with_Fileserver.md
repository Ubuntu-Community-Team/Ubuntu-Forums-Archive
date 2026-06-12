---
title: "Desktop Search to be integrated with Fileserver"
date: 2010-11-03
forum: Server Platforms
---

### Post by bkruggel on 2010-11-03
Hello!

I have a fileserver running Debian Lenny and multiple Ubuntu workstations in the same network.
The fileserver contains a lot of documents, which are searchable from every client machine through Beagle.
So there is a Beagle instace running on the server, and all workstations have Beagle installed independently.

When a user searches for something on his local machine, the Beagle Search Tool would show *local* as well as *remote* results in the same window, and the remote results would be clickable just as if it was a local file. Although the whole thing is a little buggy and experimental, it works quite well.

Now that Ubuntu Maverick has dropped Beagle support, I would like to know if there is another, newer Search Tool that supports such a networking structure.
The normally available feature is to be able to search NFS or SAMBA shares - this is not what I want, since I want one centralized search server, whose search results would be integrated into every workstations' local search results. With 10 workstations in the network, having always to search through every share individually would augment traffic in an incredible way and waste 10 times more computing resources than the old solution.

Edit:
I have finally found Pinot, but it is not installable from the repositories, due to a conflict of its dependency libtextcat-data with OpenOffice. Is this on purpose or a bug? As well, from what I can see, Desktop integration for Pinot is pretty weak.
Google Desktop would be another possibility (although I don't like Google stuff for multiple reasons) - I have found some howto's on how to hack it in order to be able to access the webinterface from different computers. Does anybody know anything about how to rewrite the paths so that a user could click on an item on the remote server and then have it open directly on his computer? (The files on the server are on /external, while they would be locally mounted as /media/server)

Thanks for your help,
Björn

---

### Post by bkruggel on 2010-11-14
Bouncing this as I see that I'm not the only one with this problem. Maybe someone has an idea?

---

### Post by bkruggel on 2011-01-15
Let's try another bump. I can't believe I'm the only one.

---

### Post by bkruggel on 2011-01-15
Let's try another bump. I know I'm not the only one.

---

### Post by TankEnMate on 2011-05-10
I'm sure you aren't the only one, I would like such a feature myself to prevent NFS spamming from multiple workstations.

---

### Post by Lars Noodén on 2011-05-10
The other four are [Strigi](http://strigi.sourceforge.net/), [Tracker](http://projects.gnome.org/tracker/), [Recoll](http://www.lesbonscomptes.com/recoll/), and [Pinot](http://pinot.berlios.de/).

---

### Post by bkruggel on 2011-09-13
Alright. This came up again recently, because we were discussing VPN access. One request was document searching on netbooks through VPN on a mobile broadband (maybe even GPRS) connection (short: forget Tracker).

Solution:

Recoll permits relatively easy management of external indexes. So what we can do is install Recoll on the server, have different indexes updated for each user through cron (or restart), have these indexes saved in the user directories and then access the index from the user's machine by NFS.
It's still not as elegant as Beagle was (there, the actual search happened on the server and only the results were sent to the client), but well. Even their website shut down now.

The only problem I see is that there is no path rewriting (the document lies on the server at /extern/user/ but on the nfs share of the networked machine on /media/servername/user). But ln -s does work for that.
Maybe someone has an idea?

I am also wondering, since Recoll is based on Xapian and makes Xapian databases, if it might be possible to simply point Omega to that database and that way have a web-frontend (for Windows and Android users). Any ideas/experiences? EDIT: simply pointing it there didn't work. Omega seems to be able to do /something/ with the index (it mentions the number of documents to be searched), but searching the index won't give any results. Not sure if having two indexes is worth the trouble...

---

