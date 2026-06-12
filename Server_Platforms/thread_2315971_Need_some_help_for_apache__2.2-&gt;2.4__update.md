---
title: "Need some help for apache  2.2-&gt;2.4  update"
date: 2016-03-04
forum: Server Platforms
---

### Post by sykerjoe on 2016-03-04
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid


Hey guys,

I just come into Trouble to Update our Ubuntu LTS to the new verisions and to migrate to the new apache version 2.4.

For me, it's not so hard to migrate the new Version or atm it's not the main  problem.

It's rather more the  update with the user prompts to decide if i want to keep the Files for apache or not.


Has anyboy some advices for me ? 

regards john

---

### Post by howefield on 2016-03-04
Thread moved to the "*Server Platforms*" forum.

10.04 Server is now [End of Life]("http://ubuntuforums.org/showthread.php?t=2276236") as you seem to already know. You might want to rephrase your last sentence to make clear what you are asking ?

---

### Post by sykerjoe on 2016-03-04
Hello @howefield

Sure

If you Update the whole System there comes some user prompts if you want to keep files, overwrite  and so on ...

But i'm not so  familar with the new apache that i can't decide which file improves the new apache and has to override an old one  and which one  should i still keep on the system.


I hope now it's a liitle bit clearer 

regards sykerjoe

---

### Post by SeijiSensei on 2016-03-04
Do you have custom virtual host configurations in /etc/apache2/sites-available/?  Custom module configurations in /etc/apache2/mods-available/?  If so, make copies of those files before updating, then copy them back.

I'll just mention the biggest change from the admin's point of view is that the default website directory is /var/www/html rather than /var/www which is the default on 2.2.

---

### Post by sykerjoe on 2016-03-07
@Seijj

Hello 

I still made an copy of the apache2 directory 

But what is with the asking prompts if i upgrade  my Ubuntu Version 

Should i replace all apache Files When the System ask me what should it do with the existing files ?   


I mean some Prompts like this: 

[COLOR=#0000ff]apache.conf (Y/I/N/O/D/Z) [default=N] ? Y [/COLOR]


Edit: Better example 

I don't know 




regards sykerjoe

---

### Post by SeijiSensei on 2016-03-07
Yes, let it rewrite the files.  Then copy back any custom files in /etc/apache2/sites-available/ and any symbolic links to those files in /etc/apache2/sites-enabled/.  Or just use a2ensite as described here: [https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration](https://help.ubuntu.com/lts/serverguide/httpd.html#http-configuration)

---

### Post by sykerjoe on 2016-03-08
@SeijiSensei 

Hello Seiji

Many thanks for help 

i hope that i can manage this at my own from this point 

regards john

---

