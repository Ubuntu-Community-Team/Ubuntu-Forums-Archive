---
title: "Can't get menu item going for Tortoise HG?"
date: 2011-03-22
forum: Ubuntu Dev Link Forum
---

### Post by dartdog on 2011-03-22
on Ubuntu 10.10 32bit
Following these instructions meticulously.
[http://g0blin.co.uk/programming/installing-tortoisehg-2-0-under-ubuntu-10-10/](http://g0blin.co.uk/programming/installing-tortoisehg-2-0-under-ubuntu-10-10/)
 I can check that all files are present and accounted for. and Mercurial itself seems to be good and working from the command line. But no luck in getting tortoise to show up in the Nautlius context menu... 

Only possible clue I have is that when I attempt to restart Nautlius with the following I get this error

tom@tom-Satellite-A105:~$ nautlius -q
No command 'nautlius' found, did you mean:
 Command 'nautilus' from package 'nautilus' (main)
nautlius: command not found
 So I tried 
tom@tom-Satellite-A105:~$ nautilus -q

(nautilus:2525): Unique-DBus-WARNING **: Error while sending message: Message did not receive a reply (timeout by message bus)
 So it seems that there is a typo or something somewhere.. I copied and pasted the scripts form the post, and ran through things twice... still no context menu...


I also have RabbitVCS for both SVN and GIT installed working fine..

I got started on this since I had it installed and working fine a while ago, just recently noticed that the Tortoise stuff vanished.

In desperation I re-installed from the Ubuntu PPA, no luck... still no context menu..

---

### Post by Seidr on 2011-03-28
Heya - Sorry that was a typo in the blog post. To restart Nautilus type 'nautilus -q'.

With regards to the error you're getting - I'm afraid I'm not sure what that means. I certainly have not seen that error while experimenting with Nautilus and TortoiseHG to write the guide - sorry :\

Perhaps purge nautilus, tortoisehg, tortoisehg-nautilus, python-nautilus and appmenu-gtk, and then reinstall nautilus/tortoisehg/tortoisehg-nautilus from the PPA, remembering to overwrite the Nautilus plugin with the current version from the reinstalled TortoiseHG.

As mentioned in the blog post, this was tested on a completely new Ubuntu 10.10 installation and found to work perfectly fine on a few test-run installs following the guide word for word (apart from that typo!).

---

