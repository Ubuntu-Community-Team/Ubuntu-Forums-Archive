---
title: "File write permissions in denied in /var/www/"
date: 2006-02-03
forum: Server Platforms
---

### Post by VinceDee on 2006-02-03
I'm trying to get a breezy web server going and can't seem to be able to do the simplest of tasks: copying files into the /var/www/ directory as normal user. I've looked for two days and can't find any information on the support forums or otherwise that has helped me solve the problem.

I keep getting a "You do not have permissions to write to this folder." error.

Sounds like a permissions problem, right? Just sudo chmod (or start Nautilus with root capability) and change the permissions of the www directory and all is good? Nope. change permissions to 775 using Nautilus, and whether I had the file owner and file group at www-data or root or my normal username it wouldn't let me copy files to the directory.

I also added my normal username as a user under www-data group...still not able to copy into the directory.

Change httpd.conf (apache2.conf) to include my user name under "user" and "group"; restarted apache, and still can't copy files to /var/www/.

I am *positive* that it's something really lame that I'm not doing right (noob to Linux), but all I want to do here is just be able to run a very small http website over my cable connection (like I've been doing with WinXP, where I can copy files to the wwwroot directory from the same XP machine with no problems). I'm even willing to ftp into the directory if I must, but it would be a lot more convenient if I could just use the same machine and drag and drop, or save html files into the www directory.

What am I doing wrong?:confused:

---

### Post by VinceDee on 2006-02-03
This is odd. After all of that drama, I rebooted the computer (due to a different issue) and I now have write access to the www directory.

I thought all you had to do to change permissions and such was just do it. Also, I restarted Apache2 after each .conf change, so I thought I was doing the things I was supposed to do.

Anyway, I guess it's all good now. :rolleyes:

---

### Post by Stereotypical Rage on 2006-02-03
Hehe, I had the same issue. I just issued **sudo chown username /var/www/ -R ** I do believe this was the command I issued.

---

