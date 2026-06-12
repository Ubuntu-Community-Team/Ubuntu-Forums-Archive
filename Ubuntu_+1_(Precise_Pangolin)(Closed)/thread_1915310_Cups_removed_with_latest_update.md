---
title: "Cups removed with latest update?"
date: 2012-01-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Robertjm on 2012-01-26
Just checked for updates to PP, and when I go over the list of items to install, it also tells me it's going to remove cups and a whole bunch of other things that are related to printing.

ARGH!!

---

### Post by Harry33 on 2012-01-26
> **Robertjm said:**
> Just checked for updates to PP, and when I go over the list of items to install, it also tells me it's going to remove cups and a whole bunch of other things that are related to printing.
ARGH!!

When using (or testing) a development version and updating it, you should take into account the following.
Several source updates consists of two or more packages. These all must generally be updated together. It often happens that one or more of these packages are published a bit later into the repository.
Now, if you try to update this kind of source (with some packages still missing), you will break your system.

So, please wait. Have a cup of coffee or two. :guitar:

---

### Post by Robertjm on 2012-01-26
I know. It's just that I was shocked to see something basic like cups get broken by an update is all. 

Believe me, it took me too long to get the Canon printer working on this alpha in the first place. I hit the cancel button and will wait till tomorrow.

---

### Post by QIII on 2012-01-26
We don't need no stinking printer!

---

### Post by TheNessus on 2012-01-26
I sure do hope 12.04 comes CUPS free. And Gwibber, and Empathy, and Evolution\thunderbird free, and... oh I can go on for ever.

---

### Post by QIII on 2012-01-26
Minimalist purist much?

Think Bodhi.  The next version will be based on Precise and, as Bodhi is, will be so minimalist you will cut your fingers on the raw edges if you are not careful.  So it's not for everyone.

Or just stick with a minimal Ubuntu install.

That, or you can do a normal install and, I don't know, replace or just not use the things you don't like.

---

### Post by cariboo on 2012-01-26
> **TheNessus said:**
> I sure do hope 12.04 comes CUPS free. And Gwibber, and Empathy, and Evolution\thunderbird free, and... oh I can go on for ever.

Time for **you** to learn how to do a minimal install, the rest of us may want or need what you don't want.

---

### Post by Jdogzz on 2012-01-26
Well I think he's right at least in the area of Gwibber:) I fail to see its purpose since half of it doesn't do anything and the other half is quite buggy.

@OP Have you considered using Google Cloud Print? Or does that require the computer to be connected to the printer still...

---

### Post by cariboo on 2012-01-26
This thread is getting pretty far off topic, read the first post again, the op said a partial upgrade wanted to remove cups, so he decided to wait for the needed depends to catch up, and then do an update. 

Some of you are trying to solve a nonexistent problem.

---

### Post by sammiev on 2012-01-26
> **cariboo907 said:**
> This thread is getting pretty far off topic, read the first post again, the op said a partial upgrade wanted to remove cups, so he decided to wait for the needed depends to catch up, and then do an update. 

Some of you are trying to solve a nonexistent problem.

+1 to that.

---

### Post by ronacc on 2012-01-26
> **Robertjm said:**
> Just checked for updates to PP, and when I go over the list of items to install, it also tells me it's going to remove cups and a whole bunch of other things that are related to printing.

ARGH!!

in a dev version this often happens for reasons someone else already stated , just wait for all of the necessary packages to hit the repos before you update .

---

### Post by ranch hand on 2012-01-27
> **Robertjm said:**
> I know. It's just that I was shocked to see something basic like cups get broken by an update is all. 

Believe me, it took me too long to get the Canon printer working on this alpha in the first place. I hit the cancel button and will wait till tomorrow.
I take it that you are;
A>upgrading with UM
B>fairly new to testing

UM is not the recommended way to upgrade a dev release.

If you must us a gui use synaptic where you can pick and choose the packages to upgrade fairly easily.

Apt-get or aptitude would be better yet.

It is fairly simple to determine which package is trying to remove things.  Just run "install" with apt-get or aptitude for the rest.

Removing little things like the desktop environment is not uncommon in testing.  Be glad it was only cups.  

The package will get a new upgrade in a day or too and be fine.  Relax and have FUN.

---

