---
title: "Create Upload.php Page"
date: 2008-07-08
forum: Server Platforms
---

### Post by cantdrive55 on 2008-07-08
I'm trying to setup a way so that I can upload files remotely without needing to go through FTP or SSH. I just want a webpage on my Apache server that will let me upload a file from the pc I'm on and it will upload to a specified directory.

I looked and found php-http-upload but couldn't find any how-to's or that kind of thing on it.

---

### Post by windependence on 2008-07-08
Do you want a drag and drop application? Try WinSCP from a Windoze machine. It's very nice.

-Tim

---

### Post by pytheas22 on 2008-07-08
Try following the guide [here]("http://php.about.com/od/advancedphp/ss/php_file_upload.htm").  If you know a bit of PHP it shouldn't be too hard.  If you need help, though, feel free to ask.

---

### Post by hyper_ch on 2008-07-09
[http://www.php.net](http://www.php.net)

Each function has one or several examples plus user comments... you can find just about everything in there.

---

### Post by cantdrive55 on 2008-07-16
Thanks for those links guys, I've got it working quite well. The one thing I would like though would be some sort of a progress bar that shows how much has been uploaded, what speed, time remaining, etc...

I found [this one]("http://pdoru.from.ro/") and really like the way it works however I can't figure out how to get it installed.

---

### Post by pytheas22 on 2008-07-17
I think that to install the thing from pdoru you need to recompile PHP on your machine, which can certainly be done but it may be a little tricky.  It may be easier to see if you can find something else for the job.  pdoru's stuff seems outdated (2005) anyway; you're better off using something that's still supported.

---

### Post by cantdrive55 on 2008-07-17
Thats what I was thinking but I couldn't find any decent looking ones that seemed to be somewhat simple. It's being used on a small office box that is just for remote uploads. The page is password protected so it's not like there will be a huge demand on the system. It's just nice to see if the file is uploading or if its just sitting thinking about uploading.

---

### Post by pytheas22 on 2008-07-18
Just a guess and I don't have time to check myself, but maybe there's a Firefox extension that would show the progress of your uploads, as it does for downloads.  You may want to look into that.

---

