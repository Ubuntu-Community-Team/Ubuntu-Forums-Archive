---
title: "nessus and ports"
date: 2007-01-17
forum: Server Platforms
---

### Post by Pitbull11188 on 2007-01-17
I recently had a problem with gaim that I couldn't figure out for 2 days. The solution involved me changing the designated port from 5190 to 5189. I'm fairly clueless when it comes to networking and ports, but as far as I can tell this means that quite recently something is blocking or using that port on me. Is there a possibility of an intrusion? I am behind a router, and after changing the port I began to run firestarter.

I also downloaded nessus, but I have no clue how to run it on my computer or any other computer in my network for that matter.

Basically here are my questions:

1.) What command can I use to determine the ip adresses of all the boxes on my network?
2.) Is there a possibility of an intrusion on port 5190?
3.) Could someone please point me to some good nessus documentation?

Thanks.

---

### Post by Ufo on 2007-01-18
You can determine the ip adresses in your network running nessus.
You need to have nessusd installed on one of the machines. 
Then you need to create user with nessus-adduser. 
After that you can start nessusd. 
Then you can start nessus client. 
Man -k nessus shows nessus related man pages, which will help you get started.
Links to very good introdustion to nessus can be found on nessus homepage
[http://www.nessus.org/documentation/](http://www.nessus.org/documentation/)
in "Books and articles about Nessus" section: Introduction to Nessus by Harry Anderson at SecurityFocus.com (three links)

Hope this helps...

---

### Post by Pitbull11188 on 2007-01-18
thanks:p

---

