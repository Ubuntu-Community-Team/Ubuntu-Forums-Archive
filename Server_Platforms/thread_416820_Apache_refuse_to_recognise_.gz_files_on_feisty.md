---
title: "Apache refuse to recognise .gz files on feisty"
date: 2007-04-21
forum: Server Platforms
---

### Post by vooor on 2007-04-21
Hi,

It now make more than a month that I installed a new server under festy (then alpha, now stable) and after hours of various forum searching and numerous test, it still don't work. Whatever I do, whatever is the version of apache (1 or 2) apache keep refuse to recognise my .gz files and so the browsers refuse to uncompress it on the fly and ask me top save it.

I use that kind of solution since more than 7 years and never had such problem. The lamp solution is correctly deployed and as the solution I need work with many compressed files I realy need this to work.

Speaking more technically, apache correctly send the .html.gz files instead of .html as it have to do, but when I read the headers I can see that the usual line "type : application/x-gzip" is missing. It's then logical than the browsers can't uncompress it on the fly.

So I check the apache configuration, the types config is as usual "TypesConfig /etc/mime.types", I read the mime.types file and see that there is no line for the .gz files (and a notice in the comments that claim that it wouldn't be philosophically correct). With a touch of hope I added the normal line about .gz but it change nothing about my problem.

An overide of the kind "AddType application/x-gzip .gz" still solve nothing.

The modules mime and mime_magic are of course loaded, the files are not corrupted. I tested many thing and I still can't get it working. 

I'm suprised that no one reported such problem. Can anyone confirm me if it work or not for him on a feisty and would anyone have any idea I could have miss ? 

thanks by advance.

---

