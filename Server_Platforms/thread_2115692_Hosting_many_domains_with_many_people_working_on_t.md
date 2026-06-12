---
title: "Hosting many domains with many people working on them?"
date: 2013-02-13
forum: Server Platforms
---

### Post by jmickela on 2013-02-13
I'm hosting a lot of sites, right now the number is around 20. While we don't allow just anyone access to the server we do have to hire contractors to work on some specific sites.

I've tried looking all over and can't find a best practices for this situation.

What is the best way to store/host multiple sites while giving users the ability to maintain those files without opening the entire system up to each user?

The closest that I was was the userdir mod, which let each user host their own site in their home directory, under their own username. But I need this for domains, not user directories.

---

### Post by jmickela on 2013-02-19
Bump, plus some more details.


The thing that is most like what I'm trying to do is setting up a shared web host. I want each domain to belong to a specific user which can read/write to the hosted site's files. When the web server creates a file on the web site it should be owned/editable by the user. Similarly, if the user creates a directory the web server should be able to access it.

---

### Post by GordThompson on 2013-02-22
I won't go so far as to claim that this is "The Best" way, but this worked okay for me:

I was looking after a server for an entrepreneur. He had perhaps 3-4 different "startups" on the go at the same time. Each had its own domain and website, and he had a small team of people that worked on them.

He also wanted to host smaller personal websites for family and friends. For example, he had an aunt who was a personal trainer and he wanted to host her site, but he wanted it separate from the "corporate" sites.

So I set up the "corporate" sites under /var/www such as...

/var/www/corporatesite1.com
/var/www/corporatesite1.com
/var/www/corporatesite2.com

For each "family" site I created a user -- e.g., 'auntliz' -- and then a directory under that user's home directory, like...

/home/auntliz/lizfit.com

...and then adjusted each file in /etc/apache2/sites-available so the DocumentRoot entry was pointing to the right directory.

For example, /etc/apache2/sites-available/corporatesite1.com contained...

DocumentRoot /var/www/corporatesite1.com

...while /etc/apache2/sites-available/lizfit.com contained...

DocumentRoot /home/auntliz/lizfit.com

---

### Post by jmickela on 2013-02-22
My issue is more about access control. We hire contractors to work on individual sites and I want to keep their access limited to just that site.

It wouldn't be that big of a deal if I were just managing a hand full of sites, but at any given moment we have 5-10 sites in active development.

A common problem I'm hitting is that if I try to mess with file ownership/permissions at all one of two things happens, the web server loses the ability to write to the site directories (meaning things like file uploads and automated plugin/module installs fail), or the contractor doesn't have the ability to write to files created by the web server. So, if you install a theme through the Wordpress interface the contractor can't FTP in and modify it at all.

Shared hosts (like Hostgator, Bluehost...) obviously have this all figured out. Each site is separate and owned by the user that owns the account, the web server can read/write those files and creates files in the name of the user who has the account. This is exactly what I need but can't find a tutorial anywhere that describes how to set it up.

---

### Post by Vegan on 2013-02-22
if you want to run a data center like operation, look at user dir for web folders and look into ftp access

also you can jail a user to their home folder

---

### Post by GordThompson on 2013-02-22
@[[COLOR=#000000]jmickela[/COLOR]]("http://ubuntuforums.org/member.php?u=1105552")

1) I certainly understand why you would want developers or maintainers to not be "locked out" of files that are created by the web server. I have run into that annoyance myself.

I got around it by doing something like this (best as I can recall; it was a while ago): assigning a site-specific group to the files and folders in the site hierarchy, using the setgid bit on the folders (chmod 2xxx) so new files and folders would inherit the group from its parent, using umask 002 so the group could write to (modify) new files, and setting existing files to chmod 664 (again, so group could write).


2) However, your wish for "Each site is separate and owned by the user that owns the account, the web server can read/write those files" makes me uneasy because it sounds like you want the web server to be able to modify *any* file on the site, and that seems like a security no-no to me. Sure, the web server might need to be able to write *some* files to *some* folders, but leaving it wide open like that sounds rather scary.

---

### Post by CharlesA on 2013-02-22
> **Vegan said:**
> if you want to run a data center like operation, look at user dir for web folders and look into ftp access

also you can jail a user to their home folder

Just giving this a +1.

I prefer sftp to ftp due to it being encrypted, but if you don't care able sending your data in clear text, you can only allow each user access to their specific directory.

As far as ssh access, you can limit them to only their folders via chroot and only allow sftp access by adding them to a certain group.

EDIT: Giving Apache write access to files being served is a bad idea. It should only have read access to reduce the risk of the potential for a web attack on your site.

---

### Post by SeijiSensei on 2013-02-22
> **CharlesA said:**
> EDIT: Giving Apache write access to files being served is a bad idea. It should only have read access to reduce the risk of the potential for a web attack on your site.

One way around this is to force uploads through the web interface.  Then you have a script (in my case a PHP script) that receives the file, writes it to the file system, and then changes the permissions so the Apache user can no longer write to it.

I've used a couple of web-based file managers, too.  I've never had to install one, but a quick search brought me to [Mollfy]("http://www.mollify.org/") which looked pretty nifty.

---

