---
title: "64 bit flash player 10 for Linux"
date: 2008-11-22
forum: The Cafe
---

### Post by duanedesign on 2008-11-22
yeah we finally have a 64 bit Flash Player. Adobe has released the alpha of 64 bit flash player 10 for Linux ahead of the release for Windows and Mac. As recently as last year, Linux users waited six months for Flash 9 to arrive on Linux, following its release on other platforms. Now the alpha 64-bit version is coming out first on Linux because "that's where we've heard the outcry the loudest," Adobe GM/VP (Platform Business) David Wadhwani was quoted as saying. It is nice to know that Adobe is listening to the Linux community. Now maybe we will get A Linux Creative Suite.

 Below is a link to download it. Use this thread to post your experiences with the new player.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by graysky on 2008-11-22
Got it on my lenny amd64 box and it's working great.

The link you provided didn't work to allow me to d/l the 64-bit version for linux, only the standard x86.  [Here](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz) is a link to download the 64-bit version.

Once you untar the file, here are the steps I took to get it working (YMMV):

```
# mkdir /usr/local/lib/flashplugin
# mv flash-mozilla.so /usr/local/lib/flashplugin
# cd /etc/alternatives
# mv flash-mozilla.so flash-mozilla.so-old
# ln -s /usr/local/lib/flashplugin/libflashplayer.so flash-mozilla.so
```

---

### Post by sonicb00m on 2008-11-22
At last they are taking Linux seriously!

---

### Post by youssef77 on 2008-11-22
Take care, it crashes any Flex application , plays youtube nicely though.

---

### Post by graysky on 2008-11-22
> **youssef77 said:**
> Take care, it crashes any Flex application , plays youtube nicely though.

Can you post an example url?

---

### Post by brianh57 on 2008-11-22
I just got it installed.  Seems to work pretty well on a few sites I tried.  This should take away one of the biggest obstacles to 64-bit becoming the most widely used version.  Very nice!

---

### Post by duanedesign on 2008-11-22
> **graysky said:**
> 

The link you provided didn't work to allow me to d/l the 64-bit version for linux, only the standard x86.  

you have to scroll down to the bottom of the page. However the link you provided is the same as the one at the bottom of the page i provided so either one is sufficient.

---

### Post by don_xvi on 2008-11-22
Is this "Flex" issue the reason Firefox crashes when I visit either:
citicards.com
or
freep.com (that's the Detroit Free Press and their homepage has an embedded video link)

---

### Post by cubeist on 2008-11-22
you can also just put the plugin in your .mozilla/plugins folder

---

### Post by rv65 on 2008-11-22
For OSS you can get a 64 bit libflashsupport.so. However, I compiled my own and it works great. 

[http://ubuntuforums.org/showpost.php?p=5374886&postcount=273](http://ubuntuforums.org/showpost.php?p=5374886&postcount=273)

Do the instructions for 64 bit but omit -m32. Follow the instructions and it works great. Hope this helps anyone.

---

### Post by graysky on 2008-11-22
> **don_xvi said:**
> Is this "Flex" issue the reason Firefox crashes when I visit either:
citicards.com
or
freep.com (that's the Detroit Free Press and their homepage has an embedded video link)

Dunno what to tell you.. both of those sites displayed just fine for me using iceweasel 3.0.3 and the 64-bit plugin.

---

### Post by brianh57 on 2008-11-23
> **don_xvi said:**
> Is this "Flex" issue the reason Firefox crashes when I visit either:
citicards.com
or
freep.com (that's the Detroit Free Press and their homepage has an embedded video link)

I also had no trouble with those sites using Firefox 3.0.4 and the 64-bit plugin

---

### Post by istblacken on 2008-11-23
also that grey box issue doesn t happen to me anymore. it seems nspluginwrapper causes that bug and we don t need it in 64 bit flash player which is nice too..

---

### Post by PmDematagoda on 2008-11-23
This thread is not really a support request, but one mostly asking for feedback, therefore it has been moved to the Cafe. But due to it's significance, I have left a permanent redirect here.

---

