---
title: "Mkdir: cannot create directory"
date: 2012-07-24
forum: Server Platforms
---

### Post by Thresholder on 2012-07-24
[FONT=Calibri]Hello,[/FONT]
[FONT=Calibri]
[/FONT]
[FONT=Calibri]I have really minimal knowledge of Linux so bear with me please.[/FONT]
[FONT=Calibri]
[/FONT]
[FONT=Calibri]I was trying to install vnc in ubuntu server 12.04 following this guide [/FONT]
  [FONT=Calibri][http://bit.ly/Ol5vC5](http://bit.ly/Ol5vC5). 
[/FONT]
[FONT=Calibri]
[/FONT]
[FONT=Calibri]I think I didn't exit root as instructed and now I get the following error:[/FONT]
[FONT=Calibri]mkdir: cannot create directory `.vnc': File exists[/FONT]
[FONT=Calibri]
[/FONT]
[FONT=Calibri] My problem is similar to this [http://bit.ly/NTMSVc](http://bit.ly/NTMSVc)[/FONT]
[FONT=Calibri]
[/FONT]
I tried some of the suggestions in my last link to no avail so I am basically stuck.

Any help much appreciated.

Thank you.

---

### Post by Vegan on 2012-07-24
try

```
su mkdir dirname
```

:guitar:

---

### Post by MadCow108 on 2012-07-24
it gives the error when you follow the instructions part "mkdir .vnc"?

just ignore the failure, mkdir creates a folder, if it already exists there is nothing to do.
mkdir -p is often preferable as it recursively creates folders and ignores failures due to it already existing
don't create it with su, that will likely just cause permission issues.

---

### Post by cortman on 2012-07-24
> **Vegan said:**
> try

```
su mkdir dirname
```

:guitar:

That's not going to work- it'll just try to su to a user called "mkdir". Try either of these-

```
sudo mkdir dirname
su -c mkdir dirname
```

---

### Post by Thresholder on 2012-07-29
Hello guys,

Sorry for not getting back earlier and thanks to each one of you who replied.

A friend helped me out in the end so not sure how he fixed it but I have taken note of all your suggestions for future reference.

Many thanks. :)

---

