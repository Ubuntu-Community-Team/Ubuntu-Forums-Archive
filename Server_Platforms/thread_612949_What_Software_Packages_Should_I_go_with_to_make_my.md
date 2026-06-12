---
title: "What Software Packages Should I go with to make my webserver secure?"
date: 2007-11-14
forum: Server Platforms
---

### Post by kustomjs on 2007-11-14
Hi Guys
I am sorry for keep asking Newbie questions but I want to make sure that I am doing this the correct way and being secure of doing this since I do not want the Feds come to my door asking about peoples credit cards and personal information being leaked by a hacker so my main question is what software packages should I download and install on to my home webserver for my small business e-commerce site that is dealing with personal and credit card information so I need to know what software packages I should get. Thanks Tim

---

### Post by timcredible on 2007-11-14
are you writing your own web server apps, or using exising open source apps like joomla?  if you're writing your own cart app, then it's up to you to make your code secure.  if you're using an existing cart app, then check the forums about patches, etc. to make sure you have any known problems fixed.  i'm assuming you'll be using apache, mysql, and myphp, so keep those up to date also.

---

### Post by kustomjs on 2007-11-14
I want to use existing software and I am going to use open source e-commmerce shopping Oscommerce. right now I got LAMP/Ubuntu 7.10 Gutsy installed on the computer

---

### Post by meatpan on 2007-11-14
Software packages might help, but you will also get (arguable more) security benefit from hardening your system by enforcing policies and understanding consequences of various server configurations.  Examples of a few policies are enforcement of strong passwords,  requiring services to  run in a chroot jail (when possible),  restricting plain text authentication, keeping your server physically secure in a safe location,  only allowing *stable* software installations, with routine security patch application, etc...

I found the server security guide to be a great start: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

BTW, this forum is great for answering security questions for a specific server.  Feel free to break down your system set up, and request input about your overall config, and which aspects are the most vulnerable.

---

