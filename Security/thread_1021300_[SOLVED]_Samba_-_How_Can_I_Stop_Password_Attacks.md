---
title: "[SOLVED] Samba - How Can I Stop Password Attacks?"
date: 2008-12-25
forum: Security
---

### Post by Kissell on 2008-12-25
I use a program like "fail2ban" to quick and easy lock down my services like ssh and ftp from brute force password attacks.

But I'm worried about my password protected Samba shares...  what's the point of having a password to connect to my shares if it doesn't lock a user out for awhile if they guess wrong a bunch of times?  I'd really like to know how to protect my shares a little better.  Even if it meant locking the unix account entirely after so many bad guesses...  I mean, if the user can't get their password right after a dozen tries, the account is essentially locked (to them) anyway.  And there's no reason it should be left open for some hacker to be free to make infinite attempts at guessing that password (which is probably the weakest point of my system).

Anyway, can someone help me out...  everytime I try to search for this answer I just come back with more posts about how to secure ssh with fail2ban.

---

### Post by HermanAB on 2008-12-25
Samba shares should not be on the public internet, since it is not secure.  Block ports 135-139 and 445 TCP in your internet router/firewall.

Cheers,

Herman

---

### Post by Kissell on 2008-12-25
The samba shares aren't accessible on the internet.  But there are plenty of reasons to need secure shares on a LAN.  

For instance, say I wanted to share sensitive data like medical records or employee personnel files and payroll information, and i wanted to share it easily to windows users so they could have an "F drive" and use it...  but I wanted to secure it against the helpdesk employees who weren't authorized to use (or modify) it.  Currently, any employee can run a kiddie script and eventually hack the passwords with brute force..  I know I can create entirely separate networks, or reserve IPs, or limit the shares to only work with certain users and from certain IPs...  but that's all a big hassle, and costly, and not as good as if I could just somehow limit the number of times someone attempted to login incorrectly.

If this can't be done with samba shares, then is there another way to accomplish this?  Samba shares are nice cause windows users can have an "F drive", I can't expect windows users to login via secure FTP and transfer the files so they can edit them and then login and transfer back the modified documents, the users are way too spoiled to put up with that extra process.  and nobody cares about security like I do, but I know if security is compromized it'll all be my fault somehow.

---

### Post by bodhi.zazen on 2008-12-26
I think you will need to use IPTables directly.

[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/](http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/)

just change the port from 22 (ssh) to the samba ports.

---

### Post by Kissell on 2008-12-26
I'm not very familiary with using iptables directly, I usually use ufw or something else that modifies it for me...  but I believe this code just tests for 8 hits on port 22 within 60 seconds...  

> 
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
sudo iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP


That's cool, I could do this with the windows sharing ports 135 to 139 and 445...  I think your right, that should stop brute force attack on samba shares...  as long as iptables is seeing the session as new the same way it sees new SSH authentication attempts...  hmmm...  it really has nothing to do with setting the failed password attempts and more of a direct layer-3 firewalling of connections in a certain timeframe...  not the answer I wanted or was expecting, but if it works, then it works...  

I'm a little worried that it would block legitimate connections, like people clicking on a subfolder more than 8 times in 60 seconds...  dunno, I guess I'll just have to do some trial and error and some testing...  probably have some time tomorrow for that, I'll let you know if it works.

---

### Post by Nepherte on 2008-12-26
You could also block ip addresses and network subnet ranges in samba directly. Add this in /etc/samba/smb.conf:
```
hosts allow = 127.0.0.1 192.168.2.0/24 192.168.3.0/24
hosts deny = 0.0.0.0/0
```
This for example allows only the local host, computers on the network 192.168.2 and 192.168.3.0. 24 is a brief notation for the subnet mask and stands for the number of ones in the binary version of the mask. 24 = 255.255.255.0 (or binary version 11111111.11111111.11111111.00000000)

---

### Post by Kissell on 2008-12-26
well, I tried to adapt the iptables rules that work for SSH, but no luck...  I think it's because SSH is handled differently as a session.  Below is what I tried and didn't work:

> iptables -A INPUT -i eth0 -p udp --dport 137 -m state --state NEW -m recent --set --name netbios-ns
iptables -A INPUT -i eth0 -p udp --dport 137 -m state --state NEW -m recent --update --seconds 20 --hitcount 2 --rttl --name netbios-ns -j DROP
iptables -A INPUT -i eth0 -p udp --dport 138 -m state --state NEW -m recent --set --name netbios-dgm
iptables -A INPUT -i eth0 -p udp --dport 138 -m state --state NEW -m recent --update --seconds 20 --hitcount 2 --rttl --name netbios-dgm -j DROP
iptables -A INPUT -i eth0 -p tcp --dport 139 -m state --state NEW -m recent --set --name netbios-ssn
iptables -A INPUT -i eth0 -p tcp --dport 139 -m state --state NEW -m recent --update --seconds 20 --hitcount 2 --rttl --name netbios-ssn -j DROP
iptables -A INPUT -i eth0 -p tcp --dport 445 -m state --state NEW -m recent --set --name microsoft-ds
iptables -A INPUT -i eth0 -p tcp --dport 445 -m state --state NEW -m recent --update --seconds 20 --hitcount 2 --rttl --name microsoft-ds -j DROP

