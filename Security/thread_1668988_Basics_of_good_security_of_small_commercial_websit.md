---
title: "Basics of good security of small commercial website?"
date: 2011-01-17
forum: Security
---

### Post by KonfuseKitty on 2011-01-17
I'm a total newbie at this and have so many questions it's difficult to know where to begin ... let's start with the basics:


1. I understand you can protect your files or directories in your website by setting file/directory permissions.  The meaning of r w x is clear to me, but I'm not sure how to proceed... Starting with the index.html file, if I wanted to make it so that anyone in the world can read it but can't modify it, do I set its permissions to rwxr-xr-x? If I set it to rwxr--r--, would that mean the file couldn't be served? I mean, what does the x setting do on a .html file, how can a .html file be executable?


2. If file permissions work on the lines of owner-group-others, in the context of a website, who is 'group'? As far as I can tell, there's only the owner, which is me, and others, which is the world accessing the site. Am I correct in thinking that by default, say when creating a website on a shared hosting server, there is no group unless I specifically set one up?


3. My ISP allows the DynDNS.org service, meaning that I could serve a website from my home. It's too early to go that route just yet, but for future reference, I would like to ask about the server software called Hiawatha. It is said to be secure, but having read some evaluations of it, it doesn't seem to offer anything that couldn't be accomplished with Apache or Cherokee, it's just that its security settings are simpler and easier to configure. Am I right about this? Or does Hiawatha truly offer something that the other major server packages don't?


That should be enough for now, though I'm sure I'll have many more questions. Looking forward to your responses - thanks in advance.

---

### Post by mikewhatever on 2011-01-17
> **KonfuseKitty said:**
> 

1. I understand you can protect your files or directories in your website by setting file/directory permissions.  The meaning of r w x is clear to me, but I'm not sure how to proceed... Starting with the index.html file, if I wanted to make it so that anyone in the world can read it but can't modify it, do I set its permissions to rwxr-xr-x? If I set it to rwxr--r--, would that mean the file couldn't be served? I mean, what does the x setting do on a .html file, how can a .html file be executable?

In the case of html, rwxr--r-- means it can be edited by the oner only, which is likely what you want. Htmls are not executable, but then permissions are there for all the files, for example, scripts, which have to be executable.

> 2. If file permissions work on the lines of owner-group-others, in the context of a website, who is 'group'? As far as I can tell, there's only the owner, which is me, and others, which is the world accessing the site. Am I correct in thinking that by default, say when creating a website on a shared hosting server, there is no group unless I specifically set one up?

In your particular case, 'group' is equivalent to 'others', but suppose a team of people was maintaining the site, they could be assigned to the admin group and allowed to edit stuff.

---

### Post by bodhi.zazen on 2011-01-17
See also : 

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

On a web server, I keep files such as index.html owned by root, group www-data, and permissions of 440 (read only).

---

### Post by HermanAB on 2011-01-18
Probably the most important things are to always use proper >8 character passwords for ALL accounts, don't use VNC or FTP on a server and set a rate limiting rule with iptables.

---

### Post by HermanAB on 2011-01-18
Probably the most important things are to always use proper >8 character passwords for ALL accounts, don't use VNC or FTP on a server and set a rate limiting rule with iptables to discourage brute forcers.

---

### Post by KonfuseKitty on 2011-01-19
Thank you all, much appreciated.


> **bodhi.zazen said:**
> On a web server, I keep files such as index.html owned by root, group www-data, and permissions of 440 (read only).


Bodhi, could you please elaborate on this. What is the benefit of index.html being owned by root rather than the user-owner? And why 440 permissions, shouldn't that be at least 744, so owner can do anything, group and others can read. If others is 0, can the world see the file on the internet at all?


One more follow up question: I take it .PHP files are executable, they should be 755, so visitors can read and execute. But if I didn't want the world to see the actual PHP code being used in the file, could I set it to 711, so they can execute the file but can't read it?

---

### Post by SeijiSensei on 2011-01-19
> **KonfuseKitty said:**
> One more follow up question: I take it .PHP files are executable, they should be 755, so visitors can read and execute. But if I didn't want the world to see the actual PHP code being used in the file, could I set it to 711, so they can execute the file but can't read it?

No, PHP files are not executable.  They are scripts that are executed by an interpreter, either mod_php which is installed into the Apache web server, or the standalone php binary.  PHP scripts that run under Apache must be readable by the www-data user that Apache runs as.  You can accomplish this by putting the scripts in group www-data and setting their permissions to 640.

