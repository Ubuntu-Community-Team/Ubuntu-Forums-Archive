---
title: "connect to vmware (pc) install on ubuntu"
date: 2008-03-27
forum: Server Platforms
---

### Post by Rick Z on 2008-03-27
Hi community,

I have installed Vmare on ubuntu.  How can I connect to the vmware (computers windows 2003 server, xp, xubuntu)?

current ubuntu ip is 192.168.0.x

vmware pc ip is 172.16.139.x

On the vmware I used the nat.  Should I use the bridge configuration?  If I have to use the bridge configuration, how do I make it to talk to my ubuntu pc or vmware to vmware pcs?

Thanks

---

### Post by adityakavoor on 2008-03-27
best way to share is by installing samba

Follow [this]("http://www.youtube.com/watch?v=Ad17kma8rNM")

Right click on the folder you want to share and select Windows share.

If you want to share the whole harddisk then share the /media folder.

Now boot Windows.

Start -> Run 

type :

```
\\<ubuntuip>
```

PS: remember \\ is very important.

---

### Post by Rick Z on 2008-03-27
Thank you for your reply... I think my problem is that I can't pinging to the vmware pc...

---

