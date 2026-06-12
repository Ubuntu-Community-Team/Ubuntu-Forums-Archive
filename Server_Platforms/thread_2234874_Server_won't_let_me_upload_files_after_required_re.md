---
title: "Server won't let me upload files after required reboot"
date: 2014-07-17
forum: Server Platforms
---

### Post by TFroehlich3 on 2014-07-17
Hello Everyone,
   My server was working fine until I had to reboot the system for what I think might have been an update. It will no longer let me upload website files to it. 
I am also having issues with the permissions every time I upload files. When I upload new updates to my websites it will pull up the web pages, but it will not show the new content (it will have a broken file icon where the new content is) until I run the command "sudo chown -R 755 /var/www" and that will not even work any longer.



Any thoughts to what I might be able to do to get it back up and running?

---

### Post by sandyd on 2014-07-17
> **TFroehlich3 said:**
> Hello Everyone,
   My server was working fine until I had to reboot the system for what I think might have been an update. It will no longer let me upload website files to it. 
I am also having issues with the permissions every time I upload files. When I upload new updates to my websites it will pull up the web pages, but it will not show the new content (it will have a broken file icon where the new content is) until I run the command "sudo chown -R 755 /var/www" and that will not even work any longer.

If you would like to check out the web page the website is [http://www.cleartoneshearingllc.com](http://www.cleartoneshearingllc.com)

Any thoughts to what I might be able to do to get it back up and running?

The commands should be
```

sudo chown -R www-data:www-data /var/www
```
Chown changes the owner of the files/directories.

---

### Post by TFroehlich3 on 2014-07-17
Okay, that command worked to get view the files! Thank you for that! Will I have to do that every time I upload new files? And do you have any thoughts on the uploading issue?

 Thank you!

---

### Post by cariboo on 2014-07-18
What service do you use to transfer files? Which ever on you use, make sure it is running, and accessible form other systems.

---

### Post by TFroehlich3 on 2014-07-19
> **cariboo907 said:**
> What service do you use to transfer files? Which ever on you use, make sure it is running, and accessible form other systems.

What I don't understand is that it was running just fine and then all of the sudden it stopped letting me upload. It will let me connect with a FTP client and navigate in the service but when I go to upload it gives me an error about not being able to create the file on the server.:-x I have no idea why this would happen all of the sudden lol

---

### Post by TFroehlich3 on 2014-07-19
> **sandyd said:**
> The commands should be
```

sudo chown -R www-data:www-data /var/www
```
Chown changes the owner of the files/directories.


That fixed my viewing issue, do you have any ideas how I can fix my uploading issue? Do I need to change permissions or something? Again, I can navigate through the server with my FTP client but it wont let me upload anything. So I went into the command line and tried "ftp example.com" and I got a message saying "connection refused"

Any thoughts?

---

### Post by TFroehlich3 on 2014-07-21
```
sudo chmod -R 755 /var/www
```
This fixed my permissions issues.

---

