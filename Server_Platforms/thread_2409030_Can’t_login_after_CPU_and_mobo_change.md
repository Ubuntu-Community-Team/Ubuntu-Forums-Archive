---
title: "Can’t login after CPU and mobo change"
date: 2018-12-26
forum: Server Platforms
---

### Post by jredmon89 on 2018-12-26
So i cloned my drive cause i had my shell on a laptop and it was intell based and now i have a stronger server that’s AMD based and it boots up perfectly fine for the most part...how ever when i try to login via Putty i can type my username in but when i type in the password it says access denied how ever on the local machine i can log in with very minor issues...anybody have any ideas i need this fixed ASAP because this server is what holds my files for the game I’m making for my employees normally i can fix issues with my server but this one has me stumped

---

### Post by wildmanne39 on 2018-12-26
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by volkswagner on 2018-12-27
It could be saved entry in know_hosts.
I've never had to delete these in putty (as I rarely use putty), but
this thread should help you locate the entry.
[https://superuser.com/questions/197489/where-does-putty-store-known-hosts-information-on-windows](https://superuser.com/questions/197489/where-does-putty-store-known-hosts-information-on-windows)

---

### Post by jredmon89 on 2018-12-27
Thank you for the reply i have deleted the registry keys and am waiting to hear back from my IT guy in Virginia for him to start my server again so i can test will report back with results

---

### Post by jredmon89 on 2018-12-27
@volkswagner i deleted the ssh keys and accpeted the new ones and it still says access denied

---

### Post by zorlax on 2018-12-28
Lets see if I got you right, multiple questions-suggestions to follow.
What are the minor issues?

 You have cloned the hard-drive in your server and moved that installation to new hardware, right? How are you trying to login, is it user@host or user@ip? If you use host did you change the hostname on the new server? Just to make sure that you're trying to connect to the right machine.

---

### Post by volkswagner on 2018-12-29
You can also try verbose mode for ssh. This may give you a hint.
Please post the output of the ssh -v result.

Well, I see you are using putty. According to [this post]("https://centrify.force.com/support/Article/KB-5452-How-to-enable-debug-for-PuTTy-SSH-clients")
you can enable verbose logging. I tried it on one of my putty clients and it didn't seem to log much, but your milage may very.

---

