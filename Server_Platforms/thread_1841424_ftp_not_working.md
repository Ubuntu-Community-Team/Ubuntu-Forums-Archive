---
title: "ftp not working"
date: 2011-09-09
forum: Server Platforms
---

### Post by flewfruit on 2011-09-09
Hi, i'm using ubuntu 10.10 on my vps. Apache2, mysql ,phpmyadmin is installed.

I tried to install ehcp but I didn't like it so i tried to remove it via apt-get remove ehcp, but it wasn't working, so i don't care about it^^.

ehcp has automatically deinstalled proftpd and installed vsftpd. I removed vsftpd and reinstalled proftpd again, the strange thing, I can't connect to my server-
> [L] **error: 10054:**so I deinstalled proftpd again and installed vsftpd again, ftp is working :lolflag:
but i don't know my user data so I can't connect, also not by creating a new user by "adduser mynewusername", always 530 login incorrect.

So what can I do that ftp is working with proftpd? In the moment I have installed proftpd again.

please help me to fix this because i'm getting sick of this shitty problem. never had this problem, but i don't have time to reinstall my o.s, i must do this very quick.

cheers

---

### Post by Entilza on 2011-09-09
You lost me.. proftpd is installed... You don't know any usernames so you tried to create a new user but ftp is still not allowing those new ussers you created?

Make sure the user is setup correctly by either sshing to the machine as that user or logging in through console.

Check any /var/log/proftpd/ logs when trying to connect.

---

### Post by flewfruit on 2011-09-09
> **Entilza said:**
> You lost me.. proftpd is installed... You don't know any usernames so you tried to create a new user but ftp is still not allowing those new ussers you created?

Make sure the user is setup correctly by either sshing to the machine as that user or logging in through console.

Check any /var/log/proftpd/ logs when trying to connect.
Hi, yes exactly. It is not allowing any users because I can't connect  : [B]error: 10054.

But with vsftdp I can connect but the login is always incorrect, also when I create a new user.
[/B]

---

### Post by Entilza on 2011-09-09
Well stick with one ftpd program for now, stay with proftpd.

Can you ftp locally from the server to itself?  ftp locahost

It sounds like this error is from a windows PC to the server is not working?  It could be firewall.

---

### Post by flewfruit on 2011-09-09
> **Entilza said:**
> Well stick with one ftpd program for now, stay with proftpd.

Can you ftp locally from the server to itself?  ftp locahost

It sounds like this error is from a windows PC to the server is not working?  It could be firewall.
I tested it on 2 pcs, not on any of them working.

I hope i get this today to work, if not i have to reinstall o.s :( :(

---

### Post by Entilza on 2011-09-09
1.  ssh to your server
2.  ftp localhost
3   login as one of the users you created or know the password to.

Does that work?

---

### Post by flewfruit on 2011-09-09
it says unkown host. and yes, I'm root.

---

### Post by Entilza on 2011-09-09
Ok now try,

ftp 127.0.0.1 

you should have localhost defined in /etc/hosts

---

### Post by flewfruit on 2011-09-09
> **Entilza said:**
> Ok now try,

ftp 127.0.0.1 

you should have localhost defined in /etc/hosts
 ftp 127.0.0.1  works but login is incorrect :/

---

### Post by Entilza on 2011-09-09
Ok so it's time to check some logs as mentioned above.

Let's see the last few lines in

/var/log/proftpd/proftpd.log

---

### Post by flewfruit on 2011-09-09
[QUOTE=Entilza;11234907]Ok so it's time to check some logs as mentioned above.

always the same: [http://img97.imageshack.us/img97/6861/screenshot1uz.png](http://img97.imageshack.us/img97/6861/screenshot1uz.png)

it says login successfull but i couldn't login.

---

### Post by Entilza on 2011-09-09
What does the ftp client report after you enter password?

Does it say "user" logged in?

Also your date is wrong on your server :)

---

### Post by flewfruit on 2011-09-09
i can't enter a pw man. it's not avaible?

---

### Post by Entilza on 2011-09-09
So you didn't create a user named "user" ? as shown in the log screenshot?

after you type ftp 127.0.0.1  what does it say?

---

### Post by Entilza on 2011-09-09
Do you have some sort of auto login setup?

try "ftp -n 127.0.0.1"

It should say connected to protftpd etc etc..

ftp> 

type "user" <enter>
You will be promtped for a user name, put the username you added <enter>

then you will be prompted for a password
type the password <enter>

---

### Post by flewfruit on 2011-09-09
hi, its working now. thanks for helping me :guitar:

---

