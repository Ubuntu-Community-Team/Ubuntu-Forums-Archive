---
title: "set up a FTP server?"
date: 2019-11-28
forum: Server Platforms
---

### Post by furioususer on 2019-11-28
I'm trying to set up a FTP server and have been following this guide: [https://help.ubuntu.com/lts/serverguide/ftp-server.html#vsftpd-userauth-configuration](https://help.ubuntu.com/lts/serverguide/ftp-server.html#vsftpd-userauth-configuration)
Ok, so I've entered the command **sudo apt install vsftpd **so I guess that vsftpd is installed, but now what? Where and how do I access it so I can set up settings and password? 
  
I'm on Ubuntu 16,04 LTS btw.

I also want to ask while I'm at it, is this guide [https://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](https://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux) solid? I just want to make sure it's not deceiving me to do something I don't understand. Do I get the experts' approval to follow this guide?

EDIT: The only thing I want is to be able to download and upload to one folder of my choosing. One user. One folder with only read-access. I'm not interested in installing an OS server or the likes. If what I'm asking for is called "plain FTP" or "sFTP", I really do not care. I'm not technically advanced so I would appreciate if you would focus more on what I want than the wrong or clumsy technical terms I may have used in this post.

---

### Post by howefield on 2019-11-28
Thread moved to the "*Server Platforms*" forum.

---

### Post by TheFu on 2019-11-28
IMHO, plain FTP as a protocol should have been killed off in 2001, replaced by sftp.  There are many, many, many, reasons NOT to use plain FTP today. A little google-fu "*stop using plain ftp*" might convince you.

sftp is a drop in replacement for plain FTP, except that authentication and data transfers are all encrypted, unlike plain FTP. sftp is also firewall friendly, using the same port that ssh uses.

I cannot recommend any plain ftp guide in good conscience.  OTOH, if you've setup openssh, then you have an sftp server already installed and configured. Any Linux file manager will support sftp:// URLs and you can drag-n-drop files between the different systems.

---

### Post by LHammonds on 2019-11-29
I agree with TheFu about plain FTP (No encryption).

I documented [how I setup vsftpd](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=228) (for Ubuntu Server 16.04) for use as an FTP over SSL service with chroot'd login accounts.

If you can get on Ubuntu Server 18.04, I have an [updated version of those notes](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=265) for that version of Ubuntu.

LHammonds

---

### Post by Morbius1 on 2019-11-29
Just a note for those responding to this question. I personally didn't understand the nature of the question because  [highlight]Where and how do I access it so I can set up settings and password?[/highlight] sounded like a question on how to edit files without a gui on the server but then I found this which goes into more detail: [https://askubuntu.com/questions/1192345/set-up-a-ftp-server-with-a-gui](https://askubuntu.com/questions/1192345/set-up-a-ftp-server-with-a-gui)

Two important notes in the askbuntu question not mentioned here:
> I want to set up a FTP server (which I can access [COLOR=#0000cd]**outside**[/COLOR] [COLOR=#0000cd]**of my home network**[/COLOR])
> I want to do the setup preferably through a graphic user interface, and not editing a bunch of text files or the likes.
        LHammonds' HowTo is applicable ( as is usually the case for his HowTo's ) to the first question not so much for the second one.

---

### Post by aljames2 on 2019-12-01
I also would not trust the wikihow steps linked above as there is no implementation of SSL certificates.  It is just plain old FTP with password being your only protection which isn&#8217;t much these days.  More should be done for security.  LHammonds tutorial is better if you want to build a secure FTP server built on Ubuntu Server.  I think it comes down to what you&#8217;re looking to accomplish; how many users, what types of client devices, local only or also remote access, etc.  If it&#8217;s just you that want to access your own files you may want to consider SSH.

---

### Post by furioususer on 2019-12-01
I googled as you suggested and found this useful text:
*"SFTP or Secure FTP, is a file transfer program based on the ssh protocol, secure shell, that adds encryption for passwords and data transmission, **while retaining the same interface as used by the plain FTP.**"*


**Question**: there may be different techniques behind FTP and sFTP, but do I really care if it's called FTP or sFTP? All I want is to download and upload to a specific folder of my choosing. I called it "ftp" in my original text, but now you've educated me on there is something called "plain FTP" (bad) and "sFTP" (good). Great! But now kindly educate me on how to get going with sFTP. As that was the entire purpose of this thread. 

[B]Another question: 
[/B]Someone wrote this on another thread where with sFTP he had limited access but with FTP he had full access, and he got the following suggestion:
*"Since I have SFTP configured properly, I was advised to remove FTP entirely and only connect via SFTP (this means uninstalling vsftpd entirely, as OpenSSH handles SFTP, not vsftpd). Doing that solved the problem of the whole filesystem being viewable via FTP."*
Does this mean I should skip installing *vsftpd* (as that lets FTP access to the entire filesystem?) and install only SSH instead? I'm confused!

---

### Post by furioususer on 2019-12-01
Nothing advanced. One user only. Just one folder with read-access. Remote access. And I'm not interested in installing a server OS or the likes. I have Ubuntu 16.04 LTS and from that I should be able to setup a basic folder where I can access with sFTP.

---

### Post by The Cog on 2019-12-01
> **furioususer said:**
> 
Does this mean I should skip installing *vsftpd* (as that lets FTP access to the entire filesystem?) and install only SSH instead? 
Yes. ssh is all you need, and iot gives you both terminal login and fire transfer. This command will install the server:
```
sudo apt install openssh-server
```
but before you open it to the internet, make sure your passwords are good and strong. There are bots out there that will sit there guessing usernames and passwords all day and night.
Look at limiting access to a single username. Better still, also set up passwordless access using public keys (google for "ubuntu passwordless ssh") and disable ssh using passwords. 

If you are calling from windows, filezilla is good for sftp file transfer, though there are others that I haven't tried. If calling from linux, a url like "sftp://myusername@myserver" works nicely.

SSH command line login is useful too from time to time. SSH is really good.

---

### Post by furioususer on 2019-12-01
Thank you for getting straight to it! 

Ok. I've now installed SSH with your command. Now what? **How do I set up the actual folder I want to access remotely?**

I googled "ubuntu passwordless ssh" and I read the explanation twice, but I couldn't quite understand how the public and private key is actually used. 
In any case, what I want to do is to share a folder remotely with a sibling of mine that lives in another city. So the content isn't THAT personal. And she is on Windows. What do you think would be easier for her (she isn't that computer savy): to use passwordless or password authentication?** Does filezilla on Windows have support for passwordless authentication?** Cause I'm hoping to give her an adress and a password and simply tell her *"login using Filezilla with this information".*

---

### Post by TheFu on 2019-12-01
Check out post #11 here: [https://ubuntuforums.org/showthread.php?t=2424320&p=13878144#post13878144](https://ubuntuforums.org/showthread.php?t=2424320&p=13878144#post13878144) for details on setting up ssh+ sftp + keys + limiting to only sftp.  If you don't lock down her account to sftp-only access, then she will have remote shell access to the system - which means all sorts of security issues if you don't trust her.

Using only passwords to secure accounts isn't sufficient, imho. Lock down the userids and the specific client-IPs where connections will come.  Or you can use ssh-keys.  Regardless, use fail2ban to block brute force attacks.

ssh is like a multi-tool for system-to-system connectivity.  Pretty much anything that should be done, can be done using some form of ssh.  There are lots of tools that use ssh for authentication and encryption of network connections - ssh, scp, sftp, rsync, x2go, sshfs, and many more. Most backup tools use it for network-based backups.  I use it as a VPN somethings too.

---

