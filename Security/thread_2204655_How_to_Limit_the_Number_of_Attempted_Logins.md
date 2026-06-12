---
title: "How to Limit the Number of Attempted Logins"
date: 2014-02-09
forum: Security
---

### Post by richard30 on 2014-02-09
This question has probably been asked a gazillion times, but the answer seems to change with subsequent versions of Ubuntu. I'm using "Lucid" Server and I would like to know how to limit the number of attempted logins before I lock out the user for a set period of time. Thanks.

(BTW, why isn't this a **standard** feature of Linux??? I'm really puzzled.)

---

### Post by thnewguy on 2014-02-09
There are a few ways to block login attempts after a certain number of failed signins. One is to run the denyhosts daemon. This program monitors secure shell connections and blocks IP addresses that fail to login a given number of times. Another way is to turn on your firewall and set the port secure shell is on to limit connection attempts. This doesn't actually prevent people from trying to login again, it just slows them down, making brute-forcing a password impractical. Runng the following commands should do the trick.

```

sudo ufw limit 22/tcp
sudo ufw enable

```

There are other ways to accomplish this, but these are the easiest. As to why blocking logins isn't enabled by default, there are two reasons. 1. It is too easy for a new administrator to lock themselves out of their own computer. Or, for that matter, for any user to lock themselves out. Legitimate users constantly mistype passwords and unlocking their accounts is a hassle. 2. Blocking login attempts makes it easy for attackers to perform a DoS attack against you. If you block failed login attempts and someone attempts to login as you (and fails) then you (the legitimate user) cannot login either. Remember, blocking login attempts can keep out the good users as well as the bad.

---

### Post by fugu2 on 2014-02-09
you should [Favorite Search Engine] for fail2ban. It's great at limiting remote login attempts, espically for ssh. If you setup the ssh server without passwords (e.g. using RSA keys only), you will have even less chance that someone can guess their way in.

---

