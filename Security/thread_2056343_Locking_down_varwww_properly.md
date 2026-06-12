---
title: "Locking down /var/www properly"
date: 2012-09-11
forum: Security
---

### Post by thany on 2012-09-11
It seems to me that there are as many ways to do this as there are sysadmins out there. This is what I came up with.

Security of /var/www is left as-is.

Security of the directories and subdirectories under /var/www have the following perm/user/group:
drwxrws--- martijn www

Security of files in those directories (recursive) is:
-rw-rw---- martijn www

martijn is the owner. www is the group.
www-data is member of www.

I need my websites to be writable by themselves. Please don't dive into this, this is just the way I need it. For this requirement, the security seems quite alright to me. Good enough at least.

However, I stumble upon an issue. When a website updates itself, it will create some new files and whatnot. But if the www-data user creates a new file, this becomes the security:
-rw-r--r-- www-data www

This I don't want. I want any new files and directory to *inherit* from their parent. The security mask should be inherited, the owner should be inherited, and the group is already inherited.

How do I achieve this? How do I make the security mask and file owners inheritable?

---

### Post by CharlesA on 2012-09-11
All the directories under /var/www/ are set to root:root with -rwx-r-x-r-x on my boxes.

That is unless I have them being served from the user's home directory.

---

### Post by Lars Noodén on 2012-09-11
You should probably remove www-data from www.  It is not such a good idea to leave the web server with general write access.

About the directories keeping the permissions, try setting the Set Group ID bit.

```

# do once
sudo chgrp -R www /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws "{}" \;

# repeat for each user:
sudo gpasswd --add martijn www

```

---

### Post by redmk2 on 2012-09-11
> **Lars Noodén said:**
> You should probably remove www-data from www.  It is not such a good idea to leave the web server with general write access.

About the directories keeping the permissions, try setting the Set Group ID bit.

```

# do once
sudo chgrp -R www /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws "{}" \;

# repeat for each user:
sudo gpasswd --add martijn www

```
I don't see the problem of www-data updating the files.  This is a system user that Apache runs under.  When you set the GID bit for all directories and files created by any user it has the www group set; correct?.  The www-data user has limited abilities by design.

If I was to do anything different I would just use the www-data group to begin with.  Actually that is what I do.  In fact I also provide the virtual hosts with a document root of /data/www/<virtual_host>.  This is a separate partition (spindle).  Do you see any problems with this set up.  If so; what problems do you foresee?

---

### Post by CharlesA on 2012-09-11
It isn't a good idea to give www-data write access. If it needs anything, it is read access only.

---

### Post by redmk2 on 2012-09-11
> **CharlesA said:**
> It isn't a good idea to give www-data write access. If it needs anything, it is read access only.
Can you explain why that is?

[COLOR="Blue"]Edit: Maybe I should be more specific.  I'm only giving write rights for www-data to the file system /data/www (the various document roots).  This is not giving execute rights or access to the system files.  We are only talking about data files here.[/COLOR]

---

### Post by CharlesA on 2012-09-11
www-data is the user apache runs as, and if apache was somehow compromised, they would have write access to that area of the file system.

---

### Post by redmk2 on 2012-09-11
> **CharlesA said:**
> www-data is the user apache runs as, and if apache was somehow compromised, they would have write access to that area of the file system.

Not trying to argue, just learn. :-)

So what you are saying is that only the data is at risk; right? 

What is the case if we have mortal users (and a group such as www-users). What risks do we have there?

The original reason I used www-data is that it was there already!  Where can we find information on hardening Apache2?

---

### Post by CharlesA on 2012-09-11
I am not too experienced with hardening Apache, but if you allow www-data to write to your site's root folder, and apache is compromised, your site could potentially be compromised as well. Even if www-data doesn't have world writable access, it might leave a hole open if there was a privilege escalation exploit left unpatched.

A compromised site can be modified to spread malware and the like.

---

### Post by redmk2 on 2012-09-11
> **CharlesA said:**
> I am not too experienced with hardening Apache, but if you allow www-data to write to your site's root folder, and apache is compromised, your site could potentially be compromised as well. Even if www-data doesn't have world writable access, it might leave a hole open if there was a privilege escalation exploit left unpatched.

