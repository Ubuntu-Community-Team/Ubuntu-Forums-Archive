---
title: "on sharing my lamp server"
date: 2009-03-24
forum: Server Platforms
---

### Post by lunaz on 2009-03-24
i have an ubuntu 8.10 server i use for files/web/ssh. i have a friend who wants an account with shell & web access.

i installed phpmyadmin & made him a user account, but he still has access to my database. how do i keep him out of there?

what is the best way to give him a shell w/o him finding his way to the rest of my stuff? would virtual machines be the thing?

i did set up that chroot+ssh thing using this howto:
[http://ubuntuforums.org/showthread.php?t=1057657](http://ubuntuforums.org/showthread.php?t=1057657)

after that i tested with filezilla on his account and he could not get out of his home dir. right now he has no shell, just sftp/phpmyadmin.

i have not given him his account details yet :)

---

### Post by BkkBonanza on 2009-03-25
In phpmyadmin you want to login as root and create a user for him. Then give that user privelages only for his own databases. That should allow him to manage his but not even see yours or others.

Likewise he should have his own shell account and only his home and web folders are owned by him and accessible. Web stuff will need to be owned by him but have group permission by apache or www (whatever it runs as). At least, that's one way to do it.

Virtual machines are a nice way to go if you want to spend the time to set it up. Install OpenVZ and configure a vps account for him . Then give him root access to his own machine. Very nice and safe as he can't get to your vps or the root server. Also makes it very easy to create other vps machines and sell/give them away later. I did this all once and it was pretty easy once you read through the OpenVZ docs. Quite a few commerical hosting companies use this package now. You can also get LxAdmin installed if you want a control panel for it.

---

### Post by lunaz on 2009-03-26
thank for the reply :) openvz look like it's worth a shot. how well would it run on my cruddy old laptop?

1.x gz processor
256mb ram

that's all i remember this early in the morning. if more specs are needed i will post when i get home.

---

### Post by BkkBonanza on 2009-03-26
Not too well at all. You just gotta have more RAM than that. Speed isn't much of an issue - you just live with slow. But for virtualization you gotta have some decent amount of memory or it just won't go.

I don't recall off hand the min specs for openvz but I'd be surprised if it could live in 256MB. Maybe 512 and it would fly. No harm in trying though.

---

