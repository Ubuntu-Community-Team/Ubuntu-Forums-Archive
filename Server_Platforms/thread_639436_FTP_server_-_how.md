---
title: "FTP server - how?"
date: 2007-12-13
forum: Server Platforms
---

### Post by renzokuken on 2007-12-13
Hi,

I have a PDC running feisty that my boss wants me to create a folder on that someone in another country can access with ftp and download the files within that folder.

Sadly, i have no idea how to do this since i've never done any ftp configuration before.

Can anyone point me in the right direction?

Thanks

Rob

---

### Post by dboot on 2007-12-13
I use proftpd. Here are the guides that helped me:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server")

[http://archiv.debianhowto.de/en/proftpd/c_proftpd.html]("http://archiv.debianhowto.de/en/proftpd/c_proftpd.html")

Good luck!

---

### Post by sbodas on 2007-12-13
A simple and secure solution would be to use sftp.  All you'd need to do is create an account on the server and set a password.  Put whatever you want to share in /home/${FTP_USER}, and they'll be able to download via sftp or scp.

If you want to restrict the user to sftp and scp, you can use rssh ([http://www.pizzashack.org/rssh/](http://www.pizzashack.org/rssh/))

The Gentoo wiki has a tutorial about setting it up: [http://gentoo-wiki.com/HOWTO_SFTP_Server_(chrooted,_without_shell](http://gentoo-wiki.com/HOWTO_SFTP_Server_(chrooted,_without_shell))

---

### Post by renzokuken on 2007-12-13
i think i have it set up using vsftpd now. if this doesnt work i'll try proftpd

i installed vsftpd, added a new user and a folder for ftp to use. when i try logging in via fireftp though i get "Unable to make connection" error.

i think i'm using the wrong hostname/domainname. what should i be using and is there an easy way to find this out from the server?

thanks

---

