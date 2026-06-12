---
title: "deployment of WWW content"
date: 2008-08-27
forum: Server Platforms
---

### Post by stanleytberry on 2008-08-27
I installed UBUNTU server v8.04.  I specified LAMP and SAMBA when it asked to select packages.  It's in a mixed network.  I want to use HomeSite on a Windows 2000 Professional system to develop WWW content.  It took me 3 days to work through smb.conf to get to the point that HomeSite on W2K can access and update a share defined as /home/stan/WWWStage.  HomeSite can create and modify files and put them back.  My thought was to synchronize my /home/stan/WWWStage and /var/www.

I don't know much about Linux but I can read.

Is there an elegant way to take the content I have developed (and placed in my staging directory) and update the Apache content directory on my server?

Any help will be appreciated.

Thanks,
Stan

---

### Post by ggaaron on 2008-08-27
You mean that you want to mirror /home/something/www to /var/www? If yes then use a symlink, remove /var/www with 'rmdir /var/www' and symlink 'ln -s /home/something/www /var/www'.

---

### Post by de0xyrib0se on 2008-08-27
It is important to note there is only **one copy of your data** this way since you are only linking to your staging folder.

---

### Post by stanleytberry on 2008-08-27
That's too easy.

/var/www is owned by root:root and has drwxr-xr-x permissions.  My /home/something/www is owned by something:something and has drwxrwxrwx permissions (and is shared via SAMBA).

I see no way to supply different permissions for the two names that refer to the one directory.  Is that possible?

Also, /var/www is the directory to which APACHE looks for content.  Will it care that /var/www has become a symbolic link?

Thanks,
Stan

---

### Post by ggaaron on 2008-08-27
If you have Options FollowSymlinks in apache configuration it won't care if it is a symlink, but yes it will be just a link to your /home/something/www directory with the same permissions, user and so on, no way to change it in this approach. If it's a testing environment then you shouldn't care, if other users access this computer and you need to have more restrictive permissions you can tar you www directory, untar to /var/www and chmod 0644 -R /var/www ; chown apache.apache -R /var/www. If you've made a script it would be quite easy to test too.

---

### Post by stanleytberry on 2008-08-27
Thanks.

What if I eventually drop this server into a DMZ?  I prob'ly won't want the staging directory on the server.  How then should I deploy the web content?

TAR file?

Is FTP secure enough?

Again, thanks,
Stan

---

### Post by ggaaron on 2008-08-27
What do you mean by deploy? You want to develop web content in your home directory and then deploy it on the same machine with proper rights and owners? I'd make a script that would copy a snapshot of you development directory (using tar/zip/cp) to production directory and set proper permissions.

---