A compromised site can be modified to spread malware and the like.

I guess I will have to create a new group.  So much for using an existing www group in my situation.  In my case the server is a test prototype and therefore is not connected to the internet.

Take heed OP we need to find a way other than using www-data either in the group or as the the group itself.

Thank you @CharlesA for your insight and patience.

---

### Post by SeijiSensei on 2012-09-11
Let's step back to the original comment about the website "updating itself."  How does this happen in practice?

I write pretty much exclusively in PHP.  My websites are dynamic since much of the content comes from SQL database records or editable component files which reside outside the DocumentRoot.  Most of my sites consist of a simple index.php shell that uses include() or require() to load the component parts of the page and send the result to the browser.  There is never any need to write a file anywhere in this arrangement.  

I make it a point to put as little as possible in the publicly-visible directories like /var/www.  Usually these directories include an index.php file, a CSS stylesheet, an /images/ subdirectory, and maybe a couple of other files that are safe to display to the public.  All of the website code is locked away in other directories outside the DocumentRoot and included into the page shell.  

I rarely have the need for applications to generate files, but when they do, I write these files to directories again outside the DocumentRoot to which the www-data user has write privileges.  That user should never have write privileges in /var/www.  That kind of insecure arrangement leads to websites being defaced or, as Charles suggests, worse things like malware distribution.

So what, exactly, are the files you need to write, and why do you need to do so?  Without specifics it's pretty difficult to determine what kinds of security policies make sense for your site.  I will reiterate, though, that letting www-data write into /var/www is never a good idea.

---

### Post by redmk2 on 2012-09-11
> **SeijiSensei said:**
> Let's step back to the original comment about the website "updating itself."  How does this happen in practice?

I write pretty much exclusively in PHP.  My websites are dynamic since much of the content comes from SQL database records or editable component files which reside outside the DocumentRoot.  Most of my sites consist of a simple index.php shell that uses include() or require() to load the component parts of the page and send the result to the browser.  There is never any need to write a file anywhere in this arrangement.  

I make it a point to put as little as possible in the publicly-visible directories like /var/www.  Usually these directories include an index.php file, a CSS stylesheet, an /images/ subdirectory, and maybe a couple of other files that are safe to display to the public.  All of the website code is locked away in other directories outside the DocumentRoot and included into the page shell.  

I rarely have the need for applications to generate files, but when they do, I write these files to directories again outside the DocumentRoot to which the www-data user has write privileges.  That user should never have write privileges in /var/www.  That kind of insecure arrangement leads to websites being defaced or, as Charles suggests, worse things like malware distribution.

So what, exactly, are the files you need to write, and why do you need to do so?  Without specifics it's pretty difficult to determine what kinds of security policies make sense for your site.  I will reiterate, though, that letting www-data write into /var/www is never a good idea.

Can I assume this```
 /var/www = DocumentRoot

```...I ask because I have this```
/data/www/<vh_dir> = DocumentRoot
```
... except for the default site which is as you have it.  The default site is just a place holder for the moment.

---

### Post by SeijiSensei on 2012-09-12
I was using DocumentRoot simply in the way Apache does.  It is the directory which corresponds to the web site root:  [noparse]http://www.example.com/[/noparse].  

Ubuntu uses /var/www as the default DocumentRoot, but my comments pertain to any directory which is accessible directly over the web with the HTTP protocol.

By the way, for readability sake, it's much better to avoid including entire long postings like mine in replies.  If there is something specific in the posting to which you are replying, just cut out that part of the text.  In your case you could have simply asked your question without quoting any of my posting whatsoever.  The context would have been obvious to anyone reading the thread.

---

### Post by thany on 2012-09-15
Okay, OP here :)

Fact of the matter is, my websites really do need general write access *in the websites* and not anywhere else. Which is working perfectly fine. No problems there.

@Lars Noodén
I already have the GID bit set, don't I?

