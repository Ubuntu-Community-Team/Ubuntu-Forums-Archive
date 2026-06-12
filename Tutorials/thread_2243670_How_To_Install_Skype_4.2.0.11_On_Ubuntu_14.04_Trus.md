---
title: "How To Install Skype 4.2.0.11 On Ubuntu 14.04 Trusty Tahr And Linux Mint 17 Qiana"
date: 2014-09-10
forum: Tutorials
---

### Post by necromonger on 2014-09-10
As you may know, the Skype version from the Canonical Partner repositories has fixes done by the Ubuntu developers, so it is better for your system then what’s available on skype.com.

In order to install Skype 4.2.0.11 on Ubuntu 14.04 and Linux Mint 17 via the Canonical Partner repository, we have to add the repo to our system:

$ sudo sh -c 'echo "deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty partner" >> /etc/apt/sources.list.d/canonical_partner.list'

Update the local repository index:

$ sudo apt-get update

Install Skype:

$ sudo apt-get install skype

Next, start Skype and Agree to the license terms.

---

### Post by Bucky Ball on 2014-09-10
*Thread moved to **Tutorials**.*

... or go to Software Sources (or Software Settings or Software Updater and click 'Settings' in the bottom left corner; I'm using xfce so not sure on Unity), click the 'Other Software' tab and enable the Canonical Partners repo ...

---

### Post by uRock on 2014-09-10
> **Bucky Ball said:**
> ... or go to Software Sources (or Software Settings or Software Updater and click 'Settings' in the bottom left corner; I'm using xfce so not sure on Unity), click the 'Other Software' tab and enable the Canonical Partners repo ...

On ubuntu I go to Ubuntu Software Center > Edit > Software Sources
[https://www.youtube.com/watch?v=HsKg2dw304c](https://www.youtube.com/watch?v=HsKg2dw304c)

---

### Post by deadflowr on 2014-09-10
> **Bucky Ball said:**
> 

... or go to Software Sources (or Software Settings or Software Updater and click 'Settings' in the bottom left corner; **I'm using xfce so not sure on Unity**), click the 'Other Software' tab and enable the Canonical Partners repo ...

Generally the same, though Unity calls it Software and Updates now in trusty.

You can also simply uncomment the canonical partners line(s) in the /etc/apt/sources.list file.

Though the version seems old to me.
I now have 4.3.0.37 installable, both for precise and trusty...

---

### Post by uRock on 2014-09-10
> **deadflowr said:**
> I now have 4.3.0.37 installable, both for precise and trusty...

Same here.

---

### Post by Bucky Ball on 2014-09-10
Let me see ... yep! Same here. 4.3.0.37 ;)

---

