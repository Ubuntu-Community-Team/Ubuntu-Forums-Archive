---
title: "system wide proxy settings"
date: 2013-04-13
forum: Ubuntu Development Version
---

### Post by gpredrag on 2013-04-13
I have just upgraded my Ubuntu to 13.04, and noticed that gnome-control-center, network, proxy settings, doesn't offer "apply system wide".
That way proxy settings are not usable to programs that use sudo, like software updater.
I am not sure if this happens in fresh 13.04 instalation or is it result of several upgrades of my machine. Can anyone confirm this?

---

### Post by jferna57 on 2013-04-16
I have the same problem.

---

### Post by jferna57 on 2013-04-16
Today I install the last upgrades an the option "apply system wide" isn't appear. 

I find this link [http://ubuntuportal.com/2012/05/quick-tips-change-system-proxy-settings-via-command-line-in-ubuntu-precise.html](http://ubuntuportal.com/2012/05/quick-tips-change-system-proxy-settings-via-command-line-in-ubuntu-precise.html) with information to change the proxy settings via command line.

---

### Post by ft_ on 2013-04-16
this option exists, I do get it in proxy settings (gnome-shell). Maybe because last updates.

---

### Post by gpredrag on 2013-04-17
> **ft_ said:**
> this option exists, I do get it in proxy settings (gnome-shell). Maybe because last updates.

Yes, it reappeared yesterday, it is mentioned in changelog. It just seemed like weird regression, had to ask if I am only one experiencing it. Everything is fine now.

---

### Post by jferna57 on 2013-04-18
Great!!!!

---

### Post by bash321 on 2013-04-19
what about system proxy settings that have to use authentication?

how would i input system wide proxy settings that require creditentials?

---

### Post by Andryg on 2013-04-23
Ive wrote this script to update apt-get proxy settings with autentication , It can be modified to to work on a network with no authentication aswell
[http://www.linuxhowto.co.za/downloads.html](http://www.linuxhowto.co.za/downloads.html)   ( the rest of the site is stil empty , Just a Hobby Linux site of mine)

---