### Post by cdenley on 2008-08-27
I use a script like this
```

#!/bin/bash
sudo rsync -rvog --delete --perms --exclude=*~ /var/www.temp/ /var/www/
sudo chmod -R 555 /var/www
sudo chgrp -R www-data /var/www
sudo chown -R root /var/www
sudo chmod -R 750 /var/www

```
/var/www.temp is where I edit the website, and I can access it from the LAN using [http://mydomain.com/testing](http://mydomain.com/testing) to test it before I "deploy" it. The last four commands are just to set the permissions a bit more strict.

---

### Post by de0xyrib0se on 2008-08-27
You can use an nfs share, you can use secure FTP whatever rocks your boat, you can even do rsynch if you like. This is if its on a different server, if its local you can just copy the files over using copy and schedule a job to do this every night if you like using cron.

---

### Post by cdenley on 2008-08-27
> **de0xyrib0se said:**
> You can use an nfs share, you can use secure FTP whatever rocks your boat, you can even do rsynch if you like. This is if its on a different server, if its local you can just copy the files over using copy and schedule a job to do this every night if you like using cron.

I use rsync to copy files locally because it will delete no longer used files and not leave anything missing for a moment. I would recommend rsync whether you are transferring locally or remotely, cron or shell.

---

### Post by stanleytberry on 2008-08-27
I really appreciate your responses.

I'm 66 years old.  HP laid me off 22 December 2006 (think about that ... I was 6 months away from 65).  I had worked for IBM for 30 years, telecommuted (programming) for 2 and a half years, worked for Compaq and then HP for another 8 years.

The one thing I've always liked was "playing" with computers.

I never used Linux when I was working for somebody else.  I now have an ipCop machine, a Netgear ReadyNAS NV+ (on which I'm hosting several MySQL databases) and my latest learning exercise is this UBUNTU server.  I've assembled the machines (the hardware) except for the NASServer (2 workstations ... 1 for me, 1 for my wife ... the ipCop box, a backup server, and the current web server).  I can't afford to update the Windows based software so I want to eventually move to Linux.

I have a web site, [HTTP://www.Stan-and-Jeanne.us](HTTP://www.Stan-and-Jeanne.us), but it's not great.  I thought, if I live long enough, that I'd like to have a LAMP server.

It's not a business ... it just keeps me alive.

Thanks,
Stan

---

### Post by eholz1 on 2008-08-29
Hello there,
I am also a new user of Ubuntu.  I am running 8.0.4 LTS server version.  I had a website, a local server for testing, but I sometimes expose it to the internet.  I have what could be called the "out of the box" install including all the LAMP stuff.  It all seems to work ok, including the MySQL db.  But...
I had two web sites on my Fedora system (blitzed in favor of Ubuntu).  I see that my web content goes in /var/www/ and so on.
I see from above that owner and group should be set to something.
I had a backup of my Fedora site, and copied it into the ubuntu server location (/var/www).

It seems that everything I copied into the /var/www is all root:root.  I do have a problem that some of my files are not readable my my php pages (like css files, etc). My css files are stored in /var/www/portfolios/css.  I made the portfolios dir in /var/www.  I tried to copy (cp -r /files/backup/portfolios /var/www/), but the css dir and its files all have '?' marks where the chmod settings should be (rwx, etc).  I was able to get the file settings to appear rwxr-xr-x etc, after I sudo chown root:root for the css dir and its files. What should the correct privs be for apache so I do not have to use sudo to edit, copy or move my web files around?  I use php. what user and group should I use to have things correct.

Thanks,
eholz1

---

### Post by ggaaron on 2008-08-29
> **eholz1 said:**
> Hello there,
I am also a new user of Ubuntu.  I am running 8.0.4 LTS server version.  I had a website, a local server for testing, but I sometimes expose it to the internet.  I have what could be called the "out of the box" install including all the LAMP stuff.  It all seems to work ok, including the MySQL db.  But...
I had two web sites on my Fedora system (blitzed in favor of Ubuntu).  I see that my web content goes in /var/www/ and so on.
I see from above that owner and group should be set to something.
I had a backup of my Fedora site, and copied it into the ubuntu server location (/var/www).

It seems that everything I copied into the /var/www is all root:root.  I do have a problem that some of my files are not readable my my php pages (like css files, etc). My css files are stored in /var/www/portfolios/css.  I made the portfolios dir in /var/www.  I tried to copy (cp -r /files/backup/portfolios /var/www/), but the css dir and its files all have '?' marks where the chmod settings should be (rwx, etc).  I was able to get the file settings to appear rwxr-xr-x etc, after I sudo chown root:root for the css dir and its files. What should the correct privs be for apache so I do not have to use sudo to edit, copy or move my web files around?  I use php. what user and group should I use to have things correct.

Thanks,
eholz1


'cat /etc/passwd | grep www'

This will give you the user name that apache is running with on Debian based systems. I can't give you this directly because I don't have a Debian based system=) You can also edit config in /etc/apache2/envvars and set a user of your choice.

---

### Post by eholz1 on 2008-08-30
> **cdenley said:**
> I use a script like this
```

#!/bin/bash
sudo rsync -rvog --delete --perms --exclude=*~ /var/www.temp/ /var/www/
sudo chmod -R 555 /var/www
sudo chgrp -R www-data /var/www
sudo chown -R root /var/www
sudo chmod -R 750 /var/www

```
/var/www.temp is where I edit the website, and I can access it from the LAN using [http://mydomain.com/testing](http://mydomain.com/testing) to test it before I "deploy" it. The last four commands are just to set the permissions a bit more strict.

I applied these settings to my webserver, and can no longer access it locally or from the web.  How do undo the damage with the permissions settings?

Thanks,
eholz1:confused:

---

### Post by ggaaron on 2008-08-30
I quite don't understand why this script changes permissions twice, but try:
'sudo chmod -R 755 /var/www' - it should give everyone right to read contents of /var/www, so it should work.

---

### Post by windependence on 2008-08-31
The symlink solution is too messy.

What I think he would like to do is have a staging enviornment so that he can test content and then push it to the web server when he is done and satisfied it is ok. There are several ways of accomplishing this. What I do is I have my web servers on a VMware box. I have prod.mysite.com as one server and staging.mysite.com as another. I test on staging and can even test OS upgrades. and patches there. When I want to push content, I rsync the document root dorectory of the staging server with the doc root of the prod server. Fast and elegant. It can also be done using Winscp with drag an drop if you don't like to run rsync in the CLI.

Alternatively, you could use something like Repliweb, although this is a commercial application. I haven't been able to find any open source alternatives but I have to believe there are some out there.

Thirdly, you could just rsync your staging and doc root directories whenever you need to with one command at the CLI.

-Tim

---

### Post by ggaaron on 2008-08-31
One more option offering also some other great features - version control system, put your site into git/mercurial/bazaar and pull/push as you wish. Just remember not to let anyone to .hg/.git/.bzr directory.

---

### Post by cdenley on 2008-09-01
> **ggaaron said:**
> I quite don't understand why this script changes permissions twice, but try:
'sudo chmod -R 755 /var/www' - it should give everyone right to read contents of /var/www, so it should work.

I was originally having problems with permissions while content was being copied. I first give everyone read access so www-data can access files while the permissions are being changed. However, looking at it now, the group owner is changed before other read access is taken away, so the first chmod probably isn't necessary.

I made www-data the group owner so nobody can read my scripts except root and www-data. Since sensitive data like database passwords or encryption keys/methods are often coded in scripts, you don't want to give more users read access than necessary.

If you're having trouble with permissions, you probably aren't using ubuntu. My script gives the www-data group read access since apache runs as a user which belongs to that group. I believe debian and other distro's would require a different group.

---

