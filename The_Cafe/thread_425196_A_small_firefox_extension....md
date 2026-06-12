---
title: "A small firefox extension..."
date: 2007-04-27
forum: The Cafe
---

### Post by freakavoid on 2007-04-27
Hi all,

Since i couldn't find another way to do the job I wrote a small extension for firefox to suit my need to quickly open a terminal in a downloaded file's location. I thought there has to be something like Open Containing Folder menu item for CLI people. I'm not sure if anybody else needs such a thing but sharing it with the community seemed not a bad idea anyway. The attached tarball contains the xpi file. Currently it's gnome only but it can easily be extended if there is any demand for it.

update: copies file's path to the clipboard now.

---

### Post by chakkaradeep on 2007-04-27
> **freakavoid said:**
> Hi all,

Since i couldn't find another way to do the job I wrote a small extension for firefox to suit my need to quickly open a terminal in a downloaded file's location. I thought there has to be something like Open Containing Folder menu item for CLI people. I'm not sure if anybody else needs such a thing but sharing it with the community seemed not a bad idea anyway. The attached tarball contains the xpi file. Currently it's gnome only but it can easily be extended if there is any demand for it.

Any screenshots and tips on how to install :) 

Thanks

---

### Post by freakavoid on 2007-04-27
> **chakkaradeep said:**
> Any screenshots and tips on how to install :) 

Thanks

Here you go.
To install it: extract the xpi from the tarball and drag+drop it to the firefox window.

---

### Post by chakkaradeep on 2007-04-27
> **freakavoid said:**
> Here you go.
To install it: extract the xpi from the tarball and drag+drop it to the firefox window.

Hey, this is really nice :) 

Good work !

---

### Post by earobinson on 2007-04-27
neat!

---

### Post by freakavoid on 2007-04-27
glad you liked it :)

---

### Post by Malta paul on 2007-04-27
Thank you, great.:)

---

### Post by Iarwain ben-adar on 2007-04-27
Hi there,
would love to get it available for KDE (how can i edit the xpi file?)


Iarwain

---

### Post by freakavoid on 2007-04-27
> **Iarwain ben-adar said:**
> Hi there,
would love to get it available for KDE (how can i edit the xpi file?)


Iarwain

Never used KDE so if you tell me the equivalent of the command line "/usr/bin/gnome-terminal --working-directory" i can fix it for you. If you want to do it your self: extract the xpi file (it's basically a zip file) and the oth.jar archive in the content folder. There is just one code file named overlay.xul find the two strings for the command "gnome-terminal" and for the option "--working-directory" and change them to their KDE equivalents. I don't know if one can detect the current desktop-manager within firefox but I'll give it a shot tonight and try to do it automatically.

---

### Post by Iarwain ben-adar on 2007-04-27
Hi,
thanks for the info :D

Problem is i can't extract it..

The KDE eq. is konsole
>  /user/bin/konsole --workdir pwd

This should work


Iarwain

---

### Post by freakavoid on 2007-04-27
> **Iarwain ben-adar said:**
> Hi,
thanks for the info :D

Problem is i can't extract it..

The KDE eq. is konsole


This should work


Iarwain

Here is the KDE version. I couldn't test it so some feedback would be nice.

---

### Post by Iarwain ben-adar on 2007-04-27
It works :D


Thanks ;)


Iarwain

---

### Post by freakavoid on 2007-05-08
update: copies path to the clipboard now. files attached to the original post.

---

