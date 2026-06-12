---
title: "Gifar ?"
date: 2008-08-03
forum: Security
---

### Post by Proton Soup on 2008-08-03
[http://it.slashdot.org/article.pl?sid=08/08/01/184220](http://it.slashdot.org/article.pl?sid=08/08/01/184220)

so is ubuntu immune to this attack, or do i need to turn off java in firefox?  sure, my system may not be at risk, but i don't really want others doing crap in my "name" on other sites, either.  what do we need to do to keep people from stealing our cookies?

---

### Post by tamoneya on 2008-08-03
it is not OS dependent so running Ubuntu does not make you immune.  At the moment though it is not in the wild.  But yes you would have to disable java script in order to be 100% safe.

---

### Post by Proton Soup on 2008-08-03
> **tamoneya said:**
> it is not OS dependent so running Ubuntu does not make you immune.  At the moment though it is not in the wild.  But yes you would have to disable java script in order to be 100% safe.

why javascript?  i didn't know it could run java apps.

also, someone here is claiming corporations already use an exploit like this for "legit" employee monitoring.

[http://www.hothardware.com/News/GIFAR_Photos_That_Look_Right_Back_At_You_/](http://www.hothardware.com/News/GIFAR_Photos_That_Look_Right_Back_At_You_/)

---

### Post by Biochem on 2008-08-04
> **Proton Soup said:**
> why javascript?  i didn't know it could run java apps.

Because the Gifar exploit is to embed a javascript inside a gif or other usually innocuous files and fool the server (which sees only a gif) and the client (which sees a javascript). Therefore to protect yourself the best way is to disable javascript.

---

### Post by Proton Soup on 2008-08-04
i guess i'm not getting good information on what exactly this thing is.  do you have a link that would explain it better?

---

### Post by Biochem on 2008-08-04
[http://www.hackaday.com/2008/08/04/the-gifar-image-vulnerability/](http://www.hackaday.com/2008/08/04/the-gifar-image-vulnerability/)

[http://blogs.zdnet.com/security/?p=1619](http://blogs.zdnet.com/security/?p=1619)

---

### Post by Proton Soup on 2008-08-04
> **Biochem said:**
> [http://www.hackaday.com/2008/08/04/the-gifar-image-vulnerability/](http://www.hackaday.com/2008/08/04/the-gifar-image-vulnerability/)

[http://blogs.zdnet.com/security/?p=1619](http://blogs.zdnet.com/security/?p=1619)

thanks for that.  they are saying Java, however, and not Javascript, which are two very different things (half the web sites out there would not even work if i turned off Javascript, including this one).  but it sounds like Sun is working on a temporary patch for the issue, so until then, i'll just keep Java disabled.  i'm not even sure what i'm missing without Java, nothing i've noticed so far.

---

