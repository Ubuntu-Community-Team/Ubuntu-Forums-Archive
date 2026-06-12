---
title: "dansguardian -tbn"
date: 2006-11-30
forum: Ubuntu Christian Edition
---

### Post by anv on 2006-11-30
I started to watch TBN from xine and and it gave this output:

-xine engine error-

there is no input plugin available to handle <html><HEAD><TITLE>Dansguardian - accass Denied</title></head>`.
Maybe MRL syntax is wrong,,,

I can watch it with mplayer, but it gives out unstable voice and picture sync, so I use xine for this as earlier yesterday.

I added in dan the mms stream address bot not blocked addresses and not blocked sites. didn't help. where I can turn it so that what ever I might watch through Xine, I can do it ?!?:eek:

---

### Post by apjone on 2006-11-30
tail the dans log as you try and watch it.

---

### Post by Darrious on 2006-11-30
What I would do is disable Dansguardian then try it.

---

### Post by mhancoc7 on 2006-11-30
> **anv said:**
> I started to watch TBN from xine and and it gave this output:

-xine engine error-

there is no input plugin available to handle <html><HEAD><TITLE>Dansguardian - accass Denied</title></head>`.
Maybe MRL syntax is wrong,,,

I can watch it with mplayer, but it gives out unstable voice and picture sync, so I use xine for this as earlier yesterday.

I added in dan the mms stream address bot not blocked addresses and not blocked sites. didn't help. where I can turn it so that what ever I might watch through Xine, I can do it ?!?:eek:

Have you commented out the entries in Banned MIME Types for dansguardian? If not, I would give that a shot.

Jereme

---

### Post by anv on 2006-12-03
Yes I add thtat link in allowed list, but didn't help. So I took away whole dansguardian. Is there other security advantage to use it or just site filtering? I noticed it was atleast connected to clamav. I try it later again. :)

---

### Post by anv on 2006-12-03
Oh I forget to ask, if I have uninstalled it, should I delete some logs/ files from somewhere before next install of dansguardian

---

### Post by mhancoc7 on 2006-12-03
> **anv said:**
> Yes I add thtat link in allowed list, but didn't help. So I took away whole dansguardian. Is there other security advantage to use it or just site filtering? I noticed it was atleast connected to clamav. I try it later again. :)

The dansguardian is only setup for filtering so no security concerns if you remove it.

> **anv said:**
> Oh I forget to ask, if I have uninstalled it, should I delete some logs/ files from somewhere before next install of dansguardian

If you use the dansguardian script from the Ubuntu CE project site to reinstall the script will ensure a completely fresh install.

Thanks, Jereme

---

### Post by mhancoc7 on 2006-12-03
I have just released a script to disable/enable dansguardian in Ubuntu CE.

[http://www.ubuntuforums.org/showthread.php?p=1841627#post1841627](http://www.ubuntuforums.org/showthread.php?p=1841627#post1841627)

---

