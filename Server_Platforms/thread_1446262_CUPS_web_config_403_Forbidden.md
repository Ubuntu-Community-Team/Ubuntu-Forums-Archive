---
title: "CUPS web config 403 Forbidden"
date: 2010-04-03
forum: Server Platforms
---

### Post by chrisbay90 on 2010-04-03
Hi all,

I recently set up a headless ubuntu server (ubuntu server 9.10). As well as many other things i would like to use it as a printer server. Being a headless machine, i would like to configure cups using the webui from another computer on the lan. However when i browse to [http://server:631/](http://server:631/) i get a 403 forbiden error.

I install cups on the server (Ubuntu server 9.10)
configured cupsd.conf  as per [https://help.ubuntu.com/9.10/serverguide/C/cups.html](https://help.ubuntu.com/9.10/serverguide/C/cups.html)
browsed to it from a ubuntu 9.04 machine using firefox on the same lan and got an 403 forbiden error.

I also tried adding the local account on the server to the lpadmin group 

sudo usermod -aG lpadmin username

but that made no difference. I do not get prompted for a username/password at all when i try to get the webui up.

Am i missing anything? Can some shed any light on how i might resolve this issue?

---

### Post by suseendran.rengabashyam on 2010-04-05
Hi,

Solution 1:

Open the file /etc/cups/cupsd.conf

In the blocks:

<Location /> , <Location /admin> and <Location /admin/conf>

Add the following line : ```
Allow all
```

Restart the CUPS server and check whether you get the same error.

You may look at
[http://ubuntuforums.org/showthread.php?t=310450](http://ubuntuforums.org/showthread.php?t=310450) for more details. 

Solution 2:

In the terminal, enter the following command 

> sudo cupsctl --remote-admin

and restart the CUPS server. 

Hope this helps.

---

### Post by chrisbay90 on 2010-04-06
Thank you very much suseendran.rengabashyam that worked perfectly.

---

### Post by vancheese on 2010-08-28
That last command worked a treat for me too - Thanks for posting it

---

### Post by rangi500 on 2012-10-09
Solution 2 worked nicely for me too (I didn't try solution 1). However it seems to completely rewrite your cups config file (/etc/cupsd.conf) so be warned!

---

### Post by overdrank on 2012-10-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

