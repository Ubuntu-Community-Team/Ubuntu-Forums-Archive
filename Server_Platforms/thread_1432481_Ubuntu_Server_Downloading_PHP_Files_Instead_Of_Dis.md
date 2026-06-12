---
title: "Ubuntu Server Downloading PHP Files Instead Of Displaying Them"
date: 2010-03-17
forum: Server Platforms
---

### Post by cusinndzl on 2010-03-17
I have an Ubuntu 9.10 server set up at my house. I have Apache2 and PHP5 installed on it. Every time I go to the server on a web page and try to load the PHP index page it downloads instead of displaying. I have virtual servers set up and have the files stored at /home/cusinndzl. If anyone needs to take a look I can let them into the webmin panel. 

Can anyone help me? I can answer more questions if you need anything answered about it.

---

### Post by k23 on 2010-03-17
> Please verify if the files /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-enabled/php5.load exist. If they do not exists, you can enable the module using a2enmod command.

[https://help.ubuntu.com/9.10/serverguide/C/web-servers.html](https://help.ubuntu.com/9.10/serverguide/C/web-servers.html)

Hope this helps!

---

### Post by Jeff Anthony on 2010-03-17
[http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_threshold=0&comments_parentId=1452&comments_offset=40&comments_per_page=20&thread_style=commentStyle_plain](http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_threshold=0&comments_parentId=1452&comments_offset=40&comments_per_page=20&thread_style=commentStyle_plain)

> f you're having this issue, please try these things:  
[LIST]
[*] Clearing your Firefox cookies and cache (press Ctrl+Shift+Del  and select them to be cleared)
[*] Resetting your Download Actions:
[LIST=1]
[*] Close Firefox
[*] Open the Firefox profile folder - see [How  to find your profile]("http://support.mozilla.com/kb/Profiles#How_to_find_your_profile")
[*] Delete the *mimetypes.rdf* file
[/LIST]
[*] Checking your Internet security software (this  includes antivirus and antispyware programs, firewalls, and more):
[LIST]
[*] In general, open the program's settings, remove Firefox from  its "Allow" list, and then let it redetect Firefox.
[*] If your program is listed at the [Firewalls]("http://support.mozilla.com/kb/Firewalls")  article here, or at the [Firewalls article at  MozillaZine]("http://kb.mozillazine.org/Firewalls"), you can get specific instructions for how to properly  reconfigure. Follow them carefully.
[/LIST]
[*] Making a new Firefox profile (see [Managing profiles]("http://support.mozilla.com/kb/Managing+profiles")). If that works, you can get your  bookmarks and passwords into the new profile by following the  instructions in the [Recovering important data from an old profile]("http://support.mozilla.com/kb/Recovering+important+data+from+an+old+profile") article.
[/LIST]
  Good luck! 


---

### Post by KB1JWQ on 2010-03-18
Has index.php been added to the DocumentIndex line in httpd.conf?

---

### Post by yesrno on 2010-03-18
I had the same problem a while ago. Try reinstalling php and restart the apache service after. Worked for me.

---

