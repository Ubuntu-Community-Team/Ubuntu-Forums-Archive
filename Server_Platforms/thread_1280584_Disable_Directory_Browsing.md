---
title: "Disable Directory Browsing"
date: 2009-10-02
forum: Server Platforms
---

### Post by bacterozoid on 2009-10-02
I'm running Ubuntu 9.04 Server. My server is currently hosting three individual websites. I set those up by adding virtual host entries in apache2.conf that link to subfolders of /var/www. All that business works fine and always has.

I'm trying to disable directory listing on Apache but haven't had any luck. I removed the Indexes option from the /var/www directory in apache2/sites-available/default and restarted Apache but that didn't work. I'm not quite sure where to go from here.

Thanks!

---

### Post by Bachstelze on 2009-10-02
IIRC, Indexing is turned on by default, so to disable it, add [font=monospace]-Indexes[/font].

---

### Post by bacterozoid on 2009-10-02
I tried that as well as removing the Indexes option completely. It didn't work.

---

### Post by wojox on 2009-10-02
How about in /apache2/sites-enabled/default ?

---

### Post by sprouty on 2009-10-02
In the apache config you can change the line:

ServerTokens Full

to

ServerTokens Prod

To stop directory browsing. you might also want to add this line for security

ServerSignature Off

---

### Post by bacterozoid on 2009-10-02
I tried it in sited-enabled/default as well as apache2.conf with no luck. I did add those two lines, sprouty (they didn't exist yet) and see that I'm no longer showing the server info, but I'm still getting directory browsing. Could it be related to the virtual hosts?

---

### Post by sprouty on 2009-10-02
Sorry mate!

I got a little confusted, this is how i blocked it:
in the directory

/etc/apache2/mods-enabled/
i renamed
autoindex.conf
autoindex.load

to
autoindex.conf.1
autoindex.load.1

So the config file is never loaded, prob not the best way but it works ;-)

---

### Post by proligde on 2012-09-17
If anyone stumbles upon this thread : I think the clean way to disable auto indexing in ubuntu is just:

a2dismod autoindex

---

### Post by sandyd on 2012-09-17
**Necromancing - thread locked/closed**

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks

---

