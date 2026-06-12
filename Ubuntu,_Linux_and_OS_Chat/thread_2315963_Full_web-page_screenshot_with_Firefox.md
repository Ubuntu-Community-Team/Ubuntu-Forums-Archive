---
title: "Full web-page screenshot with Firefox"
date: 2016-03-04
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2016-03-04
This has been around for quite some time now, but I just found out about it.

In Firefox, press *shift+F2* and type in *screenshot --fullpage filename*. The file called "filename" will be saved in your default download folder. There's also a "delay" option which I haven't tried so far.

---

### Post by SeijiSensei on 2016-03-04
What a great find!  Sure beats launching something like ksnapshot just to capture a web page.

---

### Post by Habitual on 2016-03-04
That's a Keeper.

---

### Post by sammiev on 2016-03-04
Thanks, works great.

---

### Post by kostkon on 2016-03-04
This is cool. It even shows you a preview right there on the commandline toolbar.

---

### Post by vasa1 on 2017-06-15
Can someone please check if this is now broken in Firefox 54? It appears broken for me. "Unknown error" is what I get :(

---

### Post by entropy1 on 2017-06-15
I just updated to Firefox 54.0 (64-bit) in Ubuntu Mate 17.04, and your command from post #1 worked for me.

---

### Post by #&amp;thj^% on 2017-06-15
> **vasa1 said:**
> Can someone please check if this is now broken in Firefox 54? It appears broken for me. "Unknown error" is what I get :(
vasa1 on my Gnome-wayland (17.04), if I did not specify a file name...I also received a unknown error.IE:>>"screenshot --fullpage filename" threw the error >>but "screenshot --fullpage your-title-here" worked...FWIW
```
 apt policy firefox
firefox:
  Installed: 54.0+build3-0ubuntu0.17.04.1
  Candidate: 54.0+build3-0ubuntu0.17.04.1
  Version table:
 *** 54.0+build3-0ubuntu0.17.04.1 500
        500 http://archive.ubuntu.com/ubuntu zesty-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu zesty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     50.1.0+build2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu zesty/main amd64 Packages


```

---

### Post by vasa1 on 2017-06-15
Thanks, entropy1 and 1fallen, after reading your posts I checked and it's working on Firefox 54 from the repos. 

It's not working on Firefox 54 direct from Mozilla on another machine; both are 16.04 fully updated.

---

### Post by leemer3567 on 2017-06-27
Thank you so much! This is so useful and cool.

---

