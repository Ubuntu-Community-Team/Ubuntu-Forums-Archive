---
title: "Ftp server"
date: 2009-01-20
forum: Server Platforms
---

### Post by FiskFisk33 on 2009-01-20
I am running a 8.10 server and i want to set up a ftp server on it

what do i download?

---

### Post by ibutho on 2009-01-20
Hi. You can install proftpd or vsftpd for an ftp server. Take a look [here]("http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html") for a guide on setting up an ftp server using proftpd.

---

### Post by FiskFisk33 on 2009-01-20
thanx

how do i set up users?

---

### Post by HermanAB on 2009-01-20
Just install either vsftpd or proftpd.  You don't need to set up anything.  They both work out of the box, just start the service and it should work.  To create a 'ftp user' - simply create a new user account an the user will be able to access his 'home' directory.  So if you want to use a special directory, just define it as the home directory.

Most FTP problems occur when people try to change the default configuration - don't do that - not at first anyway.

Cheers,

Herman

---

### Post by hyper_ch on 2009-01-20
is there a compelling reason why you need a FTP server? I'd rather go for sftp/scp by using openssh-server, system accounts and mysecureshell to limit those users.

---

### Post by FiskFisk33 on 2009-01-20
yes there is a reason
i want people to be able to access the files of a bf2 server i run on it, and people are used to ftp


is there a way to make a users home folder /root/bf2 ?

---

### Post by HermanAB on 2009-01-20
Just run the user wizard and set the home directory for the ftp user to what you want.

---

### Post by FiskFisk33 on 2009-01-20
yea, but when i set it to /root/bf2 it says that it is not allowed (yes i have the UI installed, i run it with startx)

how do i make a user the commandline way?
or atleast edit its home folder

---

### Post by ibutho on 2009-01-20
Instead of putting shared or ftp files in roots home directory, you should put the files you wish to share in a location like /var/ftp.

---

### Post by FiskFisk33 on 2009-01-20
i have my bf2 server installed in /root/bf2 and i want people to be able to manage its files.

---

