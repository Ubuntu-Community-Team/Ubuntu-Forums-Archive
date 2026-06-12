---
title: "apache document root external hard drive"
date: 2010-04-28
forum: Server Platforms
---

### Post by blakep2 on 2010-04-28
I am trying to use my external hard drive to store webpages and on the webpages it is uploaded to the folder.  When i navigate to the address it says it is forbidden.  I also noticed that it would not let me upload files to the folder it says i do not have permission. Can someone help me get passed the barriers.  The hard drive is ntfs.

---

### Post by Ryan Dwyer on 2010-04-28
I advise against this for many reasons:
- A USB drive is slow, has to spin up more often and will cause wear and tear
- I think the USB drive must be mounted before Apache starts
- NTFS support isn't perfect yet. I've had power failures happen, after which some files cannot be deleted from the disk.

It sounds like you have a permissions problem on the disk. Can you create files on it using sudo? What options are you using to mount it?

---

### Post by blakep2 on 2010-04-28
> **Ryan Dwyer said:**
> I advise against this for many reasons:
- A USB drive is slow, has to spin up more often and will cause wear and tear
- I think the USB drive must be mounted before Apache starts
- NTFS support isn't perfect yet. I've had power failures happen, after which some files cannot be deleted from the disk.

It sounds like you have a permissions problem on the disk. Can you create files on it using sudo? What options are you using to mount it?
it is a seagate externally powered external hard drive. If speed is not a factor would this still be a problem. Yes I can create files but when they are accessed through the web browswer it echos forbidden.  I honestly have no idea what i am using to mount it.  I am using it for a file server as well but this is rarely used, i dont know if this helps.  To set up file sharing on the drive i had to do something with 777 permissions, I believe it has been a while.

---

### Post by DGortze380 on 2010-04-28
> **blakep2 said:**
> it is a seagate externally powered external hard drive. If speed is not a factor would this still be a problem. Yes I can create files but when they are accessed through the web browswer it echos forbidden.  I honestly have no idea what i am using to mount it.  I am using it for a file server as well but this is rarely used, i dont know if this helps.  To set up file sharing on the drive i had to do something with 777 permissions, I believe it has been a while.

This sounds like an all around bad idea. I suggest you research how to secure access before changing things, apache really isn't you're best choice, what exactly are you trying to acheive?

You should do some more research before creating world writeable files (chmod 777). The default doc root for apache is /var/www. This can be changed in /etc/apache2/<conf file>, though I highly discourage you from doing this.

---

### Post by blakep2 on 2010-04-28
> **DGortze380 said:**
> This sounds like an all around bad idea. I suggest you research how to secure access before changing things, apache really isn't you're best choice, what exactly are you trying to acheive?

You should do some more research before creating world writeable files (chmod 777). The default doc root for apache is /var/www. This can be changed in /etc/apache2/<conf file>, though I highly discourage you from doing this.
i have already used the chmod 777 for the file sharing.  I am trying to add more disk space for my website for users to upload photos.  I have a apache configured for my domain already i set up a subdomain for the external hard drive and it works just when you try to access the file from a browser it is "forbidden"  I have tried to change the www-data but I do not have permission in root or my user account.  I am just trying to get past this "forbidden" problem.  I also noticed on my main public_html folder that access is denied for uploading files from the web browser can I allow this in the external hard drive if I get it set up since that is the reason i want to do this.

---

### Post by teacosy on 2011-05-18
hi...
i am having a similar problem... 

i use an internal ntfs partition for my web root...

when i try to access localhost from a browser, i get: 

403 You don't have permission to access / on this server

and the apace error log shows: 

[error] [client 127.0.0.1] (13)Permission denied: access to / denied

all was working fine for years till the 11.04 upgrade... 

im suspecting maybe a policykit thing as after the 9.10 upgrade i had to enter my password whenever i mounted an internal ntfs partition where as i didnt before that... since the 11.04 upgrade that has been fixed... 
i refer to this bug: 

[https://bugs.launchpad.net/ubuntu/+source/polkit-kde-1/+bug/575428](https://bugs.launchpad.net/ubuntu/+source/polkit-kde-1/+bug/575428)

any help on this would be great as i want to continue to use this drive for my web root...

thanks

teak

---

### Post by blakep2 on 2011-05-20
11.04's been kinda screwy for me.  I down graded to 10.10 its been perfect for me.

---

### Post by teacosy on 2011-05-20
> **blakep2 said:**
> 11.04's been kinda screwy for me.  I down graded to 10.10 its been perfect for me.

hmmm... 
i was hoping not to do that as i do like some of the improvements in 11.04... 
ive moved the main stuff i was working on to my home directory [i dont like working in var/www as my user doesnt have access] and changed the DocumentRoot to that, and it seems to work... 
although whenever i move a file from an ntfs drive/partition i have to chmod it so apache has access to it...

---

### Post by bennettg on 2011-11-30
> **DGortze380 said:**
> This sounds like an all around bad idea. I suggest you research how to secure access before changing things, apache really isn't you're best choice, what exactly are you trying to acheive?

You should do some more research before creating world writeable files (chmod 777). The default doc root for apache is /var/www. This can be changed in /etc/apache2/<conf file>, though I highly discourage you from doing this.

I am trying to do the same thing....changing the document root because i added a external hd.

i changed the /etc/apache2/sites-available/default file:

commented out DocumentRoot /var/www
added DocumentRoot /media/externalhd/C/Users/Mike

in the same file, i commented out <Directory /var/www/>
and added <Directory /media/externalhd/C/Users/Mike/>

I also have a index.html file in /media/externalhd/C/Users/Mike

i then restarted apache by sudo /init.d/apache2 restart

however, when i browse to localhost, i still see my old document root (var/www)

any ideas?

---

### Post by jsebean on 2012-01-16
run ```
apache2 -S
```

---

### Post by SeijiSensei on 2012-01-16
This is overall a bad idea.  Apache relies on Unix permissions to control access to files (as well as its own access controls as well).  In order for things to work properly the filesystem containing the shared files needs to conform to POSIX standards. NTFS doesn't qualify.

If you must use an external drive, I'd use gparted to repartition the drive and create a separate Linux partition formatted with ext4 for the web data.  If you don't have any need for NTFS, just wipe the drive and make it all ext4.

---

### Post by DukeBoxer on 2012-01-16
Also, is your external hard drive encrypted? If it is it might be the problem. I was trying to serve from an encrypted drive and always got a forbidden error. Just to test, change the document to another folder and type in "localhost" in the browser to see if you keep getting the forbidden error

---

### Post by multimedia2012 on 2012-12-29
i want to use an alternative drive than /var/www it is however an internal drive but it would not work any ideas as my max space is only 30 gb on my system drive and i have a 2 TB drive (accessable in full only through host  i would like to use,  example /host/web_server/www/   will this be ok?

well i got it working fine i changed sites available and enabled so all good.

---

