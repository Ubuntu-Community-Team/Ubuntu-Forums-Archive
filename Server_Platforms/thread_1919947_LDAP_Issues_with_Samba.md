---
title: "LDAP Issues with Samba"
date: 2012-02-03
forum: Server Platforms
---

### Post by rayne127 on 2012-02-03
I am looking to install LDAP on my file server for user authentication. I currently use my file server to host media for everyone to access, including all of our devices (mostly xbox 360) and as a backup device for all of our computers and a few other small things. Everything on the server works great and we are all able to access our files and the shared files through samba using our own usernames and passwords. There are public shared folders available to guests and all users, as well as private shares only available to authenticated users.

I recently installed Subsonic as a way to share our media with each other as well as stream to our cell phones. I would like to set up LDAP on the server to make user management more unified. My users occasionally change their passwords and it’d be nice to have sort of a single-sign on (not having to change a bunch of passwords). I currently use webmin/usermin to manage the server, and it’s been fine since webmin sync’s user accounts with samba, but there is no subsonic module for webmin. I have used this tutorial in the past to set up PDC ([http://ubuntuforums.org/showthread.php?t=1683595](http://ubuntuforums.org/showthread.php?t=1683595)) with success, however I don’t want to set up PDC at this time (maybe in the future). I just want samba and subsonic to authenticate against LDAP. 

Is there a way to have samba authenticate user information again LDAP without being a PDC? And if so, will the user file permissions be passed on just as they are with the regular Unix login?

---

