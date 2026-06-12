---
title: "Security"
date: 2008-09-11
forum: Server Platforms
---

### Post by baudday on 2008-09-11
I'm sure there are plenty of threads on this, but I would like some personal help with this. I'm really concerned about security for my server. Basically I have a wordpress installation, VSFTPD, A Mailserver, and that's about it. I wanna make sure this stuff is all secure from attacks or hackers, and I have absolutely no idea where to even begin. Is there a way I can run some tests to see how secure it is right now? And what would you suggest I do to Lock it down tight. Any resources would be helpful as well as personal advice.

Thanks in advance

---

### Post by brad8266 on 2008-09-11
A decent network firewall is a good start.

---

### Post by baudday on 2008-09-11
Okay thanks. I already have that

---

### Post by brad8266 on 2008-09-11
> **baudday said:**
> Okay thanks. I already have that

Are you running the linux firewall as well?

---

### Post by baudday on 2008-09-11
no. does that run on the server? where do i get that? what makes it different from a regular firewall? please tell me more.

---

### Post by Vegan on 2008-09-11
Don't waste your time, I use a Linksys WRT54G as a firewall and it does a great job of protecting my intranet. I have port 80 open for the Apache, 23 for Telnet and 21-2 for FTP. I have the system setup to ban IP addresses for gnawing away trying to log in.

---

### Post by baudday on 2008-09-12
Ah okay cool cool. Any other resources or suggestions? Please any help is appreciated.

---

### Post by windependence on 2008-09-12
To test your site you can use:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

A GREAT security resource:

[http://insecure.org/](http://insecure.org/)

A really really really secure operating system and one of my favorites:

[www.openbsd.org](www.openbsd.org)

-Tim

---

### Post by baudday on 2008-09-12
Thanks for that. So I ran the File Sharing test and passed. However, when I ran the Common Ports test I failed miserably. I have ports open for HTTP, IMAP, SMTP, SSH, and FTP. Is this okay? Should they be stealth or would I not be able to do all those things anymore if the were? The rest of my ports are closed, and a few are stealth.

---

### Post by cariboo on 2008-09-12
If you don't have any of those ports open your chosen services won't work.

To help secure ssh install denyhosts, it is available in the repositories, this will block brute force and dictionary attacks on port 22.

I would also drop the ftp server and in its place use sftp and scp. You can use sftp with nautlius on Ubuntu and winscp (free download) on your windows computers.

Jim

---

### Post by baudday on 2008-09-12
Ok thanks. So I intalled denyhosts. Is there any way I can know if it's doing it's job? Could you tell me more about stfp and scp? I have never heard of this. How would I move over to that?

---

### Post by windependence on 2008-09-13
> **baudday said:**
> Thanks for that. So I ran the File Sharing test and passed. However, when I ran the Common Ports test I failed miserably. I have ports open for HTTP, IMAP, SMTP, SSH, and FTP. Is this okay? Should they be stealth or would I not be able to do all those things anymore if the were? The rest of my ports are closed, and a few are stealth.

The only port I would probably not have open is FTP, but that's because I use ssh or scp to transfer files and access my servers.

The rest of your ports that are open are probably necessary, so there isn't much you can do there. IMHO, the best thing you can do is to put a hardware firewall in front of your network. Most of your routers today have some kind of rudimentary FW built in. Also good is a box you build yourself and use someting like pfsense or untangle.

-Tim

---

### Post by baudday on 2008-09-13
I'm not sure what you mean by box. I have a router with a firewall. I guess my only real problem is moving away from ftp. I started looking into Samba, which is already installed on the server, but it's giving me problems.

---

### Post by HermanAB on 2008-09-13
It is very easy to make Linux secure.  Stop the services you don't need.  If a service is not listening, nobody can misuse it.  So if you have sendmail or postfix etc running, turn it off.

---

