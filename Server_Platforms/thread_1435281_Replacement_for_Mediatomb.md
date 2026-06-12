---
title: "Replacement for Mediatomb?"
date: 2010-03-21
forum: Server Platforms
---

### Post by kwacka on 2010-03-21
I'm using one of my boxes to serve to a Philips SLA5525 & a Revo Mondo 'internet radio' devices.

Now that xulrunner has been removed from repositories for 10.04, mediatomb media server won't install (dependency upon libmozjs0d not fulfilled - there is a bug report) are there any recommended alternatives?

---

### Post by buntunoob on 2010-03-23
i ran across this looking for your fix [http://forum.boxee.tv/archive/index.php/t-8035.html](http://forum.boxee.tv/archive/index.php/t-8035.html)
it looks like you ned to make sure all the repositories are enabled and then
use the -f switch.

---

### Post by kwacka on 2010-03-24
Many thanks for the pointers -I'll be trying it out

---

### Post by mebunto on 2011-03-31
I know your horse has long bolted however, I successfully installed Mediatomb by downloading the xulrunner debs to the same folder as the package that required them, then then running dpkg.  It's running fine now.

---

