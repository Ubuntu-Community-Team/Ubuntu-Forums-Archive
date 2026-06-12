---
title: "localhost does not respond"
date: 2007-12-26
forum: Server Platforms
---

### Post by Veloteuton63 on 2007-12-26
Hi,
I set up a XAMPP configuration on my laptop (IBM thinkpad T41), running the latest XUBUNTU. The Installation went flawless. starting up the XAMPP components proceeds without any error messages, i.e. APACHE, MYSQL, PHP, FTP start running w/o any failure message.
The problem: calling localhost in my webbrowser only yields a timeout message after a certain while.
Pinging localhost (or 127.0.0.1 or 127.0.1.1 and so on) does not work, i.e. no packages returned.
I'm completely lost on this and the problem starts to get urgent for me, so if anyone has any ideas
btw.: I run the same set-up (xampp on Ubuntu on two other machines (Desktop computers w/o problem)

---

### Post by conjur3r on 2007-12-27
Can you copy/paste the following output:

# ip a

And see if you have a firewall running

# sudo iptables -L

---

