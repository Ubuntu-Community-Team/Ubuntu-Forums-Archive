---
title: "need some help with apache2."
date: 2008-10-27
forum: Server Platforms
---

### Post by meomike2000 on 2008-10-27
i have installed apache 2 and i get the it works page. why do i not get the other default page. i looked for it in the file system and it doesnt seem to exist. i cannot access the manual either. can anybody help with this.

thanks in advance.

---

### Post by bukwirm on 2008-10-27
You'll need to edit the /etc/apache2/sites-available/default file. Probably.

---

### Post by cdenley on 2008-10-27
> **meomike2000 said:**
> i have installed apache 2 and i get the it works page. why do i not get the other default page. i looked for it in the file system and it doesnt seem to exist. i cannot access the manual either. can anybody help with this.

thanks in advance.

other default page?

---

### Post by meomike2000 on 2008-10-27
i know about the other default page. the page doesnt seem to be installed. like it wasnt part of the download or i just can not find it. the location where it would be doesnt show no sign of it. i would believe that it would be located in /var/www. is this correct.

---

### Post by cdenley on 2008-10-27
> **meomike2000 said:**
> i know about the other default page. the page doesnt seem to be installed. like it wasnt part of the download or i just can not find it. the location where it would be doesnt show no sign of it. i would believe that it would be located in /var/www. is this correct.

If the page isn't installed, then how can it be the "default page"? Wouldn't a default page be installed by default by definition? When you install apache, you should have nothing but the "it works" default page, and maybe [http://localhost/doc/](http://localhost/doc/) which can only be accessed locally. What page are you talking about?

---

### Post by meomike2000 on 2008-10-27
my understanding is that there is also a page called apache2-default. is this page no longer there. i know that i used to get this page when i would first install apache and go to the default site. this time all i get is the page that says it works. is the other page no longer there?

---

### Post by porteclefs on 2008-10-27
i recently installed a LAMP and there was only the one default page. I don't think you have anything to worry about. Why do you need / want the 'other' default page?

---

### Post by alienprdkt on 2008-10-27
I think you are wondering about the file Bukwirm mentioned above.

Or you are mistaking Ubuntu for Mac OSX with Apache, which allows you to have 2 default pages one for /~usr and one for your computer.

---

### Post by cdenley on 2008-10-27
> **meomike2000 said:**
> my understanding is that there is also a page called apache2-default. is this page no longer there. i know that i used to get this page when i would first install apache and go to the default site. this time all i get is the page that says it works. is the other page no longer there?

[http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.8-1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.8-1/changelog)
> 
Don't ship default files in /var/www, but copy a sample file to
    /var/www/index.html on new installs. Also remove the now unneeded
    RedirectMatch line from sites-available/default.
    (Closes: #411774, #458093)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=411774](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=411774)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=458093](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=458093)

---

### Post by meomike2000 on 2008-10-27
i believe the page i was lookin for has been removed from the package. thanks for the responses.

---

