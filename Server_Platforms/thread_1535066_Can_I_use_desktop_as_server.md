---
title: "Can I use desktop as server  ?"
date: 2010-07-20
forum: Server Platforms
---

### Post by hoboy on 2010-07-20
I really don't what to do or even what is the right question to ask.
I want to access my pc at home over the internet, I have an ip from a hoster that will host the pc, but physically the pc will be at home in my place.
I have some documents on my pc that I want to access from outside over the internet.
Can I use ubuntu destop on my home pc then access to it with vpn ?
or do I need a ubuntu server installed ?

---

### Post by CharlesA on 2010-07-20
You can use ubuntu desktop to serve files, yes.

There isn't a need to use the server install for that.

---

### Post by hoboy on 2010-07-20
> **CharlesA said:**
> You can use ubuntu desktop to serve files, yes.

There isn't a need to use the server install for that.

thanks so I will only need to install desktop.
then have an ip configured for it, then vpn to it ?
I am right ?
if so why have the server version of ubuntu ?

---

### Post by Bachstelze on 2010-07-20
> **hoboy said:**
> 
if so why have the server version of ubuntu ?

Because not everyone fancies a full desktop running on their server.

---

### Post by cj.surrusco on 2010-07-20
If you want to simply access files from other locations, a FTP server would probably be a way to go. You can set that up on a desktop install with clients such as vsftpd or proftp.

---

### Post by pricetech on 2010-07-20
FTP would work, but security is an issue.  SSH is secure and allows for both file access and remote control of the computer.

You'll need to forward a port through your router so your external IP will connect to the internal IP assigned to your home Linux box.

---

### Post by nmaster on 2010-07-20
doing what you want is pretty simple with ssh/sftp, but....

if you feel intimidated or if you don't really know what you're doing (as described in your original post) why not try using something like google docs or ubuntu one.  as long as the data isn't sensitive, allowing someone else to store it in a cloud might make your life easier.

---

### Post by hoboy on 2010-07-20
> **neal.m.master said:**
> doing what you want is pretty simple with ssh/sftp, but....

if you feel intimidated or if you don't really know what you're doing (as described in your original post) why not try using something like google docs or ubuntu one.  as long as the data isn't sensitive, allowing someone else to store it in a cloud might make your life easier.

Thanks for the idea you have put.
My intention is to learn how to set a private server in home environment, then it is good to start slowly.

---

### Post by drdos2006 on 2010-07-20
I found this howto very, very useful.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

