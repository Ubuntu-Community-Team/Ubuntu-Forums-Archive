---
title: "If you use JuJu or LXC or both... you should read this great info"
date: 2014-04-26
forum: Ubuntu Cloud and Juju
---

### Post by bmullan2 on 2014-04-26
I posted this on Reddit's Ubuntu section so I won't copy it here.

But if you use JuJu or LXC or both together you really should read this article by Chris Glass... the title of his article is 
**[SIZE=3]Making LXC (and Juju) fly on Ubuntu     [/SIZE]**

[http://www.reddit.com/r/Ubuntu/comments/24201q/if_you_use_juju_and_lxc_this_article_is_great_info/](http://www.reddit.com/r/Ubuntu/comments/24201q/if_you_use_juju_and_lxc_this_article_is_great_info/)

Chris describes how to install and take advantage of squid-deb-proxy-client to tremendously reduce time to create/update JuJu or LXC

I just finished configuring this and did a test.

  Created an LXC container called "test1" and after logging into it did an
**apt-get install xfce4**
time to complete = **25 minutes**
next created a 2nd LXC container called "test2" and after logging into it did an
**apt-get install xfce4**
time to complete = **9 minutes !!!**   


  That was a big difference for me and my daily work flow.

 
 
Hope it helps some of you also...

---

