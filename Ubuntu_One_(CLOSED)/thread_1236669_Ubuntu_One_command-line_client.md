---
title: "Ubuntu One command-line client"
date: 2009-08-10
forum: Ubuntu One (CLOSED)
---

### Post by pytheas22 on 2009-08-10
I've been playing with Ubuntu One lately and it's pretty nice, but I'm wondering if it has a command-line client for use on systems with no web browser installed.  It would be cool if I could access shared files from headless servers.  Any ideas?

---

### Post by bacardiandwatermelon on 2009-08-10
Ubuntu One looks interesting.. Haven't heard of it before... Is it secure? But in regards to the shares.. Wouldn't samba work? Or am I missing something?

---

### Post by pytheas22 on 2009-08-10
> Ubuntu One looks interesting.. Haven't heard of it before... Is it secure? But in regards to the shares.. Wouldn't samba work? Or am I missing something?

Ubuntu One lets you share files between Ubuntu computers no matter where they're located, so it does more than samba, which is only realistic for computers on the same local network.  I think I read that the data transfers are encrypted, so barring any other vulnerabilities, it should be secure.

It will be included by default in Ubuntu 9.10 under the Applications>Internet menu.

If only I could find a CLI client for it...

---

### Post by Yvan300 on 2009-08-10
Hmmm drop box is quite better imo, and also ubuntu one is only for jaunty at the moment.

---

### Post by juancarlospaco on 2009-08-11
> **Yvan300 said:**
> Hmmm drop box is quite better imo

Until you get sniffed and your data stoled.
:) *UbuntuOne is encrypted, so its not better.*

---

### Post by pytheas22 on 2009-08-11
> Until you get sniffed and your data stoled.
UbuntuOne is encrypted, so its not better.

Are you sure Dropbox data transfers over the network aren't encrypted?  I thought they were.

---

### Post by Yvan300 on 2009-08-12
I as well.

---

### Post by juancarlospaco on 2009-08-12
> **pytheas22 said:**
> Are you sure Dropbox data transfers over the network aren't encrypted?  I thought they were.

No.
Is not encrypted really.

*i got your filesss mmmuahahaaaahaaaa* :P

---

### Post by pytheas22 on 2009-08-13
> **juancarlospaco said:**
> No.
Is not encrypted really.

*i got your filesss mmmuahahaaaahaaaa* :P

I don't want to start an argument and I have no particular attachment to Dropbox (I've never used it myself), but are you *sure*?  [According to softpedia]("http://www.softpedia.com/reviews/windows/Dropbox-Review-105200.shtml"):
> 
all files are transported over SSL

Have you seen evidence that this is not the case?  I'm just curious (and also interested in possibly writing a review of Ubuntu One, and want to know its strengths and weaknesses vs. similar tools).

---

### Post by juancarlospaco on 2009-08-13
Yep, i sucessfully sniffed DropBox files, over the network with [Wireshark]("apt:/wireshark") and [Driftnet]("apt:/driftnet")

BTW on these review say that FTP is secure, and actually is not.
:)

---

