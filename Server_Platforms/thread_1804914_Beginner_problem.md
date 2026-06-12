---
title: "Beginner problem"
date: 2011-07-15
forum: Server Platforms
---

### Post by ScottG89 on 2011-07-15
Hey guys I just setup my first webserver and before I go any further and get it on the internet, I want to make sure everything is working on my home network. I edited the 000-default file in sites-enabled to look in /var/www/hockey/Hockey (once in the Hockey folder, all of the files are there). When I go to test with localhost, the index page comes up but it does not load my styles or images, I also noticed that when I try to go to other links on the page (other .html files in Hockey folder), I get permission denied, so I'm assuming that is what is happening with it not loading my styles and images also. Can someone help me to get this working. Thank you in advance

UPDATE: index.html does not work either. So now all pages come up Forbidden, you do not have permission to access ...

---

### Post by xkaliburx on 2011-07-15
I would simply start with 2 things.   A permission list and owner list of the root folder and files in the root of the webfolder Hockey (make sure all is readable, etc.)  If everything is 403'ing, it's most likely the whole folder is not readable by apache;

chmod o+x /var/www/hockey/Hockey

Next, does your default website have error logging in the vhost?  If so, what does the error logs show.  

Lastly, regarding your .css, are you using a relative path or a full?

Let's start with the above, post back with the errors, perms', etc. unless the chmod get's things going.

Thanks ...

---

### Post by ScottG89 on 2011-07-16
Ok awesome thank you very much. I actually have a lot of it working now. I don't know how to see if my server is writing to a log, but the permissions seem to be the problem. I know of the chmod command but I have no idea how to use it. I found out if I just transfer my index.html file (the one that was in the hockey folder) into /var/www and transfer over all of the other .html and my .css files to /var/www. It works. I ran into another problem now though, I tried transferring over the couple images that I have, into /var/www file and it is having trouble reading them (probably permission problem as well). What command can I use to change the permissions for the image files. I tried your chmod o+x /var/www but it did not help. I'm not sure if that was the command you wanted me to use though. Thank you again

---

### Post by Wim Sturkenboom on 2011-07-16
Your logs are probably in */var/log/apache* or */var/log/httpd*

---

### Post by ScottG89 on 2011-07-17
It was permissions problems. I found out the command to change it. Thank you very much for your help

---

