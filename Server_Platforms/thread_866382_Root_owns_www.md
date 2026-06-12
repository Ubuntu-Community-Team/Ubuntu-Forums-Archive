---
title: "Root owns www"
date: 2008-07-21
forum: Server Platforms
---

### Post by cheetah1 on 2008-07-21
A potential customer refused to host his website on my server, as my www-folder is owned by root. Please do explain this.

---

### Post by skunkbad on 2008-07-21
Your customer should only have access to what you provide him or her access to. If your customer won't use your server because he or she demands access to areas that you don't provide access to, then you should let them find someone else to host with.

---

### Post by pdwerryhouse on 2008-07-21
Yeah, he sounds particularly clueless to me. You're probably better off without him, he probably would have caused you no end of grief with "difficult" requests.

---

### Post by ad_267 on 2008-07-21
Shouldn't www be owned by www-data? Ignore me if I'm saying something stupid, just that my www is owned by www-data.

---

### Post by cariboo on 2008-07-21
www-data is the debian way pf owning /var/www, it seems like root is the Ubuntu way.

jim

---

### Post by lswb on 2008-07-22
Did he explain why? Perhaps he considers it a security issue. Does the web server run as root?

---

### Post by windependence on 2008-07-22
> **ad_267 said:**
> Shouldn't www be owned by www-data? Ignore me if I'm saying something stupid, just that my www is owned by www-data.

You are exactly on track here, and he has every right to be concerned.

In most Apache installations, you should be running your service as an unprivileged user, and the data directory should also be owned by that user for security reasons. In Debian it's www-data, in FreeBSD it's www, etc. 

It's just better if your root account is not exposed. If the folder is owned by root, then your user needs elevated permissions to access the files and that means you need to grant access to a wider group than you normally would. chmodding all your files in the data directory to 777 is a n00bish move at best and at worst could be disastrous if a pr0n site shows up instead of your client's site.

Also if the web server can only write to files that it needs to, the damage can be limited to only those files. Okay, maybe your web pages will be damaged, but it is much easier to recover those files from a backup copy than it is to re-install your operating system.

-Tim

---

### Post by cdenley on 2008-07-22
> **windependence said:**
> You are exactly on track here, and he has every right to be concerned.

In most Apache installations, you should be running your service as an unprivileged user, and the data directory should also be owned by that user for security reasons. In Debian it's www-data, in FreeBSD it's www, etc. 

It's just better if your root account is not exposed. If the folder is owned by root, then your user needs elevated permissions to access the files and that means you need to grant access to a wider group than you normally would. chmodding all your files in the data directory to 777 is a n00bish move at best and at worst could be disastrous if a pr0n site shows up instead of your client's site.

Also if the web server can only write to files that it needs to, the damage can be limited to only those files. Okay, maybe your web pages will be damaged, but it is much easier to recover those files from a backup copy than it is to re-install your operating system.

-Tim

It being owned by root shouldn't be a problem. It depends on the rest of the permissions. www-data should only have read access. You don't want somebody exploiting a vulnerability in your scripts to modify your website. You can give the user write permissions without making him the owner, but you shouldn't give anyone write permissions that doesn't need it. If you gave everyone write access so the user can upload or modify files, then that would be a legitimate concern.

---

### Post by Necromantis on 2008-07-22
The privilege on the website folders is/can be annoying. 

I have a php script which create a (temporary) sub folder and then move files inside that folder (so the files can be access online). Later on a cleaning bot will erase the folder+files. 

With "root" access the php script just hit a brick wall and doesn't work. In the end I had to place o=rwx on the folders to get it working.

I'm still unhappy about this but I can't see any other way to make that kind of php script work without it. :confused:

To return to the post: Obviously if the person/company who need the server needs access to the www folder then root is too high - you should create another account and give that account rwx on the www folder and nothing else.

---

### Post by ad_267 on 2008-07-22
Yeah I thought you needed www-data to own the directory for things like that, so that scripts could create and edit files as the web server usually runs as www-data.

---

### Post by skunkbad on 2008-07-31
This is what I did:

   1. create a new group called www
   2. add myself to the www group
   3. chown the www directory as root:www
   4. chmod the www directory to 775
   
   sudo groupadd www
   sudo chown root:www /var/www
   sudo addgroup skunky www
   sudo chmod 775 /var/www
   
Apache no longer owns the www directory, so if apache needs to write to it, it won't be allowed. For security reasons, I was advised that apache only be allowed to own directories if it needs to.

---

