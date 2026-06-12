---
title: "Apache 2.2 users and groups in virtual hosts"
date: 2011-03-03
forum: Server Platforms
---

### Post by richwils on 2011-03-03
Hi

I have Apache up and running and have a few virtual sites enabled.  All these sites belong to the same user and group and the directory root for each site is in /home/{same-user}/www/{site-name}/htdocs/

I use Samba to connect from Windows to these directories and by default, files and directories are saved as the {same-user} and {same-group}.

My question is, would it cause a problem if I changed the user and group in the virtual server directives in /etc/apache2/sites-available/site.conf files, giving apache permission to write to these files and directories.  In the past I have changed the user and group to www-data (the default) but this seems inefficient an cumbersome compared to what I intend to do.

I use the server mostly for development, although at times I have a small site or two available to the public.  Before I do this I want to be sure I'm not leaving a gaping security hole by changing these things.

If this is all wrong, what is the standard way of running virtual hosts from apache and what is the standard document root for virtual sites?

Cheers

Rich

---

### Post by SeijiSensei on 2011-03-03
If you're pretty much exclusively using Samba to access the website directories, I'd add 

```

force user = www-data
force group = www-data

```

to the share definition.  This tells Samba to write any files to the OS as the www-data user and group, regardless of the username that's logged into Samba.  See "man smb.conf" for more details.

---

### Post by richwils on 2011-03-04
Thanks, I like that idea.  But can anyone tell me the standard practice for virtual hosts in terms of the directories they should live in?  I got a feeling that storing them in my own user area is not the best practice, or is that perfectly fine?

Cheers

Rich

---

### Post by SeijiSensei on 2011-03-04
I've kept web sites in home directories for many years now and often share those directories with Samba.  It makes it much easier for Windows users to maintain the pages.  As long as the Apache user can read the files, you'll be fine.  It's often easier to manage permissions this way than trying to stuff all the sites under /var/www.

In many cases, I'm building PHP applications where I don't want users to access the site directly.  In those situations I build administrative pages where my clients can manage content in a structured setting.  It's very hard to maintain site coherence when multiple people can upload pages that may or may not conform to the approved design standards and styles.

---

### Post by richwils on 2011-03-07
Thanks.  This has worked very well.  Prior to this, permalinks were not working for my wordpress installations.  Now they do, thank you SeijiSensei

Cheers

Rich

---

