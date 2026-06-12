---
title: "Noobish: Setting up an FTP server!"
date: 2011-10-11
forum: Server Platforms
---

### Post by DJKEMMET on 2011-10-11
First, I would like to thank the wonderful community on this forum. so far you've all proved to be a welcoming, intelligent and invaluable resource in learning about linux, it's been great.

Though my question today is about setting up an FTP server, I already have ubuntu 11.04 installed on a dell powerspec server and I'd like to set it up with an FTP to host my websites and what not. 

If any of you could give some advice or maybe share a good tutorial you've I'd be incredibly grateful. 

Thanks all!
DJ!

---

### Post by kevinthecomputerguy on 2011-10-11
Now days its better to setup sftp (file transfers over ssh) not to be confused with ftps.
 
Here is a resource to get you going, you can skip most of it if you already have ssh installed.
 
[http://woodel.com/domore/sftp/](http://woodel.com/domore/sftp/)
 
*A great client is FileZilla

---

### Post by Dangertux on 2011-10-11
> **kevinthecomputerguy said:**
> Now days its better to setup sftp (file transfers over ssh) not to be confused with ftps.
 
Here is a resource to get you going, you can skip most of it if you already have ssh installed.
 
[http://woodel.com/domore/sftp/](http://woodel.com/domore/sftp/)
 
*A great client is FileZilla

+1 on SFTP, I personally find it easier and more hassle free than FTP anyway. 

Just my opinion, good luck! :-)

---

### Post by Jonathan L on 2011-10-12
> **DJKEMMET said:**
> First, I would like to thank the wonderful community on this forum. so far you've all proved to be a welcoming, intelligent and invaluable resource in learning about linux, it's been great.

Though my question today is about setting up an FTP server, I already have ubuntu 11.04 installed on a dell powerspec server and I'd like to set it up with an FTP to host my websites and what not. 

If any of you could give some advice or maybe share a good tutorial you've I'd be incredibly grateful. 

Thanks all!
DJ!

Hi DJ

I agree with the others, that avoiding FTP is a good idea if you can.  Depending on what you're doing you might get a lot of mileage out of git to manage versions and move them around, instead of specifically a file-transfer tool.

Nonetheless, FTP can be useful, as almost every computer in the world has an FTP client already installed on it, and many things such as web cameras can do FTP uploads periodically.

To get you started:
```
sudo apt-get install vsftpd
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.DIST
sudo nano /etc/vsftpd.conf
sudo /etc/init.d/vsftpd restart
```Edit vsftpd.conf carefully.  The minimum you need to do to upload files is write_enable, which is by default commented out.  But you will probably want to make other changes depending on your circumstances.  Be warned, FTP security can be tricky if you're in the world wild internet, and getting your router to do proper NAT with FTP can be difficult.
```
write_enable=YES
```Kind regards,
Jonathan.

---

### Post by erixnow on 2011-10-12
I agree with Jonathan,  with a few extra words......
VSFTPD is a bit limited.  Proftpd is a much better choice.  There is also a module for sftp.  It is pretty much the norm for FTP (for all of the WSFTPD haters LoL).  It is a very secure server since it is a default with alot of linux and UNIX distro's.  apt-get and the basic proftpd should run out of the box (non anonymous if I remember).



Just food for thought.



Regards,
Eric Peyser

---

### Post by HermanAB on 2011-10-12
Howdy,

Both vsftpd and proftpd work out of the box.  People only have trouble if they change the settings. So installing a FTP server is pretty much a no brainer.

---

### Post by The Sorrow on 2011-10-12
SFTP is simple, quick, and easy to manage, deploy and configure. +1

---

### Post by DJKEMMET on 2011-10-13
> **Jonathan L said:**
> Hi DJ

I agree with the others, that avoiding FTP is a good idea if you can.  Depending on what you're doing you might get a lot of mileage out of git to manage versions and move them around, instead of specifically a file-transfer tool.

Nonetheless, FTP can be useful, as almost every computer in the world has an FTP client already installed on it, and many things such as web cameras can do FTP uploads periodically.

To get you started:
```
sudo apt-get install vsftpd
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.DIST
sudo nano /etc/vsftpd.conf
sudo /etc/init.d/vsftpd restart
```Edit vsftpd.conf carefully.  The minimum you need to do to upload files is write_enable, which is by default commented out.  But you will probably want to make other changes depending on your circumstances.  Be warned, FTP security can be tricky if you're in the world wild internet, and getting your router to do proper NAT with FTP can be difficult.
```
write_enable=YES
```Kind regards,
Jonathan.

So I successfully followed all these steps via ssh to my iPad 2, so do I need to get into my router and open an FTP port? 

regards,
DJ

EDIT:CLARIFICATION: What Im looking to set is something I can develope websites and web apps on. I'd like to be able to either type in the IP address and see either the directory or the home page. Like id like to build a home page for the server that lets me navagate through the folders I have stored

---

### Post by Jonathan L on 2011-10-13
> **DJKEMMET said:**
> So I successfully followed all these steps via ssh to my iPad 2, so do I need to get into my router and open an FTP port? 

regards,
DJ

EDIT:CLARIFICATION: What Im looking to set is something I can develope websites and web apps on. I'd like to be able to either type in the IP address and see either the directory or the home page. Like id like to build a home page for the server that lets me navagate through the folders I have stored

Hi DJ

Very difficult to comment on the router question without knowing where the server is and where the users are.  I'm guessing from what you describe the server and you are both in the same house: you only need to deal with your router if you want to work with the server inside and you on the outside.  Get it working first.

The easiest way to install a web server for general purposes is
```
sudo apt-get install lamp-server^
```Then you just put files and directories in /var/www and you'll be able to web to them via IP address, at least from inside your own house.  Be aware that putting a server on the world wild internet can have surprising consequences (hazards included getting hacked, sued, elected to public office, etc)

Hope that helps.  Post another thread if you want help with those, as they're definitely off topic from FTP servers.

Kind regards,
Jonathan.

---

### Post by Lars Noodén on 2011-10-13
> **DJKEMMET said:**
> If any of you could give some advice or maybe share a good tutorial you've I'd be incredibly grateful. 


You find SFTP is built into the package [OpenSSH-server](http://packages.ubuntu.com/natty/openssh-server).  No editing or configuration needed.

The SFTP clients you'll find are built into Nautilus, Dolphin, and FileZilla.

---

