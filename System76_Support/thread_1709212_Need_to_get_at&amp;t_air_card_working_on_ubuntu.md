---
title: "Need to get at&amp;t air card working on ubuntu"
date: 2011-03-17
forum: System76 Support
---

### Post by anthonykudolo@yahoo.com on 2011-03-17
I have recently purchases a  AT&T E1815 Broadband Air Card so I can access the internet. From the start it was giving me problems with my Linux System. So i got the card set up on my sister windows system and put time on it. I called AT&T tech support and they gave me some instructions to get it operational. However after creating all necessary file i continued to get a "Permission Denied" statement upon typing the execution command in terminal.

I was told to create 3 files in  **/etc/ppp/peers/**  Folder.

[B]gprs
gprs-connect-chat
gps-disconnect-chat[/B]

Then execute **/usr/sbin/pppd call gprs**  In terminal to run the AT&T Air Card. But i get permission Denied.

How do I fix this and run the software and get online???

---

### Post by Cpierce on 2011-03-17
Try this, I had the same issue. The problem was that I had too many things entered. Just follow the info at the end of this:

[http://ubuntuforums.org/showthread.php?t=1537947](http://ubuntuforums.org/showthread.php?t=1537947)

Sure hope it helps

---

### Post by anthonykudolo@yahoo.com on 2011-03-17
I have nothing entered. It just seems like i need to turn something off or on to the command will work. /usr/sbin/pppd call gprs    (is the command and it should activate the software and run the card.

But Thank You so much for replying so fast. I appreciate it.

---

### Post by isantop on 2011-03-18
Have you tried running the command like this:

```
sudo /usr/sbin/pppd call gprs
```

---

