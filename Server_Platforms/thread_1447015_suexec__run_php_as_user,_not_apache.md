---
title: "suexec / run php as user, not apache"
date: 2010-04-04
forum: Server Platforms
---

### Post by wellsr on 2010-04-04
Hey folks,

I've been at this for hours... I'm about ready to give up. When we run php scripts that move/rename/etc files, the script does not have access to write to files in our web root. Changing permissions to 777 fixes the problem, but obviously this is not an option..

I've been reading up about suexec, phpsuexec, and suphp, but we can't seem to figure any of this out.

In phpinfo(), the Server API reads : Server API Apache 2.0 Handler

but on another server (where everything works, it reads : Server API CGI/FastCGI

Is there ANY way to achieve this? I'm about to go mad. Thanks.

---

### Post by djoxyk on 2010-04-05
I'm not sure about suexec, but if i need to make some file to be temporary accessed from php i use
[@chmod]("http://php.net/manual/en/function.chmod.php")
with suexec your maximum required rights is 775

---

### Post by andyba on 2010-04-20
I have the same problem. I want to install the phpbb forum locally to create some mods, and I have problems installing them because of permissions.

Is there any way to make suexec work on my local host in ubuntu 9.10

---

