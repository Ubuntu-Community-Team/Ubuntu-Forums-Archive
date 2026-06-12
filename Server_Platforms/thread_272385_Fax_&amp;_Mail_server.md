---
title: "Fax &amp; Mail server"
date: 2006-10-06
forum: Server Platforms
---

### Post by salvo1 on 2006-10-06
Hi guys,
In my office we've a PC that run as proxy, server mail, server fax, webserver..
...i know it's not so good (Win2003 Server + [602Lan suite](http://www.software602.com/products/ls/)) but I installed it in 6...7 mins using a nice GUI.

It isn't stable, not secure... but it works.

Yesterday moring i decided to install a mail server on linux to have something free (as a free beer) and really table. From yesterday morning, the only thing that really works is Ubuntu Dapper... :)

A friend of mine suggested me:
1. Postfix
2. Qmail ("simple to configure")
3. SendMail ("compleX")

ClaimAV e SpamAssassin 

4. Hylafax

Why become crazy under a lot of .conf files? I read thousand and thousand  wiki and threads in this forum and in the italian one, but postfix doesn't work and it's really hard to configure.

Have you got any idea about a simple mail server?

---

### Post by bluefrog on 2006-10-06
you could start with [http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

This should put you on track and then up to you to pursue the good work.

(just a little question... takes 6-7 minutes to configure win2003, ok. How many hours did it take to install win 2003 and set it up as a webserver.... am not waiting for an answer on that one :-D more a troll than anything else...)

One thing though, if you are not happy with lots of conf files maybe the best thing is to stick with win2003. I say this without any offence and coming from the windows world I understand pretty well your concern. The main thing that made me change to linux was this specific fact that you can control, thx to the lots of conf files, what you are doing in Linux while in windows well, if something was wrong, I was quite unable to do anything about it. This being said I was maybe just a poor windows admin not able to use the DOS command line.

James

---

### Post by salvo1 on 2006-10-06
In Win:
1. run 602 LAN Suite
2. choose WWW path (ex: C:\Web_Server)
3. click run

And this is the webserver..

Anyway, i know it's not the right way.. but, I needed something that worked soon.

Now, i've time to start to configure the server that will sub the old one.

> One thing though, if you are not happy with lots of conf files maybe the best thing is to stick with win2003. I say this without any offence and coming from the windows world I understand pretty well your concern. The main thing that made me change to linux was this specific fact that you can control, thx to the lots of conf files, what you are doing in Linux while in windows well, if something was wrong, I was quite unable to do anything about it. This being said I was maybe just a poor windows admin not able to use the DOS command line.

I agree.

Thank you for suggestions (WebMin seems to be great!)

---

