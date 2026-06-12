---
title: "Understanding users and groups"
date: 2006-07-25
forum: Server Platforms
---

### Post by harisund on 2006-07-25
Hello everyone! 

This post was primarily intended to understand the meaning behind apache's user/group directive. What does it mean when I say "apache is running as user www-data and group www-data" ?? I don't even have those users on my machine ????

Basically a couple of websites I am trying out complain that it is not able to create data since it is not running as apache's user or group. What is that supposed to mean now? 

Anyway, I was just wondering, maybe it would help to know about the following --- 

List all groups on a machine
List all groups of a particular user
List all users of a particular group
Add/Remove a user from a group
Add/Remove a group from a user

Very grateful for any help :)

---

### Post by Thirsteh on 2006-07-25
Try Google.

[http://www.debianhelp.co.uk/userandgroup.htm](http://www.debianhelp.co.uk/userandgroup.htm)

---

### Post by LordHunter317 on 2006-07-25
> **harisund said:**
> What does it mean when I say "apache is running as user www-data and group www-data" ??Exactly what it says.  Apache uses www-data.www-data as it's accounts for all operations, after starting up as root. 

> I don't even have those users on my machine ????You obviously do, otherwise it wouldn't work.

> Basically a couple of websites I am trying out complain that it is not able to create data since it is not running as apache's user or group. What is that supposed to mean now? It means you either didn't follow directions for installing the web application or their directions are poor and you have permissions issue.

> List all groups on a machinecat /etc/group

> List all groups of a particular usergroups <user>

> List all users of a particular groupcat /etc/group | grep <group>[/quote]This will however, miss users that have the group as their primary group, you have to verify those in /etc/passwd.

> Add/Remove a user from a groupadduser <user> <group>

deluser <user> <group>

These are Debian/Ubuntu specific.  The "portable" way is usermod.

> Add/Remove a group from a userSee above.

---

### Post by harisund on 2006-07-25
> **LordHunter317 said:**
> 
You obviously do, otherwise it wouldn't work.

So does that mean I have to login as www-data in order to run web applications that write to the directory? I don't know the password for that user (I don't particularly recollect setting one for the www-data user). 

> 
It means you either didn't follow directions for installing the web application or their directions are poor and you have permissions issue.

Well, the Drupal instructions don't have any particular user directory permissions related documentation. 

Do I need to add myself to the www-data group in order to make my public_html directory (in ~) writeable?

---

### Post by harisund on 2006-07-25
> **LordHunter317 said:**
> 
You obviously do, otherwise it wouldn't work.

So does that mean I have to login as www-data in order to run web applications that write to the directory? I don't know the password for that user (I don't particularly recollect setting one for the www-data user). 

> 
It means you either didn't follow directions for installing the web application or their directions are poor and you have permissions issue.

Well, the Drupal instructions don't have any particular user directory permissions related documentation. 

Do I need to add myself to the www-data group in order to make my public_html directory (in ~) writeable?

---

### Post by LordHunter317 on 2006-07-26
> **harisund said:**
> So does that mean I have to login as www-data in order to run web applications that write to the directory?No.  It does mean that www-data needs to be able to write to that directory, or it won't work.

In fact, logging-in as www-data would be a terrible idea.  With a few exception, daemon accounts are never supposed to be interactive. 


> I don't know the password for that user (I don't particularly recollect setting one for the www-data user). You didn't and you shouldn't.

> Do I need to add myself to the www-data group in order to make my public_html directory (in ~) writeable?No, but you need to give www-data write access there.  That's a bad idea.


Why isn't drupal installed in /var/www, where it belongs?

---

### Post by harisund on 2006-07-26
Actually this was that I was looking for
List all groups on a machine -- /etc/group or /etc/gshadow
List all groups of a particular user -- groups username
List all users of a particular group --- check /etc/group or /etc/gshadow
Add/Remove a user from a group --- gpasswd -a user group or gpasswd -d user group
Create/Delete a group -- addgroup or delgroup
All groups that the current shell processes belong to -- groups

Thanks Thirsteh, I should have googled as you suggested.

---

