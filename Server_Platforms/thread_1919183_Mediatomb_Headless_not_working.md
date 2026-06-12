---
title: "Mediatomb Headless not working"
date: 2012-02-02
forum: Server Platforms
---

### Post by np123 on 2012-02-02
Hi,

So I have installed and configured mediatomb, opened a port on my firewall for it to run, and if i type sudo mediatomb in to the terminal via ssh it starts, and then I can see it on my Playstation and it works fine. As soon as i close the ssh window it shots off mediatomb. 

If I type sudo mediatomb -d it starts mediatomb but my ps3 cant see it.

Can anyone help me set mediatomb running in the background all the time even if im not logged in via ssh?

Its a headless server setup on 11.10 server edition.

Many thanks

---

### Post by volkswagner on 2012-02-02
Mediatomb should start on boot.

To restart try:

```
sudo service mediatomb restart
```



What is the output of:

```
ls -alt /etc/init.d/mediatomb
```

You should also see mediatomb in your rc scripts.

what is the output of:

```
ls /etc/rc2.d
```

---

