---
title: "Switch from Exchange to Ubuntu - New server questions"
date: 2012-02-03
forum: Server Platforms
---

### Post by Lefties on 2012-02-03
Hey all,

So, I'm running an SBS-2003 box with exchange at them moment. For different reasons, I'm giving that up and want to make the switch to a Linux machine.

I'm no sysadmin at all. I work voluntarily at a (small) cultural NGO, and just took the job to organize SBS and now the change. In this post, I would like to receive some feedback on my choices and maybe some warnings, as I will make some mistakes for sure. I'm no Linux expert (early beginner so to say...) but I can find my way through manuals :D

So, we have a desktop machine so I can experiment with it while the SBS is still running. The server should be able to:
- Act as a fileserver, for mostly mobile users. Kind of like a dropbox account, but with no size restrictions.
- Webserver for 1-5 websites
- Mailserver for those domains + around 10 POP3 accounts (import mails from other POP3 account and deliver them to users)
- (S)FTP for easy distribution of big (audiovisual)files
- Printserver for 2 USB-printers
- Exchange functionality - especially shared calenders and contact synchronisation

- All of the above need to communicate mostly with laptops with W7 + outlook installed (which will have to keep running W7).

I installed Ubuntu desktop 11.10 without problems. I used the desktop version because it works better for me, as I didn't really handle non-gui systems before. I tried installing Samba, and although some errors show up in the logs, it generally looks like printer sharing works too. I will look into shared folders today, after double-checking the error messages (if I didn't install it correctly, now is the best time to reinstall everything, as not much work is done yet.


So, based on the above, I have some questions:

1: Did I forgot anything? :P
2: I will install:
- LAMP for the webserver
- Postfix for the mailserver (including clamAV and spamassassin)
- SOGo for the exchange functionality and working with outlook clients (although Outlook over HTTP is not working yet - this might be a problem as we work mobile a lot, but maybe IMAP will work too - have to look into this)
- OpenSSH for SFTP
- Firewall (will have to look into this to find options)
 Any comments to those choices? Should I take something into consideration?
3: For filesharing - It is important for (registered!) users from outside the network to access files on the machine. I think the best way to do this is over SFTP, am I right? Can I also use this method from inside the LAN? Or do I have to configure SAMBA for this? Does this mean I have two seperate folders on the laptops, one for internal use and one for external? Or do I completely miss the point now?
Can I encrypt the shared folders with for example truecrypt? Or is this to complicated?
- RAID: I have three SATA-connectors free at the moment. Can I configure the server now without RAID, buy 3 disks later (in like 3 months), and configure a software RAID-5 for the filesharing part? Or is that not advisable?
- Security: how secure is the above setup? That probably depends on how I configure all this, but is there any important thing I am missing?
- Backup: How can I automatically backup all this? (not including the RAID-5 shared folders - I will do that seperately) 

So, that's all for now I guess. Please forgive me for asking stupid questions, I did my best to read through all the documentation, but it's a lot and I'm sure I missed something. :)

Any help or comments will be appreciated!

---

### Post by wyliecoyoteuk on 2012-02-03
couple of suggestions

BackupPC is an excellent backup tool:
[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)
Or if that is a little too much, rsync is a simpler solution.

Have you considered VPN access? you could use Samba over a VPN tunnel for the windows machines.

