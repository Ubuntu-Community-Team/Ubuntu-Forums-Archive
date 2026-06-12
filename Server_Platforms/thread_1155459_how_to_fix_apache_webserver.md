---
title: "how to fix apache webserver?"
date: 2009-05-10
forum: Server Platforms
---

### Post by gfunkera on 2009-05-10
all of a sudden my apache2 web server is acting up and wont load my web site..

i have been workin on the site all day and updating, opening, closing html and php files with no problem..

i stepped away to eat dinner and when i came back i tried opening my web site, but it doesnt work! the tab in firefox says "loading..." and the status bar at the bottom says "Connecting to <MYIPADDRESS>".. i restarted the computer and same thing is happening...

how can i fix this?

---

### Post by Mr Camouflage on 2009-05-11
No Idea, but I had the exact same problem. I tried to add a htaccess file to protect a directory, rebooted the server, but when i go to the <server>/website/ it just sits there as if its loading forever.  If I go to <server> it loads ok though. Ubuntu server 8.10. Deleted the htacces files and undid any changes I made, still wont work.

Cant see any problems in the logs, Anybody have any tips where gfunkera and I need to look to find out whats gong on with apache?

---

### Post by Mr Camouflage on 2009-05-11
Since things were busted, I updated to ubuntu server 9.04, and answered yes when asked to use the packages apache2 config files, instead of the current ones. Once the install was finished and the server restarted apache was working again.

Heres the steps I followed to update the server to 9.04 from the command line:
[http://swearingscience.com/2009/04/26/upgrading-ubuntu-server-810-intrepid-to-904-jaunty/](http://swearingscience.com/2009/04/26/upgrading-ubuntu-server-810-intrepid-to-904-jaunty/)

---

