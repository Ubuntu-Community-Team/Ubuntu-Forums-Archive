---
title: "Configuring user group permissions for Apache"
date: 2019-03-01
forum: Server Platforms
---

### Post by Drone4four on 2019-03-01
I’m trying to setup the access rights and user and group permissions to secure my Apache webserver.

In an AskUbuntu question titled, “[Permissions problems with /var/www/html and my own home directory for a website document root]("https://askubuntu.com/questions/767504/permissions-problems-with-var-www-html-and-my-own-home-directory-for-a-website/")”,  the first answer is enormously detailed, very helpful and a good reference. Another user replied with a more concise solution [here]("https://askubuntu.com/a/939922/737660"). 

Here is the solution:

```

$ sudo chown -R <user>:www-data /var/www 
$ sudo find /var/www -type d -exec chmod 2750 {} \+ 
$ sudo find /var/www -type f -exec chmod 640 {} \+
```

I can understand each operation, point by point. I’ll explain what I can but there are certain things that I need someone on this message board to clarify. I begin with what I do understand.

In the first line I am changing the group owner recursively to the given user in my public_html directory.

In the second line, I am telling my shell to locate each directory and change the mode (permissions) to 2750 in octal format which translates into `rwxr-x---`.

The third line I locate every file and change the mode to (permissions) to 640 which means `rw-r-----`

After invoking those commands, I rsync’ed all my local html up to my server and the contents of my vhosts on my server doesn’t reflect those permissions. Instead, my directories are set to drwxr-xr-x (755) and my files are -rw-r--r--  (644). They don't match.

Here are a series of non-rhetorical questions which I am seeking answers to:

[LIST=1]
[*]With directories set to 755 and with files set to 644, is this permissions scheme secure? Or would it be better and more safe for directories to be set to 2750 and files be set to 640? 
[*]To account for the discrepancy between the original intended mode changes and what I actually ended up with, I figure that the reason is because the umask wasn’t set. Is this correct?
[*]The default umask on Linux is 0002. Is this safe for websites (basic html, no CMS)?  If this is unsafe, what would you people recommend I change the umask to?
[*]Another thing I noticed is that the content which I uploaded are not members of the www-data group and have instead retained or inherited a different group attribute. Instead of <user>:www-data it is <user>:<user>. I know how to correct this using `chgrp` as sudo and use the recursive parameter, but I am just wondering: what would I need to do to automate proper group inheritance when changes are made, like when more content is uploaded?
[/LIST]

Years ago on the Ubuntu forums, [I was exploring user and group permissions]("https://ubuntuforums.org/showthread.php?t=2268991").   I had forgotten some of the nuances but refreshed my memory by reading over my lengthy forum thread. In addition, other resources that I’ve been reviewing today include Eli the Computer Guy’s slowly aging (but still very helpful) tutorial on YouTube titled “[Users, Groups and Permissions in Linux]("https://www.youtube.com/watch?v=zRw0SKaXSfI")” and Linode’s well maintained to this day a tutorial called “[Linux Users and Groups]("https://www.linode.com/docs/tools-reference/linux-users-and-groups/")”.

---

### Post by TheFu on 2019-03-01
The userid must be in the www-data group, otherwise this won't work.

After the chown, no need to use sudo anymore.  The owner of the files/directories has full control over the permissions.  Using sudo when it isn't necessary is a bad security practice - though we all to it from time to time, if only by accident.

chmod 2750 makes rwxr-s---    The setgid bit is extremely important. That is what makes working within the group possible.  There are other methods which can be required, since sometimes the web-server will need to have write authority when running to specific directories and files.  Minimizing that **is** helpful to security. Whether any specific web-app can work this way is 100% dependent on the web-app developer team and how much they care about security.

There are faster/concise ways to effectively get the **find** commands to the same result.
```
chmod -R u=rwX,g=rX,o-rwx /path/to/dir    # this keeps files and directories that already have eXecute with that permission.
find /path/to/dir -type d -exec chmod -R g+s {} \;    # this only finds directories, so it only adds the setgid flag on those.

```
Using 'find' is slower, and every exec spawns another sub-process.  Recursive chmod is fast.

But whatever you choose is fine, provided it works. ;)

