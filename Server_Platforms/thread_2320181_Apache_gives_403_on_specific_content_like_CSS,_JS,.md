---
title: "Apache gives 403 on specific content like CSS, JS, SVG and PNG"
date: 2016-04-11
forum: Server Platforms
---

### Post by andreid2 on 2016-04-11
hey there,

Last few days I've been wandering the internet in desperate search for an answer or any workable solution for my current problem. Although I have found quite some similar threads with same errors, the solutions provided in those threads did not work out for me. So, I created this thread in hope someone can help me out on this issue.

First, let me describe what I'm working on: I've got a Ubuntu 14.04 LTS machine and I have Apache2 (version 2.4.7) installed on it. The website (a Hippo CMS website) is installed in my home directory (/home/user/project). I can run the container with a maven command ("*mvn -P cargo.run*") and I use Apache along with it for serving main files.

**The issue**
When running Apache and the cargo container I can visit the welcome Apache website ("localhost:80") and I can visit my own site ("https://mysite.local", yes it is configured to be secure so I'm using port 443 for it). The apache home page is shown fully and correct (proper layout, all images are shown, etc). However, my own site only displays the textual content and JPG/JPEG images. All CSS files, JavaScript files and images of PNG/SVG format are not loaded. For each of those files I get an [COLOR=#b22222]*403*[/COLOR] error, along with the message "[COLOR=#b22222]*Forbidden. You don't have permission to access rootdir/img/someImage.svg on this server.*[/COLOR]"

So, basically Apache seems to be well configured. The website is loaded and the resources are partially accessible. As far as I can see, the problem seems to be with permissions on Ubuntu.

**Attempts so far**
Well, so far I have tried/done the next few things in order to make it work:
[LIST]
[*]Edited apache2.conf: added [COLOR=#0000cd]*DocumentRoot*[/COLOR] pointing to the directory where the page is deployed; 
[*]Edited apache2.conf: added [COLOR=#0000cd]*UserDir*[/COLOR] pointing to directory where site is deployed (in home directory); 
[*]Edited apache2.conf: added *[COLOR=#0000cd]Directory[/COLOR]* directive to www directory, allowing from all and disabling override (.htacces); 
[*]Edited apache2.conf: added [COLOR=#0000cd]*AddType*[/COLOR] directives for css & js; 
[*]Added www-var to my user group and added my user to www-var group; 
[*]chmod +777 on www directory (had no effect so changed it back to 755); 
[*]chown www directory (recursive) to www-data (and back to my own username); 
[/LIST]

None of those above worked. And it's all I could find on other community disccusions and Google.
Also, there are no errors in the log files of Apache. If anyone wants to see an specific item then let me know.


**The solution**
Who knows what to do to enable me showing the content from my home directory to Apache?


Thanks in advance!!

---

### Post by slickymaster on 2016-04-11
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by SeijiSensei on 2016-04-11
It sounds like the images are stored in /home/user/project/img if /home/user/project is the DocumentRoot for the site in question.  What are the permissions on those directories and the files therein?  What are the permissions on /home/user itself?  Those are the permissions that matter in your case, not the ones on /var/www/html.

---

### Post by andreid2 on 2016-04-11
Hey SeijiSensei, thnx for the reply.

The images are indeed stored in /home/user/project/img. If I run "namei -m /home/user/project/img" I get the next info:
```
drwxr-xr-x /
drwxr-xr-x home
drwx------ user
drwxrwxr-x project
drwxr-xr-x img
```

For the record, I'm not using the default /var/www folder. I've configured the RootDirectory directive in apache2.conf to "/home/user/project".
I also checked the sources (the JS and CSS files, as well as the images) and they all have "-rwxr-xr-x" permissions.

Oh, and all files and folders have as owner "user". I've also (recursively) set them all to "www-data:www-data" (apache user), but that had no effect either. So turned it back to "user" and added "user" to the apache "www-data" group. Which, of course, still had no effect :).

---

### Post by SeijiSensei on 2016-04-11
The problem is that /home/user has 700 privileges.  That limits access to everything store in that directory to just the user. The least permissive solution is this:
```
chmod 711 /home/user
```
That allows all other users, including the "www-data" user that Apache runs as, the ability to list directories below /home/user but not read any of the files there.  Then because /home/user/project has 775 permissions (user and group can write; everyone can read), and /home/user/project/img has 755 permissions (user can write, everyone can read), the www-data user should be able to see the files in /home/user/project/img.  However if the files in that directory have only 600 permissions (user r/w, everyone else none), then you'll need to run "chmod -R 644 /home/user/project/img" to assign global read privileges to the files in that directory.  I'm guessing that's not too likely, and that the real problem is the 700 permissions on /home/user.

---

### Post by andreid2 on 2016-04-12
Awesome, that did the trick!

The solution: I've chmod-ed /home/user with 711 permissions and that works just fine! Thanks for the solution, SeijiSensei :).


But it is weird, though, that although I added www-data to my user group, it has no access to my home directory. I'd say that anyone in my usergroup has the same priviliges as I initially have. Now it looks as if those user groups are a bit of a hollow item, rendering a bit useless if it comes to permissions/priviliges. Ah well, that's another problem. The main problem of this topic has been solved, finally! :).

---

### Post by SeijiSensei on 2016-04-12
With 700 privileges on /home/user, group members have no rights either.  That is what the middle digit controls.  If you want to grant full privileges to user, read and list privileges to group, and nothing to anyone else, use 750 on directories and 640 on files.

Sometimes it's easier to use symbolic privileges to be certain.  For instance
```
chmod 750 /some/directory
```
is the same as
```
chmod u+rwx,g+rx,o-rwx /some/directory
```

---

