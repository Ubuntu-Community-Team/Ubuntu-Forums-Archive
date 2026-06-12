---
title: "ttf in php"
date: 2006-09-23
forum: Server Platforms
---

### Post by pht3k on 2006-09-23
hi,

I want to have captcha for my blog.  And i must have the PHP GD library and TTF fonts enabled to use this feature.

For GD everything is fine.  But for TTF i am not sure.

I installed php from terminal with apt-get.  All i can find with google is to add ttf support while doing a .configure command.  Is there a way to add it also via apt-get.  Or do i have to reinstall php from source?

Thanks for your help,
pht3k

---

### Post by pht3k on 2006-09-23
any1?

---

### Post by pht3k on 2006-10-20
i can't beleive no1 can give me a hint here ...

---

### Post by MeerkatC on 2006-11-12
Hi, I found your thread whilst tearing my hair out trying to get TTF fonts working in PHP. I was ready to download the PHP source,  do the configure thing and compile but then found this thread..

[http://ubuntuforums.org/showthread.php?t=284221](http://ubuntuforums.org/showthread.php?t=284221)

I had already copied the font in the directory where the script was running - all that was missing was a "./" in front of the font name!

Hopefully that'll help you - if not it might help others who have the same problem and find your thread like I did.

---

