---
title: "Good repository practice?"
date: 2005-09-23
forum: Repositories &amp; Backports
---

### Post by cydizen on 2005-09-23
Hello everyone, 

 I just had a couple questions regarding proper package management.  First let me caveat this by saying I am currently in the latest preview release of Breezy, however I have had Hoary boxes as well.  Generally speaking I prefer to only use packages as provided by the main, supported repositories, however there are a couple of packages out there that are must haves (dvd support... etc).

My question is should I....

a) Download the wanted packages and install them manually.

b) Enable the universe repos and use synaptic to install them.

It's easy enough to use the universal repos, but is it bad practice to turn them 'on' and 'off' as I need packages?  Is it bad to just open them up and go to town? 

I really value stability, but there are packages that I mentioned that I must go outside of the main repos to get.  

What practices do you guys use?  


Thanks for your time / opinions,

Bruce

---

### Post by Xian on 2005-09-24
I've been using Breezy and strictly use Synaptic with the main/restricted/universe/multiverse repos enabled. I've yet to run across any issues that would tempt me to dissuade you from doing likewise. Of course, it is always more stable to not delve into universe/multiverse but I have not experienced issues with what is installed on my box.

---

### Post by chettyk on 2005-09-25
I share Cydizen's concern about ensuring stability. I am using Hoary. I normally keep universe and multiverse repos disabled, and enable them only when I need a package that cannot be found in the main repos. Bu that is a real pain. Each time apt's sources.list file is changed, I need to run update. Plus the packages installed from universe and multiverse don't get upgraded.

Is it the case that universe and multiverse repos contain only program files that don't exist in the main repos? If I run upgrade with universe and multiverse repos enabled, is there a danger that a a stable version of some program file that has been installed from the main repos would be overwritten by one from universe and multiverse repos?

---

### Post by Leif on 2005-09-25
you should use repositories whenever possible, otherwise you're missing out on half the fun of apt.

universe, multiverse etc. are distinct from main; see [http://www.ubuntu.com/ubuntu/components/document_view](http://www.ubuntu.com/ubuntu/components/document_view)

the packages in universe and multiverse are not supported the same way main is, but they really are completely safe 99% of the time, and will not affect anything in main anyway. the extra repositories are taken from debian, and that usually ensures a high standard.

---

### Post by chettyk on 2005-09-25
Thanks, Leif. I'll take your advice and see how it goes.

---

### Post by cydizen on 2005-09-26
Alrighty, thanks to those who responded. I am going to give it a shot leaving the non standard repos open. 


Regards,
Bruce

---

