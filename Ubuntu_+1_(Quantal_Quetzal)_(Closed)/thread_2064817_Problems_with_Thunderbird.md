---
title: "Problems with Thunderbird"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by thedoctor81877 on 2012-09-30
I have just upgraded from Lubuntu 12.04 to 12.10 beta 1, and now whenever I open Thunderbird,it immediately closes and I have no idea what is going on nor how to fix it. Any help is appreciated. Thanks.

---

### Post by Frogs Hair on 2012-09-30
Try to open the program from the terminal with the following and post the output in code tags #. There may be a clue as to what's happening.  ```
thunderbird
```

---

### Post by thedoctor81877 on 2012-09-30
OK, here's what I get when I do that:

```


** (thunderbird:15893): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (thunderbird:15893): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image

(thunderbird:15893): GLib-GIO-ERROR **: Settings schema 'org.gnome.Evolution.DefaultSources' is not installed

Trace/breakpoint trap (core dumped)



```

---

### Post by Frogs Hair on 2012-09-30
It seems to be complaining about the theme . Have you tried a different theme ? Also install all updates if you haven't already.

---

### Post by thedoctor81877 on 2012-09-30
OK, then I have 2 questions/problems.

1. How do I change the theme when it will not stay opened, and
2. When I try to update I keep (both in the updater, and in the terminal) getting the following:

```


W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/source/Sources  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.150 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

Thanks.

---

### Post by daslinkard on 2012-09-30
Just thinking out loud here but what about purging Thunderbird and then doing an install followed by a search for updates?

---

### Post by thedoctor81877 on 2012-09-30
Upon purging, reinstalling, and updating, I get:

```


enigmail.js: Registered components
caught error TypeError: Cc['@mozilla.org/mime/pgp-mime-decrypt;1'] is undefinedmimeDecrypt.jsm: MimeDecryptor registration done
** (thunderbird:16164): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (thunderbird:16164): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image

(thunderbird:16164): GLib-GIO-ERROR **: Settings schema 'org.gnome.Evolution.DefaultSources' is not installed

Trace/breakpoint trap (core dumped)


```

---

### Post by thedoctor81877 on 2012-10-02
I have tried removing thunderbird, then updating, and finally reinstalling thunderbird - but to no avail. I still get the previous messages when I attempt to run Thunderbird from the terminal. Can anyone help me please? Thanks a bunch!

---

### Post by daslinkard on 2012-10-02
Are you able to get Thunderbird to work without crashing when running the following command?
```

thunderbird -safe-mode
```

---

### Post by thedoctor81877 on 2012-10-02
Yes, daslinkard, it does seem to run in safe mode! So, what do I do next?

---

### Post by thedoctor81877 on 2012-10-02
OK, it runs, but I still get the following:

```


** (thunderbird:26380): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (thunderbird:26380): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image




```

---

### Post by daslinkard on 2012-10-02
> **thedoctor81877 said:**
> I have just upgraded from Lubuntu 12.04 to 12.10 beta 1, and now whenever I open Thunderbird,it immediately closes and I have no idea what is going on nor how to fix it. Any help is appreciated. Thanks.

I'm wondering if this is a bug that you found being that you upgraded to the 12.10 beta 1 version?

---

### Post by thedoctor81877 on 2012-10-02
I am not sure, though that is possible. As best I can tell all of my other software works fine. Is there any way to tell, and if so, what can I do -- besides waiting for the full upgrade?

---

### Post by daslinkard on 2012-10-02
> **thedoctor81877 said:**
> I am not sure, though that is possible. As best I can tell all of my other software works fine. Is there any way to tell, and if so, what can I do -- besides waiting for the full upgrade?

My question for you now would be if you are using IMAP and if some how that is causing a conflict?

I'm also wondering if you could reset your home folder with .mozilla?

---

### Post by thedoctor81877 on 2012-10-02
Please forgive my ignorance, but how do I ascertain if I am using IMAP, and how could I reset my home folder with .mozila?

---

### Post by thedoctor81877 on 2012-10-02
OK, I looked and was able to ascertain that I am using IMAP for Thunderbird, but do not know enough for your other comment here.

---

### Post by daslinkard on 2012-10-02
> **thedoctor81877 said:**
> OK, I looked and was able to ascertain that I am using IMAP for Thunderbird, but do not know enough for your other comment here.
OK, let's start over here....

First, I want you to completely purge Thunderbird (I believe you have tried this before, right?)  After TB has been purged I want you to start the following sudo commands....```

sudo add-apt-repository ppa:mozillateam/thunderbird-stable
``````
 sudo apt-get update
``````
sudo apt-get install thunderbird xul-ext-calendar-timezones xul-ext-lightning
```

Restart the machine and see if that fixes it....if not, we might need to make a new profile and proceed from there.  Let me know!

---

### Post by thedoctor81877 on 2012-10-02
I tried everything you mentioned, and upon restarting the machine, and running TB from the terminal, I still get the same problems. Now, when I restarted the machine, the software updater started - though I am not sure if any of the updates are for TB. It is still running, bc the updates are @ 120MB+. BTW, Thanks for all of your help, I really appreciate it!

---

### Post by thedoctor81877 on 2012-10-02
The updates are finished, and now TB opens fine (so far w/o crashing!) but in the terminal I still get a BUNCH of error and warning messages (more than before). Should I be worried about these?

---

### Post by daslinkard on 2012-10-02
I would say that as long as it is functioning properly you should be fine....as long as you are happy with the outcome for this thread....go ahead and mark this as solved once you verify the issue is resolved!

---

### Post by thedoctor81877 on 2012-10-03
OK, and thank you very much!!!

---

### Post by daslinkard on 2012-10-03
> **thedoctor81877 said:**
> OK, and thank you very much!!!
Just wanted to check in to make sure that all is good in the world of TB on your machine?

---

### Post by oldos2er on 2012-10-03
Moved to Ubuntu +1 (Quantal Quetzal).

---

### Post by thedoctor81877 on 2012-10-04
Yes, I think it is working fine now, and thanks again for all your help!!!

---

### Post by daslinkard on 2012-10-04
> **thedoctor81877 said:**
> Yes, I think it is working fine now, and thanks again for all your help!!!
No worries at all!

---

