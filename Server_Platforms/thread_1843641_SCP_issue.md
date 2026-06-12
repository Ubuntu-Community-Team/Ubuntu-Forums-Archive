---
title: "SCP issue"
date: 2011-09-13
forum: Server Platforms
---

### Post by aliov_85 on 2011-09-13
Hello I'm trying copy generated certificates from server to my localhost. The server is a remote server with the 10.04 ubuntu server. Could please how can I copy a file like "ta.key" to my local machine through scp?


sudo scp -r [email]xxx@sdfs.prgmr.com[/email]:/etc/openvpn/ /home/home/VPS/

---

### Post by BkkBonanza on 2011-09-13
What error messages are you getting. Your command appears ok.

---

### Post by aliov_85 on 2011-09-14
Yes the error I get is the following:

Permission Denied

---

### Post by BkkBonanza on 2011-09-14
Probably user xxx has no access to that directory on your server. The sudo only applies to the local machine permission to write the file. The user xxx still needs correct permissions on the server.

The rsync command is good for this type of copying too but you would have the same issue. 

Sometimes what I do is copy the files to my home dir on the server using sudo, and change perms, before accessing them remotely. But if you do and they are important files make sure you delete them after and preferably with secure delete too so they can't be recovered.

---

### Post by aliov_85 on 2011-09-15
Ok when I remove the keyword "sudo" the query becomes the following:

```
scp xxxx@xxx.prgmr.com:/home/openvpn/clientcerts /home/home/VPS/
```

, I get the following:
sudoprotocol error: unexpected <newline>
home@laptop:~$ : sorry, you must have a tty to run sudo
sudo: sorry, you must have a tty to run sudo
sudo: sorry, you must have a tty to run sudo
sudo: sorry, you must have a tty to run sudo

I copied files to home as well and I'd the same problem. Do you probably have an idea?

---

### Post by Lars Noodén on 2011-09-16
> **BkkBonanza said:**
> 
The rsync command is good for this type of copying too but you would have the same issue. 

You can get around that by using  [--rsync-path='sudo rsync'](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo)

---

### Post by BkkBonanza on 2011-09-16
> **Lars Noodén said:**
> You can get around that by using  [--rsync-path='sudo rsync'](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo)
Interesting! I didn't know that but will try it next time I need to copy privileged files. Thanks.

---

### Post by BkkBonanza on 2011-09-16
> **aliov_85 said:**
> Ok when I remove the keyword "sudo" the query becomes the following:

```
scp xxxx@xxx.prgmr.com:/home/openvpn/clientcerts /home/home/VPS/
```

, I get the following:
sudoprotocol error: unexpected <newline>
home@laptop:~$ : sorry, you must have a tty to run sudo
sudo: sorry, you must have a tty to run sudo
sudo: sorry, you must have a tty to run sudo
sudo: sorry, you must have a tty to run sudo

I copied files to home as well and I'd the same problem. Do you probably have an idea?

I'm not sure what's happening there. You're getting a sudo error message but say you're not using sudo. The scp command requires that you have ssh access to the server as it will use ssh as the underlying transport. Make sure you can just ssh in to the server as user xxx first. Also try to provide more detail showing the actual command you type and the results because the error above doesn't seem to make sense in the context of what you say you did. Ideally a copy/paste of the terminal showing what you typed and what results. 

Also be aware that giving the -v option to scp (and ssh too) will show you more debugging info and may help track down the problem.

---

### Post by aliov_85 on 2011-09-17
Ok now there are no errors. However the file is not yet transfered. I use the following command:
```
 rsync -e "ssh -l xxx@xxx.prgmr.com:/home/openvpn/clientcerts/ca.crt" --rsync-path='sudo rsync' -av  /home/home/VPS
```

and I get the following message:
> sending incremental file list
drwxrwxr-x        4096 2011/09/14 00:52:19 VPS
-rw-rw-r--       52908 2011/08/13 16:23:44 VPS/SSh_key_generation2011-08-13 16:23:43.png
-rw-rw-r--         410 2011/09/10 00:43:01 VPS/vps.txt
-rw-rw-r--         410 2011/09/10 00:43:00 VPS/vps.txt~
drwxrwxr-x        4096 2011/09/14 00:52:19 VPS/VPSServerCertificates

sent 172 bytes  received 14 bytes  372.00 bytes/sec
total size is 53728  speedup is 288.86


I'm Almost there, Am I missing permissions?
Thank you

---

### Post by BkkBonanza on 2011-09-17
There's no reason to use the -e option with rsync because the default remote shell is ssh anyway. You would only do that typically if the remote ssh is listening on a non-standard port or some other non-default option was needed. When you provide the shell that way you just give the program name and options, not the source path. 

With the default shell your command should work like this,

rsync --rsync-path='sudo rsync' -av [email]xxx@xxx.prgmr.com:/home/openvpn/clientcerts/ca.crt[/email]  /home/home/VPS

(except if your local /home/home/VPS has only root perms then you would need to run "sudo rsync ..." to be able to write the files there)

