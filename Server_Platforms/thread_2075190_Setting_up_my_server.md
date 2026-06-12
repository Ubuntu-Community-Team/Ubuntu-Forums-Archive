---
title: "Setting up my server"
date: 2012-10-23
forum: Server Platforms
---

### Post by prostudent on 2012-10-23
I've installed Ubuntu Server with a LAMP Stack. Now here's what I want to do:


[LIST=1]
[*]Install Moodle. I found this page but perhaps you know a better one. If you could help me finding a better one that would be great.       [http://docs.moodle.org/23/en/Step-by-step_Install_Guide_for_Ubuntu](http://docs.moodle.org/23/en/Step-by-step_Install_Guide_for_Ubuntu)
[*]I've only installed the OS. If you could give precise instructions on how to connect it to the web, I would be grateful. I'm currently following this tutorial [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)                                                                                                    and I'm planning to install this                                               [http://www.dyncommunity.com/questions/7252/setting-up-dyndns-client-on-ubuntu-how-to-do-a-bas.html](http://www.dyncommunity.com/questions/7252/setting-up-dyndns-client-on-ubuntu-how-to-do-a-bas.html)
[/LIST]

---

### Post by Habitual on 2012-10-23
> **prostudent said:**
> I've installed Ubuntu Server with a LAMP Stack. Now here's what I want to do:


[LIST=1]
[*]...[]("http://docs.moodle.org/23/en/Step-by-step_Install_Guide_for_Ubuntu")
[*]...instructions on how to connect it to the web, I would be grateful...
[/LIST]
How did you make this post?


2 things to help you out.
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

### Post by mittwit on 2012-10-23
It sounds like your server on your home or office network. If so for now I wouldn't worry about the connecting to the internet bit, just work on getting moodle working locally.

---

### Post by Lars Noodén on 2012-10-23
Do you already have Apache running?  That's the first step.  

The second step would be to enable SSL so that your connections to Moodle are encrypted by using HTTPS instead of HTTP.  Otherwise, in a production environment your more clever students will sniff the staff's passwords.

The document in item 1 above is a bit out of date.  Moodle 2.2.3 is available via the repository.  So you can install it with apt-get or synaptic or the software center.

---

### Post by LHammonds on 2012-10-23
If you plan to run your server for an extended period of time, you might want to check out how I install Ubuntu Servers and separate/configure your partitions so they have room to grow as well as having a good backup/restore method.  Having some functions automated via script is also handy and documented in my thread.

Check my signature for the link.

LHammonds

---

### Post by Lars Noodén on 2012-10-23
> **LHammonds said:**
> Check my signature for the link.


Can you update the body of your post to include the link?  That way the information will still be there a month or six from now when you change your sig.

---