@CharlesA
Forcing readonly only complicates things for the moment that my websites need their write-access, and I don't want things to become complicated. If Apache is compromised, yes the websites will be too. I realize that. But I also realize than if (when) Apache is comprimised, I've got my backups *and* a bigger problem on my hands, which is a comprimised Apache that needs updating. So not much of a problem as far as I can see. Also, my websites are not that popular yet, lowering the chance of a blackhat hacker coming along.

@SeijiSensei
A website updating itself is for example WordPress. It downloads a new zipfile, extracts it and overwrites itself with the zip file's contents. It's not that complicated, is it? I need this functionality, because updating manually is a pain in the rear, and updates are released quite regularly.


I still don't quite get what needs to be done to get things straight? At least I was right in that there are as many solutions as there are sysadmins :)

---

### Post by SeijiSensei on 2012-09-15
> **thany said:**
>  Also, my websites are not that popular yet, lowering the chance of a blackhat hacker coming along.

Popularity is irrelevant.  Attackers run scripts which scan by IP address looking to find vulnerable applications.  WordPress has been a popular target in the past because it has had some vulnerabilities, and because it is used by inexperienced people who are less informed or less concerned about security.  I see these types of automated attacks in my logs every day.

> A website updating itself is for example WordPress. It downloads a new zipfile, extracts it and overwrites itself with the zip file's contents.

Write a script that downloads the updates to a writable directory outside the DocumentRoot, unzips the contents, changes the permissions on DocumentRoot to be writable, copies the update files, then changes the permissions back to read-only again.

I'll just add that many of us prefer to watch an update take place rather than trusting it to happen automatically.  Sometimes an update will go haywire.  If you aren't there to watch what happens, you won't know your site has a problem until someone reports that it has  become unusable.

---

### Post by Lars Noodén on 2012-09-16
> **thany said:**
> I already have the GID bit set, don't I?

If you followed the middle steps in #4 above, then yes it should be SGID.  You only need to do that once.  

About read vs read-write access for the web server, I'd strongly recommend finding a workflow that does not involve violating the W^X principle.  Any machine connected to the net is being constantly scanned.

---

### Post by Ryan Dwyer on 2012-09-16
Please, for the love of God, don't make your DocumentRoot writeable by Apache. I've had to fix malware issues on other peoples sites caused by this too many times. Some scanner finds a vulnerability in an uploader on your site and uploads a backdoor script. This script tells the attacker everything about the server it's running on and allows them to easily run shell commands or modify files on mass. For example, injecting malware into every PHP file on your site. I've also seen some that make image files interpreted as PHP, then inject themselves into the images. I then have to peruse access logs and create one-off scripts to revert everything back. It takes hours of my time.

If Apache can't write to the DocumentRoot, there is no way these scripts will be able to deface your website when it finds an exploit in your application code.

Wordpress has an FTP update method. You enter your FTP details and it connects to itself via FTP and updates the files that way as a privileged user. The FTP details you entered are not stored anywhere. If your application must be able to update itself, consider using this method.

---

### Post by wacky_sung on 2012-09-17
> **Ryan Dwyer said:**
> Please, for the love of God, don't make your DocumentRoot writeable by Apache. I've had to fix malware issues on other peoples sites caused by this too many times. Some scanner finds a vulnerability in an uploader on your site and uploads a backdoor script. This script tells the attacker everything about the server it's running on and allows them to easily run shell commands or modify files on mass. For example, injecting malware into every PHP file on your site. I've also seen some that make image files interpreted as PHP, then inject themselves into the images. I then have to peruse access logs and create one-off scripts to revert everything back. It takes hours of my time.

If Apache can't write to the DocumentRoot, there is no way these scripts will be able to deface your website when it finds an exploit in your application code.

Wordpress has an FTP update method. You enter your FTP details and it connects to itself via FTP and updates the files that way as a privileged user. The FTP details you entered are not stored anywhere. If your application must be able to update itself, consider using this method.

I think it is always better to have a backup plan than just wasting your time trying to restore.As long as you run a service open to the internet and you are prone to all kind of attacks in which you cannot stop but only contain the damage done. I just find that backup and vulnerability scan help to contain the known vulnerability found. Beside that, manually harden your web server, script, etc which perhaps help to contain exploits/attacks.

---

