---
title: "Apache2 randomly stopped working today"
date: 2018-03-09
forum: Server Platforms
---

### Post by stevens.r on 2018-03-09
All of my media server web apps i have hosted through reverse proxy in apache just suddenly stopped working today.
I can only access them through local ip or localhost. 
I also have a website that acts as a container for those app it call Muximux [https://github.com/mescon/Muximux](https://github.com/mescon/Muximux)
that also just stopped working reinstalling Muximux didn't work any suggestions would be greatly appreciated.

Here is whats in apache error log for this morning if others are needed i can post them.

[Fri Mar 09 07:35:01.991805 2018] [mpm_prefork:notice] [pid 2460] AH00163: Apache/2.4.18 (Ubuntu) OpenSSL/1.0.2g configured -- resuming normal operations
[Fri Mar 09 07:35:01.991830 2018] [core:notice] [pid 2460] AH00094: Command line: '/usr/sbin/apache2'
[Fri Mar 09 10:17:49.527795 2018] [:error] [pid 14607] [client 216.218.206.66:35732] PHP Warning:  file_get_contents(): Filename cannot be empty in /var/www/Muximux/muximux.php on line 1122

---

### Post by wildmanne39 on 2018-03-09
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by SeijiSensei on 2018-03-09
> ```
[Fri Mar 09 10:17:49.527795 2018] [:error] [pid 14607] [client 216.218.206.66:35732] PHP Warning: file_get_contents(): Filename cannot be empty in /var/www/Muximux/muximux.php on line 1122
```

Have you looked at line 1122 in muximux.php?  file_get_contents() is a PHP function that reads the contents of a file into a string.  Apparently there's some bug either in the code or your configuration that fails to pass a filename to the function on that line of the script.  Beyond that I don't think I can help very much.

---

### Post by stevens.r on 2018-03-10
i found what seems to be someone trying to get into my server wouldn't let me post if i copied and pasted so i attached the file access.log.1 file

does this matter
did they get in
is this what caused apache to randomly stop working 

any help would be greatly appreciated

wrong file

here is the right one

line 1122 of muximux has not changed no updates in over 6 months and i reinstalled a new version just to check and it still doesn't work

tried to find out if apache was updated in /var/log/apt but the files are either empty or end with .gz and are in some sort of code or something

any ideas?

the dpkg.log.1 has something in it but only from February

from what ive seen so far it looks like the server hasn't updated anything since feb 24 so i have even less of an idea as to whats wrong here now

---

### Post by stevens.r on 2018-03-10
could someone point me towards a removal and reinstall guide for apache

one that actually works for Ubuntu 16.04 

i know enough to follow a guide but idk if what im following is right or not


is it as simple as this 

sudo apt-get remove apache2
sudo apt-get purge apache2
sudo apt-get install apche2

---

### Post by SeijiSensei on 2018-03-10
Yes, but run "sudo apt update" first to download and compile the package lists so everything will be up-to-date.  (You can just use "apt" these days in places where you formerly used "apt-get".)

Purge will delete the contents of /etc/apache2/, I believe, so make sure you back that up before you reinstall.

You might want to make a copy of /var/www/, too.

I didn't see much in that log to suggest anyone managed to compromise your server.  There's a suspicious request for "admin.php," but you don't have one of those, and the server returned a 404 "not found" error. There's little you can do to protect against random villains sending random HTTP GETs to your server. Even a basic installation of Apache is secure against that sort of crap.

Here's a hacking attempt I culled from a server I manage just now:

```
[Tue Mar 06 10:13:52.887708 2018] [access_compat:error] [pid 4132] [client xxx.xxx.xxx.xxx] AH01797: client denied by server configuration: /var/www/.ssh
```

If there is a user for whom /var/www is the home directory, a .ssh subdirectory would contain that user's public and private SSH keys.  Anyone who would configure a server like this hasn't the first clue about security.  But apparently stupidity like this is common enough that there are automated scanning bots looking for this particular security flaw.

---

