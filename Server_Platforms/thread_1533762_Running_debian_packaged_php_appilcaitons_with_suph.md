---
title: "Running debian packaged php appilcaitons with suphp"
date: 2010-07-18
forum: Server Platforms
---

### Post by wobblycogs on 2010-07-18
Hi,

I'm trying to get a Mantis but tracker working on my freshly installed  10.04 server. After the initial install I got the good old probably of  Apache not processing PHP files and instead just asking me if I wanted  to download them. I thought this was strange as I have Joomla installed  on this box and it works file.

Anyway, after much head scratching I've figured out what's wrong. The  suPHP apache extension which now seems to be the default PHP module  contains the following setting:

# By default, disable suPHP for debian packaged web applications as  files
# are owned by root and cannot be executed by suPHP because of min_uid.
<Directory /usr/share>
    suPHP_Engine off
</Directory>

Since Mantis is a Debian package it's under /usr/share so the PHP  doesn't get processed. I briefly commented this directive out and set  min_uid=0 and lo and behold Mantis worked fine.

My question then is this: how can I get any Debian packaged PHP  application to work? 

I considered changing the ownership of the Mantis directory but I don't  think that will work because it's still under /usr/share. The best I can  come up with is to manually install Mantis but I'd rather not do that  when there is a perfectly good package available.

Thanks for any help.

---

