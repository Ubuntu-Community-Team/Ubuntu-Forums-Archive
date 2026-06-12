---
title: "sshd2_config"
date: 2011-01-16
forum: Server Platforms
---

### Post by Red Rebel on 2011-01-16
I am reading *Implementing SSH, Strategies for Optimizing the Secure Shell* by Himanshu Dwivedi. After giving an overview of the sshd_config file, he starts talking about the sshd2_config file. I cannot find this file, and I am not exactly sure what he is talking about. I am attaching some excerpts from the book to give you guys an idea of what I am talking about. First let me say that, I asked this question on a different forum and someone said basically, that sshd2_config does not exist. I respectfully disagree because I don't think the author would bring it up. Please click on individual  attachments and let me know what you think. Any Help would be greatly appreciated. 
[ATTACH]181279[/ATTACH]

[ATTACH]181278[/ATTACH]

[ATTACH]181280[/ATTACH]

thanks again

---

### Post by cariboo on 2011-01-16
I run openssh-server on my server, I don't have an sshd2_config in /etc/ssh:

[CODEcariboo@willy:/etc/ssh$ ls -l
total 148
-rw-r--r-- 1 root root 125749 2010-05-19 10:30 moduli
-rw-r--r-- 1 root root   1616 2010-05-19 10:30 ssh_config
-rw-r--r-- 1 root root   2453 2010-11-03 15:40 sshd_config
-rw------- 1 root root    668 2010-11-03 15:40 ssh_host_dsa_key
-rw-r--r-- 1 root root    600 2010-11-03 15:40 ssh_host_dsa_key.pub
-rw------- 1 root root   1675 2010-11-03 15:40 ssh_host_rsa_key
-rw-r--r-- 1 root root    392 2010-11-03 15:40 ssh_host_rsa_key.pub][/CODE]

The above is a listing of the directory

The author of the book is probably talking about ssh which is different from the version used on Ubuntu.

---

### Post by Red Rebel on 2011-01-16
ok, i think I can answer my own question. As I read on, I realized that, he is talking about 3 different server options. OpenSSH, SSH Communications’ SSH Server, and VanDyke Softare’s VSHell SSH server. I am using OpenSSH, that is why the sshd2_config file is not there. 

I will let users post any additional input before I close this in the next few days. 

thanks.

---

