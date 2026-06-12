---
title: "Ubuntu Server, SSH web access, SFTP, and port forwarding"
date: 2014-12-10
forum: Server Platforms
---

### Post by scott.bouch on 2014-12-10
Hello, 

This is my first post, so I hope it's in the right place...

I have recently set up a headless Ubuntu Server (14.04) at home, and lovely it is too.

It's currently running the great Zoneminder software to monitor and record my CCTV. LAMP is installed, as Zoneminder is web-based, so on my LAN I can view the website hosted on the server. All installed over SSH locally.

I also am using it as a PLEX Media Server, and have successfully set up port forwarding in my router to allow me to listen to my music while at work.. All installed over SSH locally.

Now, I want to achieve a few other things, but am having difficulty with gaining access over the internet..

I'd like to achieve:
[LIST]
[*]FTP (SFTP). 
[*]View a home-hosted website (I can see the Apache "it Works" page on my LAN at home, but can't get the port forwarded). 
[*]View my Zoneminder website across the web (but password protected). 
[*]Remote (over the web) SSH terminal. 
[/LIST]

Router: TalkTalk Huawei HG533

I've port-forwarded what I believe to be correct:
 
[LIST]
[*]22 to internal port 22 for SSH (fails) 
[*]Port 80 to internal port 80 for websites (fails) 
[*]Port32400 to internal port 32400 for PLEX, (this works well) 
[/LIST]

I don't yet have a DDNS account, but have been testing using my external IP address from my home (I assume this should work) and have tried it from work. Just wanted to prove it works before paying for a DDNS account.

I've been trying to no avail:
```

user@laptop:~$ssh -p 22 user@##.###.###.##
ssh: connect to host ##.###.###.## port 22: Connection timed out

```

I can SSH quite happily on my LAN. I don't know if Ubuntu comes with a firewall that blocks these ports or not by default..?

When using Firefox to try and remotely access ##.###.###.##:80, it just times out.. I was hoping for the default Apache "It Works" page..

I'm fairly new-ish to Linux (a year or two), but am gaining confidence, so please, just assume I know nothing, and spell out all commands to run as if I'm an idiot... Any help is well appreciated...thanks...

I hope I've given enough info to get started, please tell me if any more info would help...

Thanks, Scott.

---

### Post by slickymaster on 2014-12-10
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by Lars Noodén on 2014-12-10
Is your ISP blocking incoming on ports 22 and 80?  You can check with this scanner: 

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

If so, you might have to move the external forwarding to very high port like you have with PLEX.

---

### Post by scott.bouch on 2014-12-10
Hi Lars,

Thanks, that's a great suggestion (you may well be correct).

I'll try it when I get home (at work currently), as the website doesn't let me change the IP address to my home one.

Thanks, Scott

---

### Post by scott.bouch on 2014-12-10
Thank you Lars, you were correct!

I popped home at lunch time, adjusted my ports and can now:
- SSH remotely!!
- View the default Apache "It Works" web page!

Only trouble now is FTP...

I tried using FileZilla, and I think it's connecting, as I'm not getting a timeout, but am having the connection refused - so I guess I need to allow connections somehow...

```
Status:   Connection attempt failed with "ECONNREFUSED - Connection refused by server".
```

Any help on the FTP front would be great, thanks

---

### Post by Lars Noodén on 2014-12-10
FileZilla can use SFTP.  Just use the "site manager" instead of quick connect.  There you can specify SFTP and the right port.  

Alternately you can use the regular file manager in Ubuntu.  Press ctrl-L and then enter the URI for your server and it will log you in:

```

sftp://user@xx.yy.zz.aa/home/user/Documents/

```

That won't work with keys though, last I checked, and setting the SSH server to ignore passwords and use only keys is a fairly good idea these days.

---

### Post by scott.bouch on 2014-12-10
Thanks again, slightly different results this time with FileZilla:

Status: Connecting to ##.##.###.##:port
Response: fzSftp started
Command: open "user@##.##.###.##" port
Error: Network error: Connection refused
Error: Could not connect to server

---

### Post by Lars Noodén on 2014-12-10
I hardly use FileZilla so I'm not sure how to reproduce your error.  But to get it to where you can log in, try File->Site Manager->New Site->
Then set Host, Port, Protocol, and User and then try "connect".

---

### Post by scott.bouch on 2014-12-10
Yes, that's what I did the second time around, and generated the second error message. I don't mind using alternatives to FileZilla, I just had it to hand!

I also just tried setting up an FTP server in Nautilus from my Ubuntu laptop, and got timeout issues.. (the FileZilla laptop is a W7 machine)

Is three anything I need to do my server to enable SFTP connections?

---

### Post by Lars Noodén on 2014-12-10
SFTP works over SSH and is a built-in part of the OpenSSH server, so if you can log in with SSH you can do the same with SFTP on the same port.  I think it is just a matter of finding the right settings with FileZilla since it does support SFTP quite well.  

As for [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp), it should be avoided except in a few remaining edge cases.  In most cases you can use SFTP.

---

### Post by scott.bouch on 2014-12-10
Thank you Lars for all your help, I'll have another crack at it tonight / tomorrow to see if I can find where I'm going wrong.

Cheers, Scott.

---

### Post by nerdtron on 2014-12-10
If you can ssh to the server you should be able to use sftp on filezilla because sftp just uses ssh. Are you using the correct port in Filezilla?
Just use the IP of the server on the Host field, Username, password and provide the port you use for ssh. Let's see if there's any error.

---