Onto your questions.
1)  The answer is, it depends. Why not just tell **rsync** to retain the permissions? It can do that when the userid in the rsync command is also the owner on the target system.
2) there is a default umask. Looks like 022 from what you report. You can change it to 027, if you like.
3) The default umask is system dependent. You can change it for the system or for the userid. Whether that is safe depends on many things.
4) If you upload using sftp and the userid in the connection is in the www-data group, and the setgid flag/bit is set on all the relevant directories BEFORE the upload, then the group would be retained.

But all these permissions things should be tested in temporary directories with some play files before touching any production directories while you aren't 100% positive of what they do.  Play around with different chmod and umask and directories and different users who are and are not in the group.  Once you do this, something should "click" and assuming you keep using permissions, you'll never need to learn this stuff again.

Lastly, just to avoid lurker confusion - setgid != sticky bit.   The most common use of the sticky bit is on /tmp/.

---

### Post by Bashing-om on 2019-03-06
Drone4four; Hey -

TheFu has the right of it :)

---

### Post by Drone4four on 2019-03-06
> **TheFu said:**
> After the chown, no need to use sudo anymore.  The owner of the files/directories has full control over the permissions.  Using sudo when it isn't necessary is a bad security practice - though we all to it from time to time, if only by accident.
Thanks for the pointer.

> There are faster/concise ways to effectively get the **find** commands to the same result.
```
chmod -R u=rwX,g=rX,o-rwx /path/to/dir    # this keeps files and directories that already have eXecute with that permission.
find /path/to/dir -type d -exec chmod -R g+s {} \;    # this only finds directories, so it only adds the setgid flag on those.

```
Using 'find' is slower, and every exec spawns another sub-process.  Recursive chmod is fast.
But whatever you choose is fine, provided it works. ;)

You should contribute to this or something similar to the StackOverflow question I mentioned earlier titled  &#8220;[Permissions problems with /var/www/html and my own home directory for a website document root]("https://askubuntu.com/questions/767504/permissions-problems-with-var-www-html-and-my-own-home-directory-for-a-website/")&#8221;. I&#8217;m sure you would get many upvotes and fast!

> 1)  The answer is, it depends. Why not just tell **rsync** to retain the permissions? It can do that when the userid in the rsync command is also the owner on the target system.

Here is the rsync command I always use: ```
$ rsync -va --stats /home/<localuser>/dev/projects/<DN3>/public_html/* <remoteuser>@<remotehost>:/var/<DN3>/html/ 
```
What would you recommend that I add to this rsync command to preserve the user and group permissions when I use it?

> 2) there is a default umask. Looks like 022 from what you report. You can change it to 027, if you like.

Here is the permissions scheme in my Apache public_html folder: 

```

<user>@<remotehost> /var/www/angeles4four.info/html$ umask
0002
<user>@<remotehost> /var/www/angeles4four.info/html$ ls -la
total 20368
drwxr-s---  4 <user>   www-data     4096 Mar  7 00:40  .
drwxr-s---  3 <user>   www-data     4096 Feb 24 02:16  ..
-rw-rw-r--  1 <user>   www-data       62 Mar  1 15:32  .htaccess
-rw-r--r--  1 <user>   www-data      341 Jan 28 07:25 'How to install Matomo.html'
drwxrwsr-x  2 <user>   www-data     4096 Mar  1 15:11  css
-rw-r-----  1 <user>   www-data     3157 Mar  7 00:40  index.html
drwxr-xr-x 12 www-data www-data     4096 Mar  5 02:20  piwik
-rw-rw-r--  1 <user>   www-data 20823821 Mar  5 02:17  piwik.zip
drwxrwsr-x  2 <user> www-data     4096 Mar  7 01:36  testdirectoryforTheFu
<user>@<remotehost> :/var/www/angeles4four.info/html$ cd
<user>@<remotehost> :~$ umask
0002

```

It appears on my system, for both my public_html folder in /var/ **AND** my user&#8217;s home directory, the umask is set to 0002, not 022 as you&#8217;ve suggested. What would you make of this discrepancy? It may help to take a look at the permissions as they appear above.

> 3) The default umask is system dependent. You can change it for the system or for the userid. Whether that is safe depends on many things.

