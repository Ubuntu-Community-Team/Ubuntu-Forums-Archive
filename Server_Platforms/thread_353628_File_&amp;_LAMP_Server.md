---
title: "File &amp; LAMP Server"
date: 2007-02-04
forum: Server Platforms
---

### Post by lenwood on 2007-02-04
Hi All, I'm considering putting one of my old desktops back into use as a home file & LAMP server with Ubuntu Server. I got the idea from [this]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html") article. The author's setup instructions are pretty clear. I've read through it a couple of times and understand everything that he says. I have two questions before I get started:

1) would [Webmin]("http://www.webmin.com/index.html") be of any help at all? I don't want to install the desktop because ultimately this will be a headless server. But it looks like Webmin could be just the ticket. Does anyone have any feedback on this?


2) Are there any tips or advice that anyone could give before I get started? Anything I should know before I start?

Thanks in advance. I'm looking forward to getting back into the Linux world. I installed Ubuntu on an old laptop last summer, and was so pleased with the experience that I was hesitant to give the computer to my brother when he needed a computer.

Thanks,
Len

---

### Post by Smandola on 2007-02-05
Hi Len,
Ultimately what are you looking to do with your home file & LAMP server ?
Base on the link in your post, this guy uses his headless server for some file sharing, and uses the web tools to administer his server.  Is this what you are looking to do ?

If you are looking to have a simple file server, webmin would be an easy way for you to manage your headless server.  I'm sure that there are other methods.  But webmin is definitely one of the easier remote methods. 

To Answer your questions. 
```
1) would Webmin be of any help at all? 
I don't want to install the desktop because ultimately this will be a headless server. 
But it looks like Webmin could be just the ticket. Does anyone have any feedback on this?
```
I think webmin would be an easy way of managing your headless server.  Webmin can be served up with your Apache server, and is one of the easier methods of remotely administering your server.  I'm sure that I'll get flamed in saying that.  I know that webmin will not truely replace the prompt, but I think its fairly encompassing.  That being said, I'm sure that there are things webmin is missing, but for my needs, it works just fine.

```
2) Are there any tips or advice that anyone could give before I get started? Anything I should know before I start?
```
Have you been to the webmin site [http://www.webmin.com/](http://www.webmin.com/)
I like how the webmin site looks almost exactly like webmin once its installed on your server.  Webmin also has a documentation section.  FAQ and what not... [http://www.webmin.com/index2.html](http://www.webmin.com/index2.html)
This maybe something to check out if you are just browsing for info.  

Good luck with your install and with webmin.  Post back if you have any other questions.
s.

---

### Post by Mike'sHardLinux on 2007-02-05
1) Yes. With Webmin, you can control just about every aspect of a server.

2) Sounds like you are off to a good start. I would have recommended reading through a how-to or two. I'd say jump right in and follow the how-to. My favorite way to learn is by doing.

It is typical for a new Linux user to install/re-install Linux over and over again as they are learning, and trying to get their setup just right. Sometimes this is because we end up breaking our installs when we are tinkering around, other times it's just to try something different. Try not to let it get to you if something doesn't work perfectly the first time. There's so many ways for things to go wrong - typos (in either the how-to or your own typo), differing software versions, accidentally skipping a step(s), etc....

I've only played around with Webmin, and it wasn't for me, but there's a few people on the forums who use it.

---

### Post by Brazen on 2007-02-05
I install webmin on every server I set up.  In fact, I've installed it on my desktop system too, since I'm so used to using it.  Most things I prefer to edit the config files directly (using ssh) but every once in a while it's nice to be able to see a graphic representation of what's going on, to help sort things out.

By the way, the latest version of webmin has a new theme that no longer looks like the site theme, just in case you install it and are confused about what Smandola said.

---

### Post by lenwood on 2007-02-05
Thanks for the input everyone. I'm really looking forward to tinkering with Linux again, even if I'm not running it on a desktop this time. I'll post my experience here if anything comes up.

Thanks,
Len

---

### Post by Smandola on 2007-02-15
Brazen, Good call on the changes... I had an old version of webmin installed.  The current version 1.320 has a very different look and feel compared to previous releases.  I installed the new version, and I'm forcing myself to learn it.  I'm not finding it as simple to use as previous, but maybe its just me.  Good catch.

s.

---

