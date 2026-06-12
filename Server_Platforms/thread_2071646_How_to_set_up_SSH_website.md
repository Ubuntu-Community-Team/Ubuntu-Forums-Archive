---
title: "How to set up SSH website"
date: 2012-10-16
forum: Server Platforms
---

### Post by JD32 on 2012-10-16
I know there is probably already a thread on this or even an article on the web but i cant seem to find what i need and i don't exactly know how to phrase it to find the info i need. 

I have a home SSH server running with a domain and everything. I can access remotely via Ubuntu, Filezilla etc. I want to create my own little website to get in and browse, make changes and download from any computer via a web browser without the need for extra software. How do i go about this?

Thanks

---

### Post by chadk5utc on 2012-10-16
not sure exactly what it is you want to do? if your looking to setup a web server there are tons of guides and howto's for this here's one [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by sandyd on 2012-10-16
You will need a web server in addition to the SSH server.

The web server will serve the files, and you can upload the files via ssh.

Note that if you want a domain like **ubuntuforums.org** - you will have to pay for it. Otherwise, there are quite a lot of free places that offer free subdomains

---

### Post by HermanAB on 2012-10-16
Webmin

---

### Post by volkswagner on 2012-10-16
There are web based ssh softwares such as [sshterm]("http://sshterm.com/forum/").

I have not used it so I can't comment.  You can also find others by searching "web based ssh client".

---

### Post by ubhi on 2012-10-16
Webmin is best for your purpose as suggested by HermanAB.... you need to open https 10000 port at your place from where you want to access it....

---

### Post by JD32 on 2012-10-16
i already have a domain from dyndns.com... that gets me in the right direction, ill try webmin i think thats what i want. Is webmin that same as using Apache?

---

### Post by chadk5utc on 2012-10-16
webmin is more of an administration interface for servers where apache is the actual www server(serves html content)

---

### Post by JD32 on 2012-10-17
Well i got webmin up and running. Still kinda lost on how to use it tho. Got Apache set up and my domain pointing to the web server. How do i share files to download? (for example) i want to be able to login from say school and download a document i may have been working on at home. Do i use SSH or do i need to install a FTP module or something?

---

### Post by CharlesA on 2012-10-18
It would probably be easier (and more secure) to just use something like DropBox or the like.

If you want to download the files via apache, you would need to make them acessible to the public (unless you only allowed your IP address to connect). You would be better off with using SFTP or Dropbox as suggested earlier.

---

### Post by Lars Noodén on 2012-10-18
> **JD32 said:**
> Do i use SSH or do i need to install a FTP module or something?

If you have SSH server installed, then you already have SFTP and don't need (or want) FTP.  

You can get to your server via Nautilus or Dolphin by pressing ctrl-L and then entering the URI for that machine.  It will be something like this:  sftp://user@xx.yy.zz.aa/ where you substitute the right user name and ip number or hostname.

---

### Post by anonymouschief on 2012-10-19
Ah, you mean that you would like to access files on your server without using SSH or SFTP, and you would like to access those files through a web browser.

Take a look at OwnCloud:
Home Page: [http://owncloud.org/](http://owncloud.org/)
Install instructions: [http://owncloud.org/support/install/](http://owncloud.org/support/install/)

---

