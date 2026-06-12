---
title: "Samba on Ubuntu Server 18.04.1 via Webmin: Files can be read but *not* modified"
date: 2018-11-04
forum: Server Platforms
---

### Post by christianarmedforces on 2018-11-04
Hello, Ubuntu Forums community!

(This is an alias account that I have just made on behalf of the computer gaming community that I co-lead, i.e. the "Christian Armed Forces.")

I have just setup an Arma 3 game server in a private [SSDNodes ]("https://www.ssdnodes.com/")VPS with Ubuntu Server 18.04.1 (self updated) using [LinuxGSM]("https://ubuntuforums.org/linuxgsm.com/lgsm/arma3server/"). I have also installed the latest version of Webmin on the server, which I knew would be helpful for the group's whole leadership team to use to coordinate mod file uploads, etc. To that end, since I will be the main server administrator, I knew that at least I (but ideally all of the administrators) should have direct access to the game server directory via my(our) desktop(s).

To begin, I followed this guide:
[https://www.linux.com/learn/samba-configuration-webmin](https://www.linux.com/learn/samba-configuration-webmin)

I am able to connect to the host by \\<ip address>\arma3server (which points to the directory "/home/arma3server"), but I can only connect by using the **root **account (not a proper long-term solution, obviously, and a potential security risk), and no matter what I do, I cannot modify or change the files. I can open them, but I cannot make any changes. I have the directory itself set to "Writable" in the Webmin Samba module. 

What I have tried:
[LIST]
[*]Recreating the Samba file share with 777 access at all levels 
[*]Manually adding root and my preferred users to the "Read/Write" user option 
[*]General tinkering with a variety of smaller settings 
[/LIST]

What am I missing? Does anyone have any experience with a similar setup?

My end goal is to be able to modify the contents of the "/home/arma3server" folder directly on my desktop -- and to let my fellow administrators do the same. We do not need anything more complicated than that.

Thank you in advance for your assistance. Please let me know if there is any further information that I should provide in order to help you help me.

-ChristianArmedForces

EDIT: I am trying to connect from Windows 10 Professional 64-bit.

---

### Post by wyliecoyoteuk on 2018-11-05
Might be obvious, but have you added the users as samba users as well as linux users?

Posting the samba.conf file (with any sensitive info redacted) would help.

---

### Post by christianarmedforces on 2018-11-05
Thank you for the reply.

I did try adding users as samba users via the Webmin samba control panel option to sync users. For the time being, I have gone down a different pathway, finding that FTP (via ProFTPD) works well enough for what we need. To avoid waste, and because I knew that I had messed with the samba configuration(s) too many times (seeing as samba itself stopped working after my last attempt with it), I just purged samba and the samba configuration files from the server via the terminal.

My suspicion is that the problem with samba has something to do with not connecting on a local network. Thus, out of curiosity, is samba known to work well with connection to a VPS? If you really think that I should be able to get this exact setup to work, then I may try again from scratch. Thank you again.

---

### Post by wyliecoyoteuk on 2018-11-06
Samba is not really routable, so that might be your issue.
I use it on my home network remotely, but I use it via VPN tunnel.
You really shouldn't make a Samba server visible on the internet, it isn't secure enough.
And if possible, you should use SFTP. 
FTP is quite vulnerable to man in the middle attacks.
Webmin also has a built-in file manager, which is quite easy to use, and it defaults to HTTPS.

---

### Post by TheFu on 2018-11-08
Use **sftp** or any ssh-based solution,

Plain FTP shouldn't be used and should have died in 1995 with telnet.
Samba shouldn't be used over any internet connection. Most WAN networks will block it, rightly.

Avoid using passwords, ssh-keys or ssh-certs are much preferred. These keys work for all ssh-based tools, so ssh, scp, sftp, rsync, stunnel and almost all backup tools honor them.  They also support the ~/.ssh/config file on the client to control connections.

Also, block brute-force attacks by either locking down the ssh ports to only be available from the specific IPs, not the entire world.  No reason to let anyone outside your country have access to any ssh stuff, right?  Block them all.  tcp-wrappers is a good 2nd layer.

Using something like **fail2ban** or **denyhosts** is often useful.

And setting up webmin on a public system is a terrible idea.  It allows the world another 20-100 attack vectors.  If you must use webmin, only allow access from localhost (there is a webmin server option for this). To access webmin, it is customary to use an ssh tunnel.

On non-VPS Ubuntu setups, root is disabled.  Most answers here will assume that is the case.  Remote root access should be disabled ASAP after a normal userid is created and added to the sudoers.  That should be step 1, before even patching, IMHO.

---

### Post by christianarmedforces on 2018-11-09
Thank you for the follow up.

FTP it is, then, as well as Webmin's built-in file manager (for smaller tasks).

---

### Post by TheFu on 2018-11-09
> **christianarmedforces said:**
> Thank you for the follow up.

FTP it is, then, as well as Webmin's built-in file manager (for smaller tasks).

**SFTP**!!!   NEVER plain FTP.

**sudo apt-get install openssh-server fail2ban**
That will install and setup reasonable defaults for sftp use.  If the ssh/sftp/scp system is on the internet, you'll want to put in a few more security settings.  Google "harden ssh" for lots of ideas on that.

---

