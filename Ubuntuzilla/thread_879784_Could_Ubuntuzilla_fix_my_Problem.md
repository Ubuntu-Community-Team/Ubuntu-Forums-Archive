---
title: "Could Ubuntuzilla fix my Problem?"
date: 2008-08-04
forum: Ubuntuzilla
---

### Post by geecee on 2008-08-04
I am running FF 3.0.1 from the Ubuntu Repository on my Kubuntu laptop. I have noticed that on some web pages, FF3 does not reproduce images clearly. There are no such problems when using the Konqueror browser.

At this URL you will find screen shots of a page displayed in FF3 and the same page displayed in Konqueror. The original image is also there.
[http://tempy.ubeauty.fastmail.com.au/](http://tempy.ubeauty.fastmail.com.au/)

The page is also OK using FF2 on my Vista box. 

It has been suggested that I try using Ubuntuzilla to download the latest version, however I understand that 3.0.1 IS the latest version. Will anything be different if I use Ubuntuzilla?

---

### Post by nanotube on 2008-08-04
hi
well... first, i don't see any difference between your 'firefox' and 'konqueror' screenshots...?

second, ubuntuzilla installs the mozilla build, which is compiled with some different options and (probably) tries to be as generic as possible. so even though the version is the same, it will be a somewhat different firefox.

that said, i don't know if it will make any difference, but you won't lose anything if you try it and see - if it doesn't do it for you, just use ubuntuzilla's 'remove' command and it will put your system back to where it was before.

---

### Post by geecee on 2008-08-04
Thanks for your reply. I will give it a try.

BTW, if you look at the text in the screenshots, in particular the small text near the top you will see the difference. On the original site, this text is actually a series of images, not true text.

---

### Post by Master Chief on 2008-08-04
It looks like the images are resized in Firefox, and we do have a pref for that so please check the following preference with about:config

```
browser.enable_automatic_image_resizing
```

---

### Post by geecee on 2008-08-05
Well I have installed Ubuntuzilla and think I will stick with it even though it did not fix my problem.

BTW, the "browser.enable_automatic_image_resizing" didn't help either.

Thanks for trying.

---

### Post by nanotube on 2008-08-05
> **geecee said:**
> Well I have installed Ubuntuzilla and think I will stick with it even though it did not fix my problem.

BTW, the "browser.enable_automatic_image_resizing" didn't help either.

Thanks for trying.

hm well, could you post a higher-resolution screenshot of what you are seeing, in konq vs firefox - if i can see what it is you are seeing, maybe i can figure it out. :)

---

### Post by geecee on 2008-08-06
:oops:  :redface:
I just discovered that if I adjust both browsers to give the same image size I get pretty well the same result.

Sorry! Thanks for trying.

---

### Post by nanotube on 2008-08-06
> **geecee said:**
> :oops:  :redface:
I just discovered that if I adjust both browsers to give the same image size I get pretty well the same result.

Sorry! Thanks for trying.

cool :)

---

### Post by Master Chief on 2008-08-07
> **geecee said:**
> :oops:  :redface:
I just discovered that if I adjust both browsers to give the same image size I get pretty well the same result.

Did you file a bug report?  If not, let's start by adding a link and (possibly) clear steps to reproduce the bug. Thanks.

---

### Post by geecee on 2008-08-09
> **Master Chief said:**
> Did you file a bug report?  If not, let's start by adding a link and (possibly) clear steps to reproduce the bug. Thanks.

Ummm! I think that my previous post indicates that there IS no bug.

---

