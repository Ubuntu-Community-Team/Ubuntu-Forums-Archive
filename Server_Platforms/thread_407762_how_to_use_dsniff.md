---
title: "how to use dsniff"
date: 2007-04-12
forum: Server Platforms
---

### Post by hockey97 on 2007-04-12
HI I just can't find anyplace to know how dsniff works and what must be done to run it.
I know it's a password sniffer ect with other tools, is this just for lan or would it be used on internet?? I saw some post stating that it can be used to get hotmail passwords ect
I basicly want to know how it operates like and how can you use it on website, and how to protect your website from it.

---

### Post by gaten on 2007-04-12
Try this: [http://www.irongeek.com/i.php?page=security/AQuickIntrotoSniffers](http://www.irongeek.com/i.php?page=security/AQuickIntrotoSniffers)

As far as Lan/Internet is concerned, this is what you need to know:

{Hotmail User} ==> {Sniffer} ==> {Hotmail.com}

The sniffer would somehow need to position himself between the user and the server, how that is done is something you'd need to figure out on your own, this isn't a hacking forum. 

If you should know one thing about sniffing and protecting against it, its this: **Don't use clear text protocols!** This means **HTTP, FTP, POP, SMTP** (basically everything your average user tends to use on a daily basis).

If your email/web site/whatever does not use an encrypted protocol and you care about your password being sniffed, stop using that service. Gmail and Yahoo Mail both offser **POP3 over SSL**, which will encrypt your  user/pass. It isn't the ultimate in security, as there are ways around that too, but its alot better than Pop3 or HTTP traffic

---

### Post by hockey97 on 2007-04-12
What I am asking is  can dsniff or ettercap they sniff on the internet or only local networks, the reason  I ask was not to do some hacking it was to protect my websites from hacks from these tools , just want to know if these tools on other computer over the internet can read me?? I have read that place and also many other websites to me seems like only local network they can sniff. But I thought that it may be possible if the person can get a hold of your ip andress of your router or network ip that they can sniff for your passwords and user names.

---

### Post by gaten on 2007-04-12
>  	What I am asking is can dsniff or ettercap they sniff on the internet or only local networks, the reason I ask was not to do some hacking it was to protect my websites from hacks from these tools , just want to know if these tools on other computer over the internet can read me?? I have read that place and also many other websites to me seems like only local network they can sniff. But I thought that it may be possible if the person can get a hold of your ip andress of your router or network ip that they can sniff for your passwords and user names.

For someone to sniff your traffic, they have to position themselves between YOU and the computer you are talking to. This can be done a number of ways, but like you said the most common is by sitting on the same internal network you are on. So basically, as long as you harden your machine and don;t run scripts/executables you don't know, you should be fine. Also use SSH and the like.

---

### Post by hockey97 on 2007-04-12
I got ssh installed so that should protect me from any sniffing on my network right.

---

### Post by tturrisi on 2007-04-13
> **hockey97 said:**
> I got ssh installed so that should protect me from any sniffing on my network right.
NO!

You seem to be missing the point.  For someone to sniff your network traffic they would need to have their computer connected by wire or by wireless to your network.  Or they would need to connect to your network using software that is running on a computer on your network, such as a backdoor trojan or a remote access software/trojan.  Or they would need to exploit a vulnerability in existing software, such as php, apache or other software that has not be updated with security fixes.

Or the sniffer would need to connect to a computer just outside your network, such as an isp router or isp gateway, or some other router.  Such cases are exremely extremely rare.   In such cases the sniffer picks up all traffic routed through the device that has been compromised, not just your network.  However, the sniffer won't be able to see your local traffic, only the stuff being sent to the outside (WWW) or the stuff sent inbound (from the WWW).

For example, if you have a wireless network that is not using WEP or WPA security, then any fool could sniff your email, ftp, and other non-secure data.  SSH, SSL, SFTP will only secure the data IF it is being used.  Thus, don't use FTP to access your lan remotely, use a secure protocol such as ssh or sftp.

---

