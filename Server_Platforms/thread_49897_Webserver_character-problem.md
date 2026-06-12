---
title: "Webserver character-problem"
date: 2005-07-18
forum: Server Platforms
---

### Post by Gizmo on 2005-07-18
Hello!
I have installed Ubuntu 5.04 server-installation at my computer.
I run Apache webserver at the computer with mysql & php.
When people visit my site they se the character å ä ö  Å Ä Ö as strange signs like ? # etc. 
When people visits the site, their webbrowser automatic sets unicode-mode.
And when their sets the code-mode manuall to ISO-8859-1 do they se the Å Ä Ö characters perfect.
BUT! When they do a site-update, like pressing "Refresh" or just clicking a link, the webbrowser returns to unicode again.
I think this strange stuff depends on the server,  do someone have a idéa of what the problem could be? Is the server sending out a message to the browsers to set unicode-mode when it visits my server?

BTW, When i installed Ubuntu server-installation did i choose Swedish as language and Swedish keyboard if that makes any difference.

An exampel is [http://jockepocke.mine.nu/calle/index2.html](http://jockepocke.mine.nu/calle/index2.html)

// Gizmo

---

### Post by LordHunter317 on 2005-07-18
Apache2 is probably set to make the default charset UTF-8.  Any files that don't have a charset encoded or use multiviews will be sent UTF-8.  You can change this by editing /etc/apache2/apache.conf

---

### Post by Gizmo on 2005-07-18
Thanks allot LordHunter317!

This little tiny sentence was wrong  :-P 

 # AddDefaultCharset ISO-8859-1   ](*,) 

Thanks again  :-P

---

