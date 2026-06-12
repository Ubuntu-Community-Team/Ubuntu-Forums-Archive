---
title: "Building a future - proof mail server on 12.04"
date: 2012-12-08
forum: Server Platforms
---

### Post by petarpetrovic on 2012-12-08
Hi there,

I have a spare VPS Linode box and I would like to turn it into a mail server. I would like to run Postfix + Dovecot + Managesieve + MySQL virtual users stack. I've found some good tutorials about setting up a mail server on 12.04 and that's fine. However, I want to ask more experienced people whether it is safe to actually use Ubuntu as the OS of choice. Namely, I want to be sure that when I upgrade my server to the next LTS release, my mail server will continue to work flawlessly. I am not a professional sysadmin, therefore I don't know how to troubleshoot very much, but I can follow step by step tutorials on just about anything. I would say that I am an intermediate Linux user.

For example, when Dovecot got updated from 1.x to 2.x, a whole bunch of things got changed. So, if I choose to run a mail server on Ubuntu today, is there a way to be sure that it will work in future versions of Ubuntu? Is it really that hard to troubleshoot issues when you do an upgrade? Email is kind of critical for me and I would really like to host email myself, if only as a hobby and something to do in my spare time (I enjoy being in the terminal, to be honest).

---

### Post by Vegan on 2012-12-08
no such thing as future proof

i suggest using a virtual machine for your mail appliance so that when it needs to be changed to a new appliance then simply create a new virtual machine.

i run my own private cloud, linux is a useful tool in that field.

---

### Post by sandyd on 2012-12-09
> **petarpetrovic said:**
> Hi there,

I have a spare VPS Linode box and I would like to turn it into a mail server. I would like to run Postfix + Dovecot + Managesieve + MySQL virtual users stack. I've found some good tutorials about setting up a mail server on 12.04 and that's fine. However, I want to ask more experienced people whether it is safe to actually use Ubuntu as the OS of choice. Namely, I want to be sure that when I upgrade my server to the next LTS release, my mail server will continue to work flawlessly. I am not a professional sysadmin, therefore I don't know how to troubleshoot very much, but I can follow step by step tutorials on just about anything. I would say that I am an intermediate Linux user.

For example, when Dovecot got updated from 1.x to 2.x, a whole bunch of things got changed. So, if I choose to run a mail server on Ubuntu today, is there a way to be sure that it will work in future versions of Ubuntu? Is it really that hard to troubleshoot issues when you do an upgrade? Email is kind of critical for me and I would really like to host email myself, if only as a hobby and something to do in my spare time (I enjoy being in the terminal, to be honest).
+1 to nothing is future proof

You can also use a enterprise mailserver package such as Zimbra or Axigen. Those provide upgrade instructions, along with changelogs and everything. iRedMail is pretty good as well, but is just a set of scripts to manage a mailserver.

---

