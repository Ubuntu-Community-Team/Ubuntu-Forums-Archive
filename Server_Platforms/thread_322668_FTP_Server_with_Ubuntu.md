---
title: "FTP Server with Ubuntu"
date: 2006-12-20
forum: Server Platforms
---

### Post by foxhound_oki on 2006-12-20
Hi, i am a computer specialist and programmer of my school and i need help on how to use ubuntu server as an ftp site, i allready have a ubuntu server as domain controler.  if someone can give me the steps or somewhere to go to that has directions to get ftp server installed and how it works.  aslo will this be able to work outside of my main routers firewall >>>  can people access it from home?

---

### Post by PilotJLR on 2006-12-20
vsftpd is the best choice... check this out:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

People can use it from home it you allow it thru the firewall. Basically, open tcp ports 20 and 21, and do a port forward if this server has a private ip inside a NAT.

---

### Post by chrisfay on 2006-12-20
> Hi, i am a computer specialist and programmer of my school

Then you should know that FTP is terribly insecure.:p  
Unless you're emotionally tied to it, check out SCP or SFTP to take advantage of SSH encryption. Unless of course you have no qualms with username and passwords being sent in the clear.

---

### Post by PilotJLR on 2006-12-21
Well, depends on what you're using it for.

If kiddies are uploading webpages for a CS class, then they may not need 128 bit AES encryption.  :-)

Yeah, SCP is a pretty nice means for secure file transfer, if that's what you need.

---

### Post by chrisfay on 2006-12-21
> If kiddies are uploading webpages for a CS class, then they may not need 128 bit AES encryption.

...
> **chrisfay said:**
> Unless of course you have no qualms with username and passwords being sent in the clear.

---

### Post by PilotJLR on 2006-12-21
Yeah, I read your post too fast  :-)

---

### Post by dannyboy79 on 2006-12-22
> **chrisfay said:**
> Then you should know that FTP is terribly insecure.:p  
Unless you're emotionally tied to it, check out SCP or SFTP to take advantage of SSH encryption. Unless of course you have no qualms with username and passwords being sent in the clear.

not entirely true, you can setup FTP to use SSL/TLS.

---

### Post by chrisfay on 2006-12-22
> not entirely true, you can setup FTP to use SSL/TLS.

You could also tunnel it manually through SSh or a VPN. My point was to highlight its default insecurity and provide valid alternatives. 

The risk of using plain FTP can be reduced substantially through other methods as well, including locking users into their home directories or similar restrictions. But you still have those passwords sent for all to see.

---

### Post by nmincone on 2006-12-22
Foxhound, I apologize for the other posters not answering your question. ProFTP is a very good starting point for you. It can be installed through #sudo apt-get proftpd
It can be configured through #sudo apt-get gproftpd as a front end or setup through a config file located in /etc
You'll find lots of info at their project page [located here at proftpd.org/]("http://www.proftpd.org/")
The other suggestions about SFTP, SCP, and SSL are valid though and relatively easy to implement into your ftp server. I hope this helps you a bit.

---

### Post by PilotJLR on 2006-12-22
Not being sarcastic, but I was under the impression I did... the link I provided to the vsftpd howto is pretty straightforward to implement.
I'm not sure which server has a larger install base, but I've been under the impression that vsftpd is considered more enterprise class. RHEL, for example, uses it by default for ftp service.


> **nmincone said:**
> Foxhound, I apologize for the other posters not answering your question. ProFTP is a very good starting point for you. It can be installed through #sudo apt-get proftpd
It can be configured through #sudo apt-get gproftpd as a front end or setup through a config file located in /etc
You'll find lots of info at their project page [located here at proftpd.org/]("http://www.proftpd.org/")
The other suggestions about SFTP, SCP, and SSL are valid though and relatively easy to implement into your ftp server. I hope this helps you a bit.

---

### Post by Brazen on 2006-12-22
I don't think it could have been answered any better than that link PilotJLR provided.  Both Proftp and vsftp are considere enterprise-ready, but vsftp is more popular, probably due to it being lighter and faster and not including a lot of unnecessary features as Proftp.

---

### Post by nmincone on 2006-12-23
PilotJLR, I mean no disrespect :) , it's just the majority of responses were based on implementing security strategies.

---

### Post by dannyboy79 on 2006-12-25
> **chrisfay said:**
> You could also tunnel it manually through SSh or a VPN. My point was to highlight its default insecurity and provide valid alternatives. 

The risk of using plain FTP can be reduced substantially through other methods as well, including locking users into their home directories or similar restrictions. But you still have those passwords sent for all to see.

not true again, when you use TLS/SSL the password is NOT sent thru as plain text.

---

### Post by chrisfay on 2006-12-25
> not true again, when you use TLS/SSL the password is NOT sent thru as plain text.

Of course its not...re-read my post.

> The risk of using plain FTP can be reduced substantially through other methods as well, including locking users into their home directories or similar restrictions. But you still have those passwords sent for all to see.

My comment about passwords in the clear was regarding plain ftp without 'any' added encryption mechanism. I even added on to your suggestion with SSH or VPN. Where did you get your comment from?

FTP IS insecure without aditional configuration modifications. Period.

---

### Post by PilotJLR on 2006-12-25
> **nmincone said:**
> PilotJLR, I mean no disrespect :) , it's just the majority of responses were based on implementing security strategies.

None taken!  :-)
Just wanted to make sure the question was answered okay.

---

### Post by PilotJLR on 2006-12-25
Wow, this really turned into an FTP smackdown.
Basically, install vsftpd or proftp and then use some form of security feature. If you want.


> **chrisfay said:**
> Of course its not...re-read my post.



My comment about passwords in the clear was regarding plain ftp without 'any' added encryption mechanism. I even added on to your suggestion with SSH or VPN. Where did you get your comment from?

FTP IS insecure without aditional configuration modifications. Period.

---

