---
title: "Highly Available LAMP Server"
date: 2009-12-16
forum: Server Platforms
---

### Post by barnesey on 2009-12-16
Hi,
I am planning on makeing a webserver/s and i have been on the user documentiuon and found some things that i might find useful. One of the things i found was a highly avaliable webserver ([https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)). However i am still newish to ubuntu and found this confuseing. Does any one know of a guide for "dummies" to achive this.

---

### Post by Skidbladniir on 2009-12-16
Linux, unfortunately, isn't too well documented :(.  Google-ing will bring results, and I found some fairly easy-to-understand tutorials at [http://ubuntugeek.com/](http://ubuntugeek.com/)

Also, according to memory (I might be wrong about this), you can't install "LAMP" outside of the first installation process.  You can install the individual packages, but there isn't one large suite or anything of the type.

---

### Post by User3k on 2009-12-16
> **Skidbladniir said:**
> Linux, unfortunately, isn't too well documented :(.  

???

The Linux Documentation Project, just to name one.

[http://tldp.org/](http://tldp.org/)

---

### Post by Skidbladniir on 2009-12-16
Well, I haven't been able to find anything easy for the "Ubuntu Noob," such as myself.  And by poorly documented, I mean it's hard to really learn anything from the commands and such.  I know I have to do a lot of google-ing.

---

### Post by wojox on 2009-12-16
You can install the whole thing:

```
sudo tasksel install lamp-server
```

---

### Post by User3k on 2009-12-16
> **Skidbladniir said:**
> Well, I haven't been able to find anything easy for the "Ubuntu Noob," such as myself.  And by poorly documented, I mean it's hard to really learn anything from the commands and such.  I know I have to do a lot of google-ing.

I agree. It is hard coming from Windows to Linux when you are completely new. And a lot of times the Linux users in general that reply forget how much of a difference there is for the average user. There are some who have and are attempting to make things easier for new users to understand and get the hang of things. Windows and Linux are both operating systems but they do things differently.

---

### Post by Skidbladniir on 2009-12-16
Exactly.  I love Ubuntu now that I've seen it.  I admit, I have had to run fsck many times (stupid Firefox - I switched to chrome), but I'm suffering through all the errors, and I &#9829; it so far.

Anyway, I did not know you could install a lamp package for Ubuntu server... * Makes sure to check tutorial date next time *

---

### Post by memilanuk on 2009-12-17
There are a lot of things in Windows that took you a long while to figger out as well... but if thats what you started with, it probably didn't stand out as much as when you are trying to learn a new OS from scratch (kind of like growing up speaking a language vs. learing it from ground zero in mid-life).

For most things in Ubuntu, your first stop for information (after the Official Manual) should be the Community Documentation.  I don't know how many gems I've found in there the last few months.  It's awful 'free form', and due to the multiple releases and different approaches possible, they aren't always 'cook book' recipes, which may be what you're looking for i.e. step 1, step 2, step3... done.  For better or worse, a certain amount of 'reading between the lines' and independent reading for understanding/learning is expected.  And for what its worth... a LAMP server is a great project for someone getting started (I have one that I tinker with) but a high-availabilty server setup is another beast entirely, and really only for specific situations... and its not really a beginner project.

---

### Post by Sporkman on 2009-12-17
There's plenty of linux documentation out there, you just need to know how to google for it & get a good eye for sifting through the results. You'll get that over time.

---

### Post by barnesey on 2009-12-18
I have setup up a LAMP server before and found it quite easy and reliable. However a fancy a bit of a challange and decided to see if i can make a highly avaliable setup. I have learnt a few things about Ubuntu server from the collage i go to and got some infomation about this.
I have found some other infomation on google but i have learnt a few things out my self, i will also go and do some more googleing and see if i can find anything else.

---

### Post by llawwehttam on 2009-12-18
Linux documentation is often on a knowledge base so that Linux geeks can understand it but noobs will have trouble.

Read the linux noob guide in my signature.

---

