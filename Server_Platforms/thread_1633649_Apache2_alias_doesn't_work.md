---
title: "Apache2 alias doesn't work"
date: 2010-11-29
forum: Server Platforms
---

### Post by Strega on 2010-11-29
Hello,

I'm trying to set up 2 aliases with PHP files in it. But in both cases I get a 403 Forbidden error. This is what the /etc/apache2/conf.d/alias file looks like:```
Alias /~strega /home/strega/www/

<Directory /home/strega/www/>
DirectoryIndex index.html index.php
Options FollowSymLinks
AllowOverride None
order allow,deny
allow from all
</Directory>

Alias /~demos "/home/strega/private/orangebox/cstrike/cfg/match_demos/"

<Directory "/home/strega/private/orangebox/cstrike/cfg/match_demos/">
DirectoryIndex index.html index.php
Options FollowSymLinks
AllowOverride None
order allow,deny
allow from all
</Directory>

```
What am I doing wrong?

Regards,
Strega

---

### Post by SeijiSensei on 2010-11-29
Remove the tilde's from the aliases.  Just use "strega" and then connect to [http://server/strega](http://server/strega).

---

### Post by Strega on 2010-11-29
I still get the same error :s

---

### Post by James78 on 2010-11-29
What happens if you remove

AllowOverride None
order allow,deny
allow from all

And replace that with

allow from all
AllowOverride All

??

This problem could also be file permissions related. You could check your Apache error logs to see if they state anything useful.

---

### Post by SeijiSensei on 2010-11-29
> **James78 said:**
> This problem could also be file permissions related. You could check your Apache error logs to see if they state anything useful.

What are the permissions on /home/strega?  700?  Try "chmod 711 /home/strega" for a start.  Remember that any file that you plan to display on the web must be readable by the "www-data" user that apache runs under.  Try this:

```

cd /home
chmod 0711 strega
cd strega
chgrp www-data www -R
chmod g+r www -R

```

That grants permission to members of the www-data group (essentially just the www-data user itself) to read files in /home/strega/www and below.  

If that works, follow the same approach to your other aliased directories. As James78 notes, /var/log/apache2/access_log and /var/log/apache2/error_log are your friends.

---

### Post by Strega on 2010-11-30
It's weird, it worked for the first alias, but not the second :s
This is what the error.log says:```
[Tue Nov 30 18:14:45 2010] [error] [client *.*.*.*] (13)Permission denied: access to /demos denied

```

---

### Post by SeijiSensei on 2010-11-30
The permissions have to be correct along the entire path of /home/strega/private/orangebox/cstrike/cfg/match_demos/.  I suspect the commands I gave you didn't turn on the read privilege in /match_demos/.  Navigate to there with "cd /home/strega/private/orangebox/cstrike/cfg/" then use "ls -l match_demos" to check the permissions and "chmod 0711 match_demos" if the execute bits aren't set.  Make sure the files in match_demos are readable by the www-data group as well.

---

### Post by Strega on 2010-11-30
This is what I get if I do ls -l```
drwx--x--x 2 strega www-data 4096 Nov 30 17:56 match_demos

```Do the folders like cstrike and cfg all the way to the root also have to be set with chmod 0711 ?

Regards,
Strega

---

### Post by SeijiSensei on 2010-11-30
That's what I thought was wrong.  Try this:

```

cd /home/strega/private/orangebox/cstrike/cfg/
chgrp www-data match_demos
chmod u+rwx,g+rx,o-rwx match_demos
chmod u+rw,g+r,o-rwx match_demos/* 

```

The first chmod gives all privileges to user strega, list and read privileges to group www-data, and no privileges to anyone else.  The second one gives the same permissions for files in match_demos.  If there are other directories below match_demos, you need to treat them the same way as you do match_demos.

I switched to symbolic codes in chmod for better clarity.  The octal codes like 750 are not so obvious!  The permissions above translate to 750 and 640 respectively.  You can drop the leading zero and get the correct results, but the non-zero values of that digit are meaningful.  See "man chmod" for details about the set uid, set gid and "sticky-bit" values.

---

### Post by Strega on 2010-11-30
I copied your code line by line and it still gives the same error :s
[http://109.230.234.21/demos](http://109.230.234.21/demos)
It's really weird, because the /strega dir does work.

---

### Post by SeijiSensei on 2010-11-30
> **Strega said:**
> I copied your code line by line and it still gives the same error :s
[http://109.230.234.21/demos](http://109.230.234.21/demos)
It's really weird, because the /strega dir does work.

I think there's a missing permission somewhere in the chain.  Try this:  Use "ls -l /home/strega" then "ls -l /home/strega/private" etc., all the way down, and post the results here.  Put them inside [noparse]```

```[/noparse] tags if you can.

Here's another possibility -- the permissions are right, but the access rules in Apache are wrong.

> ```
Alias /~demos "/home/strega/private/orangebox/cstrike/cfg/match_demos/"

<Directory "/home/strega/private/orangebox/cstrike/cfg/match_demos/">
DirectoryIndex index.html index.php
Options FollowSymLinks
AllowOverride None
order allow,deny
allow from all
</Directory>

```

Do you actually have an index.html or index.php in the /match_demos/ directory?  Try removing that directive and adding "Indexes" after "FollowSymLinks" in the Options directive.  Without enabling Indexes, you can't list a directory over the web.  If match_demos just contains a set of files, and no index.php/index.html, then Apache will refuse to list the directory and report a denial of access.

---

### Post by Strega on 2010-12-01
> Do you actually have an index.html or index.php in the /match_demos/ directory?  Try removing that directive and adding "Indexes" after "FollowSymLinks" in the Options directive.  Without enabling Indexes, you can't list a directory over the web.  If match_demos just contains a set of files, and no index.php/index.html, then Apache will refuse to list the directory and report a denial of access.
Yes, I do have an index.php file int the directory. I changed the alias file a little like I think you wrote.```
Alias /demos /home/strega/private/orangebox/cstrike/cfg/match_demos/

<Directory /home/strega/private/orangebox/cstrike/cfg/match_demos/>
Options FollowSymLinks Indexes
AllowOverride None
order allow,deny
allow from all
</Directory>

```As for the permissions of the folders/files, all the folders in the /home/strega/ look like this```
drwxr-xr-x 4 strega strega   4096 Dec  1 03:59 private

```except for the /home/strega/www/ directory ( works )```
drwxr-x--x 2 strega www-data 4096 Nov 30 17:55 www
```and the /home/strega/private/orangebox/cstrike/cfg/match_demos/```
drwxr-x--- 2 strega www-data 4096 Nov 30 17:56 match_demos
```I see there is one "x" missing in the last code, could that be the problem?

---

### Post by SeijiSensei on 2010-12-01
> **Strega said:**
> I see there is one "x" missing in the last code, could that be the problem?

No, that just controls whether users other than strega and members of the www-data group can list the contents of match_demos.  What are the permissions on the files in that directory itself?  What happens if you disable index.php by renaming it to something like index.php.disabled?  Does Apache display a list of the files in match_demos?

---

