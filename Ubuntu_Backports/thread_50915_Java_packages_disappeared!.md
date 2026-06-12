---
title: "Java packages disappeared!?"
date: 2005-07-21
forum: Ubuntu Backports
---

### Post by tzutolin on 2005-07-21
Hello, everyone

I just reloaded and found the jdk and jre are gone. Does anyone have the same problem too?

---

### Post by jjross on 2005-07-22
yes ,i am having the same problem, i am hoping to find some answers here on the forum

---

### Post by kevcart3 on 2005-07-22
I am having the same problem, looks like they have been removed from the repo. If this is the case, does anyone know an alternate repository for the java package?

---

### Post by mo42 on 2005-07-22
Java packages are very easy to make with java-package. A short description how to do it is here: [http://serios.net/content/debian/java/with-java-package.php]("http://serios.net/content/debian/java/with-java-package.php")
I hope that this is a good alternative for you.

---

### Post by GTvulse on 2005-07-22
[QUOTE=tzutolin]Hello, everyone

I just reloaded and found the jdk and jre are gone. Does anyone have the same problem too?[/QUOTE]
 It is due to corruption in the Package.gz files. Let's hope they are regenerated properly during the day (that's an automagic process).

---

### Post by jesse on 2005-07-22
You can always get blackdown java by adding the following to sources.list 

deb [http://ftp.iasi.roedu.net/pub/mirrors/ftp.blackdown.org/java-linux/debian/](http://ftp.iasi.roedu.net/pub/mirrors/ftp.blackdown.org/java-linux/debian/) sarge non-free

If java is no longer in the backports it's too bad.

---

### Post by jdong on 2005-07-23
Relax guys :)

The master server had a disk space problem. Everything is fine now :)

---

### Post by sinbad782 on 2005-08-24
Hi,
  I found today that i couldn't download the sun-j2re1.5 package. I have all the backports (official and unofficial repositories) mirrors in my sources.list. I'm not sure if this is the same problem - has anyone else had this problem?

---

### Post by andril on 2005-08-24
Yes, I am also experiencing this issue. I noticed it this am when I replaced my hard drive and attempted to reinstall java. I hope that we can get this fixed soon  ](*,) 

I am stuck without it

---

### Post by Exeggcute on 2005-08-24
Several packages are missing...

I am experiencing problems with the following packages:

sun-j2re1.5 and sun-j2sdk1.5 are missing;
acroread is downgraded to 5.0;
transcode is missing (unable to install dvdrip).

Please, let us know when this is fixed! Thank you very much!

---

### Post by tzutolin on 2005-08-24
Yeah, I would also like to know this, thanks!!

---

### Post by bytheway on 2005-08-24
I'm seeing this same problem.  It looks to me like the Packages.gz file is not correct, as its missing at least the acroread and java packages.

---

### Post by tzutolin on 2005-08-24
[QUOTE=bytheway]I'm seeing this same problem.  It looks to me like the Packages.gz file is not correct, as its missing at least the acroread and java packages.[/QUOTE]

Yeah, and firefox  ;-)

---

### Post by titus1950 on 2005-08-24
Java,acroread,samba,missing......????
What is going on???????

---

### Post by tzutolin on 2005-08-24
[QUOTE=titus1950]Java,acroread,samba,missing......????
What is going on???????[/QUOTE]
 Just like bytheway said, maybe the Packages.gz is broken...

---

### Post by jdong on 2005-08-25
yeah, /var is full. I'll see what I can do, but most likely it's gonna involve work from ubuntu-geek.

Meanwhile, I'd like to complain loudly about FreeBSD's default of 256MB for /var.... Yes, that includes /var/tmp (which is the default tmp) and /var/log!

---

