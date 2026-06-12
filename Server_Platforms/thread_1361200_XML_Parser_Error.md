---
title: "XML Parser Error"
date: 2009-12-21
forum: Server Platforms
---

### Post by humphreybc on 2009-12-21
I'm trying to set up my home server to use AjaXplorer, but recently I started getting errors like these:

Error parsing XML for user : TypeError: Cannot read property 'nodeValue' of null

When trying to access folders in AjaXplorer, or log in. I removed AjaXplorer and re-installed it and set up all my users etc again but the problem came back as soon as I tried to access one of my repositories that I had set up.

I read elsewhere that this may be caused by editing PHP/Apache files with the wrong editor... something to do with it using the wrong charset and adding 3 bytes to the start of the document. I have been using nano on my Ubuntu server to edit these files.

I just removed and purged lamp-server^ and then reinstalled it, but that didn't seem to fix anything. I don't want to re-install Ubuntu Server Edition on the server, I just did that yesterday.

What else can I try to reinstall/purge/reconfigure to get stuff back to default - if it *is* that wrong editor thing?

Very frustrating. Even if I do get this XML problem fixed, there is still the matter of the nasty [I/O 2038 error]("http://www.ajaxplorer.info/forum/search.php?PostBackAction=Search&Keywords=2038&Type=Topics&btnSubmit=Search") in PHP..

---

### Post by a9k3d on 2009-12-22
Check what the user and group are on the repositories you're having trouble with. Often setting www-data as group will help weird "read" errors. It could be that the whole file isn't getting opened.

---

### Post by humphreybc on 2009-12-22
Hi, thanks for your reply. Unfortunately time is of the essence and I just ended up reinstalling Ubuntu Server Edition on the Server, which fixed the problem.

It also fixed a number of other problems - so I'm fairly happy now :)

---

