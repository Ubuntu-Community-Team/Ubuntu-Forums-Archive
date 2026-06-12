---
title: "Compiz effects"
date: 2014-01-27
forum: Ubuntu Development Version
---

### Post by Rodolfo_Mena on 2014-01-27
Hi! guys. I just installed  Ubuntu 14.04 daily build, and it doesn't come with all the Compiz effects. in other words Compiz Fusion is not included.
What  comes to my mind. it is that it's because is not the final realese.
Any ideas if  the final realese. will come with all the conpiz effects. (Fusion) to be more specific.

Thanks in advance.
[h=1][/h]

---

### Post by deadflowr on 2014-01-27
compiz effects are built in with default settings already.
If you want to manipulate them then install compizconfig-settings-manager.
You might also need to install the compiz-plugins, or compiz-plugins-extras, or something like that.

It's been this way for quite a while, and I don't see them adding the gui anytime soon for the release.

---

### Post by Elfy on 2014-01-27
*Thread moved to **Ubuntu +1**.*

---

### Post by Cavsfan on 2014-01-27
Here are the things that were either installed or I added:

[ATTACH=CONFIG]249786[/ATTACH]

You'll need to install **gnome-session-flashback** and anything else it pulls in too if you haven't already.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-session-flashback
gnome-session-flashback:
  Installed: 1:3.8.0-1ubuntu3
  Candidate: 1:3.8.0-1ubuntu3
  Version table:
 *** 1:3.8.0-1ubuntu3 0
        500 http://mirrors.advancedhosters.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

A screenie:
[[IMG]http://www.zimagez.com/miniature/screenshotfrom2014-01-25181018.png[/IMG]]("http://www.zimagez.com/zimage/screenshotfrom2014-01-25181018.php")

---

### Post by deadflowr on 2014-01-27
Why would you need gnome-session-flashback?

---

### Post by Cavsfan on 2014-01-27
> **deadflowr said:**
> Why would you need gnome-session-flashback?

Oh I just took it that he wanted to login to Gnome Flashback (with Compiz). That was why I said that. If not then just forget gnome-session-flashback.

---

### Post by deadflowr on 2014-01-27
> **Cavsfan said:**
> Oh I just took it that he wanted to login to Gnome Flashback (with Compiz). That was why I said that. If not then just forget gnome-session-flashback.

No problem.
I just thought maybe you had some abracadabra stuff that made compiz run better or something.

---

### Post by fantab on 2014-01-28
> **deadflowr said:**
> compiz effects are built in with default settings already.
If you want to manipulate them then install compizconfig-settings-manager.
You might also need to install the compiz-plugins, or compiz-plugins-extras, or something like that.

It's been this way for quite a while, and I don't see them adding the gui anytime soon for the release.

+1.
See the screenshot to see what all packages you need for fully functional compiz
[ATTACH=CONFIG]249882[/ATTACH]

---

### Post by zika on 2014-01-28
> **fantab said:**
> +1.
See the screenshot to see what all packages you need for fully functional compiz
[ATTACH=CONFIG]249882[/ATTACH]Minus 3 transitional dummy packages...

---

### Post by Cavsfan on 2014-01-28
> **deadflowr said:**
> No problem.
I just thought maybe you had some abracadabra stuff that made compiz run better or something.

I just can't see wasting that space on the left side with Unity. That's just me. I'd much rather have the right side of the screen showing system info and weather from VinDSL's conky and Paramvir's weather.
With both it makes the usable desktop too small for me.
But, yes I've got it all going really good. I even have the Emerald window decorator running without a problem.
The cube rotates and all the goodies in Cairo Dock and Compiz have it really looking good. :)

If you look at the screenie I posted you can see that Impulse has Cairo Dock jumping around to the beat of the music. :)

---

### Post by Rodolfo_Mena on 2014-01-29
Thanks guys, but none of your answer had helped.

---

### Post by deadflowr on 2014-01-29
> **Rodolfo_Mena said:**
> Thanks guys, but none of your answer had helped.

In what way?

What do you seem to miss?
Are you missing some of the extra plugins?
Then run
```
sudo apt-get install compiz-plugins
```

---

