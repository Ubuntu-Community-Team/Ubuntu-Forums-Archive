---
title: "noobish: how to allow web user to upload files onto my server via a web browser?"
date: 2011-10-11
forum: Server Platforms
---

### Post by lethalfang on 2011-10-11
I've been looking around, but haven't been able to figure it out yet.
I have a rudimentary web server running with apache2 on my server. I want to add a function, where a user can upload files to my server with his/her browser. 
Which application and which website should I be looking to do this? 
I don't need something too sophisticated. I don't except more than a handful people who will ever do that. 

Thanks.

---

### Post by e79 on 2011-10-11
just my $0.02, but I guess you would need to create an 'upload form' in your webpages, whether you use html or php.

have a look here:
[http://commons.apache.org/fileupload/](http://commons.apache.org/fileupload/)

But the easiest way I would see it for you would be to host a little ftp/sftp/vsftp server on the same machine

[https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html)

Hope this shed a bit of light

---

### Post by drdos2006 on 2011-10-11
Normally you would make a group or add users with permissions to FTP the files to their directories.

Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

Do search in the HOWTO for "uploads"........

regards

---

