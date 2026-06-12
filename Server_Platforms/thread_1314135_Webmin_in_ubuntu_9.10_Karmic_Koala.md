---
title: "Webmin in ubuntu 9.10 Karmic Koala"
date: 2009-11-04
forum: Server Platforms
---

### Post by n0name2 on 2009-11-04
Hy there

I want to ask is it recommended to install and run webmin and virtualmin in Ubuntu 9.10?

I am asking this because I am new to to ubuntu server administration and i found tasks such as setup and configuration of postfix, apache, webdav, dns,.. etc. much harder to accomplish without webmin and most off all it goes very slow.
In 7.04 i used webmin and it was wery easy to setup and configure and much quicker.

I heard that webmin messes up config files, i don't really want that on my new machine :)

Therefore i am asking you if it is not recommended to run webmin what alternatives do you propose for beginner like me, or is the best to try myself out in plain config with help of doc? Have to mention that i am student and i don't have really tons of time :)
Thanks in advance.

regards
dejan

---

### Post by nathanm412 on 2009-11-04
I used webmin successfully on my Ubuntu 9.04 server. I didn't have any problem with it for over 6 months. I even learned how to setup bind by manually working with the config file that webmin generated for me. 

Now that I have a better handle of what I am doing, I worry that webmin may conflict with config files that I also work on manually. I've decided that I will go without the training wheels as I build my Karmic server.

---

### Post by n0name2 on 2009-11-06
Jeah I think that i will exactly same thing. Don't want either webmin to mix with files that I am editing manualy.
Will go, and will see what happens with my linux box :)

---

### Post by chitx2000 on 2009-11-14
I upgraded my 9.04 recently to 9.10 and now seems my webmin won't load up. I tried upgrading it to the latest webmin version 1.490 but still the page won't load. I just don't know where to start debugging 9.10 so webmin will work again . . .

---

### Post by prsjm3qf on 2009-11-15
You've just got to be careful. Webmin can't get it right for every distro all the time and does sometimes screw things up.

However, it has an excellent, well featured file manager and combined gui text editor that makes remote admin of a non-gui system just so much easier.

I use webmin in this way combined with an ssh terminal connection and don't generally use the modules. It then pretty much gives you everything you'd get from a remote desktop login.

You've got to be careful not to expose your webmin login to the world though.

---

### Post by chitx2000 on 2009-11-15
> **chitx2000 said:**
> I upgraded my 9.04 recently to 9.10 and now seems my webmin won't load up. I tried upgrading it to the latest webmin version 1.490 but still the page won't load. I just don't know where to start debugging 9.10 so webmin will work again . . .

I found this link that tells about the issue with Karmic and Webmin

[http://sourceforge.net/tracker/index.php?func=detail&aid=2876859&group_id=17457&atid=117457](http://sourceforge.net/tracker/index.php?func=detail&aid=2876859&group_id=17457&atid=117457)

---

### Post by IcyTexx on 2010-01-23
How about Virtualmin?
It still doesn't work.

---

