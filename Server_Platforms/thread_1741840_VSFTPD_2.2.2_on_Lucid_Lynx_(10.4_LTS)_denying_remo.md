---
title: "VSFTPD 2.2.2 on Lucid Lynx (10.4 LTS) denying remote access"
date: 2011-04-28
forum: Server Platforms
---

### Post by Eldarrion on 2011-04-28
I'm running into an issue with my VSFTPD configuration. I've been running it for about a year or so now without issues. About a week ago, when I needed to add a new user, everything seemed fine... until all users started reporting that they are unable to connect. I tried testing the configuration locally (SSH to the box, then ftp to localhost) and connection was working fine with the latest user I added. Following that, I attempted to connect remotely and that's when I discovered that the users weren't just imagining the issue. The moment a user name is given after connecting to the FTP server, the connection drops. I'm thinking it is an issue with PAM... or specifically, VSFTPD not going to PAM when connecting from a remote location (on eth1). Checking the PAM logs in /var/log/auth.log showed that suspicion to be on track as there was nothing added to the file when I tried to connect using the external IP address. The moment I attempted connection on an internal IP (192.168.x.x, eth0) I managed to connect without issues again. After pulling my hair for several hours, I seem to be completely unable to figure out where the problem is coming from or how to resolve it.

Here are the contents of my vsftpd.conf:

```

listen=YES
anonymous_enable=NO
local_enable=YES
virtual_use_local_privs=YES
write_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
guest_enable=YES
user_sub_token=$USER
local_root=/home/ftpmaster/$USER
chroot_local_user=YES
hide_ids=YES
user_config_dir=/etc/vsftpd/
anon_upload_enable=YES
log_ftp_protocol=YES

```And the contents of /etc/pam.d/vsftpd:

```

auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
auth    required        pam_pwdfile.so pwdfile /etc/vsftpd/passwd
account required        pam_permit.so

```If anyone is able to point me in the right direction as to what I might be doing wrong or why VSFTPD seems to be bypassing PAM when the connection comes from eth1 but not from eth0, I'd be very grateful.

---

### Post by Lars Noodén on 2011-04-29
Since you already have SSH running why not just use SFTP instead?

It's already there and needs no further configuration for basic use for secure file transfer.

---

### Post by Eldarrion on 2011-04-29
Bit of an annoyance when trying to explain to the average Joe user about SFTP. Heck, it took several hours to try to explain to a web designer how that works and all he had to do was click a single check box on Dreamweaver. Otherwise I wouldn't be bothering... plus there's the whole thing that it was working... and now isn't anymore without any configuration changes on my part... overall not a nice situation to be in.

---

### Post by Lars Noodén on 2011-04-29
It may be faster and easier to explain SFTP than diagnose and repair FTP, especially if it is already there.  If nothing else it is a work-around until you can repair FTP, or not.

---

### Post by Eldarrion on 2011-04-29
That may well be true, but when your boss comes in and makes the claim that your FTP doesn't work because user X didn't follow the simple instructions you've provided to connect to SFTP with five different free FTP clients it tends to be a nuisance in and of itself. Even more so when he gives up and goes: "Make it work for FTP."

I don't know, maybe I'm just the lucky one to get the users that don't follow instructions and simply go and say "It doesn't work" rather than reading the full e-mail. Believe me, when someone reported how the VSFTPD wasn't working, my first reaction was that they're doing something wrong as it's become common practice at this point. Yes, I have SSH running and users can connect via SFTP... and I had already prepared the e-mails to send to current users. Either way, I certainly wouldn't mind solving the issue as well. Would probably save me a nice lot of trouble in the long run, but I'm stumped... and any kind of diagnostics I've thought to run so far have proven less than helpful in the matter.

---

### Post by Lars Noodén on 2011-04-29
For clarification, you can connect and log in from localhost using FTP.  From a remote host you can connect initially but not complete a log in, right?

---

### Post by Eldarrion on 2011-04-29
I can connect and login from localhost and from the internal network on eth0. I can connect externally (eth1), but get disconnected the moment I type in the user name. Checking /var/log/auth.log for info from PAM, I see login attempts to the FTP server that are coming in on eth0/localhost, but nothing gets logged when I'm connecting on eth1. Makes me think it is an issue with VSFTPD not sending data to PAM when connected to on the eth1 interface. Still, I might be wrong.

---

### Post by Eldarrion on 2011-04-29
To add insult to injury, ftp-ing in from another linux machine works without a hitch on both interfaces. FTP-ing in from a Windows machine, on the other hand, does not. Baffling to say the least.

---

### Post by 3L33T on 2011-04-29
Are the remote users ftp'ing from windows command line? or using IE?

On IE, try logging into your ftp server using this URL:

> 
   ftp://username@<ip address>


---

### Post by Eldarrion on 2011-04-29
It would seem that I owe the community an apology. As it turned out in the end, the issue was caused by a bug in the Astaro firewall firmware. Not sure how exactly they managed to produce a bug like that, but updating the firmware solved the problem. Thanks to all that tried to help.

---

### Post by 3L33T on 2011-04-29
> **Eldarrion said:**
> It would seem that I owe the community an apology. As it turned out in the end, the issue was caused by a bug in the Astaro firewall firmware. Not sure how exactly they managed to produce a bug like that, but updating the firmware solved the problem. Thanks to all that tried to help.

Apology accepted.

Now, go download 11.04 and post back your thoughts re: UNITY ;)

---

### Post by Eldarrion on 2011-04-29
I was actually working on that after the issue got resolved. Not sure why I went with LTS in the first place, but eh... either way. I still say they should have went with "Naughty Newt" for a name, though. ;)

---

