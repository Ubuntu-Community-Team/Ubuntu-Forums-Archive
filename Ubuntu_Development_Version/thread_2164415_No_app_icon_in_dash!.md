---
title: "No app icon in dash!"
date: 2013-07-31
forum: Ubuntu Development Version
---

### Post by redcylon on 2013-07-31
Just did an update yesterday an I coundn't find an App icon in Dash. Even typing apps name in Dash didn't produce any result. 

Thanks in advance.

---

### Post by MG&amp;TL on 2013-07-31
> **redcylon said:**
> Just did an update yesterday an I coundn't find an App icon in Dash. Even typing apps name in Dash didn't produce any result. 

Thanks in advance.

What is the app called? Thanks.

---

### Post by redcylon on 2013-07-31
I guess all the app. When I opened the app, there's Home, Files, Videos, Music, Images and Contents icon right at the bottom of the dash. There's no app icon as it used to be. Typing the names of the app in Dash doesn't poped-up any of the app. I can launch app only from the launcher and also from the terminal.

---

### Post by MG&amp;TL on 2013-07-31
Oh, I see. *None* of the apps show.

Can you open a terminal (Ctrl-Alt-T) and copy-paste the output from the following command?

```
apt-cache policy unity-lens-applications
```

The command checks to see if the application lens package is installed.

---

### Post by redcylon on 2013-08-01
Installed: 7.0.0+13.10.20130729-0ubuntu1
  Candidate: 7.0.0+13.10.20130729-0ubuntu1
  Version table:
 *** 7.0.0+13.10.20130729-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
        100 /var/lib/dpkg/status

[ATTACH=CONFIG]244984[/ATTACH]

---

### Post by MG&amp;TL on 2013-08-01
That's...odd. I'm sorry, I have no idea why it's not working then. My only suggestion would be that it might have crashed somehow. :(

---

