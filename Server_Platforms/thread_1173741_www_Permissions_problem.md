---
title: "www Permissions problem"
date: 2009-05-30
forum: Server Platforms
---

### Post by ybmatters on 2009-05-30
Hi all, I'm new to nix and ubuntu (using jaunty), but quite experienced windows user. Sorry if I'm asking a FAQ, but I could not find an answer.

I'm trying to set up a web development environment for myself and have successfully installed LAMP, ftp etc. (steep learning curve but fun :p)

I followed the instructions at [http://ubuntuforums.org/showthread.php?t=10159](http://ubuntuforums.org/showthread.php?t=10159) to move the location of my web-site to be within a shared area of my home directory - something like /home/shares/www/

If I place a test index.html file here, I can access it from my windows machine vis: http:/192.168.x.x (ip of ubuntu machine). All works fine.

If I take a site I've developed within Dreamweaver and ftp it to the appropriate directory it gets there fine, but I cannot access it (forbidden) UNTIL I go to the /www/ directory and set the permissions for others to "read only" and apply those permissions to enclosed files.

**[COLOR=Green]How do I enable permissions etc so that any sites I upload will simply be available within my LAN?[/COLOR]**

---

### Post by theboytony on 2009-05-30
hi I'm no expert but don't you do this in the apache config file, for each site allow access by ip address ie 192.168.1.*

---

### Post by sanemanmad on 2009-05-30
Hmm... I really don't think that is possible. what it sounds like is a permissions issue when you upload the document to the directory. What are the permissions of the documents being uploaded? what do they look like after uploaded?

... I am not sure about your FTP setup, however mine is based off of "virtual users", thus all permissions are masked and appear to be owned by "user", however they are actually not.

---

### Post by ybmatters on 2009-05-30
Thanks theboytony, but it's not that, because once I fix the permissions it works.

sanemanmad, its definitely a permissions issue. I've made some progress but...

Once I upload the files with ftp, the basic html files only have -rw------- access, and a sub-directory with images has drwx------ with it's files also having -rw-------. So owner has rw. At this point I get "forbidden" when I try to [http://192.168.x.x](http://192.168.x.x)

Now I can change them in my ftp client to -rw-r--r-- so everyone has read access. I have to do this for the top level files. I have to change the "images" directory to drwxr-xr-x and its files to -rw-r--r-- then all works as expected.

However, my hosting service simply allows me to upload to it and somehow it fixes the permissions to make things automagically available - which is what I'd expected and would like to work if possible. They must have some sort of script that runs on a CRON job or something I guess - but that's beyond me at this time.

I'll keep chipping away at it, but if someone knows how to do it, I'd be grateful for the hint in the right direction.

---

### Post by ybmatters on 2009-05-30
[COLOR=Blue]**The Solution**[/COLOR]

[COLOR=Black]Amazingly simple really: Create a CRON job to run every minute. The command is simply _[COLOR=Green]chmod -R o+rx directory_name/*[/COLOR]_

Note: my directory is immediately under the home directory so under ubuntu cron runs from there (leastways as I understand it).

So every minute whatever is in that directory has its permissions changed. Whatever I upload will get permissions soon enough.:popcorn:
[/COLOR]

---

