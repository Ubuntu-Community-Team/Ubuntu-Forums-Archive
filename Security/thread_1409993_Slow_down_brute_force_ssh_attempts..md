---
title: "Slow down brute force ssh attempts."
date: 2010-02-18
forum: Security
---

### Post by eldaria on 2010-02-18
Hello, 

I have noticed a lot of brute force login attempts on my server.
And was wondering if ssh has a possibility of slowing down connections.
I don't want to block on iptables since I only want to block failed attempts.

I used to have a router, that if your failed your login, it would let you type your username again, but it would wait with the password prompt for 1 minute, and if you failed again it became 2 minutes, 4 minutes, etc, basicaly doubling the time everytime you failed.
Is it possible to make something similair with sshd?

Regards.
Brian

---

### Post by scottuss on 2010-02-18
Fail2ban is really good, it blocks IPs that attempt to make too many incorrect log ins.
[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

Also, one trick that I always find stops the casual snoopers and bots, change your port from 22 to something really high

---

### Post by eldaria on 2010-02-18
> **scottuss said:**
> Fail2ban is really good, it blocks IPs that attempt to make too many incorrect log ins.
[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

Also, one trick that I always find stops the casual snoopers and bots, change your port from 22 to something really high


Installed fail2ban, will give it a try.

Changing the port is not an option since I sometimes use it for tunneling where only ssh is allowed.

Thanks for the tip,

---

### Post by bodhi.zazen on 2010-02-18
You can use denyhosts, fail2ban, or a few rules to iptables. You may need to watch the number of attempts if you are doing file transfers, for example scp, svn+ssh, etc.

---

