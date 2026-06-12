---
title: "Unable to Update"
date: 2010-06-27
forum: Ubuntuzilla
---

### Post by NightTiger2 on 2010-06-27
Hello

I don't know if this is directly related to Ubuntuzilla, but i have installed it and now when I try to update Firefox thru the Check For Updates I get this:

[IMG]http://img202.imageshack.us/img202/3973/screenshotwug.png[/IMG]

help please?

---

### Post by witeshark17 on 2010-06-27
See this [ thread](http://ubuntuforums.org/showthread.php?t=1518611)

---

### Post by NightTiger2 on 2010-06-27
I"m still trying to figure out what I need to do actually: the package firefox-mozilla-build in the synaptic version 3.6.6 is Firefox version 3.6.6 and I just need to install it?

---

### Post by nanotube on 2010-06-27
> **NightTiger2 said:**
> I"m still trying to figure out what I need to do actually: the package firefox-mozilla-build in the synaptic version 3.6.6 is Firefox version 3.6.6 and I just need to install it?

yes, just install the latest firefox-mozilla-build (which is 3.6.6) from the ubuntuzilla repo, restart firefox, and that's all.

---

### Post by NightTiger2 on 2010-06-27
that gives me this error

"E: /var/cache/apt/archives/firefox-mozilla-build_3.6.6-0ubuntu1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox 0"

---

### Post by nanotube on 2010-06-27
> **NightTiger2 said:**
> that gives me this error

"E: /var/cache/apt/archives/firefox-mozilla-build_3.6.6-0ubuntu1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox 0"

Hi
well it appears that your earlier install was not from the ubuntuzilla repository... did you by any chance use the ubuntuzilla script?

---

### Post by NightTiger2 on 2010-06-27
Yes I have that's what I figured out from the instruction , bad move?

---

### Post by nanotube on 2010-06-28
> **NightTiger2 said:**
> Yes I have that's what I figured out from the instruction , bad move?

yea script is now deprecated, instead use the repository (if you're on 32bit).
i'd suggest to use the script to uninstall, then install using the repo.

the latest instructions are always on the ubuntuzilla website, [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by NightTiger2 on 2010-06-28
Ok all fixed, thanks nanotube :)

---

### Post by nanotube on 2010-06-28
> **NightTiger2 said:**
> Ok all fixed, thanks nanotube :)

great :)

---

### Post by houndi on 2010-08-26
There you need to change the settings. the settings can be downloaded in google, there are no settings obtained oautomatically

---

