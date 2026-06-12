---
title: "installation XAMPP 1.8.0"
date: 2012-07-24
forum: Server Platforms
---

### Post by Jonasbraun on 2012-07-24
hello, help please, I have problems to install, XAMPP 1.8.0 ,when I try installing appears this


tar xvfz xampp-linux-1.8.0.tar.gz-C / opt
tar (child): xampp-linux-1.8.0.tar.gz-C: No se puede open: No existe el archivo o el directorio
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now.

thanks

---

### Post by jsartti on 2012-07-27
change "tar xvfz xampp-linux-1.8.0.tar.gz-C / opt" with "sudo tar xvfz xampp-linux-1.8.0.tar.gz -C /opt" (add blank space between .gz and -C and remove blank space between / and opt).
Sorry for my bad english, i speak spanish.

---

### Post by Lars Noodén on 2012-07-27
I hope that since you last posted you've been able to find Apache2, PHP and MySQL in the Ubuntu repositories and installed either via the Software Center or Synaptic.

XAMPP is a crutch for people still on Windows and works for them.  If you are on Windows, then XAMPP can help you but this is then the wrong forum to ask for help.  If you are on Ubuntu, then this is the right forum but XAMPP is the wrong way to go about things in Linux.  It installs a version of perl that conflicts with the version that comes pre-installed with Ubuntu.  And it installs versions of PHP, Apache2 and MySQL that will conflict with what's in the repository.  

Linux distros provide an easier way to install and maintain packages via their repositories.  If you stick with the repository versions, then dependencies, conflicts and security updates will be managed for you automatically.  If you try to deal with XAMPP on Linux then you have to do all that manually.

I'd strongly recommend removing the files that came with XAMPP and getting everything via the Software Center or Synaptic.  It will save you lots and lots of headache and heartache over time as you have to try to keep things secure, compatible and up to date.

---

### Post by dakshbhatt21 on 2012-09-01
hey dude if you want to reinstall xampp from first then go through this article . . .

[http://daksh21ubuntu.blogspot.com/2012/01/how-to-install-xampp-in-ubuntu.html](http://daksh21ubuntu.blogspot.com/2012/01/how-to-install-xampp-in-ubuntu.html)

and then you can faced one error called "security concept problem" for that visit this

[http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html](http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html)

---

