---
title: "apache related question"
date: 2008-12-19
forum: Server Platforms
---

### Post by fouadk on 2008-12-19
hi everyone...

i am migrating a website from a red hat server to the new 8.10 ubuntu server,,,,

i have a 1.5GB website that i need to migrate...my problem is that when i migrated the website, pictures dont appear anymore....
after doing some investigating, the pictures name in the HTML are all capital letters like for example "PIC.JPG", but in /var/www/pics/ all files are lower letters....

this worked fine on RED HAT but not in ubuntu,,,is there is anything special that i need to add to the apache conf file in order to make it ignore case sensitivity ???

please help

thanks in advance

---

### Post by hyper_ch on 2008-12-19
I guess you did transfer them from the redhat box, to windows, to linux?

Simplest way to fix would be to make all image files upper case.

---

### Post by fouadk on 2008-12-19
yeah that right,i transfered from red hat to windows to ubuntu...you think if i transfer the website directly from red hat to ubuntu,i wouldnt face this problem ? coz renaming all the pics is out of the question

---

### Post by MJN on 2008-12-19
[Edit: I missed your response. Transferring directly should avoid the issue entirely, but renaming files is also easy if necessary]
 
There is an Apache module available (the hilariously titled [mod_speling]("http://httpd.apache.org/docs/2.0/mod/mod_speling.html")) which effectively makes Apache case-insensitive however I would not recommend its use because it adds a processor overhead and is little more than a sticking plaster over what it technically a problem. The URI spec is case sensitive and hence your links ought to match those of the file system.
 
So, you've got two ideal choices - change your HTML, or your filenames as hyper_ch suggested. I too would go with the latter. There are many script examples floating around the web to rename files from upper to lower case.
 
Mathew

---

### Post by hyper_ch on 2008-12-19
some simple ways to move the files over:

- make on the RH server a tar, that will keep the according file names, copy it to the windows machine (or directly to the new one) and extract it there.

- use rsync to get directly a copy.

- use httrack to "copy the website"

---

### Post by fouadk on 2008-12-19
thanks a lot everyone...i transfered the files directly from RH to ubuntu using scp...

Now i am facing some problems with php since RH had php4 and ubuntu have php5...

Is ubuntu server LAMP setup secure by default ?

Thanks in advance

---

### Post by martien on 2008-12-19
Well if you get your php from apt-get it comes with Suhosin Patch, so yes, it comes with security added. If no, then you have to check manually (its easy to crate phpinfo page) and there is the all apache and php configuration.
And last but not unimportant, remember - the most security is provided by your own mind and skill.

---

