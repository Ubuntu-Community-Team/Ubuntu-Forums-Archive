---
title: "SSH Security -- Someone is brute forcing me"
date: 2013-08-12
forum: Security
---

### Post by kr6511292 on 2013-08-12
So I setup a server from my Ubuntu 13.04 desktop.  The only traffic my router is setup to forward to the server is SSH, Apache, and Tomcat (22, 80, and 8080).  I setup key only ssh authorization and disabled root logins.  I have a couple questions.

To get putty to connect to my box with key's the guide I followed told me to disable PasswordAuthentication and UsePAM.  Disabling the first is fine, but it my server won't let me connect with keys if I disable UsePAM.  Why would this be?

Secondly, and most important is I can see from my logs all the user names the hacker/bot is trying to use.  The message is something like this

Received disconnect from *: 11: Bye Bye [preauth]

Does this mean my key only setup is working as expected and how can I further protect myself?

---

### Post by zealibib slaughter on 2013-08-12
If they are using the same ip address every time then you can use iptables to explicitly block all connections from that address.  Thats what I would do just to be safe.  As far as the key issue goes I've been having the same problem since 13.04, my server refuses my key.

---

### Post by lisati on 2013-08-12
One package that some of us have found useful in this kind of situation is *[fail2ban]("https://help.ubuntu.com/community/Fail2ban")*.

---

### Post by kpothi on 2013-08-14
While fail2ban is my recommendation too, fail2ban along with [ufw](https://wiki.ubuntu.com/UncomplicatedFirewall) may fit your requirement. If you have a static IP, then you may allow SSH connections only from your IP to your server, using UFW. Otherwise, you may use fail2ban that filters brute force attacks to some extend. Both ufw and fail2ban are highly configurable, like other Linux tools. So, you may explore both, when you get a chance.

---

### Post by Hungry Man on 2013-08-14
Iptables, Fail2ban, and port knocking might help you out.

---

### Post by Velnias on 2013-08-14
You doing it right ( key only authorization ), no need additional tweaks ( except for fun and cleaner logs ). 

However things may differ for Apache Tomcat.

---

### Post by sh4d0w808 on 2013-08-14
A little tweak: put your sshd to high port (above 1024). Of course, it will not prevent brute-force attacks from real attackers but prevents script-kiddie activities against your ssh and provides - as Velnias wrote - cleaner logs.

---

