---
title: "Problems w/ RSA keys"
date: 2014-05-04
forum: Server Platforms
---

### Post by netrix-g on 2014-05-04
Hello, firstly thank you for a really well thought out post !

I am a noob to Ubuntu/file server/NAS and to some extent MAC OSX.

I have an HP N54L micro server with Ubuntu Server v11 installed and a RAID 5 array set up via the command line following various other "how to" posts. I was struggling with share permissions etc, and installed Ubuntu desktop (as up upgrade from the command line)
So, now from my MAC I can see the shares on the file server :)

I then found your post and tried to pick out the things I need/want to do and started with the RSA keys, but I'm stuck :(

When I enter this command on my MAC:
netrix:~ Netrix$ scp -p xxxxx ~/ .ssh/id_rsa.pub [EMAIL="netrix@192.168.x.xxx"]netrix@192.168.x.xxx[/EMAIL]: .ssh/authorized_keys2 (substituting xxxxx with my port number and inserting a valid IP address) I get the following error: 
.ssh/authorized_keys2: No such file or directory

Am I missing something obvious ?

Any help very much appreciated !

Regards

Netrix


Just to add - I think I added an incorrect space after the ~/
I have removed it but I now get the error:
ssh: connect to host 192.168.x.xxx port 22: Connection refused
lost connection

The Listen command for the ssh port on the Ubuntu server reports that I have successfully changed the ssh port from 22 to one of my choice.

R

Netrix

---

### Post by Iowan on 2014-05-04
Moved to Server Platforms.
Hopefully, you'll find more help than 97 posts deep in a [tutorial]("http://ubuntuforums.org/showthread.php?t=1895084") :)

---

### Post by steeldriver on 2014-05-04
Unlike ssh, scp uses an uppercase -P for the port number. Also you probably need to give the full path to your home dir i.e.

```

scp **-P** xxxxx **~/.**ssh/id_rsa.pub [EMAIL="netrix@192.168.x.xxx"]netrix@192.168.x.xxx[/EMAIL]:**/home/netrix/**.ssh/authorized_keys2

```

(assuming your home dir on the remote host is called /home/netrix). Be aware that this command will overwrite any existing remote .ssh/authorized_keys2 file (rather than appending to it) - is that really what you want? If not, you should consider using **ssh-copy-id** instead

```

NAME
       ssh-copy-id  -  install  your  public  key in a remote machine's autho&#8208;
       rized_keys

SYNOPSIS
       ssh-copy-id [-i [identity_file]] [user@]machine

DESCRIPTION
       ssh-copy-id is a script that uses ssh to log into a remote machine  and
       append  the  indicated  identity  file  to that machine's ~/.ssh/autho&#8208;
       rized_keys file.

       If the  -i  option  is  given  then  the  identity  file  (defaults  to
       ~/.ssh/id_rsa.pub) is used, regardless of whether there are any keys in
       your ssh-agent.  

```

---

### Post by Lars Noodén on 2014-05-04
The file *authorized_keys2* has been deprecated since OpenSSH version 3.0:  [http://www.openssh.com/txt/release-3.0](http://www.openssh.com/txt/release-3.0)
You can put the public keys in *authorized_keys* instead.  

However, as mentioned [ssh-copy-id](manpages.ubuntu.com/manpages/trusty/en/man1/ssh-copy-id.1.html) should take care of things for you.

---

### Post by netrix-g on 2014-05-05
Many thanks for moving the post, and for the replies above :)

I can now successfully ssh to my server, no doubt I'll be back here with more questions as I work my way through the tutorial.

Have a great day

R.
Netrix

---

### Post by netrix-g on 2014-05-09
I'm back with another RSA keys problem - I'll append to this thread but may start another if no one "sees it" :-)

I successfully set up ssh and was able to remote to my HP server from my mac. I was having issues with permissions and Samba and Netatlk so decided to start again with the server install. I reinstalled Ubuntu Server 14.04 and started to follow the guide again [[tutorial]("http://ubuntuforums.org/showthread.php?t=1895084")]

