---
title: "request download button on apache"
date: 2010-09-20
forum: Server Platforms
---

### Post by desmane on 2010-09-20
Hi people, 

I have a web server in my kitchen with apache running on it. Since the upload speed is quite low due to my isp I would like to execute a bash script that uploads a file to another server through a website (which is htaccess protected) 

The idea in general: Someone with access to my website browses through a folder, copies a file path to an input form and presses "upload". Rather than executing a bash script directly I could have a cron job running in background that finds the path and then uploads the file to the other server I have userspace on and is accessible via sftp/ssh. The file would be than erased later after a couple of days or so. That person would be able to access the file with higher speed some time later without logging in via ssh and doing all that manually. 

Is that even possible somehow?

Thanks in advance

---

### Post by LightningCrash on 2010-09-20
Yep, it's possible... there is really no preformed software to do what you suggest, though.

You can use `tmpreaper` to clean up the old files.

---

### Post by desmane on 2010-09-21
thx, but I guess the main problem is the form on the website, i'd manage to write a script to upload the file somehow but how do I make this button? :)

---

