---
title: "My Servers time keeps resetting to Jan. 2002 on restart"
date: 2007-04-12
forum: Server Platforms
---

### Post by Skeletor on 2007-04-12
Hi All,
  I followed the instructions on the Perfect Setup tutorial to setup my Ubuntu 6.10 Server LAMP box:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p7](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p7)

I tried to add this time synchronization:
"
17 Synchronize the System Clock

It is a good idea to synchronize the system clock with an NTP (network time protocol) server over the internet. Simply run

apt-get install ntp ntpdate

and your system time will always be in sync. 
"

I was able to install this NTP, but when I ran it it could not find any server to synchronize against.  I noticed that it reset my system time to Jan. 2002 (which is incorrect.)  I uninstall ntp, ntpdate using apt-get remove from root, but every time I restart my server the time on it gets reset to Jan. 2002.  

Any advice on how to fix this?  I'm not sure if there is some startup script that "ntp" modified that now fails and sets the server time to some default.  How can I diagnose and fix this problem without reinstalling all the software on my server?  I'm about ready to reinstall all the software because this time/date problem is driving me nuts.  But I want to learn more about Ubuntu and Linux in general and fix the problem the smart way, even if it is a lot more work.

Thanks for any help you can provide.

---

### Post by Skeletor on 2007-04-12
ok, I kind of fixed my own problem.  There is something about posting a question that makes me start looking for solutions:

[http://www.defcon1.org/html/Software_Articles/Soft-Updates/System-Clock/system-clock.html](http://www.defcon1.org/html/Software_Articles/Soft-Updates/System-Clock/system-clock.html)

Has the info I needed to synch my system clock correctly.

---

