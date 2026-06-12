---
title: "Everytime I upload website files I have to change the permissions to view??"
date: 2014-07-04
forum: Server Platforms
---

### Post by TFroehlich3 on 2014-07-04
Hello Everyone,   I have a web server setup in my basement and it is working just dandy, except every time I upload files to it I have to run the command "sudo chmod -R 755 /var/www" in order to view the websites because if I don't it will say I do not have permission to view the webpage. I am running multiple websites with vhosts, just an FYI, and I followed the tutorial linked below. Can someone please tell me something that I can do to fix this issue or tell me if the tutorial is wrong, which I have noticed from time to time.[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-ltsThank](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-ltsThank) you so much!

---

### Post by nerdtron on 2014-07-05
The thing about the web page directory /var/www is that every file in there should at least by world readable. Because it is a webpage and you want to display it, anyone should be able to read it, not just the owner or the group.

 It is not necessarily "chmod -R 755 /var/www" because if you do this, even normal files will have execute permissions which can have security issues.

It's a lot safer if you do it like "chmod -R a+r /var/www" which basically says, give anyone read permissions on these files.

Regarding permissions when you upload files, it is caused by the user who uploaded the files, and also if the permissions of the files themselves. If you upload using the root account and most files have permissions 600, you will surely need to change permisisons that after the upload. 

A solution to this is that before you upload files to the server, say "webpage_folder", you should change the permissions first. Then you tar (or zip) the folder. Now that the webpages are zipped, you upload the zip file to the server and extract them where they should be place. This method preserves the permissions of file and folder that you want to upload.

---

### Post by sandyd on 2014-07-06
> **TFroehlich3 said:**
> Hello Everyone,   I have a web server setup in my basement and it is working just dandy, except every time I upload files to it I have to run the command "sudo chmod -R 755 /var/www" in order to view the websites because if I don't it will say I do not have permission to view the webpage. I am running multiple websites with vhosts, just an FYI, and I followed the tutorial linked below. Can someone please tell me something that I can do to fix this issue or tell me if the tutorial is wrong, which I have noticed from time to time.[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-ltsThank](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-ltsThank) you so much!

What FTP server are you using - there are several things that you may change to make things work without having to chmod.

---

### Post by TFroehlich3 on 2014-07-17
> **sandyd said:**
> What FTP server are you using - there are several things that you may change to make things work without having to chmod.

I am using filezilla

---

### Post by TheFu on 2014-07-17
a) stop using ftp. Use **rsync** over ssh with key-based authentication. It is one of the few times when more security is actually more convenient too!  FTP use should have ended 15 yrs ago. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) explains.  rsync will set the permissions to match to source system permissions, which is very handy.

b) The group permissions should be set to allow the webserver gid access and add the group sticky bit - g+x to the directory permissions. This will force any newly created files to be of that same group, provided the user pushing them is as well. Or you could just setup the ssh connection so your userid keys are located inside the web-server userid ~/.ssh/ directory ... then all files would be placed as that userid. That would simplify everything.  Learn about the ~/.ssh/config file so you can control which userid+key is used, when.  I wish I would have learned this about 8 yrs before I did.

c) I disagree that files should be world-readable under a web server.  An understanding of UNIX userid, groupid and file permissions will make this clear.  Of course, it is just another opinion you are reading - we all have them.  It is time to spend 30 minutes practicing with UNIX directory/file permissions by following a **good tutorial**. These are the core for all UNIX security, so your time won't be wasted.

---

### Post by TFroehlich3 on 2014-07-19
> **TheFu said:**
> a) stop using ftp. Use **rsync** over ssh with key-based authentication. It is one of the few times when more security is actually more convenient too!  FTP use should have ended 15 yrs ago. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) explains.  rsync will set the permissions to match to source system permissions, which is very handy.

b) The group permissions should be set to allow the webserver gid access and add the group sticky bit - g+x to the directory permissions. This will force any newly created files to be of that same group, provided the user pushing them is as well. Or you could just setup the ssh connection so your userid keys are located inside the web-server userid ~/.ssh/ directory ... then all files would be placed as that userid. That would simplify everything.  Learn about the ~/.ssh/config file so you can control which userid+key is used, when.  I wish I would have learned this about 8 yrs before I did.

c) I disagree that files should be world-readable under a web server.  An understanding of UNIX userid, groupid and file permissions will make this clear.  Of course, it is just another opinion you are reading - we all have them.  It is time to spend 30 minutes practicing with UNIX directory/file permissions by following a **good tutorial**. These are the core for all UNIX security, so your time won't be wasted.

DO you have any links for some good tuts?

---

### Post by TheFu on 2014-07-19
> DO you have any links for some good tuts? 

I do not. I learned this in the early 1990s where all my peers would only say "RTFM" over and over and search engines were new, magical, things.  It is a different world now. Better in some ways, worse in others.

I suspect google "ubuntu permissions tutor" would yield something good.  Use "ubuntu" not because there is any difference from it and "linux", but because ubuntu guides tend to be written in a more accessible, easier to understand, way.  Also, try to stay with reputable websites for this stuff. In the beginning, it is hard to know if a blog-site is reputable or not. Just be careful of they have you *leaving the reservation* too much.  Sites with "ubuntu" in the name are probably preferred over others.  Of course, jdpfu.com is "golden" always. ;) Er ... perhaps not.  We choose to run Ubuntu to avoid all the manual stuff that other Linux distros require, right, so try to only use normal commands that don't require installation from source, if you can.

---

