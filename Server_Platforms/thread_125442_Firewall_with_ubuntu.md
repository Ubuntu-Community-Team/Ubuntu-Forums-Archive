---
title: "Firewall with ubuntu?"
date: 2006-02-03
forum: Server Platforms
---

### Post by iMac on 2006-02-03
I just switched to Linux, and I have a question. Should I use a firewall with Ubuntu? I am a basic user who will webserf, and use instant messenger. I am running Ubuntu on a ppc. I ran a ShieldsUP! test, and all my ports are shown as "stealthed". Should I still use a firewall?

---

### Post by hscottyh on 2006-02-03
If you are not behind a firewall (router) you should.

---

### Post by iMac on 2006-02-03
I have a router but it doesn't have a firewall

---

### Post by towsonu2003 on 2006-02-03
you can use firestarter. it is easy to configure tru its wizard and u wont have to worry about it once it's up (except opening ports when you need them) ```
sudo apt-get update
sudo apt-get install firestarter
```

PS. There is a great deal of previous forum threads about this, where ppl argue you won't need a firewall vs. ppl who argue firewall is a good tool to have as a 2nd layer of protection.

---

### Post by iMac on 2006-02-03
I just pasted the code into the termenal and it downloaded some things, what do I do next?

---

### Post by towsonu2003 on 2006-02-03
Before configuring, read its quick help / faq / manual page here: [http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)
Don't configure it without first reading that stuff. 

Find it in Applications>System tools>Firestarter. Run it once and it will show you a wizard. Use the wizard to configure the firewall. Make sure you have port 80 and port 443 open to outbound connections (one is http, other is https). Once done, it will sit on the top right corner of the screen during your session (but won't come up during the next session / boot, which is okay). From now on, if you cannot connect to some place, first think: "do I have the required port open in firestarter". 

In the next session, you won't see firestarter, but it is running in the background. check with ```
sudo /etc/firestarter/firestarter.sh status
```

---

### Post by iMac on 2006-02-04
Thanks So Much!

---

### Post by towsonu2003 on 2006-02-04
you're most welcome :)

---

