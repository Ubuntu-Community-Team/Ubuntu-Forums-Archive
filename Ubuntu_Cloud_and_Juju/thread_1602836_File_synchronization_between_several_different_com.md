---
title: "File synchronization between several different computers"
date: 2010-10-21
forum: Ubuntu Cloud and Juju
---

### Post by Sergii on 2010-10-21
Hi guys,

I would like to ask you one question. Imagine there are several computers, all running different OS (say, windows, mac and Linux). I have one single bunch of my data, which I want to keep synchronized on all of these computers. I'm working periodically on all computers, each time changing my data. I want the changes I make to happen immediately (or almost immediately) on other computers. 

Question: Is it possible to do so?

The complications:
- The data are large, ~ 100 GB (but the changes are small, so not much to copy at once
- All computers has dynamic IP, One of them is a notebook, so may be connected in hotel, cafe or airport.
- I have no central server, where I can keep the data and access to them from outside.
- The solution must be free, open-source and if possible secure.

What I've tried:
- Ubuntu One will not help - just not enough space even for paid version. And as I understand, It can't do synchronization between computers, not having the copy on Ubuntu servers
- Other commercial services has similar limitations.
- p2p solution - i've found only Tonido, but it has no x86-64 version, so I can't use it.
- Usual synchronization software doesn't work when you have dynamic ip (of course, I can figure out some crazy way to send IP by e-mail and so on, but it is not very elegant solution)


Thank you very much in advance for help

---

### Post by kim0 on 2010-10-22
Dropbox works great [http://www.dropbox.com/pricing](http://www.dropbox.com/pricing)
Win/Mac/Linux/Mobile/Web
Might be worth paying for in your case

---

### Post by Sergii on 2010-10-22
Thank you very much for suggestion. However, I've tried Dropbox, and it has a number of limitations: It stores my data on its own server, and the space is limited. Even paid version don't solve this problem.

I was thinking about something like "personal torrent", where my shared data are limited only with size of my hard drives.

---

### Post by kim0 on 2010-10-25
This may be promising [http://sparkleshare.org/](http://sparkleshare.org/)
Linux only for now though

Another solution unison might be worth a look, might need some work though [http://old.masker.net/2008/02/synchronize-a-folder-across-machines-over-the-internet-mac-pc-whatever](http://old.masker.net/2008/02/synchronize-a-folder-across-machines-over-the-internet-mac-pc-whatever)

---

