---
title: "software updater utility throws error &quot;not enough disk space&quot;"
date: 2014-04-03
forum: System76 Support
---

### Post by apdobaj on 2014-04-03
I have a Darter Ultra running 13.10 and periodically when I do a software update I get the error (see attached). I learned how to use the apt-get "purge" flag to delete old kernel downloads, but this is a bit of a hassle. Is there an easier way?

---

### Post by mörgæs on 2014-04-03
The screen shot suggested **sudo apt-get clean**. In addition you could try **sudo apt-get autoremove**.

---

