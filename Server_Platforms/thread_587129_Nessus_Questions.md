---
title: "Nessus Questions"
date: 2007-10-22
forum: Server Platforms
---

### Post by americanLoki on 2007-10-22
So I am trying to learn how to use Nessus and I am having some problems on Ubuntu. I was able to install and get both the server and client working just fine on Windows Server 2003. I am currently running Gutsy and am having some problems with updating the plugins on the version included in the repos, or installing version 3. I get 404 errors when trying to update the plugins via the command
```
sudo nessus-fetch --plugins
```
Anybody know where this is pointing? Or where the config file is so I can look myself?

Also has anybody had any luck installing version 3 on Gutsy yet?

Any help or direction would be greatly appreciated.

---

### Post by beertinted on 2007-10-22
I just got it working on gutsy 7.10 - I installed nessus from synaptic (it looks like the package is:nessus_2.2.9-2_i386.deb) then basically followed these steps

[http://linuxpoison.blogspot.com/2007/10/scan-vulnerability-by-using-nessus.html]("http://linuxpoison.blogspot.com/2007/10/scan-vulnerability-by-using-nessus.html")

note, when you register, you'll get an email with a command to issue for linux, use it, except don't include the path (just use 'nessus-fetch --register XXXX-...) and when you register and get all 16k plugins, things slow down a bit, just give it time to load/login. And don't forget to use sudo, or login as root (that's what I did).

edit: I also used this site while installing/researching
[http://www.arsgeek.com/?p=740]("http://www.arsgeek.com/?p=740")

---

### Post by americanLoki on 2007-10-23
I totally forgot about the registration email. After plugging it in and following the links you sent I am all good. Thank you very much.

---