### Post by CharlesA on 2013-02-22
> **SeijiSensei said:**
> One way around this is to force uploads through the web interface.  Then you have a script (in my case a PHP script) that receives the file, writes it to the file system, and then changes the permissions so the Apache user can no longer write to it.

I've used a couple of web-based file managers, too.  I've never had to install one, but a quick search brought me to [Mollfy]("http://www.mollify.org/") which looked pretty nifty.

+1.

I have the script I use to upload to my host chmod the files before it uploads them via rsync:

```
find $SITE -type d -perm -g+rw -exec chmod g-w {} \;
```

---

### Post by jmickela on 2013-02-25
I've thought about using userdir before, but from what I can't tell it's really only for giving users webspace under a domain that's hosted somewhere else.

Like, you may have example.com in /var/www
but you want john to be able to host a site at example.com/~john

Plus, I think it would have all the same permissions issues.

What about using something like suEXEC?

---

### Post by mackhucks on 2013-02-25
How about using proftpd and virtual users? You can mask the users to use apache's uid/gid. You could set the virtual user to use the desired host directory.

-MH

---

### Post by GordThompson on 2013-02-26
> **jmickela said:**
> I've thought about using userdir before, but from what I can't tell it's really only for giving users webspace under a domain that's hosted somewhere else.

Like, you may have example.com in /var/www
but you want john to be able to host a site at example.com/~john

Plus, I think it would have all the same permissions issues.
I tend to agree. I don't see how that approach would help with the permissions issue unless you had all of the developers use the same login (the one for the site owner) and shared logins are a Bad Thing.

> **jmickela said:**
>  What about using something like suEXEC?
That would allow the web scripts to run under an account other than 'www-data', but which account would that be? From what I can see (I've never used suEXEC myself) you'd still need to pick a user, so you would likely bump into the "shared login" problem cited above.

OTOH, the approach I offered still allows each developer to have their own login, and the sites that they can work on are controlled by the groups to which they belong. 

Simple example: Say you want to have two web sites, beef.com and pork.com. You start by creating a group for each one

```
gord@testbox:/var/www$ sudo addgroup beef_dev
Adding group `beef_dev' (GID 1002) ...
Done.
gord@testbox:/var/www$ sudo addgroup pork_dev
Adding group `pork_dev' (GID 1003) ...
Done.
```You create the folders for the two sites...

```
gord@testbox:/var/www$ sudo mkdir beef.com
gord@testbox:/var/www$ sudo mkdir pork.com
```...and they initially have the default ownership and permissions:

```
gord@testbox:/var/www$ ls -la
total 16
drwxr-xr-x  4 root root 4096 Feb 26 07:04 .
drwxr-xr-x 14 root root 4096 Feb 26 07:02 ..
drwxr-xr-x  2 root root 4096 Feb 26 07:04 beef.com
drwxr-xr-x  2 root root 4096 Feb 26 07:04 pork.com
```So, you change the group and chmod each one to 2775

```
gord@testbox:/var/www$ sudo chgrp beef_dev beef.com
gord@testbox:/var/www$ sudo chgrp pork_dev pork.com
gord@testbox:/var/www$ sudo chmod 2775 beef.com
gord@testbox:/var/www$ sudo chmod 2775 pork.com
```Now the ownership and permissions look like this

```
gord@testbox:/var/www$ ls -la
total 16
drwxr-xr-x  4 root root     4096 Feb 26 07:04 .
drwxr-xr-x 14 root root     4096 Feb 26 07:02 ..
drwxrwsr-x  2 root beef_dev 4096 Feb 26 07:04 beef.com
drwxrwsr-x  2 root pork_dev 4096 Feb 26 07:04 pork.com
```Now add each of the developer logins to their respective group(s)

```
gord@testbox:/var/www$ sudo adduser gord beef_dev
Adding user `gord' to group `beef_dev' ...
Adding user gord to group beef_dev
Done.
```If your umask is already 0002 (mine was)...

```
gord@testbox:/var/www$ umask
0002
```...then when somebody uploads a file (I used SFTP) it looks like this

```
gord@testbox:/var/www$ ls -la beef.com
total 12
drwxrwsr-x 2 root beef_dev 4096 Feb 26 07:10 .
drwxr-xr-x 4 root root     4096 Feb 26 07:04 ..
-rw-rw-r-- 1 gord beef_dev   45 Feb 26 07:10 index.php
```The file is owned by the person who uploaded it, but it can be modified by any member of the group.

Similarly, if one of the developers creates a new subfolder, e.g., "images", then that subfolder inherits the group and permissions of the parent:

```
gord@testbox:/var/www$ ls -la beef.com
total 16
drwxrwsr-x 3 root beef_dev 4096 Feb 26 07:10 .
drwxr-xr-x 4 root root     4096 Feb 26 07:04 ..
drwxrwsr-x 2 gord beef_dev 4096 Feb 26 07:21 images
-rw-rw-r-- 1 gord beef_dev   45 Feb 26 07:10 index.php
```

---

### Post by SeijiSensei on 2013-02-27
I usually just point the DocumentRoot for each virtual host to a location within the user's home directory.  If each user has an individual group that www-data also belongs to, you can create /home/user and /home/user/website with 750 permissions and ownership belonging to the user and her group.  Then the web server can read all the files, but the individual users cannot see any files but their own.

---

