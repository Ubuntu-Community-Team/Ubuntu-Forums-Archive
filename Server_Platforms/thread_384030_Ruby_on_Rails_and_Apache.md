---
title: "Ruby on Rails and Apache"
date: 2007-03-14
forum: Server Platforms
---

### Post by Paul41 on 2007-03-14
I followed these instructions to install Ruby on Rails and set up fastcgi for Apache [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails). Everything works OK when I run it with the webrick server, but when I try to run it on apache it just displays the code to me instead of parsing it. The Apache server itself is fine because I run php on it with no problems. It is only with RoR that I am having problems.

I don't know anything about Ruby on Rails (I was installing it to learn) so I could be missing something obvious. Does anyone have any ideas what could be going wrong?

---

### Post by Brazen on 2007-03-14
Try this [https://help.ubuntu.com/community/DinkelVersus/ApacheServer](https://help.ubuntu.com/community/DinkelVersus/ApacheServer) and maybe it will give you an idea of something you missed.

---

### Post by Paul41 on 2007-03-14
> **Brazen said:**
> Try this [https://help.ubuntu.com/community/DinkelVersus/ApacheServer](https://help.ubuntu.com/community/DinkelVersus/ApacheServer) and maybe it will give you an idea of something you missed.

I looked through this and I didn't miss anything as far as installing. The Apache virtual host file was different in this file than the one I had, but when I try it I get a different problem. I get this error when I try to go to the site.


> Routing Error

no route found to match "/rails/cookbook/public/" with {:method=>:get}

---

### Post by Paul41 on 2007-03-14
Well I just went back to my original virtual host file before adding anything about fastcgi and it seems to be working now :-k .  I haven't really had a chance to test it out good yet, I have just run one of the default files. I will post back if I am still having the problem once I get to do further testing.

---

### Post by Brazen on 2007-03-14
Are you using Dapper or Edgy?

---

### Post by Paul41 on 2007-03-14
Edgy

---

### Post by Brazen on 2007-03-17
I've heard some funky problems on Edgy.  If you are wanting this to be a production server, I would strongly urge you to try it on Dapper.

---

### Post by Paul41 on 2007-03-17
This is not for production.  It is just my local development box.

---

