---
title: "Local Web Server and FTP and MySQL Gui Tools and Browser"
date: 2009-10-02
forum: Server Platforms
---

### Post by jc1cell on 2009-10-02
Hello everyone,

As you can see from the title, I'm having issues with aspects of working in a virtual web server installed for local development of web sites. I installed a Joomla Appliance from turnkey linux that is working great (as far as I know). I'm able to see it on the network by pinging from my hosting OS to the servers ip address. I have been able to upload a site to the web server into the /etc/www folder using sftp.

Here's where the problems begin. The only way I can access the site in my browser is by going into webmin, find the file and double click it. Then it opens in my browser. If I understood correctly, I should be able to put the host name(joomla or localhost)or ip address followed by the site folder and the index.htm file and it should show up inside the browser but that doesn't work.

Regarding accessing the server via ftp, I have been able to upload using sFTP without any problems. It even takes me to the www folder after I set up a user via webmin and gave it a setting of www as the root folder for the specific user. Now, after installing vsftp I still can't access the server via ftp (I don't know if I should even worry about that since sFTP is more secure).

Finally were down to MySQL GUI Tools. The log in request server host name, port (it puts in a default port number) and user and password. I have put in Joomla, localhost and the server ip address and cannot get in. I used mysql user and password and the user created for ftp access and neither worked.

I'm very new with regards to working in this environment and can't figure out how to get this with everything i have already read on the subject. I'm pretty sure I'm missing a step that needs to be taken and am hoping you guys can steer me in the right direction.

Thanks for any help you may provide.

jc

---

### Post by BQAggie2006 on 2009-10-02
> I should be able to put the host name(joomla or localhost)or ip address followed by the site folder and the index.htm file and it should show up inside the browser but that doesn't work.Do you get any kind of error message/page when you try to access it normally?

> Now, after installing vsftp I still can't access the server via ftpTry the VSFTPD configuration listed here: [http://www.doyouubuntu.com/wordpress/?p=57&lang=en](http://www.doyouubuntu.com/wordpress/?p=57&lang=en)

> I have put in Joomla, localhost and the server ip address and cannot get in.Have you tried using the port and credentials listed here: [http://www.turnkeylinux.org/appliances/joomla](http://www.turnkeylinux.org/appliances/joomla)

---

### Post by jc1cell on 2009-10-05
Thanks for the reply BQaggie.

After thinking about it for a bit I decided that it would be better to simply install the server on its own rather than using that appliance from turnkey linux. Following that I will work on any joomla install I want to make.

As a guide to installing the LAMP server in a virtual environment I used [this]("http://blog.johan-mares.be/ict/linux/installing-a-virtual-ubuntu-lamp-server-on-mac-os-x-using-virtualbox/") guide to help me out.

I was having problems with installing the virtual additions because I didn't notice they were for a linux host.Since I'm on an XP host,i eliminated the section about the virtual additions and just continued without it.

Everything runs great except for one thing. When I originally installed with the virtual additions as in the tutorial I can't access any sites that are deeper in the tree (plus the fact that I can't restart the server because of the linux host virt. addit.). What I mean by this is that I can access http://"ipaddress"/"username"/index.htm but I can't access http://"ipaddress"/"username"/"clientsite1"/index.htm.

When I did the install with no virt. addit. at all I can't see anything at any level on the browser. I'm no linux guru basing most of what I do off of tutorials geared for what I want (like the one linked to) so I have no idea what's going on.

Any help would be greatly appreciated.

jc

---

