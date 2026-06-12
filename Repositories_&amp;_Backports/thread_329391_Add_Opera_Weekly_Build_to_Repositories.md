---
title: "Add Opera Weekly Build to Repositories"
date: 2007-01-01
forum: Repositories &amp; Backports
---

### Post by pak33m on 2007-01-01
Hello,

I have been manually installing the weekly builds of Opera from here:

[http://snapshot.opera.com/unix/Weekly-521/intel-linux/](http://snapshot.opera.com/unix/Weekly-521/intel-linux/)

And I use the opera_9.xx-xxxxxxxx.6-shared-qt_en_i386.deb weekly build.

Am I able to add the link above to the repositories or does it actually need to be a repository in order to get the file listed above?

Also, I've tried to create a script to do the same, to no avail.  The /Weekly-number changes as the weekly is added.  I've tried using a * & ?'s in my script but nothing works.

Any help would be appreciated.

---

### Post by ffi on 2007-01-01
The url changes with every build, I don't now if it would be possible to add it as a repo, don't think so....

[http://snapshot.opera.com/unix/Weekly-](http://snapshot.opera.com/unix/Weekly-)**521**/intel-linux/

521 is the build number...

---

### Post by pak33m on 2007-01-01
Hi ffi,

Yeah, that's what I'm up against.  I forgot to mention that the URL changes with each build.  Thank you for the input.  I've also asked the question in the comments page at the Opera Weekly Desktop blog page.

I'll keep hammering away at it in the meanwhile!

---

### Post by ffi on 2007-01-02
What I find far more annoying is that I have to uninstall the previous version of Opera first, everytime I want to upgrade because Gdebi says: "error: Conflicts with the installed package 'opera'". Do you have the same problem?

---

### Post by pak33m on 2007-01-02
That may well have happened to me once before.  The "conflict" could be happening if you're upgrading from the static version to the shared version or vice versa.  You should use the shared version over the static.  At least that's what I did in the beginning & have been problem-free since.

Here's what I do (in two steps) to upgrade to the weekly build:

1.  Download the opera_9.xx-xxxxxxxx.6-shared-qt_en_i386.deb
2.  At the CLI type dpkg -i opera_9.xx-xxxxxxxx.6-shared-qt_en_i386.deb (from the path where the file was downloaded).

Once the above listed command is run the last output to be generated will be that the "database is being updated" (something like that) & then return to the CLI without any error output.  

Oh, and then I check the version under the help menu to make sure Opera was upgraded.

I hope this helps you out.

---

### Post by ffi on 2007-01-02
Thanks, but I want to use gdebi because upgrading would just be point n click and I always use the shared build, because the static build is just to ugly. Now I first have to uninstall opera before installing the new version :-|

btw:

[http://my.opera.com/community/forums/topic.dml?id=172441](http://my.opera.com/community/forums/topic.dml?id=172441) but that's only for finals.....

---

