---
title: "How to make a apache website for gaming?"
date: 2013-11-24
forum: Server Platforms
---

### Post by joehopper7 on 2013-11-24
Hey, this is a proberlem not a tutorial. (sorry for my english, i'm german)

I am trying to make a Apache website for my game server but I am having some troble making it. I have went though alot of tutorials on how to do it but they didn't work.

The website template I want is this: [http://design.d3x.co/demo/mcgeneric/](http://design.d3x.co/demo/mcgeneric/)
But when I put all the files which I downloaded here: [http://dstats.net/download/http://design.d3x.co/download/mcgeneric-102.zip](http://dstats.net/download/http://design.d3x.co/download/mcgeneric-102.zip)
Its comes up like this:[ATTACH=CONFIG]248056[/ATTACH]   (I made it smaller)

Can someone please help me.

Thanks

---

### Post by sffvba[e0rt on 2013-11-24
*Thread moved to **Server Platforms**.*

---

### Post by nerdtron on 2013-11-25
Where did you extract the zip file containing the html documents?
I assume you extracted it in the /var/www/ folder?
If so post the output of
```
ls -lh /var/www/
```


You might need to edit the permissions of the files.
```
sudo chown -R www-data:www-data /var/www/
sudo chmod -R a+r  /var/www/
```

---

### Post by joehopper7 on 2013-11-27
Thanks! Its works!

---

