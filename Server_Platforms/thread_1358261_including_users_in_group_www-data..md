---
title: "including users in group www-data."
date: 2009-12-18
forum: Server Platforms
---

### Post by tapas_mishra on 2009-12-18
This question is about apache2 on Jaunty.

I do not want the users of my site 
to have write permissions in my Document Root but then also on the same time I want apache to be able to write in the webroot so that if I upload a file then it is possible for the enduser to do so but I will not give 777 permission
to /var/www/somesite/upload/
Some where I came to know that apache2 runs as user www-data if I change the permissions of /var/www/somesite/upload/ to rwx for www-data or make its ownership be changed to www-data how will one more user be able to write in same file basically, I think I should have another user in group www-data and then can give the permissions to group to read and write is it right or not.

---

### Post by volkswagner on 2009-12-18
You can add a user to www-data with usermod command.

```
man usermod
```

```
suod usermod -a -G www-data username
```

---

### Post by HighCommander540 on 2009-12-18
> **volkswagner said:**
> You can add a user to www-data with usermod command.

```
man usermod
```

```
suod usermod -a -G www-data username
```

Ok, just want to point out the is the most insecure set-up ever. Do no do this. It will make your server very vulnerable. 

If you really want something secure. Allow the users to make their own files and folders, then write a script to change the group on the files to "www-data". That is all you need then set the permissions to 0775. This will achieve what you want.

I thought about doing what you want to first, then I realized what that model would do to your system. It would cause a lot of problems. The model that I recommend is very secure and still allows Apache to do what it needs.

---

### Post by tapas_mishra on 2009-12-18
Well thanks for pointing that out what I am not clear with is when PHP script is running developed by a developer then what is the uid of process or the script as I see that using function call move_uploaded_file() needs write permission in the folder inside document root so if I do not give any one a permission to write how will they be able to upload the deocument.

---

### Post by Lars Noodén on 2009-12-18
@ tapas_mishra : you're on the right track but must use a different group.  www-data is the group used by the web server and is the default groups for any processes or scripts that it calls.  Bugs, errors, misconfigurations and misfeatures in the scripts would also have those write permissions.  So giving write access to web directories to the group www-data could allow uninvited guests to make use of your system in ways that you might not find the most enjoyable.  

What you can do is make another group, say 'webmasters' and then make the directory a member of that group and make any users who should have write access also members.   volkswagner's instructions above work, just don't use www-data because of its reserved purpose.  

```

# set the group ownership 
sudo chgrp webmasters /var/www/somesite/upload/

# set the group permissions, plus sgid
sudo chmod g=rwxs,o=rx /var/www/somesite/upload/

```

If access permissions need to get more complicated consider mounting the /var/www/ partition with **acls** enabled.

---

### Post by slakkie on 2009-12-18
Why would that be insecure btw? I fail to see the issue..

---

### Post by tapas_mishra on 2009-12-18
> **slakkie said:**
> Why would that be insecure btw? I fail to see the issue..
many reasons because you would not potentially be willing to allow people to have access to write what ever they wish and similar issues.If you still did not get the point then just reply back here.

---

### Post by slakkie on 2009-12-18
I would assume you give people the right to write data as member of the www-data group because they need to and know what they are doing. 

The solution with a wrapper script that moves files and chowns them to www-data is different how?

---

### Post by tapas_mishra on 2009-12-18
> **slakkie said:**
> I would assume you give people the right to write data as member of the www-data group because they need to and know what they are doing. 

The solution with a wrapper script that moves files and chowns them to www-data is different how?
Well that depends upon what you want to do I would prefer to make another group and give it read write access rather than including the users to www-data.

Some one else reading this thread should point out.

---

### Post by volkswagner on 2009-12-18
> **tapas_mishra said:**
> many reasons because you would not potentially be willing to allow people to have access to write what ever they wish and similar issues.If you still did not get the point then just reply back here.

Please explain the security issue here.  As I am not expert and others may be enlightened.  

As far as I know www-data group can't alter config files, nor are they in the sudoers.

Off hand I don't really see how adding a middle group changes the security risk to www-data executables.

---

### Post by tapas_mishra on 2009-12-18
> **volkswagner said:**
> Please explain the security issue here.  As I am not expert and others may be enlightened.  

As far as I know www-data group can't alter config files, nor are they in the sudoers.

Off hand I don't really see how adding a middle group changes the security risk to www-data executables.
Well I was referring to suid scripts and I am not the right person for Apache since I am new to web technologies.May be some one else can enlighten us.

---

### Post by Lars Noodén on 2009-12-18
Including users in the group www-data is not such a problem.

What is a problem is granting write permissions anywhere on the computer to that group.  

Why?

Because all your web services, including scripts, get run by default as members of that group.  With that level of access, if a visitor your web site can find a way to write to the file system then he can write his own scripts and run them one your machine.  That can be used to find a way to escalate further access, eventually to root.  If not to root, it can still be used to set up a corner on the web site or take over the main web site.

---