A Linux webserver is vastly flexible and you are right when you say permissions for one use case is not the same for another. In terms of the needs of myproject, it&#8217;s just basic HTML and CSS with piwik (now matomo). It&#8217;s low traffic. In the html head I include the meta tag with name="robots" content="noindex,nofollow" attributes, it prevents access on Google. Only the people I provide with a link can access the site. I&#8217;ve maybe had two dozen web visitors over the past 4 years who have seen the content of my two other vhosts. It&#8217;s more of a testing ground and for my personal reference than anything else. I am the only member of my web team and there is no sensitive information really. With the tiny amount of traffic, security is not a significant necessity.  I have no enemies. haha. Given this usecase, is 0002 better or 0022? Or would you suggest something else, **@TheFu**?

> But all these permissions things should be tested in temporary directories with some play files before touching any production directories while you aren't 100% positive of what they do.   Play around with different chmod and umask and directories and different users who are and are not in the group.  Once you do this, something should "click" and assuming you keep using permissions, you'll never need to learn this stuff again.

Regarding that last point, user and group permissions kinda click in my head but I haven&#8217;t really had enough practice day-to-day to retain my knowledge so only when something breaks and I have to reconfigure my lamp stack do I have to return to my forum posts and re-learn **some** of what I had learned previously. Like I said, this is a hobby project and I am not a professional sysadmin or student in a CS program. So I don't have full time practice. ugh. 

I gather that configuring Unix permissions becomes &#8216;elegant&#8217; with time. I wish I was more disciplined in my spare time to maintain my knowledge at a pro-sysadmin level.  I&#8217;ll just continue to chug along. As a hobby, I learn at a snail's pace of the years. I am currently learning Python and I&#8217;ve deployed more than one Django project last year and hope to continue with these projects this year.

---

### Post by SeijiSensei on 2019-03-07
One general rule to consider is making sure the permissions structure forbids the www-data user from writing anywhere in the DocumentRoot. Many defacings and other exploits of websites happen when an attacker can trick the web server into writing into areas it should not have access to.  Web applications do sometimes need to write files to the server, particularly those that use the HTTP uploading method.  I make sure that the www-data user can only write into those directories where the uploads are stored and nowhere else in the web tree.  In applications I write myself I usually direct uploads to a directory entirely outside the web tree itself.

---

### Post by TheFu on 2019-03-07
0002 and 002 are the same. It is common to leave off the first octal in umasks and permissions. It is optional.  Only new files and new directories care about a umask. Any chmod completely overrides any umask.

Using funky characters is a bad idea for files in an rsync (or anywhere).  Special processing is required. Anything that isn't alphanumeric, if "funky" - spaces, ' " and brackets, parenthesis, shift-numbers .... any other punctuation, or high ascii.

If you are running servers, then using the manpage system is mandatory.  According to the rsync manpage:
```
        -p, --perms                 preserve permissions
...
       -p, --perms
              This option causes the receiving rsync to set  the  destination
              permissions  to  be  the  same as the source permissions.  (See
              also the --chmod option for a way to modify what rsync  considâ
              ers to be the source permissions.) 

```
There are a few pages more about -p in the manpage.  Mandatory reading.

There are also permission defaults when using other file transfer methods, so if the umask is ignored, then check the manpage for those other commands - look for 'perm" inside.

I can't remember specifically if setgid will be transferred using any file transfer method or not. rsync has options to handle that, if needed. You could always use a** tar | tar **over ssh, if you prefer that.  That's how we did transfers before rsync (well, with rsh, not ssh).

I'm active in some specialized parts of stack overflow, but tend to ignore Linux/Unix areas. I post to my blog when I have something to say, which happens seldom these days, but there are 1200+ articles there already. Don't think I said anything about permissions except to learn them.  Permissions are well covered in hundreds of Unix books already.  DRY.

IMHO, programmers need to know the OS their programs run on better than the admins. As in all areas of life, there are new, average, intermediate and experts in administration.  I'd guess I'm about intermediate since many admins are much better than I, but many are much worse too.  My time and experience with Unix systems makes up for lack of skill. 

BTW, I've never had a full-time job as an admin. It was always a side-task, part of my duties as a developer. I never studied CS either.

My webapps don't allow uploads of files. That isn't the sort of work I do. Most of the file systems where webapps run are using read-only NFS mounts. This forces an attacker to hack 2 systems, not 1.  Data is stored in a DBMS running on a different VM.  I don't use shared hosting for a number of reasons, which appear to unimportant to you.

---

