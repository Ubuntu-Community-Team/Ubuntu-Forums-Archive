---
title: "Web Server: Most Secure File Permissions?"
date: 2009-01-06
forum: Server Platforms
---

### Post by secondstage on 2009-01-06
What are the most secure file permissions for images, static html files, php scripts, and directories that will be on a web server?

Apache2 is in place. I do not know the user that Apache2 is running from though. I would assume the default www-data user.

---

### Post by samosamo on 2009-01-06
my recommendation: setting it up with full access to both user and www-data, so you do not have to sudo all the time when making changes.

find /var/www -type d -exec chmod 2775 {} \; # note the sticky gid
find /var/www -type f -exec chmod 0664 {} \;
chown -R secondstage.www-data /var/www

now the only two users that have full write access is you and apache process and you don't have to sudo to modify.

---

### Post by secondstage on 2009-01-07
So the same permissions for all of the files?

So even the PHP scripts don't have execution?

---

### Post by windependence on 2009-01-07
You may also want to consider chrooting your server if you require that kind of safety.

-Tim

---

### Post by secondstage on 2009-01-07
I'll look into that. I have some unknown user agent accessing my site.

Seriously someone has the user agent of "Toata dragostea mea pentru diavola". and somehow they accessed a "/roundcube//bin/msgimport"(which to my knowledge doesn't exist on my server) Should I be alarmed? I checked the SSH logs, and nothing there.

---

### Post by q.dinar on 2009-01-07
if he successfully accessed on that line of log should be number "200"(ok) or "304"(not modified) .

---

### Post by secondstage on 2009-01-07
Said person accessed my server twice. On the first it came up as 400, and the second time a 404 (file not found?). What is the 400 mean?

---

### Post by cariboo on 2009-01-07
Error 400 means a bad request has been sent.

Jim

---

### Post by windependence on 2009-01-07
> **secondstage said:**
> Said person accessed my server twice. On the first it came up as 400, and the second time a 404 (file not found?). What is the 400 mean?

This is certainly nothing to get excited about. You will probably see hundreds of these if you have any kind of traffic at all. I actually see thousands of them on my production servers, but I would only worry if they get in. Trying to block these is futile because most times they use someone else's IP address or spoof it so you are just blocking legitimate traffic. Use good security practices and don't worry about it.

You could also use an intrusion detection system like snort if you are really anal about this kind of stuff.

-Tim

---

### Post by Vegan on 2009-01-07
I have my web folder in a different location: /web, and its chmod 777 so that I can muck with the files easy enough. The folder is chowned to nobody:nogroup making its secure enough. Then I have samba making the folder visible to a Windows XP box.

Clumsy, but I have a Linksys box that allows me to get away with all kinds of shortcuts.

phpBB remarks that its config file is world modifyable, but works fine otherwise.

:guitar:

---

### Post by windependence on 2009-01-07
Ummm if your permissions are 777 on that directory, literally the whole world can see it no matter WHO  owns it. Apache uses certain permissions by default for a reason. Changing them is usually not a good idea. This is why I use SCP to put my files on the web server. I can become any user I want hence no permissions issues. 

Instead of just "making things easy" you should really learn about Linux permissions and ownership, otherwise you'll be sure to be hacked.

-Tim

---

### Post by scorp123 on 2009-01-09
> **windependence said:**
> Ummm if your permissions are 777 on that directory, literally the whole world can see it no matter WHO  owns it. Not only *see* but also **write** to it!  :-k

---

