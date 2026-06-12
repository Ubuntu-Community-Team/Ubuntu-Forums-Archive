---
title: "Personal Cloud Storage - Ubuntu Server 8.04"
date: 2008-05-30
forum: Server Platforms
---

### Post by Forvak on 2008-05-30
Hello,
I have a server with a fast internet connection which I would like to turn into a file server. My basic wants are:
   
   File upload/download from anywhere
   Works with MacOS/WinXP/Linux
   GUI for users, must be "mother friendly"
  
There are five people who would be using it as cloud storage. The server has 1TB of storage and plenty of processing power.

Can anyone suggest how to implement this? I looked at an FTP server, but am wondering if there is anything built for this type of project.

Thanks!

---

### Post by nix4me on 2008-05-30
You need to setup a Samba fileserver.  That will allow you to share folders on the files server to other machines on your network.  If you want to share with other people on the internet, then i recommend you setup a secure SSH server and use SFTP.

---

### Post by Forvak on 2008-06-06
The server is hosted in a remote location, so samba isn't going to work. SSH with FTP would work, but isn't the easiest to work with for non tech people. Is there any kind of browser based file storage system? 
Ie: log in, view your uploaded files, able to download/upload from the browser? I've seen things like it but don't know what they are.

Thanks!

---

### Post by garethsimpsonuk on 2008-06-07
Well 2 keep user friendly, you would have 2 go with sftp, ftp is just too unsafe, it isn't too difficult to use. Mind you I'm sure there must be some sort of file management script, or even a content management script that has features such as storing your bookmarks or playing your music. If there isn't one ther's definately a need for one.

---

### Post by Rhubarb on 2008-06-07
If you install a LAMP server, you could run eyeOS on it:
[http://www.eyeos.org/](http://www.eyeos.org/)

It's a Desktop written in PHP that anyone with almost any web browser can go to.
There is also a program called eyeSync that allows you to automatically upload files to your eyeOS username from a local folder on your machine (works in linux / OSX / windows).

---

### Post by garethsimpsonuk on 2008-06-07
nice 1! it's bookmarked, that'll come in handy. is it useful 4 u Forvak?

---

### Post by nix4me on 2008-06-07
Have you tried SSH with SFTP?  It's very easy to setup and very secure.  It's also very easy for your users to access using the free Filezilla program which is available for both windows and linux.

---

### Post by technodigifreak on 2008-06-07
This one requires Apache and PHP, but [http://www.phpwebftp.com/features.html](http://www.phpwebftp.com/features.html) has treated me well for a long time, and is relatively easy to implement over SSL.  There are plenty of other pieces of software like this, so finding an alternate shouldn't be an issue if you need a "GUI". Otherwise, you can't go wrong with ssh/sshfs/sftp.

---

### Post by pdonner on 2008-06-08
i believe firefox has a brower based plugin that you can install to do FTP.  I used it once but have other tools so haven't used it in a while.  whether or not it will work with sftp I am not sure.  check in the FF plugins section.

---

### Post by sciurus on 2008-06-09
If you want user-friendly and secure, what you want is webdav over ssl.

---

### Post by Forvak on 2008-09-10
Thanks all, sorry for being so slow to respond. A trip and the first few weeks of college ate my memory and time.

eyeOS looks really interesting. I'll definitely be implementing that at some point!

I ended up installing vsftpd and spending the time (always a good idea) to learn how to configure it properly. Once set up it IS quite easy for clients (read as family) to access it with firefox or a free FTP client.

Thanks for all the tips and suggestions, they helped.

---

### Post by rivercity on 2009-10-05
You might want to check out [http://www.tonidoplug.com](http://www.tonidoplug.com). It fits your requirements

---

