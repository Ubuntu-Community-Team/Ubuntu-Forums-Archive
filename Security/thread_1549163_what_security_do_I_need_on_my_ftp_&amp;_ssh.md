---
title: "what security do I need on my ftp &amp; ssh?"
date: 2010-08-09
forum: Security
---

### Post by wlraider70 on 2010-08-09
I just got my dyndns & port forwarding set up.
So now i can ssh and ftp into my box over the internet. 

How do i secure theses things? And are they SSL?

when I $ ssh user@ip  
I get full access to the root.
Same for ftp.
I only want to access certain documents through the ftp.

for ssh, I guess i would like to send a few commands, but lily not many. 




The only user name and password i have set up is ME the main user. My password is not very strong, but I don't want to change it for when I am sitting at the box.

---

### Post by Bachstelze on 2010-08-09
SSH is encrypted, FTP is not. Do you really need FTP?

---

### Post by wlraider70 on 2010-08-09
It is not essential, my thinking is to access files that i might have forgotten as often happens to me.

Can i do this though ssh and download them?

---

### Post by Bachstelze on 2010-08-09
> **wlraider70 said:**
> 
Can i do this though ssh and download them?

Yes, you can use sftp or scp.

---

### Post by kr651129 on 2010-08-09
> **wlraider70 said:**
> 
when I $ ssh user@ip  
I get full access to the root.
Same for ftp.


The best way to limit access is to create a second account for your ssh and ftp and then limit the read write access to one folder.

---

### Post by bodhi.zazen on 2010-08-09
To secure ssh - Use keys, disable passwords, and configure your firewall to block brute force cracking attempts or use denyhosts or fail2ban.

IMO there is no need to use ftp, either use scp or sftp and disable ftp altogether.

---

### Post by CharlesA on 2010-08-09
Just use sftp/ssh. No need for ftp. I use ssh/sftp all the time when I need to access a file when I am away from home.

---

### Post by Logan1985 on 2010-08-09
If you happen to be using a Windows machine to connect to your Linux box then WinSCP is a good tool to use. It supports SFTP, SCP and FTP (you'll probably want to use SFTP)

Available here - [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

Just to add to what's already been said, I also reccomend not using FTP at all. 

I also advocate the use of a second account for what you want, with a strong password.__

---

### Post by CharlesA on 2010-08-09
Filezilla works for sftp as well (even when you use keys)

---

### Post by bodhi.zazen on 2010-08-10
> **CharlesA said:**
> Filezilla works for sftp as well (even when you use keys)

Off topic :

Thanks for the tip on that. I did not know that about filezilla, I may check it out. 

I have always uses winscp as it is small, light weight, and portable. winscp obviously will do sftp, ssh, scp w/ putty keys (you can import openssh keys to putty).

Does filezilla use openssh keys, or do then need to be converted ?

---

### Post by Bachstelze on 2010-08-10
> **bodhi.zazen said:**
> Off topic :

Thanks for the tip on that. I did not know that about filezilla, I may check it out. 

I have always uses winscp as it is small, light weight, and portable. winscp obviously will do sftp, ssh, scp w/ putty keys (you can import openssh keys to putty).

Does filezilla use openssh keys, or do then need to be converted ?

OpenSSH. Recent versions of FZ can just use ssh-agent (importing the keys directly into FZ doesn't work with passphrase-protected keys, which renders it basically useless).

Not sure if ssh-agent works on Windows, though...

---

### Post by wlraider70 on 2010-08-10
> **bodhi.zazen said:**
> To secure ssh - Use keys, disable passwords, and configure your firewall to block brute force cracking attempts or use denyhosts or fail2ban.

IMO there is no need to use ftp, either use scp or sftp and disable ftp altogether.


Can you elaborate bit, I'm not familiar with all that.

---

### Post by Bachstelze on 2010-08-10
> **wlraider70 said:**
> Can you elaborate bit, I'm not familiar with all that.

It's all in the guide. ;)

[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

---

### Post by CharlesA on 2010-08-10
> **bodhi.zazen said:**
> 
Does filezilla use openssh keys, or do then need to be converted ?

You need to use .ppk (PuTTY keys) but, unfortunately they will not have a passphrase (yet at least, last I heard, they were still working on it.)

I've tried WinSCP and didn't really understand how to ssh with it, since all I saw was scp/sftp.

---

### Post by Bachstelze on 2010-08-10
> **CharlesA said:**
> You need to use .ppk (PuTTY keys) but, unfortunately they will not have a passphrase (yet at least, last I heard, they were still working on it.)

I've tried WinSCP and didn't really understand how to ssh with it, since all I saw was scp/sftp.

Oh, right. Actually, you can import an OpenSSH key, it will convert to ppk on the fly. So much on the fly that I didn't even notice. :p

---

### Post by bodhi.zazen on 2010-08-10
> **CharlesA said:**
> You need to use .ppk (PuTTY keys) but, unfortunately they will not have a passphrase (yet at least, last I heard, they were still working on it.)

I've tried WinSCP and didn't really understand how to ssh with it, since all I saw was scp/sftp.

You use putty for a ssh connection , winscp is for scp/sftp (will do ftp as well).

I will wait until Filezilla supports passwords on the keys.

---

### Post by wlraider70 on 2010-08-10
2 questions.


1)

can anyone help with this line

ssh-copy-id username@remotehost


```

luke@media:~$ ssh-copy-id luke@media
/usr/bin/ssh-copy-id: ERROR: No identities found
luke@media:~$ ssh-copy-id
/usr/bin/ssh-copy-id: ERROR: No identities found
luke@media:~$ ssh-copy-id luke
/usr/bin/ssh-copy-id: ERROR: No identities found
luke@media:~$

```

Not sure what im doing wrong.
EDIT:

i also got this

```

luke@media:~$ sudo cat ~/.ssh/authorized_keys
cat: /home/luke/.ssh/authorized_keys: No such file or directory
luke@media:~$

```




2) 

I'm going to use sftp, are the controls in ssh-server

Can i uninstall my ftp packages?

---

### Post by bodhi.zazen on 2010-08-10
You need to make a key first, normally you keep your keys in ~/.ssh

You need to keep server/client clear

~/.ssh/key = client

~/.ssh/authorized_keys = server

The .pub key goes to the server (into authorized_keys), the private key stays on the client.

You can specify a path (if your private key is not in ~/.ssh)

ssh -i /media/flash_drive/ssh/key user@server
ssh-copy-id -i /media/flash_drive/ssh/key user@server

etc ..

See the man pages for details.

---

### Post by CharlesA on 2010-08-10
> **bodhi.zazen said:**
> You use putty for a ssh connection , winscp is for scp/sftp (will do ftp as well).

I will wait until Filezilla supports passwords on the keys.

Ah ok. I thought as much.

I've been using psftp instead of filezilla for a while, since I don't like how it strips the passphrase from the key.

---

### Post by wlraider70 on 2010-08-11
I got it thanks.

What do i change to disable password login?

---

### Post by bodhi.zazen on 2010-08-11
> **wlraider70 said:**
> I got it thanks.

What do i change to disable password login?

See the Ubuntu wiki :

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Specifically:

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication)

---