Or you could look at something like SME server
[http://www.smeserver.org/](http://www.smeserver.org/)
which has a lot of the work done for you.

---

### Post by Lars Noodén on 2012-02-03
> **Lefties said:**
> 
3: For filesharing - It is important for (registered!) users from outside the network to access files on the machine. I think the best way to do this is over SFTP, am I right? Can I also use this method from inside the LAN? Or do I have to configure SAMBA for this? 

Another option is to skip Samba and use SFTP/[SSHFS](https://help.ubuntu.com/community/SSHFS) for your transfers.  These will work the same whether you are on the LAN or from somewhere else far away on the Internet.  

With SFTP there is a wide range of clients and even SSHFS should work on [legacy operating systems](http://ubuntuforums.org/showthread.php?t=1027820).

Otherwise, for Samba, you'll need to run OpenVPN for remote access.

---

### Post by Lefties on 2012-02-03
Hi wyliecoyoteuk,

Thanks for your reply!

I actually didn't think of VPN. Might actually be the perfect solution, as I don't need any outlook over HTTP anymore, it would function as within the LAN (or am I wrong there?). The only problem is that I've never worked with VPN before, so it's something new to figure out. But I guess I'll manage that :)

Thanks for the backup suggestion, looks very nice indeed!

I'll have a look into SME-server, it has a lot included, might very well be an option as well!

---

### Post by Lefties on 2012-02-03
Lars, thanks to you too!

For the reason stated above (outlook with SOGo) I tend to go for a VPN-solution. I just quickly browsed through the OpenVPN website, am I correct in saying that you need to pay an annual fee per user to use the software? That is, after you used the two included testaccounts?

---

### Post by Lars Noodén on 2012-02-03
[OpenVPN](http://packages.ubuntu.com/oneiric/openvpn) is free of charge and licensed under the GPL.  There might be some service contracts available somewhere but to install it and run it, just grab it from the Ubuntu repository.

---

### Post by Lefties on 2012-02-26
So, short update. I've been reading and experimenting a lot, done a lot of fresh installs when I ****** something up again (and again and again...)

I'll report some of the troubles and how I solved them for future google hits...

Samba was relatively pain-free, although I missed something in the config-files (still don't know what). Solution was to use SWAT to get a working config-file, look for changes and try after a clean install. Works like a charm now!

Then came openVPN, which turned out to be the biggest issue of them all. But as mostly, it was my own fault (I think). After following this tutorial for setting up a [bridge]("https://help.ubuntu.com/11.10/serverguide/C/network-configuration.html") and then [OpenVPN]("https://help.ubuntu.com/11.10/serverguide/C/openvpn.html") it seemed that brctl cannot function next to network manager. Uninstalling network manager and manually editing /etc/network/interfaces worked. OpenVPN is now up and running. Only thing I should do is reconfigure encryption from 1024 to something higher. Writing this now, I see that the OpenVPN-guide for 11.10 changed quite a bit, the new version would've been much more helpful. Which is good for anyone trying this now ;)

There are a few people working on our websites at the moment who need access to /var/www from outside our network. Using a Samba share and VPN was not an option, as they are only working on the website and should'nt have access to any other files on the network. Samba could probably be configured for this too over VPN, but I didn't want to go into the hassle and use auth for samba. So I installed an SFTP-server and created the users with strong passwords as per [this thread]("http://www.binaryroyale.com/index.php/2011/04/creating-sftp-accounts-in-ubuntu-e-g-for-uploading-website-files/"). And as soon as I opened port 22 I got brute-force attacks. I checked some firewall programs, but that's too complicated for me. The solution I found was [fail2ban]("http://www.fail2ban.org/wiki/index.php/Main_Page"), which also gave me the option of temporarily banning some romanians so my apache error log doesn't get filled with error messages from bots looking for phpmyadmin-exploits...

As for BackupPC, that is exactly what I need. Thanks for that!



Postfix is what is giving my a headace now. I installed it as per [this guide]("http://flurdy.com/docs/postfix/"), but for some reason I cannot connect via telnet on my LAN to port 25. Sending mails via phplist works, telnet at the local machine too. Anyone any idea? netstat -tap gives *:smtp *:* LISTEN, as it is supposed to I guess...

---

### Post by SeijiSensei on 2012-02-27
> **Lefties said:**
> Postfix is what is giving my a headace now. I installed it as per [this guide]("http://flurdy.com/docs/postfix/"), but for some reason I cannot connect via telnet on my LAN to port 25. Sending mails via phplist works, telnet at the local machine too. Anyone any idea? netstat -tap gives *:smtp *:* LISTEN, as it is supposed to I guess...

Probably you need to change the "[mynetworks]("http://www.postfix.org/postconf.5.html#mynetworks")" directive to enable access from remote hosts.  You might also check "[inet_interfaces]("http://www.postfix.org/postconf.5.html#inet_interfaces")" to make sure it's listening on all interfaces.  I believe the Ubuntu default is to listen only on localhost.

---

### Post by collisionystm on 2012-02-27
While you are testing, try Zentyal. You wont regret it...

---

