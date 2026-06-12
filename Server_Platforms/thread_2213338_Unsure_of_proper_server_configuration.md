---
title: "Unsure of proper server configuration"
date: 2014-03-26
forum: Server Platforms
---

### Post by dubrewski on 2014-03-26
If this is in the wrong section or not a valid post I do apologize, let  me know and I will fix it. Let me start out by saying that along with  this being my first go at setting up a server, I am still fairly new to  Linux itself. I have been trying to do this as much on my own as  possible with the help of the good old google machine. I've reached a  point where Im over whelmed by the amount of different options and at  the very least I could use a nudge in the right direction.

What I  am trying to accomplish is a server that will function as a local  media/file server, a vpn and a personal web server/cloud. I would like  to allow for 10 - 15 users to be able to go to my hosted page, login and  have access to X gbs of personal storage along with a large shared  media storage. I would like the users to have the abilities to transfer  files between each other at their own discretion and be able to stream  content from their personal storage or the shared media storage. The  shared media would also be accessible locally. If I could throw some  email in there as well that would be nice but not a big deal. At some  point I would like to be able to host a few more smaller sites running  on VMs but that's not in the near future. Each component on its own seems  simple enough but as I try to combine them I just get a little scatter  brained.

Would a combination of ownCloud, Subsonic and openVpn be  able to handle all this (minus the email and VMs) or am I going in the  complete wrong direction?  Thanks in advance for any input, suggestions  and criticisms. 

-dubrewski

---

### Post by carlo3 on 2014-03-26
Hey there, I've pretty much been doing similar to yourself over the past couple weeks and am also new to setting up this sort of machine. I made a thread [here]("http://ubuntuforums.org/showthread.php?t=2210840") and there's been really helpful posts from others, maybe take a look at it and see what information you can use.

My needs are on a much smaller scale than yours, but for the local media/file server I ended up going with ZFS for the file system and sharing drives through Samba. The hardest part was making sure all the permissions were in order, and setting up the relevant users/groups.

I was looking at [Zentyal]("http://www.zentyal.org/server/#server-features") too before deciding that it was a bit overkill for my home use, but it sounds like it ticks quite a few boxes for you.

Carlo

---

### Post by dubrewski on 2014-03-27
Thanks for the response. I wish I saw your thread before, there is a few links in there I hadn't checked out yet. Zentyal looks interesting but being my first attempt I feel more comfortable sticking with Ubuntu right now. At least I know there is a good support community I can reach out to if need be. Do you have any web features with your setup?

---

### Post by carlo3 on 2014-03-27
The only things i can think of with my setup that might be web features are phpvirtualbox and the plex web client. I'd like to get ownCloud up and running on my setup too, now I have setup Virtualbox I will probably run a machine just for all the web services to keep things nice and modular.

There's an online demo of ownCloud too, you could check to see it does everything you'd like it to.

---

