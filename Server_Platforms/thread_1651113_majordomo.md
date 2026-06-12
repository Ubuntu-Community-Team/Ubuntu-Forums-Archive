---
title: "majordomo"
date: 2010-12-22
forum: Server Platforms
---

### Post by Vegan on 2010-12-22
So I recall from antiquity the program called majordomo so I was wondering what I need to do to get it up and running successfully.

---

### Post by windependence on 2010-12-22
Why?
 
-Tim

---

### Post by SeijiSensei on 2010-12-22
I've run a number of lists with both majordomo and majordomo2.  While there's less documentation for the latter on the Internet, I've found it more customizable than the original.

For the original majordomo, the main documentation site is [here](http://www.greatcircle.com/majordomo/).  Most of the documentation for majordomo2 is kept in help files within the application itself; the main site is [here](http://www.mj2.org/).

Both of them rely on Perl scripts and a few executables.  You'll need to install from source, I suspect, since a quick search doesn't turn up any .deb's in the Ubuntu or Debian repositories.

Most of the documentation for the majordomos expect you to be running sendmail to handle the aliases they require for the lists and list owners.

---

### Post by Vegan on 2011-01-31
I could not find it in the default CVS so I am not too worried. Looks like the program has faded into obscurity.

---

### Post by lisati on 2011-01-31
An alternative to majordomo is mailmain. Some documentation can be found [here]("https://help.ubuntu.com/community/Mailman").

---

### Post by SeijiSensei on 2011-01-31
That's not true for majordomo2: [http://ftp.mj2.org/pub/mj2/snapshots/](http://ftp.mj2.org/pub/mj2/snapshots/)

I see daily versions through today. I doubt there's much development these days, so I'm not certain why you'd need a CVS repo.

I have one original majordomo installation that hasn't been updated in close to a decade. My majordomo2 installation is about three years old now, I believe.  

The GNU organization would prefer that we all use [mailman]("http://packages.ubuntu.com/lucid/mailman"), but it never clicked with me.

---

### Post by Vegan on 2011-02-19
Looks like a lot of work for mailman to install and configure.

I am using a forum for now, its easy to use and setup.

---

### Post by crazyk4952 on 2011-09-17
> **Vegan said:**
> Looks like a lot of work for mailman to install and configure.

I am using a forum for now, its easy to use and setup.

I was able to get mailman up and running in less than 10 minutes from a fresh Ubuntu 10.04 install...

Mailman really isn't that bad!

---