I don't put my scripts into the web root, but maintain a separate "include" directory in another branch of the filesystem tree.  Usually my "index.php" script consists of nothing more than a few parameter settings and a bunch of include() commands.  Everything else sits outside the publicly-visible directories like /var/www.

---

### Post by Jive Turkey on 2011-01-19
One thing may need clarification for the OP here. The file permissions for your web directory apply to local users on that machine, not the users on the internet.  Apache can serve the files if user "www-data" can read them regardless of the other permissions/ownership of the files.

[q]3. My ISP allows the DynDNS.org service, meaning that I could serve a website from my home. It's too early to go that route just yet, but for future reference, I would like to ask about the server software called Hiawatha. It is said to be secure, but having read some evaluations of it, it doesn't seem to offer anything that couldn't be accomplished with Apache or Cherokee, it's just that its security settings are simpler and easier to configure. Am I right about this? Or does Hiawatha truly offer something that the other major server packages don't?[/q]

I would recommend working with apache, or some other web server in the default repositories until you are more comfortable (than me currently) administering linux.  You will find more helpful documentation for apache to help you learn the ropes.  That said, I have seen some credible reports that nginx is the most efficient one out there, especially for high traffic situations.

---

### Post by KonfuseKitty on 2011-01-20
Thanks again, I think I'm slowly starting to understand this better. Please let me know if I got it right:


1. Website files served by a web server can (and should) always have 'other' set to 0, because the site visitors never access the file directly as 'other', it is the server software that is accessing the file as a particular user.
2. By convention, Apache is set up as user and group 'www-data' and only needs read permission to be able to serve the file, even if it's a script like .php. So 'group' permission on website files needn't be (and usually shouldn't be) higher than 4.


This still leaves me with the question of what owner permissions should be. Bodhi said owner should be root and permission 4, but how can you then work with the file? You, the file author, aren't root, and need at least 6 to write the file... What am I missing?


Additionally, if I put my .php files in a directory not visible to the public, what shoud be the permissions of this directory and the files within it? I'm not clear what user and group PHP would then be accessing the files as, while the files remain invisible to everything else. Would PHP need to be assigned to its own group, and permissions set for it on the files?


One more question: how do bots and spiders access website files? They don't do it through a browser...

---

### Post by bodhi.zazen on 2011-01-20
> **KonfuseKitty said:**
> Thanks again, I think I'm slowly starting to understand this better. Please let me know if I got it right:


1. Website files served by a web server can (and should) always have 'other' set to 0, because the site visitors never access the file directly as 'other', it is the server software that is accessing the file as a particular user.
2. By convention, Apache is set up as user and group 'www-data' and only needs read permission to be able to serve the file, even if it's a script like .php. So 'group' permission on website files needn't be (and usually shouldn't be) higher than 4.


This still leaves me with the question of what owner permissions should be. Bodhi said owner should be root and permission 4, but how can you then work with the file? You, the file author, aren't root, and need at least 6 to write the file... What am I missing?


Additionally, if I put my .php files in a directory not visible to the public, what shoud be the permissions of this directory and the files within it? I'm not clear what user and group PHP would then be accessing the files as, while the files remain invisible to everything else. Would PHP need to be assigned to its own group, and permissions set for it on the files?


One more question: how do bots and spiders access website files? They don't do it through a browser...

Well, first off, I advise you use the proper terminology for Linux permissions.

Second, if you did not read this page, go back and review it as a next step:

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Every directory and file has an owner, group, and other.

There are subtle differences between permissions on files and directories.

For the most part, for read only (ro) access directories need a permission of 5 (r-x) and files 4 (r--).

The above link explains why.

Another thing you should understand is there is more then one way to do things in Linux and often one technique is no better then another, it is more important to understand why.

IMO, static files on a web server should be owned by root:www-data with permissions of 440

root can still read and write the file (root has ultimate permission), www-data (apache) has ro access, and no other user can read or modify the file.

This way if apache is compromised, the intruder can not directly modify your files. This would not be the case if the files were set to permissions of 777 or 666 or other.

The principle here is to give the lease access to the files and thus increase security. There is no reason your user "nobody" (or orhte system users) should need access to the files, thus permission is denied to "other" users.

---

### Post by perspectoff on 2011-01-20
On a server on which there will only be one local user, it is ok to give that user ownership of folders instead of root. It saves you always having to be root to work with files, so I agree with that.

If the server might have many "administrators" with access to it, each with varying levels of expertise, then leaving the installed files available only to root is not a bad idea to keep eager beavers from changing your setup files.

For a WebDAV server, for example, you often want both local access (user owner or group) as well web access (www-data owner or group) to the folder in which changeable files are to be stored. Leaving such a WebDAV folder with root as owner would be problematic.

BTW, I understand your terminology just fine.

---

### Post by KonfuseKitty on 2011-01-21
Thanks guys, it's all good info. I've now started experimenting with a shared hosting account and have two final questions:


1. What would be your guess how a shared hosting account is set up if it serves files from its "public-html" folder even with file permissons set as low as 400? My uneducated guess is that the account is set up as a 'rootjail' and Apache is running as root. That's the only way I can explain it being able to serve files with group permission of 0. Is this an insecure setup?


2. Setting up a password-protected folder, implemented with the .htaccess method, .php files in the folder were served if they were referenced by a file in the "public-html" folder, but required authentication if accessed directly. Since the idea is to protect raw .php code from prying eyes but not stop executing it, this behaviour is fine with me. However, how secure is it? Is it possible for bots and spiders to somehow crawl their way to the files in the protected folder?

---

### Post by SeijiSensei on 2011-01-21
> **KonfuseKitty said:**
> Since the idea is to protect raw .php code from prying eyes but not stop executing it, this behaviour is fine with me. However, how secure is it? Is it possible for bots and spiders to somehow crawl their way to the files in the protected folder?

I'll reiterate my earlier suggestion that you keep the PHP code out of the public server tree and reference it with include() or require() commands.  Something like this:

/var/www/index.php

```

<?php
$include_dir="/var/www/include/";

require($include_dir."startup.php");
require($include_dir."front_page.php");
?>

```

---

### Post by KonfuseKitty on 2011-01-21
Yes, that's exactly what I'm doing. It's just that the location of the included .php file can't remain secret because the path is visible in the calling file, if the calling file can be retrieved as is, without its php code being executed. Hence my question.

---

### Post by SeijiSensei on 2011-01-21
Well the answer to that question is no.  As long as the PHP interpreter sees the file first, the end user will only see the generated HTML.  

You can further limit knowledge of where the included files are stored by setting the "include_path" parameter in /etc/php.ini.  Then you can remove any references to the included director(ies) in the scripts themselves.

Another route is to use a different extension for the included files than .php.  I use .inc for this purpose, then have a FilesMatch directive in the Apache configuration like this:

```

<FilesMatch \.inc$>
deny from all
</FilesMatch>

```

That blocks all downloads of files ending in .inc.

---

### Post by CharlesA on 2011-01-21
> **KonfuseKitty said:**
> Yes, that's exactly what I'm doing. It's just that the location of the included .php file can't remain secret because the path is visible in the calling file, if the calling file can be retrieved as is, without its php code being executed. Hence my question.
If the server is serving php up correctly, then that won't happen.

I can't even wget a php file from a web server without it rendering it as html, I just tried it on my webdev server and all I got was a normal xhtml file.

@SeijiSensei: Do you have your own server set up? I'm curious how that would work if you are using shared hosting.

EDIT: Thanks Senji, I fixed a few of the includes references I was using. They look much cleaner now. :)

---

### Post by SeijiSensei on 2011-01-22
> **CharlesA said:**
> @SeijiSensei: Do you have your own server set up? I'm curious how that would work if you are using shared hosting.

Yes. I've never used a shared hosting account.  I've been running my own HTTP servers since 1995, when I had one connected to the Internet over a dedicated 28 Kbps modem line!  I need full control over the servers I use since they're typically doing many different things like e-mail, DNS, and web hosting, not to mention running custom scripts for various purposes like backups.

These days you can lease a virtual server for peanuts.  I just migrated one of my clients off a physical machine they were renting for $200/month to a Linode VM at $30.

> Thanks Senji, I fixed a few of the includes references I was using. They look much cleaner now. :)

You're quite welcome, Charles!

---

### Post by CharlesA on 2011-01-22
> **SeijiSensei said:**
> Yes. I've never used a shared hosting account.  I've been running my own HTTP servers since 1995, when I had one connected to the Internet over a dedicated 28 Kbps modem line!  I need full control over the servers I use since they're typically doing many different things like e-mail, DNS, and web hosting, not to mention running custom scripts for various purposes like backups.

That's nice. I can run a web server at home, but they block port 80, and it's technically against the ToU to do so, so that's not going to happen. That and I don't want to mess with port redirects and junk.

> These days you can lease a virtual server for peanuts.  I just migrated one of my clients off a physical machine they were renting for $200/month to a Linode VM at $30.

That's a good deal. I've seen VPS for $20 a month at [http://bluemilecloud.com/](http://bluemilecloud.com/) and that would probably be the way I'd do it if could afford it. ;)

---