(I've not tried the rsync-path option yet but it sounds like it should work to give you root perms on the remote server, and you would need to have sudo privileges there of course)

---

### Post by aliov_85 on 2011-09-17
Thank you for your response. I really don't understand why I get this error:

> 
home@laptop:~$ rsync --rsync-path='sudo rsync' -av [email]xxx@xxx.prgmr.com:ali.txt[/email] /home

sudo: sorry, you must have a tty to run sudo
protocol version mismatch -- is your shell clean?
(see the rsync man page for an explanation)
rsync error: protocol incompatibility (code 2) at compat.c(174) [Receiver=3.0.8]


---

### Post by BkkBonanza on 2011-09-17
It sounds like something isn't configured correctly. Have you checked that you can use ssh to login on that server without similar problems. After login try to use the sudo command manually. eg. "sudo ls -lsa".

I've never seen that tty error. But doing a google gives me this,
[http://www.cyberciti.biz/faq/linux-unix-bsd-sudo-sorry-you-must-haveattytorun/](http://www.cyberciti.biz/faq/linux-unix-bsd-sudo-sorry-you-must-haveattytorun/)

which seems to say that some systems need to have the -t option for ssh to work correctly. IF that's the case then with rsync you would need something like,

rsync -e "ssh -t" --rsync-path='sudo rsync' -av [email]xxx@xxx.prgmr.com:ali.txt[/email] /home

Ubuntu server doesn't usually have this issue in my experience so perhaps your server is running some pther Linux?

---

### Post by aliov_85 on 2011-09-17
Well I've no problem with SSH. However according to [this]("http://www.openssh.org/faq.html#2.9") because of shell initialization. So I'm quiet sure the reason SCP & rsync fails is related to the fact that when I connect to my VPS there is running script. This is because when I run the following command:

"ssh [email]xx@rxx.prgmr.com[/email] /usr/bin/true" I get this:

> Options for xxx
1. out of band console (press ctrl-] to escape, not resizeable)
2. create/start (try this if the vps "does not exist")
3. shutdown
4. destroy/hard shutdown
5. reboot
6. swap i386/amd64 bootloaders (pvgrub) currently amd64
7. view/add/remove ssh authorized_keys
8. exit
press the number> sudo: sorry, you must have a tty to run sudo


Should I configure initializer or the shell?
Regards

---

### Post by BkkBonanza on 2011-09-17
If the server has been configured to restrict ssh logins to only a specific program (menu) then you will not be able to run other programs over ssh such as rsync, scp etc. 

You can check this by looking at the /etc/ssh/sshd_config on the server. Look for the ForceCommand statement.

---

### Post by aliov_85 on 2011-09-18
I went through sshd_config file
> vi /etc/ssh/sshd_config and I entered that ForceCommand. I've still the same problem. Is my command right?

ForceCommand sudo /root/scp 

How about rsync?

Thanks

---

### Post by BkkBonanza on 2011-09-18
No. You want to see if the command is there and remove it. If you don't have root access on the server then you cannot do that. That command forces the login to only allow that one command. 
 
Also that is not the only way of restricting you. If your login shell has been replaced then that would also cause a problem like this. You probably need to contact whoever admins that system and ask about how to do what you want. It sounds like they have taken steps to restrict what you can do.

---

### Post by aliov_85 on 2011-09-18
> **BkkBonanza said:**
> No. You want to see if the command is there and remove it. If you don't have root access on the server then you cannot do that. That command forces the login to only allow that one command. 
 
Also that is not the only way of restricting you. If your login shell has been replaced then that would also cause a problem like this. You probably need to contact whoever admins that system and ask about how to do what you want. It sounds like they have taken steps to restrict what you can do.

Ok friend, it was very kind of you. I don't find how to mark your post as asnwer. Tell me if this possibility exists, otherwise thank you again.

---

### Post by Lars Noodén on 2011-09-18
> **aliov_85 said:**
> I don't find how to mark your post as asnwer.


Go to the top of the page and select the link "Thread Tools"  From there, one choice is to mark the thread as "Solved"

---

### Post by aliov_85 on 2011-09-24
Hello, I've checked my administrator. He told me to create a no-root user. So I'm pretty sure that I don't have anymore the problem initial configuration of bash.

But I've still problems copying files from server to local. 

SCP:
> scp [email]david@xxx.xxx.prgmr.com:/home/ali.txt[/email] /home/home/VPS
I get this:
> david@XXX.xxx.prgmr.com's password: 
ali.txt                                       100%   26     0.0KB/s   00:00 

With rsync I've the following error:

> rsync error: error in rsync protocol data stream (code 12) at io.c(601) [Receiver=3.0.8]

Do you know why?

---

### Post by Lars Noodén on 2011-09-24
Please post the full line you are using with rsync.

---

### Post by aliov_85 on 2011-09-24
Yes:
 rsync --rsync-path='sudo rsync' -av [email]david@xxx.xxx.prgmr.com:/home/ali.txt[/email] /home/home/VPS

---

