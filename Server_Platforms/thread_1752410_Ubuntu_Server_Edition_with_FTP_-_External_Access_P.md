---
title: "Ubuntu Server Edition with FTP - External Access Problems"
date: 2011-05-07
forum: Server Platforms
---

### Post by EneilShade on 2011-05-07
Hello all,
I am new to this forum, but not too new to Ubuntu. Just today I decided to set up an FTP server (proftpd) on my little HP downstiars. Needles to say, I had a few problems. I fixed most things, and local access on port 21 is a happy operation, but I cannot access the FTP server from the outside world, and yes, I have port forwarded properly. Is there any sort of setting I need to change in proftpd.conf?

Thanks for all help.

---

### Post by volkswagner on 2011-05-07
Do you have any software firewall running such as UFW?

```
sudo ufw status
```

You need to verify port 21 is not blocked by your isp.

From inside your LAN, navigate to canyouseeme.org, check port 21.  If you get errors, either your isp blocks port 21, or your forward is not working.

---

### Post by EneilShade on 2011-05-07
Thanks for your assistance! Although, neither of those things was my problem. canyouseeme.org found my computer, and the firewall is off. The problem I am having is that I am using WordPress, and I was trying to install a new theme. This process uses FTP (understandable). So, I put a FTP server on my Ubuntu server and directed it to my public_html directory. When I access the FTP server using its local address (192.168.1.11), it is happy. When I attempt the external connection, it fails miserably: "Cannot find folder public_html".

Thanks so much for your quick response anyway!

---

### Post by Lars Noodén on 2011-05-08
FTP sometimes requires two ports to be open.  Are you using [active or passive FTP](http://fetchsoftworks.com/fetch/help/Contents/Concepts/ActiveAndPassive.html)?

Myself, I would recommend dropping FTP completely and use SFTP instead.

---

### Post by EneilShade on 2011-05-08
I discovered and solved the problem: I had set the wrong permissions on the public_html directory, and when I changed them, I did not even have to use FTP. But in doing so, I accidentally removed myself (the only user that has a password that I know) from the sudoers list. I am reintslling now... :)

Thanks for all of your help!

---

