---
title: "FTP Server over SSL"
date: 2007-07-12
forum: Server Platforms
---

### Post by guilly on 2007-07-12
Quick question, I've managed to setup an ftp server using proftpd, now that i seem to be a little mroe informed it seems like a good idea to enable some sort of security. SSL seems to be the easiest way to approach this, now my question is can i enable SSL without reconfiguring my entire server using vsftp (I think that's what its called) or do i basically have to install other packages and start over??

any other suggestions are welcomed aswell!!!

cheers!!

---

### Post by Wim Sturkenboom on 2007-07-12
I think it can be done with proftpd as well; read the documentation.

I use vsftpd under slackware using SSL.

---

### Post by guilly on 2007-07-12
> **Wim Sturkenboom said:**
> I think it can be done with proftpd as well; read the documentation.

I use vsftpd under slackware using SSL.

Sorry but by read the documentation do you mean the man pages?? for proftp? or is there a readme file of some sort stored inside proftp folder? 



Anyone know forsure if it can be done?

---

### Post by Footballkid4 on 2007-07-12
[http://www.castaglia.org/proftpd/modules/mod_tls.html](http://www.castaglia.org/proftpd/modules/mod_tls.html)

If you used apt-get to install proftpd, it's pretty simple.  If not, I think you have to recompile it with mod_tls.

If you did, edit /etc/proftpd/proftpd.conf and add:

```
<IfModule mod_tls.c>
# Enable the TLS engine
TLSEngine on

# Add support for SSLv2 and TLSv1  If you only want TLS, then just change this to TLSv1
TLSProtocol SSLv23

# Is TLS required on the connection, or just a possibility
TLSRequired off

# Path to files
TLSRSACertificateFile /etc/ssl/certs/ftps.crt
TLSRSACertificateKeyFile /etc/ssl/private/ftps.key

# Whether or not to verify clients connected on an SSL connection
TLSVerifyClient off
</IfModule>
```

---

### Post by hawzor on 2007-07-12
Hey guilly, do you have a specific application in mind, as in, are you intending to host access a lot of anonymous users or something? Or are you using FTP for your own website development, perhaps using something like Dreamweaver or SecureFX to post files?

If the latter, I can highly recommend sFTP which doesn't even require proftpd, hence no SSL/TLS, which, in my experience is the only reasonable FTP server for many apps.

sFTP actually just rides on the sshd, so that is all you really need. It is fast and neat IMHO, and secure without fuss and without muss.

---

### Post by guilly on 2007-07-12
Thanks footballkid, i did use apt-get instal proftp so that should work fine

hawzor,

my only intentions for my ftp is for personal storage and ease of public access when i'm not at home, as well for some of my school collegues to access it for upload or download whatever


so i'm assuming the information that footballkid provided me is the easiest way to do this?

---

### Post by hawzor on 2007-07-12
Er, to my way of thinking, **apt-get remove proftpd **and use sshd is the easiest way. No configs needed.

---

### Post by guilly on 2007-07-12
alright thank you!

---

### Post by nix4me on 2007-07-12
if you don't like ssh server, proftpd with ssl works very well.  I've been running it for over 4 years.

nix4me

---

### Post by Wim Sturkenboom on 2007-07-13
> **hawzor said:**
> Hey guilly, do you have a specific application in mind, as in, are you intending to host access a lot of anonymous users or something? Or are you using FTP for your own website development, perhaps using something like Dreamweaver or SecureFX to post files?

If the latter, I can highly recommend sFTP which doesn't even require proftpd, hence no SSL/TLS, which, in my experience is the only reasonable FTP server for many apps.

sFTP actually just rides on the sshd, so that is all you really need. It is fast and neat IMHO, and secure without fuss and without muss.
Unless something has changed, I do not recommend sFTP. Reason is that it is a mission to jail users to there home directories. And not jailing them to thir home directories allows them to snoop around everywhere,

---

### Post by guilly on 2007-07-13
Ok, So so far i believe my best approach is just simply to configure SSL into my proftpd.conf file....

Nix, what woudl the benefit be by doing SSH, I am currently using remote desktop as well with VNC so would it be an advantage if i were to conifgure an SSH server that way when i remote in i would be secure as well.

Although just for additional information, I do all my administering inside my own LAN, I think on very rare occasions i would remote into my linux box from the outside world

Thanks for the info guys!!

---

### Post by hawzor on 2007-07-13
Yes, I will definitely agree with what Wim said. Jailing is not an option.

But if you are the only user and your password or key security is bulletproof, sFTP's main reward is the immediate availability with literally no setup. Your choice.

---

### Post by guilly on 2007-07-13
> **hawzor said:**
> Yes, I will definitely agree with what Wim said. Jailing is not an option.

But if you are the only user and your password or key security is bulletproof, sFTP's main reward is the immediate availability with literally no setup. Your choice.


There will be other users joining, but to a minimum. 10-20 users max

---

### Post by ruibernardo on 2007-07-13
Hi guilly,

I also agree that SSH is best for SFTP. Since you want to be easy to setup and don't want SSH, here is how I got SFTP with SSL with vsftpd (sorry, never used proftpd).

```
sudo apt-get install vsftpd
```
Edit the configuration file with (maybe you shoud backup this file first, just in case):

```
sudo nano /etc/vsftpd.conf
```In this file, use these settings:

```
# Forbids anonymous login
anonymous_enable=NO
# Allow local users to login
local_enable=YES
# Allow writing
write_enable=YES
```To chroot users, use one of these options:

```
# 1. All users chrooted by default:
chroot_local_user=YES
chroot_list_enable=NO

# 2. Just some users are chooted:
chroot_local_user=NO
chroot_list_enable=YES
# add a list in /etc/vsftpd.chroot_list with the users that should be chrooted.

# 3. Just some users are "free":
chroot_local_user=YES
chroot_list_enable=YES
# add a list in /etc/vsftpd.chroot_list with the users that should be "free".
```For SSL:

```
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
```Restart vsftpd:

```
sudo /etc/init.d/vsftpd restart
```

I think that's it.

---

### Post by frodon on 2007-07-13
I'm curious to know how you can create a TLS/SSL encryption without creating a certificate or maybe i'm missing something.

Anyway the best encryption for FTP according to many expert sites is TLS encryption, if you want to set it with proftpd i wrote guide, you just need to create a certificate and make proftpd use it, all is explained here :
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by guilly on 2007-07-13
epimeteo, 

thanks for the help... 

what would the difference be with continuing with my current configuration with proftp using TLS like frodon mentions or just starting over with vsftp using SSL

Frodon, i used your how to to create my ftp and it was excellent much appreciated.... the only reason i'm researching SSL is because that is what i was introduced to in school? TLS i've read abotu but unfamiliar

if someone could give me a break down about the major differences and what would be best for my situation that would awsome

thanks!!

---

### Post by ruibernardo on 2007-07-13
> **frodon said:**
> I'm curious to know how you can create a TLS/SSL encryption without creating a certificate or maybe i'm missing something.



Hi frodon, 

there is no need to create the ssl certificate with vsftpd. The vsftpd package and it's configuration uses the "snakeoil" certificalte that comes installed by default with Ubuntu. You just need to enable the options in the configuration file as I posted.

If you try it like posted, with the options I've suggested, and use "ftp-ssl" command (sudo apt-get install ftp-ssl), not ssh's "sftp" command, it works "almost" out of the box (almost, because you got to tweak vsftpd to not use anonymous login).

But yes, certainly proftpd will do the work too.

---

### Post by nix4me on 2007-07-13
im my opinion, vsftpd is crap.  proftpd is much better.  and yes, a TLS encryption is the way to go.  creating a certificate is easy.  just read the very well written howto on the forums.

nix4me

---

