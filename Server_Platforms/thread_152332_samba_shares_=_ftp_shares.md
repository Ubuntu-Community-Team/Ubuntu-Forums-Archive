---
title: "samba shares = ftp shares"
date: 2006-03-29
forum: Server Platforms
---

### Post by gaspedalo on 2006-03-29
Hi I'd like to have the samba shares of our server to be available over internet, just like in the lan. I thought I would fire up a small ftpd, do a little config (less than 5 minutes) and done. But then came reality ;-)
So my question is there an easy way to achieve this?

---

### Post by chuckyp on 2006-03-29
vsftp  Should do the trick with about 5 minutes of config.

---

### Post by echo $USER on 2006-03-29
[QUOTE=chuckyp]vsftp  Should do the trick with about 5 minutes of config.[/QUOTE]

He's right, just run "sudo apt-get install vsftpd".  Your directory will be in /home/ftp.  The default settings are very paraniod with just anonymous access with read only.  But you can configure it any way you like using "sudo gedit /etc/vsftpd/vsftpd.conf".

---

### Post by gaspedalo on 2006-03-30
[QUOTE=echo $USER]He's right, just run "sudo apt-get install vsftpd".  Your directory will be in /home/ftp.  The default settings are very paraniod with just anonymous access with read only.  But you can configure it any way you like using "sudo gedit /etc/vsftpd/vsftpd.conf".[/QUOTE]


hm, I've already tried vsftp and I had a look at the config file. Unfortunately I haven't found any good howto, just a list of thousands of options. Could you hint me into the right direction of how sharing folder xy with user z?

---

### Post by echo $USER on 2006-03-30
Here are a couple of sites that I used:

[http://www.vsftpdrocks.org/faq/]("http://www.vsftpdrocks.org/faq/")
[http://vsftpd.beasts.org/vsftpd_conf.html]("http://vsftpd.beasts.org/vsftpd_conf.html")

So if you wanted user z to access folder xy:
Create an account for user z and a home directory /home/z
Enable local user login in the vsftpd.conf and save 
then run "sudo /etc/init.d/vsftpd restart"
Then user z can log in and access /home/z

You should also disable anonymous log in, and with th e default setting user z will only have execute and read privilages until you enable write in vsftpd.conf.

Hope this helps.

---

### Post by gaspedalo on 2006-03-31
[QUOTE=echo $USER]So if you wanted user z to access folder xy:
[/QUOTE]

Helps a lot, thank you.
You describe how user z gets access to folder z, unfortunately you forgot to mention how he gets to folder xy :mrgreen: and exactly that is my biggest problem.
I'll try using symbolic links.

---

### Post by gaspedalo on 2006-03-31
found it. creating a symbolic link totally does the trick. I am amazed!

---

### Post by echo $USER on 2006-03-31
Could you give me a link or just explain symbolic links?  i dont know myself, i'd like to find out.  Thanks

---

### Post by gaspedalo on 2006-04-05
[QUOTE=echo $USER]Could you give me a link or just explain symbolic links?  i dont know myself, i'd like to find out.  Thanks[/QUOTE]
just do 
ln -s \directory\xy linkname
in the folder you can reach from ftp. Then you can follow the symolic link if the rights are done carefully.

---