### Post by tapas_mishra on 2009-12-18
See the entire issue is I want to set the permissions or arrange the users on webserver but at the same time I do not want to give 777 permission in directory where document etc needs to be uploaded ,my problem is I used move_uploaded_file() and had permission 755 but this gave me following error
```

[function.move-uploaded-file]: failed to open stream: Permission denied 
```then I changed permissions  to 775 but still same problem then I changed the permissions to 777 the error was resolved but then this has its own security concerns so I am concerned as now what permissions should I be able to set or how do I run the PHP scripts so that the users can upload or download the files but also the permissions on the directory are not 777  so I am asking as to what uid does these scripts are being called as or to which group they belong if I get a hint here I will be able to do it. Which I have almost got .
To resolve the error above does not mean that I leave my directories writeable for any one.


> **Lars Noodén said:**
> @ tapas_mishra : you're on the right track but must use a different group. www-data is the group used by the web server and is the default groups for any processes or scripts that it calls. Bugs, errors, misconfigurations and misfeatures in the scripts would also have those write permissions. So giving write access to web directories to the group www-data could allow uninvited guests to make use of your system in ways that you might not find the most enjoyable. 

What you can do is make another group, say 'webmasters' and then make the directory a member of that group and make any users who should have write access also members. volkswagner's instructions above work, just don't use www-data because of its reserved purpose. 

```

# set the group ownership 
sudo chgrp webmasters /var/www/somesite/upload/

# set the group permissions, plus sgid
sudo chmod g=rwxs,o=rx /var/www/somesite/upload/

```If access permissions need to get more complicated consider mounting the /var/www/ partition with **acls** enabled.

Lars I wish if you could point me to the right tutorial or keyword to google since this is an important issue and I wonder if it is not documented  I also want to know  what does www-data do and why is it present ,if I have to go through this process.
I googled and to my surprise I came across only these four links
[http://www.google.co.in/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=Nw7&q=securing+apache2+move_file_upload()&btnG=Search&meta=&aq=f&oq=]("http://www.google.co.in/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=Nw7&q=securing+apache2+move_file_upload%28%29&btnG=Search&meta=&aq=f&oq=")

some information is given here 
[http://www.mysql-apache-php.com/fileupload-security.htm](http://www.mysql-apache-php.com/fileupload-security.htm)

---

### Post by Lars Noodén on 2009-12-19
> **tapas_mishra said:**
> See the entire issue is I want to set the permissions or arrange the users on webserver but at the same time I do not want to give 777 permission in directory where document etc needs to be uploaded ... I changed permissions  to 775 but still same problem then I changed the permissions to 777 the error was resolved but then this has its own security concerns so I am concerned as now what permissions should I be able to set or how do I run the PHP scripts so that the users can upload or download the files but also the permissions on the directory are not 777  


Thanks.  It takes a few rounds to define the scope of the problem.  

If there are php scripts in the DocumentRoot, /var/www/htdocs, then make another directory *outside* of that hierarchy, e.g. /var/www/uploads and use the [Directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory) runtime directive to allow read access in the manner appropriate to your service.  Then change just that one directory's permissions in the filesystem so that the group can write to it, 775.  If done right, that makes sure that no scripts are parsed there by the server.  If you can upload a php script, say index.php, into that directory and when viewed by the web browser it should show up as source code.  

> **tapas_mishra said:**
> so I am asking as to what uid does these scripts are being called as or to which group they belong if I get a hint here I will be able to do it.

See two places:
/etc/apache2/apache2.conf
/etc/apache2/envvars

Specifically look in apache2.conf for 

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

and in envvars for 

export APACHE_RUN_USER
export APACHE_RUN_GROUP

Historically the httpd and many other daemons ran as 'nobody'  However, to keep things separate, individual services get unique group memberships.  Why groups?   Because that's the easiest way to manage permissions.  If you try to grant / revoke / manage permissions on a user by user basis, it quickly fails to scale up and mistakes start to happen costing time and security.

So httpd, when started is run by root and thus has the privileges of root.  It only needs that level of privilege to bind to privileged ports (< 1024) and after that it starts several unprivileged child processes running under the user and group specified in apache2.conf and envvars.  All subsequent scripts or processes called by httpd will be run with that user and group by default.

If special exceptions for user and group permissions are needed for specific processes then the [SuexecUserGroup](http://httpd.apache.org/docs/2.2/mod/mod_suexec.html#suexecusergroup) can be used to set something else for a specific process or script.

---

### Post by Lars Noodén on 2009-12-19
@ tapas_mishra : you forgot to post the answer here in this thread
It's pretty close to what I wrote, but more detailed.  I had seen it first I would not have needed to write much of the above.  

[http://ubuntuforums.org/showthread.php?t=1358763](http://ubuntuforums.org/showthread.php?t=1358763)

---

### Post by tapas_mishra on 2009-12-19
> **Lars Noodén said:**
> @ tapas_mishra : you forgot to post the answer here in this thread
It's pretty close to what I wrote, but more detailed.  I had seen it first I would not have needed to write much of the above.  

[http://ubuntuforums.org/showthread.php?t=1358763](http://ubuntuforums.org/showthread.php?t=1358763)
My apologies for the same :)  but I appreciate the effort you did in clarifying the same here.

---

