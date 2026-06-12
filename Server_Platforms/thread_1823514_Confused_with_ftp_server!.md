---
title: "Confused with ftp server!"
date: 2011-08-12
forum: Server Platforms
---

### Post by ghelis on 2011-08-12
Hello,i am a bit (or totally confused here!).

I have some questions:

1) I want when someone trying to access my ftp domain(not from my home network) ,to ask him for username and password.

2) What is the difference between filezilla and vsftpd?They do the same job?(Ok,i added a user with vsftpd and now,what?)
(Filezilla works and i can upload files)

3) When someone tries to connect to my domain(outside of my home network) it shows the "It works" page.When i access my domain from my pc it shows me the files i uploaded!How can i fix this???

4) When i try to connect via another pc (in my home) ,it shows the routers interface!

5) Filezilla works with SSH but when i try with FTP or when i use the wizard connection manger it shows the "connection timed out"
I use shorewall and in the shorewall/rules i have "HTTP..SSH...FTP".

Thank you!

---

### Post by Ozymandias_117 on 2011-08-12
> **ghelis said:**
> Hello,i am a bit (or totally confused here!).

I have some questions:

1) I want when someone trying to access my ftp domain(not from my home network) ,to ask him for username and password.

2) What is the difference between filezilla and vsftpd?They do the same job?(Ok,i added a user with vsftpd and now,what?)
(Filezilla works and i can upload files)

3) When someone tries to connect to my domain(outside of my home network) it shows the "It works" page.When i access my domain from my pc it shows me the files i uploaded!How can i fix this???

4) When i try to connect via another pc (in my home) ,it shows the routers interface!

5) Filezilla works with SSH but when i try with FTP or when i use the wizard connection manger it shows the "connection timed out"
I use shorewall and in the shorewall/rules i have "HTTP..SSH...FTP".

Thank you!

1. You'll have to modify the config files to not allow annonymous FTP usage.

2. Filezilla is a program for connecting to FTP servers, vsftpd is a FTP server daemon.

3. Sounds like you're connecting to [http://yourdomain.com](http://yourdomain.com) from outside instead of [ftp://yourdomain.com](ftp://yourdomain.com)  You will probably have to mess with your router config to forward ports 20 and 21 to your server.

4. See above answer.

5. If you can't connect to your FTP server in the first place, of course Filezilla is going to time out...

---

### Post by ghelis on 2011-08-12
> 1. You'll have to modify the config files to not allow annonymous FTP usage.

1) Where these config files are located?

> 3. Sounds like you're connecting to [http://yourdomain.com](http://yourdomain.com) from outside instead of [ftp://yourdomain.com](ftp://yourdomain.com) You will probably have to mess with your router config to forward ports 20 and 21 to your server.

3)  When someone tries to connect(outside of my home ) to [ftp://mydomain](ftp://mydomain) , it doesn't connect.Also, the same if i try from my pc.(But with [http://domain](http://domain) ,(from my pc)it works).

> 5. If you can't connect to your FTP server in the first place, of course Filezilla is going to time out...

5) Obviously sth with the question 3) above?

Thanks for the help.

---

### Post by Ozymandias_117 on 2011-08-12
> **ghelis said:**
> 1) Where these config files are located?



3)  When someone tries to connect(outside of my home ) to [ftp://mydomain](ftp://mydomain) , it doesn't connect.Also, the same if i try from my pc.(But with [http://domain](http://domain) ,(from my pc)it works).



5) Obviously sth with the question 3) above?

Thanks for the help.

1. It will be in /etc I always used proftp, so I don't know the filename, just use ```
ls /etc/*ftp*
``` and you should find it

3. That makes it sound like FTP isn't actually working at all and you're transferring files over HTTP.  So... with that in mind, where did you PUT the files you're trying to transfer?

---

### Post by ghelis on 2011-08-12
> It will be in /etc I always used proftp, so I don't know the filename, just use 
Code:
ls /etc/*ftp*

This gives me the vsftpd.conf file in which i have selected "anonymous=NO"

> 3. That makes it sound like FTP isn't actually working at all and you're transferring files over HTTP. So... with that in mind, where did you PUT the files you're trying to transfer?

I forgot to mention that i use ubuntu server in virtualbox.
So,with filezilla i take files from my host and put them in a directory in the guest.
(the ssh connections works,but as i said the ftp no)

---

### Post by Lars Noodén on 2011-08-12
> **ghelis said:**
> the ssh connections works...

If you have SSH, then SFTP is already installed and configured.  So you can try SFTP instead of FTP.  It will simplify life a lot to remove the FTP server.

---

### Post by ghelis on 2011-08-12
> If you have SSH, then SFTP is already installed and configured. So you can try SFTP instead of FTP. It will simplify life a lot to remove the FTP server.

If i try sftp://domain in the opera browser it doesn't load (as with ftp)and from the firefox it says "Firefox doesn't know how to open this address, because the protocol sftp isn't associated with any program."

---

### Post by Lars Noodén on 2011-08-12
> **ghelis said:**
> If i try sftp://domain in the opera browser it doesn't load (as with ftp)and from the firefox it says "Firefox doesn't know how to open this address, because the protocol sftp isn't associated with any program."

Try it in Nautilus or another file manager.

---

### Post by ghelis on 2011-08-12
> Try it in Nautilus or another file manager.

It works with ssh but still not with ftp.

---

### Post by Lars Noodén on 2011-08-12
> **ghelis said:**
> It works with ssh but still not with ftp.

Try SFTP in Nautilis or another file manager.

---

### Post by ghelis on 2011-08-12
Yes,i tried it in nautilus.

---

### Post by ghelis on 2011-08-12
Ok,it works!
I assume i didn't have the filezilla opened when trying to access ftp address.But the http worked!

---

