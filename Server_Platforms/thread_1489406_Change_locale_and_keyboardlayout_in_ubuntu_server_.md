---
title: "Change locale and keyboardlayout in ubuntu server 10.04"
date: 2010-05-21
forum: Server Platforms
---

### Post by ansiktsburk on 2010-05-21
Hello.
I did a install of ubuntu server in vmware (easy install so I was never asked about keyboard layout, etc.) and I got an english keyboard layout (but I really wanted a swedish one, and I think that should have been detected!)
I changed the /etc/default/locale to be 
LANG="sv_SE.UTF-8" 

but that did not help much.
Running dpkg-reconfigure locales
shows:

perl: warning: Setting locale failed
LANGUAGE = unset
LC_ALL = unset
LANG = sv_SE.UFT-8

and it generates a lot of en_XX.UTF-8 locales. No swedish

There is no X installed so I need a command lines solution to this.
Any ideas?

---

### Post by adomenech on 2010-07-22
try
sudo dpkg-reconfigure console-setup

salut
Albert

---

