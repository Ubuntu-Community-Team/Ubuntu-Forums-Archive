---
title: "Do I need an outbound firewall to keep my files from appearing on the internet?"
date: 2011-07-23
forum: Security
---

### Post by chazinams on 2011-07-23
I'm new to computers and don't yet understand how to be secure.

What should I do to keep important files on my computer from being uploaded to the internet? Don't I need an outbound firewall to prevent this?

What causes my computer to send an outbound request to the internet that would result in files being uploaded from my computer onto the internet? I'm afraid to put anything of importance (like reports that I've written for work) onto a computer with internet access because I don't want them to be uploaded to the internet. I wouldn't upload them on purpose obviously, but I'm afraid it would happen without my knowledge because I don't know what I'm doing.

---

### Post by jramshu on 2011-07-23
By default all ports are closed in Ubuntu. Unless you tell it to, it's not sending 'out' anything, such as files and such.

---

### Post by The Cog on 2011-07-23
The main thing is not to install a server on your computer. Ubuntu will not upload your files on its own. The danger is of someone managing to gain control over your computer and have it send the information. There are basically two ways they can gain control:

Firstly by connecting to a service that your computer is running and using that to get the computer to do things. This can't happen with a default Ubuntu install because there are no services running that accept connections. If you do install services (SSH server or web server for instance), make sure all your user passwords are good, and keep up to date on patches. One that catches lots of people out is the remote desktop. Don't change your settings to allow remote desktop access.

Secondly by running programs yourself that do naughty things. You should only ever install software from trusted sources (The Ubuntu repositories should be all you need). Some document viewing programs can be tricked into doing unwanted things by documents (images, PDF files etc) that are carefully made to exploit bugs in the viewers, so again keep up to date on security patches. And don't open attachments in unexpected emails.

This should be enough to remain reasonably secure. But also look at the security sticky threads at the top of this forum. There is sooo much good info in them.

---

### Post by Thewhistlingwind on 2011-07-23
Not unless your a windows user in the year 1995.

Doesn't hurt to turn on the firewall anyway.

---

### Post by bodhi.zazen on 2011-07-23
> **chazinams said:**
> I'm new to computers and don't yet understand how to be secure.

What should I do to keep important files on my computer from being uploaded to the internet? Don't I need an outbound firewall to prevent this?

What causes my computer to send an outbound request to the internet that would result in files being uploaded from my computer onto the internet? I'm afraid to put anything of importance (like reports that I've written for work) onto a computer with internet access because I don't want them to be uploaded to the internet. I wouldn't upload them on purpose obviously, but I'm afraid it would happen without my knowledge because I don't know what I'm doing.

Actually a firewall would not really help unless you blocked all outbund traffic. Firewalls block ports and not content, so, there would be no way of doing this with iptables.

In theory you could perhaps send your outbound traffic through a filtering proxy, but it would be complicated and prone to failure.

You are far better off learning tools such as apparmor.

When running Ubuntu I confine all network aware applications with apparmor.

---

