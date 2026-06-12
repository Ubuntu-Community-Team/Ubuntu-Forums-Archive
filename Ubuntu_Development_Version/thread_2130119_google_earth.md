---
title: "google earth"
date: 2013-03-28
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-03-28
just me or anyone else. i am having the same problem that i finally fixed in 12.10 the google earth splash screen loads and then the program crashes.

---

### Post by tdockery97 on 2013-03-28
Uh, just you?  I just installed it this morning on today's build and it works fine.  You probably aren't getting direct rendering from your video driver.

---

### Post by rburkartjo on 2013-03-28
tdoc tks will see if i can get it to work. did with 12.10; just wanted to make sure it was just me.

---

### Post by rburkartjo on 2013-03-28
get this error message

Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /root/.googleearth/crashlogs/crashlog-51547930.txt

Please include this file if you submit a bug report to Google.

---

### Post by tdockery97 on 2013-03-28
You might try this.  Uninstall the version of Google Earth you currently have.  Then go here: [http://packages.linuxmint.com/list.php?release=Nadia](http://packages.linuxmint.com/list.php?release=Nadia).  Look in the "Import" section for googleearth.  Download the .deb package you need (64 or 32 bit).  Try installing that .deb file.  If Google Earth still doesn't work, it has to be a problem with your video driver.

---

### Post by mcellius on 2013-03-28
I installed it in 13.04 and it's working well.  However, I had previously installed *googleearth-package* from the Software Center and I didn't bother to remove it first, so I don't know if something left over from that install affected the recent one.  Anyway, I ran the following commands and it works fine (64-bit version):

> 
wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb)

(For the 32-bit version, use)

> 
wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)

Then:
> 

sudo dpkg -i google-earth-stable*.deb
> 

sudo apt-get -f install

---

### Post by tdockery97 on 2013-03-28
Glad you got yours working.  Sometimes it's just a matter of missing dependencies.

---

### Post by rburkartjo on 2013-04-11
note i finally got it to work . it was a driver problem.

---

