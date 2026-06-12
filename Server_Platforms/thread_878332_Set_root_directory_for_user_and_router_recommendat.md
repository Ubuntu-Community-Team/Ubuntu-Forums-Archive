---
title: "Set root directory for user and router recommendation"
date: 2008-08-02
forum: Server Platforms
---

### Post by Kapli on 2008-08-02
Hello,
I have an ubuntu-server running in my basement. It hosts a few websites and a ventrilo server.
I am looking for answers on 2 things:
1. I have added a user with adduser, and he can connect to my server via winSCP which I also use. I have created a folder in /var/www/ where I have setup a virtualhost so that anything he puts in there will show on his domain, so it acts as his root directory for his website. I have chowned him that directory. Now what I want to do is make it so that when he logs in with winSCP he automatically goes to that directory and he can't go anywhere ele. I want it to be his root directory and he can do anything there but not go anywhere else. I have looked into jail and stuff but didn't really understand it.
2. I have a home network and recently got fiber net so my speeds are currently 10/5. They didn't give us a router so we have to buy our own. Now I am looking for a solid wireless router that works good for both my home network and my server. Any suggestionsn on this? I've been looking at D-Link DIR 655 and 635, but recently read that D-Link wasn't so good for linux servers or something. 

So yeah, that's it ;D
Thanks in advance for any answers

- Kapli

---

### Post by windependence on 2008-08-02
WinSCP can be configured to use any directory as the default on his side.

What you'll need to do is set up a group for "users" or something like that and then disallow that group read access to everythiing but their directory.

Someone out there may have a more elegant solution however.

-Tim

---

### Post by cariboo on 2008-08-03
I still like creating a symlink in /var/www to the users home directory, that way he can't muck about with any permission or ownership, except in is home directory.

Jim

---

### Post by Kapli on 2008-08-03
windependence:
Could you elaborate on how exactly to do that?

cariboo907: I created a symlink by 
```
ln -s /var/www/NAME /home/NAME
```
So this creates a link in the /home/NAME to the /var/www/NAME 
But he can still go anywhere so how do I restrict him to only his home directory?

Any suggestions for a router?

Edit: Hm.. I think what I need to do is remove all permissions on NAME user on everything that he doesn't own. He only owns /home/NAME and /var/www/NAME. Any easy way to do this?

Edit2: After a friend of mine who is experienced with linux helped me he found this for me [http://www.minstrel.org.uk/papers/sftp/](http://www.minstrel.org.uk/papers/sftp/)
Trying to get it working right now, I also just changed the virtualhost to the home directory of NAME. 
Also, I think I found a good router [Linksys WRT54GL]("http://prisguide.hardware.no/product.php?product_id=38359")

---

### Post by cariboo on 2008-08-03
You can set up your user as a limited user, make sure he is not a member of the admin group to start.

There is a good tutorial here:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

Watch out which Linksys wrt54 router you buy. I've got a wrt54gs and although it works well for my setup there is no way I can run some of the other firmware that is available.

Jim

---

### Post by Kapli on 2008-08-03
I found exactly what I was looking for 
[http://ubuntuforums.org/showthread.php?t=858475](http://ubuntuforums.org/showthread.php?t=858475)

Followed that tutorial and it works perfect. It is the WRT54GL which I'm looking into and will possibly buy, it appears to have good feedback and loads of linux firmware and stuff so yeah probably gonna go for that.

---

