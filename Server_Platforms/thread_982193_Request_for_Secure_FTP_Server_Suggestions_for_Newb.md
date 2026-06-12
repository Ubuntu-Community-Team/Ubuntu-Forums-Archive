---
title: "Request for Secure FTP Server Suggestions for Newbie"
date: 2008-11-14
forum: Server Platforms
---

### Post by paiwacket on 2008-11-14
Ubuntu Server 8.04 intel

Can anyone offer clarification/suggestions of the various ftp servers that appear when get apt is run from webmin?

I seek  secure ftp that covers at least control. Secure control AND data might be preferable. 

Thanx,  -Barry

---

### Post by hictio on 2008-11-14
You mean "secure" as in the FTP session being encrypted with SSL?
If so, I had pretty good experiences setting up [ProFTPD with SSL](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html), it wasn't on an Ubuntu Server, tho.

---

### Post by cdenley on 2008-11-14
> **hictio said:**
> You mean "secure" as in the FTP session being encrypted with SSL?
If so, I had pretty good experiences setting up [ProFTPD with SSL](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html), it wasn't on an Ubuntu Server, tho.

I had bad experiences using ProFTPD with an SSL certificate. It would stop working every month. Once I replaced my CA-signed password-protected certificate with a self-signed passwordless one, it worked fine.

The original poster mentioned apt and webmin. Are you running an FTP server, or connecting to an FTP repo? How do apt and webmin relate to secure FTP?

---

### Post by HermanAB on 2008-11-14
FTP, per definition isn't secure.  If you want secure file transfer, then the best way to do it is with OpenSSH.

Cheers,

Herman

---

### Post by paiwacket on 2008-11-14
Perhaps my newbie description isn't clear. Within Webmin, to install software packages from APT I click on 'search APT'. Searching  for 'FTP Server' reveals a plethora of choices, hence my question here.

-Barry

---

### Post by inphektion on 2008-11-14
search for vsftp.  I use it on a public ftp server and it is in fact very secure.  Not ssl ( I don't use that ). but i use chrooted virtual users and never had a problem with reliability, speed, security, etc.

---

### Post by cdenley on 2008-11-14
> **inphektion said:**
> search for vsftp.  I use it on a public ftp server and it is in fact very secure.  Not ssl ( I don't use that ). but i use chrooted virtual users and never had a problem with reliability, speed, security, etc.

Without SSL, there is no encryption involved. This means that tranfers and more importantly passwords are sent in plaintext over the internet. That is most definitely NOT secure.

VSFTPD and ProFTPD both support SSL encryption, and are the most common FTP servers used in Linux. If the server is just for you to transfer files, then I would use ssh as HermanAB suggested.

---

### Post by rev0lv3r on 2008-11-15
Remember that SFTP is different from FTPS.

I found setting up an ftp server (even with the assistance of Webmin) a little too much overkill for me.
If it were as simple as BPFTP, FileZilla Server, or Serv-U on Windows, then maybe I could've gone somewhere
Alas, I just used OpenSSH. It allowed me to use the built-in system user accounts and works no matter where I go and how I access (win/mac/linux...)
The only disadvantage is on high-throughput connections, ssh is much slower than FTP. FTP easily will saturate the hdd bottleneck, while SSH seems to max out at around 200k/s.

---

### Post by cdenley on 2008-11-15
> **rev0lv3r said:**
> Remember that SFTP is different from FTPS.

I found setting up an ftp server (even with the assistance of Webmin) a little too much overkill for me.
If it were as simple as BPFTP, FileZilla Server, or Serv-U on Windows, then maybe I could've gone somewhere
Alas, I just used OpenSSH. It allowed me to use the built-in system user accounts and works no matter where I go and how I access (win/mac/linux...)
The only disadvantage is on high-throughput connections, ssh is much slower than FTP. FTP easily will saturate the hdd bottleneck, while SSH seems to max out at around 200k/s.

If you need a GUI to configure your FTP server, you can try gproftpd. The reason ssh is slower is because of the encryption. If you're transferring between two fast computers, it goes much faster.

---

### Post by daboroe on 2008-11-15
use an openssh server. it is more secure and easy to set up.

---

### Post by hictio on 2008-11-15
> **daboroe said:**
> use an openssh server. it is more secure and easy to set up.

Indeed it is  (for a personal server).
If you have to give access to people you don't trust, or people that does not know anything about Linux (unless you run your SSH server chrooted) you are basically giving that people a shell account to your system.

---

### Post by daboroe on 2008-11-15
how do you do it chrooted? I installed mine through when it asks to install LAMP, OpenSSH, etc

---

### Post by cdenley on 2008-11-16
> **daboroe said:**
> how do you do it chrooted? I installed mine through when it asks to install LAMP, OpenSSH, etc

MySecureShell has been suggested before, and apparently intrepid has a ChrootDirectory option.
[http://ubuntuforums.org/showthread.php?t=943200](http://ubuntuforums.org/showthread.php?t=943200)
I think a chroot gives admins a false sense of security. If someone gets root inside a chroot, it is really easy to get root outside a chroot. A restricted shell like scponly is probably more important.

---

### Post by morningboat on 2008-11-21
> **rev0lv3r said:**
> Remember that SFTP is different from FTPS.

I found setting up an ftp server (even with the assistance of Webmin) a little too much overkill for me.
If it were as simple as BPFTP, FileZilla Server, or Serv-U on Windows, then maybe I could've gone somewhere
Alas, I just used OpenSSH. It allowed me to use the built-in system user accounts and works no matter where I go and how I access (win/mac/linux...)
The only disadvantage is on high-throughput connections, ssh is much slower than FTP. FTP easily will saturate the hdd bottleneck, while SSH seems to max out at around 200k/s.

I think web admin should be fine for most users. If you want to have a simpler server to install and provide FTPS/TLS, you can have a look at [CrossFTP Server]("http://www.crossftp.com/"), It looks similar to FileZilla Server, etc. There is a guide for installation: [url="http://www.youtube.com/watch?v=bg3GBEeSm9U"]
How To Set Up An FTP Server[/url]

---

