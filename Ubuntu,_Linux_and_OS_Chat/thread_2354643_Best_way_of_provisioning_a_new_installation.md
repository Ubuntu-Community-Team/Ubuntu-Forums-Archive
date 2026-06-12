---
title: "Best way of provisioning a new installation?"
date: 2017-03-04
forum: Ubuntu, Linux and OS Chat
---

### Post by horsebox2 on 2017-03-04
I started writing a set of Ubuntu post installation scripts, after forking a script I found on github but its time consuming and I don't wanna reinvent any wheels. Is there a good post installation repository which is the most advanced post installation script system available? That would be worth forking. Or is there a better approach, such as using chef or puppet or something?

---

### Post by TheFu on 2017-03-04
Check out ansible and their galaxy.

Can't recommend chef or puppet for single systme use. They have too much setup.  Ansible takes about 20 minutes to start using. They have a nice introduction video.

"most advanced" isn't really relevant is it?  The method that gets you to the end the most efficiently is what matters, right?
[http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) is how I setup servers.

---

