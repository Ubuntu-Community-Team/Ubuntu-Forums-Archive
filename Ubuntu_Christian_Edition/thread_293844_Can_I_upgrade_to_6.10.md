---
title: "Can I upgrade to 6.10 ?"
date: 2006-11-05
forum: Ubuntu Christian Edition
---

### Post by glenn69 on 2006-11-05
I noticed that Ubuntu is now at 6.10 Edgy.  I have CE version of Ubuntu. Can I follow the directions on Ubuntu site to upgrade CE to 6.10 or will that not work?

Thanks

---

### Post by catlett on 2006-11-05
I would say no. Ubuntu CE is now up to v1.4. That says to me that it is different enough that they have there own versions. Opposed to xubuntu being 6.10 and kubuntu being 6.10 along with Ubuntu.
It appears ubuntu ce has a upgrade_me script. That is the one you want. I don't know much about ce but this may be a good place to start [http://www.whatwouldjesusdownload.com/christianubuntu/news/2006/10/ubuntu-ce-v14-released-october-3-2006.html](http://www.whatwouldjesusdownload.com/christianubuntu/news/2006/10/ubuntu-ce-v14-released-october-3-2006.html)

---

### Post by mhancoc7 on 2006-11-05
> **glenn69 said:**
> I noticed that Ubuntu is now at 6.10 Edgy. I have CE version of Ubuntu. Can I follow the directions on Ubuntu site to upgrade CE to 6.10 or will that not work?

Thanks

In theory yes. However, Ubuntu CE is being built with Dapper as its base. This is due to Dappers status as an LTS (Long Term Support) release. Ubuntu CE is really simply Dapper at its core. So you could follow the steps to upgrade to Edgy. I would not recommend it however. I have only tested it once and it did not go well. There have been reports of users using the convert_me script to convert there Edgy install, but this is not supported or recommended. I am planning on releasing some scripts for Edgy users after the next release of Ubuntu CE. These will be unsupported, but I believe there is definitely a demand for them.

The main reason that we are sticking with Dapper is due to its stability. We may eventually move to Edgy, but for now it will be Dapper.

On a side note, I have never been very successful with upgrading from one release to the next of Ubuntu. I have always found it better to just to a fresh install. This can of course be annoying since you spend all that time getting everything setup and then have to do it all over again. :)

If you have any questions just let me know.

God Bless, Jereme

---

### Post by mysticrider92 on 2006-11-09
I just reinstalled Ubuntu CE using a v1.3 cd after wiping the hard drive, and upgraded to Edgy using the "gksu update-manager -c" (I think that is right) command and it seems to be working fine. I haven't tried the v1.4 upgrade script yet, I will try that in a few minutes. I did this on an install that I had done nothing to, I don't know how it will work if you have changed anything, so I would say just use at your own risk.


[edit]: Woot! Ubuntu CE 1.4 running on Ubuntu 6.10! The only problem is now I don't have a splash screen (nothing major, I'll try to fix it later).

After running the v1.4 upgrade script on the install, it looks like a few things *might* have crashed, I got two error reports saying that I needed to upgrade some things, resulting in two minor package management errors.

[edit2]: Everything form CE seems to be working right now except Automatix, which I don't think has been finished in Edgy.

---

### Post by mhancoc7 on 2006-11-09
> **mysticrider92 said:**
> I just reinstalled Ubuntu CE using a v1.3 cd after wiping the hard drive, and upgraded to Edgy using the "gksu update-manager -c" (I think that is right) command and it seems to be working fine. I haven't tried the v1.4 upgrade script yet, I will try that in a few minutes. I did this on an install that I had done nothing to, I don't know how it will work if you have changed anything, so I would say just use at your own risk.


[edit]: Woot! Ubuntu CE 1.4 running on Ubuntu 6.10! The only problem is now I don't have a splash screen (nothing major, I'll try to fix it later).

After running the v1.4 upgrade script on the install, it looks like a few things *might* have crashed, I got two error reports saying that I needed to upgrade some things, resulting in two minor package management errors.

[edit2]: Everything form CE seems to be working right now except Automatix, which I don't think has been finished in Edgy.

Thanks for keeping us updated. Sounds promising. Have you tested the Configure Parental Controls GUI in 6.10? I would be interested if it is working with 6.10.

God Bless, Jereme

---

### Post by mysticrider92 on 2006-11-09
The GUI works fine. I haven't tested the blocking yet, i'll probably try that tomorrow.

---

### Post by mhancoc7 on 2006-11-09
> **mysticrider92 said:**
> The GUI works fine. I haven't tested the blocking yet, i'll probably try that tomorrow.

Thanks!! I just released v1.5!!

God Bless, Jereme

---

