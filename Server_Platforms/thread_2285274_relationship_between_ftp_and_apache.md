---
title: "relationship between ftp and apache?"
date: 2015-07-04
forum: Server Platforms
---

### Post by feifansnf on 2015-07-04
Hi everyone, 
I'm new to ubuntu and server and ftp. This is the first time i set up a web server and ftp server. My goal is to have the ftp path to be the same as my apache directory path. So i can upload files into my website. 
So, as I watch different tutorials online, I'm very confused with all the different use of user. First, i see that i have two ftp folder associated with a user i created under /home/  one is admin, other one is feifan(my name).
then when i use ls -l, i see all the files belong to either root or feifan. now what is the difference between this ownership of feifan and the ftp's feifan?  or is it the same? can someone explain the relationship of these please?

Back to my goal, my first attempt was to setup two virtual hosts and move the apache directory to be the same as my ftp directory. but it wasn't a success. I keep getting access denied, you don't have permission... I tried giving all the folders chmod 777, but still wasn't working. So I went back to use the default /var/www/ for my virtual hosts. 
as i decided my second attempt would be to move ftp directory to be my apache directory. I am getting all kind of confusion I talked about with the user and stuff. and now i'm here asking about it :D
what is the best practive for me to achieve my goal of having ftp and apache at the same directory here? 
thanks in advance

---

### Post by TheFu on 2015-07-04
Please don't do FTP.  Use sftp from the **openssh-server** package. There are many reasons for this. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

Use your normal userid to login through ssh or sftp - hopefully you've setup ssh-keys and NEVER use a password.  ssh, scp, sftp all use the same authentication.  Apache has ZERO to do with this.  After you install openssh, install fail2ban to limit brute force attacks.

Please don't chmod 777 - that is dangerous to server security.  Please learn Unix file and directory permissions so you understand exactly which permissions are necessary, provide those and no more, to get the access needed for directories and files. File and directory permissions are CORE to Unix security - attempting to run a server without a good understanding of these basic ideas is a really bad idea.

Ubuntu has a tutorial on this stuff: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)  Spend 45 minutes with a few different userids and groups to see how they fit together. Nothing can replace that hands on experience. There are many other similar tutorials on the web for the same thing.

If you need help with ssh - there are many step-by-step guides too.  Basically, IMHO, any Unix system needs to have ssh running - always. With fail2ban protecting and ssh-keys, there aren't any real risks to doing this.

Oh - and don't forget the purge whatever FTP server you have running. You don't need/want that anymore.

---