I really don't want to block IP addresses, not just because it's a hassle to reserve addresses, but also it's not secure, because someone could just hijack an allowed IP pretty easily and then start a brute force attack.  I'd much rather lock the account after so many failed attempts to connect to a samba share.

---

### Post by bodhi.zazen on 2008-12-26
I am not sure if it will work, but it should.

First, what are your current IP tables rules ? Order of the rules counts.

Second, how did you test it ? did you try to brute force the password ?

---

### Post by Kissell on 2008-12-26
I cleared the iptables > iptables -F INPUT before loading those rules above.

I tested it by attempting to login to the samba share incorrectly from a windows machine, by entering the wrong password sevearl times...  The test rules above specify a hitcount of 2, so guessing the password wrong twice should add a DENY rule for that IP.  However, after attempting to map a drive a half-dozen times in about 10 seconds with the wrong password each time, it still allowed me to map the drive using the correct password, so i concluded the rules weren't working, at least not as I intended.

---

### Post by bodhi.zazen on 2008-12-26
OK, well iptables is 2 attempts per second. A brute force attack will be much faster then you are typing your password like that.

If I can make a few suggestions, I advise you secure sensitive files by using good passwords and then assign static ip addresses. Limit samba connections by ip address.

See :

[http://www.gentoo.org/doc/en/articles/samba-p2.xml](http://www.gentoo.org/doc/en/articles/samba-p2.xml)

[http://articles.techrepublic.com.com/5100-10878_11-5084069.html](http://articles.techrepublic.com.com/5100-10878_11-5084069.html)

---

### Post by Kissell on 2008-12-26
seconds is set to 20, hitcount is set to 2...  I think that should mean two failed connections in under 20 seconds...  definately something I can test quick enough without a brute force tool.

I already limit access in samba via static IP addresses...  and use strong passwords...  but this is an encrypted drive that is shared...  the weak point in security is the static IPs...  if someone were to take the box and put it on their own network, or in some way hijack the IP, they would be allowed to infinitely brute force the samba share...  I'm not okay with that.  No matter how strong my passwords are, they will get in eventually...  I want better security than a guaranteed thing that someone can definitely get in if they try.  And without being able to stop a brute force attack against infinite password attempts, then that's what I have, is a guaranteed way someone can get in if they want to...  say someone stays at work late when the PCs are shut off and manually enters one of those restricted IP addresses into their laptop and starts hacking away, leaves the program running overnight everynight...  I'd just feel a lot safer if it wasn't so easy to hack into a samba account, no matter how good the password is on it, or if you limit the IP addresses, anybody can get in over a short amount of time, because it doesn't stop you from guessing the password as many times as you want.

---

### Post by bodhi.zazen on 2008-12-26
I can not find any referance on how to do what you want with samba.

I suggest you change to ssh.

You can mount ssh shares with sshfs and on windows use winscp. winscp is easy to use and has a gui interface.

You can then use denyhosts or fail2ban. You can further secure ssh with keys and other techniques.

Access would be limited by Linux permissions. If that is not sufficient, you can add access control lists.

It takes a little effort to set up, but I will increase security.

---

### Post by Kissell on 2008-12-26
I think that will work, just abandon samba and go to ssh.

I already use SSH for my linux clients and limit with fail2ban, and it works great...  

my problem was the windows clients, who needed samba to have an "F drive"

But, if I can use "winscp" to use ssh and map drive letters to the linux box on windows clients, then I can just abandon samba.  Not 100% ideal, because it requires loading and configuring the windows clients differently, versus just making one change on the file server.  But it will get me the result I want.

Thanks

---

### Post by bodhi.zazen on 2008-12-26
Well, the bad news, I do not think you can map winscp to F:\

See if this helps :

[http://systembash.com/content/map-drive-letter-sftp-ssh-review/](http://systembash.com/content/map-drive-letter-sftp-ssh-review/)

---

### Post by Kissell on 2008-12-26
sftpdrive looks very promising...

It seems kinda weird to pay for software that works really well and does what i want...  then again, we are talking about a windows-side app.

---

### Post by HermanAB on 2008-12-26
Hmm, well, here is how to do it using Free software:
[http://smithii.com/map_a_network_drive_over_ssh_in_windows](http://smithii.com/map_a_network_drive_over_ssh_in_windows)

You can also install Windows Service for UNIX from the Microsoft web site.  That will give you NFS support.  Then you can tunnel NFS over SSH using the same method described above.

You can also tunnel Samba (either port 139 or 445), but NFS is much easier to get to work than Samba.


Cheers,

Herman

---

### Post by Kissell on 2008-12-26
Thanks...  Not that I don't think it's worth paying for...  but I do like it when payment isn't mandatory, especially when a viable alternative IS free.

The reason I was stuck on using samba was the ease of configuration and price... all windows clients already have the ability to map samba shared drives...  and can do so via a login script controlled to all machines in active directory, no individual machine config.

But, if I can't secure samba against brute force password attacks, then I'm just going to stop using samba, and config all the windows machines to use one of these other solutions...  I use SFTP extensively in the linux world, I just wish windows could map drives to SFTP natively (as they are, without UNIX services or anything else installed) but it appears that wishing it isn't going to change it.  It appears the only way to get the security I want is to stop using samba and go touch every windows machine.

---

### Post by HermanAB on 2008-12-26
Yah,the first thing I would do is configure RDP on each Windows PC, so that one can do the rest of the work from a central point.

---

