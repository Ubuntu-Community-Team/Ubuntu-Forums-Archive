---
title: "Descisions... ftp vs sftp vs ssh. HELP!"
date: 2005-08-18
forum: Server Platforms
---

### Post by rubbish on 2005-08-18
Hey, first of all I just want to say I am new to Linux.I have been running Ubuntu for a couple of weeks now.

Now I would like to turn my Ubuntu desktop into a server. I just basically want to download and upload files from another computer (running OS X Tiger) that is in a remote location through the internet. I don't want anybody else will access the server, so I would like to make it as secure as possible.

Been reading up on some of this stuff. Read about **VSFTPD** and the ftp service it provides. However, I also read that it can be unsecure since usernames and passwords are sent in the clear. 

I then stumbled upon sftp and ssh, both of which are provided by **OPENSSH**. I don't think I will be needing ssh, and think sftp sill be enough for what I require. Can I configure **OPENSSH** to only enable sftp and disable ssh or other services that I don't need.

Other than that just want to know what you guys think I should be using ftp, sftp or ssh. Also could you please provide me to a link to a good detailed guide on setting up **OPENSSH** properly.

Thanks in advance to anyone kind enough to help. Cheers.

---

### Post by gruepig on 2005-08-18
SFTP sounds like what you want.  I'd strongly recommend avoiding FTP, as there have been numerous holes in most ftp servers, and ftp sends your passwords and transfers in clear text (unencrypted).

I don't know of a way to run an sftp server without an ssh server (since sftp-server really runs as a subsystem of sshd).  In my experience, running an ssh server is secure if you have strong passwords/passphrases on all your accounts and if you use a firewall to restrict access to certain IPs.

You will see a lot of login attempts (in /var/log/auth.log).  However, as long as you use good passwords, this is nothing to worry about.  If you're really concerned, you might want to check this log file frequently (I run a cron job weekly to email me a summary of successful logins and login attempts).

The default sshd configuration is reasonably secure, but you can also tweak it a lot.  The main config file is /etc/ssh/sshd_config; it's pretty well-commented and you can also see the sshd_config manpage.  To restart the ssh server after making changes, run '/etc/init.d/ssh restart'.

My config includes (among other things):
UsePrivilegeSeparation yes
LoginGraceTime 200
PermitRootLogin no
PermitEmptyPasswords no
X11Forwarding no
MaxStartups 5
Subsystem       sftp    /usr/lib/sftp-server

If you really want to have sftp access only, I think you could do something like the following:  Create a new user account which will be used for sftp only (no ssh, no local logins).  Set the user's shell to sftp-server ('usermod -s /usr/lib/sftp-server username').  This restricts that user to sftp only.  Then modify sshd_config so that the only user who can use ssh/sftp is that newly-created user ('AllowUsers username').

By the way, if you're looking for a graphical SFTP client for OS X, Fugu is pretty good.

Hope this helps.

---

### Post by rubbish on 2005-08-18
Yeah. Great. Thanks for the help. Just wanted to get info and advice from someone with more experience than I have. Thanks.

---

### Post by nad on 2005-08-20
Good advice from gruepig.

I would just like to add that you can tweak your hosts.allow and host.deny files to allow login attempts from only specific addresses (ranges, etc). This will greatly reduce your log activity as the script kiddies out there will quickly become frustrated with attempts upon your port #22.

---

### Post by Velox Letum on 2005-08-20
I use my firewall to block out any access (aside from IPs with legitimate access such as me from other computers (ie, 192.168.0.*), or myself at my workplace. I also use sftp, and it falls under the same rules. My passwords are long (12-20 chars or so) strings that appear to be gibbrish with lowercase, uppercase, numbers, punctuation, but really mean something to me...only to me which makes it secure from guessing, but easy for me to remember.

---

### Post by gruepig on 2005-08-21
Sounds excellent.  I think you can safely run sshd without worrying.

---

### Post by Killick on 2005-08-21
For an even securer & more convenient system, have a look at using ssh keys and disabling passwords completely. 

I use the same large passphrase for all my ssh keys and have them loaded on boot. No need for any more passwords/key entering when I connect to remote machines.

Killick

---

### Post by LordHunter317 on 2005-08-21
If it's just you doing the transfers, the value of a seperate sftp account is quite questionable indeed.

---

