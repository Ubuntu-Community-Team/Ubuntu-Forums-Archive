---
title: "Can I install packages to Ubuntu from the Mandrake CDs?"
date: 2005-04-08
forum: The Cafe
---

### Post by muzza on 2005-04-08
I have just installed Warty (only got 56k - waiting for Hoary CD) and I like it a lot already.  I tried Mandrake and it almost turned me off Linux for life.

However, there is a lot of software on the Mandrake CDs (6 of them) I was wondering, since I've only got dialup, if it is possible to somehow install some of these into Ubuntu.  Would save heaps of time, eh?

Being the clueless newbie that I am, I would need severe but tender hand holding and patient instructions - that is, if it is possible.

Any takers?

---

### Post by tnilsson on 2005-04-08
[QUOTE=muzza]I have just installed Warty (only got 56k - waiting for Hoary CD) and I like it a lot already.  I tried Mandrake and it almost turned me off Linux for life.

However, there is a lot of software on the Mandrake CDs (6 of them) I was wondering, since I've only got dialup, if it is possible to somehow install some of these into Ubuntu.  Would save heaps of time, eh?

Being the clueless newbie that I am, I would need severe but tender hand holding and patient instructions - that is, if it is possible.

Any takers?[/QUOTE]
 I have actually installed 2 mandrake rpms on my Ubuntu Hoary laptop. It was the meanwhile plugin for gaim. And it worked just fine! I installed them with the command alien. That was the only packages I haven't been able to find for Ubuntu.

---

### Post by muzza on 2005-04-08
[QUOTE=tnilsson] I installed them with the command alien.[/QUOTE]

Sorry, you've lost me already.

---

### Post by Leif on 2005-04-08
copy whichever rpms you want to install to a directory on your hard disk. in that directory, type "alien *.rpm". then "dpkg -i X.rpm" for whichever rpm you want to install.

---

### Post by Perfect Storm on 2005-04-08
But it's no guarentee that converting a .rpm to .deb will work. Tried it with 5 rpm packages and only two of them worked.

---

### Post by az on 2005-04-08
Open a terminal
cd (rpm directory)
sudo alien -i <package.rpm>


Do this at your own risk.  There are differences between prebuilt mandrake packages and prebuilt debian packages.  If you had the source, you could built it with no problem.  Prebuilt binary packages are different.

---

### Post by poofyhairguy on 2005-04-08
[QUOTE=muzza]
Being the clueless newbie that I am, I would need severe but tender hand holding and patient instructions - that is, if it is possible.

Any takers?[/QUOTE]

Here. I'll give you a solid answer: Yes you can install prgrams from the Mandrake CD. No, you should not do it. Mandrake programs and Ubuntu programs use different formats. Everyone is talking about Alien to convert between the two, but Alien doesn't work nearly as well as getting the REAL Ubuntu packages from the Ubuntu server or whatever.

I'm sorry, thats the way it is. Everytime I do a new Ubuntu install and I download over 100mb to get my system how I want, I always think that if I had dial-up I would have a Mac.

---

### Post by muzza on 2005-04-09
[QUOTE=poofyhairguy]Here. I'll give you a solid answer: Yes you can install prgrams from the Mandrake CD. No, you should not do it. .......,..... I always think that if I had dial-up I would have a Mac.[/QUOTE]


Thanks poofyhairyguy, (and everyone else)  I think I'll take your advice and stick to the mac for MP3 and movies.  Ubuntu for web/email/office/gimp for now.

---

### Post by UbuWu on 2005-04-09
For MP3 playback, install gstreamer-mad, it is only 139kb, I think that would be doable even on dialup  :wink:

---

### Post by jdong on 2005-04-09
I **STRONGLY STRONGLY STRONGLY** advise against installing Mandrake packages onto Ubuntu. It's almost guaranteed to break something.

---

### Post by TravisNewman on 2005-04-09
mp3 and movies are pretty simple to get working in Ubuntu.

It's just a matter of installing a few packages from the repositories.

please use the three links in my signature ;) You can find a few things in the Faq/howto forum to help you on your quest.

---