All was well until I got to the SSH when I tried to generate the rya keys from my MAC again;

entering this command on the MAC 
scp -P 2xxxx ~/.ssh/id_rsa.pub [email]netrix@192.168.xxx.xxx:.ssh[/email]/authorized_keys2

Gives me the following error:

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
16:f3:19:38:27:d3:xx:a0:09:xx:77:26:xx:3a:33:ba.
Please contact your system administrator.
Add correct host key in /Users/Netrix/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/Netrix/.ssh/known_hosts:3
RSA host key for [192.168.xxx.xxx]:2xxxx has changed and you have requested strict checking.
Host key verification failed.
lost connection

Can anyone give me a heads up on how to add the correct host key to /Users/Netrix/.ssh/known_hosts in order to move forward ?

Many thanks in advance

Regards

Netrix

---

### Post by Lars Noodén on 2014-05-09
If you did reinstall and didn't carry the server's keys forward to the new installation, then you'll have to update your client's known_hosts file.

First, on the server itself, double check the key fingerprint.

```

ssh-keygen -lf /etc/ssh/ssh_host_rsa_key

```

Make sure that is the one you are getting when connecting with the client.  

If it is, then you can edit ~/.ssh/known_hosts.  The error message tells you which line.

```

Offending RSA key in /Users/Netrix/.ssh/known_hosts:3

```

That error tells you which file to edit and which line to remove from it.  In that case it is the third line.  If you do not want to remove the key manually, you should also be able to use [ssh-keygen](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html) to remove the problematic key.

```

ssh-keygen -R [192.168.xxx.xxx]:2xxxx 

```

That will remove that key from known_hosts and store it in known_hosts.old

---

### Post by netrix-g on 2014-05-09
Thank you for the speedy reply !!

I removed the offending line and all is well :)

I'm very impressed with Ubuntu and really really impressed with how little system resource it uses. Having been a life long Windoze user it is a very steep learning curve !!

Thanks again for your time

Regards

Netrix.

---

### Post by netrix-g on 2014-05-09
*UPDATE*    I spoke too soon !!!

I did a bunch of programming for MSMTP (which didn't work :( ) so I thought I'd reboot the server with the sudo reboot command.

When it finished rebooting I logged in via the keyboard on the server - and tried to ssh from the MAC and get the following error

Permission denied (publickey)

The only changes I made were to msmtp and wring a few scripts for cron to use (as per the tutorial)

This learning curve is getting steeper by the minute !!

Regards

Netrix

It seems I added a line to the ssh config file too - (as per the tutorial) 
passwordauthentication no


I just hashed this out and I can now ssh from the MAC

---

### Post by Lars Noodén on 2014-05-09
When you reinstalled, did you wipe the whole machine or were the user directories left intact?  If you erased the directories, then you'll have to copy the public key to the server again.

---

### Post by netrix-g on 2014-05-09
Lars, I did wipe the whole machine and then followed the tutorial from this site [tutorial]("http://ubuntuforums.org/showthread.php?t=1895084") 

In the ssh conf file I had the following set 
[COLOR=#000000]passwordauthentication no[/COLOR] I commented this out and could then ssh from MAC to server.

I am now struggling to get Ubuntu to send emails etc. I have tried ssmtp and msmtp to use a Gmail account, and get similar problems;

currently, with ssmtp programmed, if I type;
echo 'Hello from Server' | mail -s 'Hello from Server' [EMAIL="myusername@gmail.com"]myusername@gmail.com[/EMAIL]

I get the following error;
mail: cannot send message: Process exited with a non-zero status

Googling hasn't helped me thus far ……. do you have any pointers that would help me ?

Regards

Netrix

---

### Post by spynappels on 2014-05-11
Hi,

I'd recommend that you start a new thread for this question, so that the thread title reflects the issue, you may find you get more answers that way ;)

In general terms, you need to check whether you can reach the smtp server and what it's telling you when you try to connect. Without more data it's hard to say what's going on, but I think the most likely reason is authentication failure.

Regards,
Stefan

---

