---
title: "Samba not appearing on Mac computers"
date: 2009-06-08
forum: Server Platforms
---

### Post by spinanicky on 2009-06-08
Hi guys, 

I have just redone our server at home (basically to stop everyone downloading at the same time and killing the internet).

Right now I am just trying to set up the samba side of things and I have it working nicely for windows. NAS appears in the network tab and I can connect and edit the folders/contents. 

However, for some reason it does not appear on my house mate's mac (there are 3 macs in the house and 1 pc). Yesterday it did appear in their network list but when they tried to open folders it simply said the original source could not be found. I have attached my samba config file and would greatly appreciate any help. 

Again keep in mind that its working fine under windows... just not on the macs.

Thanks!

**PLEASE SEE ATTACHED SMB.CONF FILE**

---

### Post by guilly on 2009-06-08
I have this issue with my MacBook as well sometimes. I find it's easier to go in Finder and select connect to server punch in your servers IP and your good to go.

---

### Post by spinanicky on 2009-06-08
That allows them to connect but then they still can't access the folders... it keeps saying it cant find the original folder or something similar

---

### Post by guilly on 2009-06-08
Oh ok, sorry I miss read your post.

When I get home tonight I can post my smb.conf for you to take a look at if you wish.

---

### Post by spinanicky on 2009-06-08
that would be great! thanks

---

### Post by guilly on 2009-06-08
sorry for the delay, 

here is my smb.conf and like i said i connect to my shares with a Macbook on a daily basis.

---

### Post by Interpreter on 2009-06-09
Hi there, just dropping this line real quick.

I not gonna say i know much about your issue, as i dont have a mac, nor does my flatmate.

One thing though, I was under the impression that samba per se is supposed to ease the sharing between one system (Linux, MAC, bananas) and Windows.

And as from how I understood it SAMBA does not try to ease the sharing btween linux and mac.

Possible that you guys are trying to eat soup with japanese stick so to say?
I may be a dumb moron though, off googling about its features...
oh have a nice one..

---

### Post by guilly on 2009-06-09
I believe it's quite the opposite. SAMBA is supposed to ease the sharing accross multiple platforms. I don't believe SAMBA is platform dependent.

anyone else have a say on this??

> **Interpreter said:**
> Hi there, just dropping this line real quick.

I not gonna say i know much about your issue, as i dont have a mac, nor does my flatmate.

One thing though, I was under the impression that samba per se is supposed to ease the sharing between one system (Linux, MAC, bananas) and Windows.

And as from how I understood it SAMBA does not try to ease the sharing btween linux and mac.

Possible that you guys are trying to eat soup with japanese stick so to say?
I may be a dumb moron though, off googling about its features...
oh have a nice one..

---

