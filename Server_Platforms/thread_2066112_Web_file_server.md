---
title: "Web file server"
date: 2012-10-03
forum: Server Platforms
---

### Post by Hoube78 on 2012-10-03
Hi,
I'm looking to setup a web file server so no more than 10 friends can access some files.
 
I need them to be able to access from web browser, most have IE but some have others.
 
I need them to be able to upload and download the files and it needs to be password protected.
 
Some people have already pushed me towards a windows home server system but I'm here to see if you can convince me otherwise :)
 
I've got resonable IT experiance (not much with ubuntu thou).
 
I have a spare computer if needed or my desktop.
 
I need my friends access to be easy e.g. I want to send them a web address they go to log in with username and password and they can see the folders with files in.
 
Any help or advice welcome I'm off for the next few days so I am free to have a play with Ubuntu.
 
Thanks,
 
J

---

### Post by Cheesemill on 2012-10-03
I run [AjaXplorer]("http://ajaxplorer.info/") on my Ubuntu Server to access files through a web interface.

---

### Post by hasan.akgoz on 2012-10-04
setup an ftp server like proftpd.

---

### Post by Lars Noodén on 2012-10-04
If you have openssh-server already install then you already have SFTP and don't need to add anything for file transfer.  As a bonus, SFTP is secure, unlike FTP:

[list]
[*] [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

If you are looking to share access to some folders, you will have to set the appropriate group permissions.

```

sudo addgroup webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws "{}" \;

sudo gpasswd --add hoube78 webmasters
sudo gpasswd --add colleague1 webmasters
sudo gpasswd --add colleague2 webmasters
# etc.

```

Once the permissions are set, then you can leave them.

---

### Post by Hoube78 on 2012-10-04
Hi All,
 
I'm not to comfrotable with ftp or sftp.... will my friends need to be able to access through a web browser? They wont install anything to their computers so it needs to be web browser base.

---

### Post by Lars Noodén on 2012-10-04
The file managers Dolphin and Nautilus both have a SFTP built in.  So they don't need to learn anything new to be able to upload files to the server.  Just press ctrl-L and then enter the URI of the web page: sftp://user@xx.yy.zz.aa/some/path

Otherwise Ajaxexplorer might be an option, but you will need to set up HTTPS first.

---

### Post by Hoube78 on 2012-10-04
> **Cheesemill said:**
> I run [AjaXplorer]("http://ajaxplorer.info/") on my Ubuntu Server to access files through a web interface.
 
I like the look of this, how easy is it to install on ubuntu etc?
 
Will my friends be able to access using smart phones likie windows 7 and iphone?

---

### Post by kgatan on 2012-10-04
Ajaxplorer is easy to install, its just a web page you unpack in your www folder.
Some tweaking with file permissions may be needed.
There can also be some configuration needed depending on how large files you want to be able to upload.

There is an official app available for iphone/ipad for ajaxplorer but i believe its not free.
Don't know about Windows phones or Android.

---

### Post by HermanAB on 2012-10-04
Dropbox is probably the easiest.

---

### Post by LHammonds on 2012-10-04
There is also an option called [OwnCloud]("http://ubuntuserverguide.com/2012/05/install-owncloud-4-ubuntu-server-1204-lts.html").

---

### Post by hasanarbab on 2013-05-29
ok fellows, it is a bit older thread but I'm going to add a very simple solution. A very very simple file server, not with any options, but simply access required files and download if needed. I'll try to explain step by step, not an expert in writing tutorials yet.

1. install Apache 2, open terminal, type "sudo apt-get install apache2", provide password on prompt, wait for it to install, respond accordingly if install requires a response.

2. do not close terminal yet. type "gksudo nautilus", provide password on prompt, a file explorer window will open. At this point, be very very careful as all your file system is open to you with all securities removed.

3. click on "File System" in left side menu. browse to the folder which you want to share over http. FYI, your home folders will be in "/home/username". username is the your ubuntu login username.

4. right click on folder to be shared, select "Make Link" from popped menu. a link will be created at same place.

5. now, right click on that created link and select "cut" from popped menu

6. click on "File System" in left side menu again.

7. browse to folder "var" and then to folder "www".

8. right click on empty space and select "create new folder". name it whatever you want.

9. open that newly created folder and right click in empty space and select "paste". your previously made link will be pasted here.

10. now, open firefox or chrome or whatever browser you like. in address bar type "http://localhost/foldername" foldername is the folder you created in /var/www.

That's it you are done, you'll see the name of folder you actually wanted to share in a list opened in front of you in your browser. click it and all your required files/folders are right there. click on any file and it'll be downloaded/opened accordingly.

I hope instructions are clear and helpful.

---

