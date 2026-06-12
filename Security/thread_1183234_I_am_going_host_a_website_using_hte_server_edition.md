---
title: "I am going host a website using hte server edition, are there free antivirus for it?"
date: 2009-06-09
forum: Security
---

### Post by siyangqiu on 2009-06-09
I am going to use the ubuntu server edition to host a website. That means I will need some security. Which free antivirus and firewall should i use? Are there any? and how do i use it since i am not familiar with only the command line.

---

### Post by linux_lover69 on 2009-06-09
Firestarter for firewall. Thats what I'v been using for my site. And sorry I'd tell you how to use it through the command line, but I don't know how. Because I turned the desktop edition into a server.

---

### Post by iwc5893 on 2009-06-10
I did the same thing not too long ago, and followed the "Perfect Server" guidelines at [http://www.howtoforge.com/](http://www.howtoforge.com/)

It will walk you through the steps of setting up ClamAV and spamassassin as part of the installation.

---

### Post by cariboo on 2009-06-10
If you aren't running a mail server, there is no need for spamassassian or an anti-virus app.

You would be better off reading the security links in this [sticky]("http:///ubuntuforums.org/showthread.php?t=1046738").

---

### Post by DGortze380 on 2009-06-11
Really no need for anti-virus on a Linux Web Server.
Your firewall is IPTables: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Jekshadow on 2009-06-13
You already have a firewall preinstalled (iptables) and if you are not interacting with Windows clients, you do not have to worry about an anti-virus. And about the command line, heres a few commands to start you off. Google anything else.

[LIST]
[*]ls - List all files/directories within the current directory
[*]mv - move (usage: mv [file location] [file destination]
[*]cp - copy (usage: cp [file location] [copied file location])
[*]rm - delete (usage: rm [file] or rm -rf [directory])
[*]sudo - give yourself temp root privilages (usage: sudo [command])
[*]apt-get install - installation (usage: sudo apt-get install [package to be installed])
[*]apt-get remove - the opposite of the above, same usage
[*]mkdir - create a directory
[*]rmdir - remove a directory
[/LIST]

---

