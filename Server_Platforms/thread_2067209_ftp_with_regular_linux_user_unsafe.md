---
title: "ftp with regular linux user unsafe?"
date: 2012-10-06
forum: Server Platforms
---

### Post by Ortix on 2012-10-06
So after i've finally set up my home server, I want to make sure it's secure enough..

Firewall wise everything is good to go, but i'm worried about my ftp. FTP should be fine when the user logging in goes to a folder where no harm can be done to the system, however the standard linux users can FTP into the server.

For example, i can type in my IP address and FTP into the server with the root user. Not really safe if you ask me. This goes for all current linux users. On one hand, it's pretty handy to have this feature when I need to make some changes or if i need access to certain folders (i never log in with root btw), but it's also frightning.

What would the pro's advise me on this? Is it something unavoidable? Should i "jail" all users to their home directory? I don't know what to do! :(

---

### Post by Lars Noodén on 2012-10-06
FTP is unsafe for uploads.  That is because the username, password and entire session are transmitted in the clear, unencrypted:

[list]
[*][http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*][http://www.openlogic.com/wazi/bid/188103/](http://www.openlogic.com/wazi/bid/188103/)
[/list]

So if you are logging in with FTP with a regular user's account, those credentials are being spread around the net and could end up causing trouble because other people can get your password that way.

A better way would be to use SFTP.  If you have the package OpenSSH-server installed, then you already have SFTP set up.  No additional configuration is needed.  

In addition to the text-based SFTP client that comes with Ubuntu, there are also graphical clients built into the file managers Nautilus and Dolphin.  To use either, press ctrl-L and then enter the URL for the server: sftp://user@xx.yy.zz.aa/some/path/

---

### Post by Ortix on 2012-10-06
Ok for some reason sftp works now! it didn't use to work for some reason but now it does. So from now on i'll use SFTP to do file transfers. Also, it isn't a problem that the users in question can still actually FTP into my server unsecured? This might be phrased confusingly so i'll just note that I am the only user of the server (and sometimes my dad). So there is no problem leaving the set up as is, as long as i use SFTP from now on?

---

### Post by Lars Noodén on 2012-10-06
You can leave the set up as is if SFTP works, but it would be recommendable to remove FTP if you are not using it.  It's generally considered a good idea to remove services that you don't use.

---

### Post by thnewguy on 2012-10-06
Since there isn't any reason to leave FTP running and you have indicated the root account is enabled, it is a bad idea to leave FTP running. Attackers are likely to brute-force the password on your FTP server eventually and gain access to your system.

I recommend turning off FTP and making sure root access is disabled for the SFTP server. The configuration file for SFTP is located in at /etc/ssh/sshd_config

---

### Post by JKyleOKC on 2012-10-06
Much depends on the specific FTP server you use. I run proftpd here, and it offers configuration options that can make it quite safe. One such option is to prohibit login or any access at all, for all users except those specified in the option. In my case I specified that only user "ftp" with an alias of "anonymous" can get in, and this prohibits access to any normal user including myself but allows the usual anonymous access. Other options control access to specific directories and can block access to the rest of your system. Accessible directories are either read-only or write-only but never read-write, so they cannot be used for anonymous storage areas. I can move files between them, but not through the FTP program itself.

The result is that first-time customers for my data recovery services can upload their damaged files to my FTP server, using a special program that I make available to them that wends its way through my security measures, but script kiddies have not managed to break in since I tightened the access rules (although a dozen or more try to do so each day)...

The proftpd package is available in the repositories. I highly recommend it.

---

### Post by Bachstelze on 2012-10-06
Anonymous FTP is fine of course (most open source software is distributed that way) as long as you disallow uploads completely (otherwise, you might get some very nasty things uploaded).

If you are going to let real users log in, though, you should setup SSL encryption so that passwords and data do not travel in the clear. vsftpd can do this, I suppose proftpd and others can, as well. It is also a good idea to only allow some users to login, and probably to chroot users to their home directory as well, so that they can't go look around (unless they also have login access, of course).

But just use SFTP if you can.

---

### Post by Ortix on 2012-10-07
Very informative guys! much appreciated. I will take the necessary measures tomorrow. I would also like to say that this is a great community! I used to go to tweakers.net but the only reaction they have is: "google it"... and then the needy mods close my threads because I didn't put enough effort in looking for the answer. 

Sorry for the rant, all these good replies just jumbled my emotions :')

Have a great day!):P

---

### Post by TheFu on 2012-10-07
For the last few years, some backdoor has been discovered in the source code for the most popular FTP servers used. 
* ProFTP [http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787](http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787)
* vsFTP [http://www.h-online.com/open/news/item/Vsftpd-backdoor-discovered-in-source-code-update-1272310.html](http://www.h-online.com/open/news/item/Vsftpd-backdoor-discovered-in-source-code-update-1272310.html)
* and others.

FTP servers are major targets for attack.  Unless you have a real reason to run FTPd, don't.

I always love seeing a blog article I wrote referenced here. Thanks Lars!

Setting up ssh/sftp/scp in a secure manner isn't very hard. [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) explains.  Using key-based ssh authentication works easier and much more securely than FTP.

Googling for an answer first is appreciated here too. ;)

---

### Post by Ortix on 2012-10-07
> **TheFu said:**
> 

Googling for an answer first is appreciated here too. ;)

Thansk for the articles! I bookmarked them and reading them in the train tomorrow ;)

And I always google first. Obviously it's much faster than just sitting and waiting for an answer. But regardless of how much I google, i get told to google more. I then wonder what that community is meant for if asking questions is practically not allowed :P

---

### Post by Lars Noodén on 2012-10-07
> **TheFu said:**
> I always love seeing a blog article I wrote referenced here. Thanks Lars!

Thanks for writing it.  It does a good job of saying what needs to be said.  SFTP is too easy to set up so it does not get guides and howtos.  Thus when searching for file transfer, it does not come up in the search engine results.  So it's important that blog posts like yours bring up the key points about using SFTP.

---

### Post by TheFu on 2012-10-07
> **Ortix said:**
> And I always google first. Obviously it's much faster than just sitting and waiting for an answer. But regardless of how much I google, i get told to google more. I then wonder what that community is meant for if asking questions is practically not allowed :P

Searching online fails for everyone sometimes.

Learning how-to search is definitely a learned skill.  The trick is to be specific, but not so specific that nothing is found.  Sometimes when I can't find the answer, it is because I'm using the wrong terminology. Someone else teaches me the better term to search with and the heavens open with results. ;)

---

