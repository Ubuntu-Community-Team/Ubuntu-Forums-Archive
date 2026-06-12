---
title: "apparmor"
date: 2009-02-14
forum: Security
---

### Post by menschtx on 2009-02-14
I followed the instructions for installing apparmor for firefox, but afterwards firefox won't open. I did notice > riting updated profile for /usr/lib/firefox-3.0.6/firefox.sh.
Setting /usr/lib/firefox-3.0.6/firefox.sh to complain mode. 
Then laterSetting /usr/lib/firefox-3.0.6/firefox.sh to enforce mode.
Reloaded SubDomain profiles in enforce mode. How do I change from enforce mode to complain mode?

---

### Post by bodhi.zazen on 2009-02-15
Please see : [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

> # Set complain
[COLOR=green]user@Entropy:~# sudo aa-complain firefox
Setting /etc/apparmor.d/usr.lib.firefox-3.0.4.firefox.sh to complain mode[/COLOR]

# Set enforce
[COLOR=red]user@Entropy:~# sudo aa-enforce firefox
Setting /etc/apparmor.d/usr.lib.firefox-3.0.4.firefox.sh to enforce mode.[/COLOR]Watch your logs for errors and modify your profile. If you run into problems try running 

sudo aa-logprof

logprof will give you a hint at the problem if you are stuck, but does not replace manual editing as it is often overkill.

See also the example profiles posted in the apparmor thread (I go through firefox) as well as this thread :

[http://ubuntuforums.org/showthread.php?p=6353911](http://ubuntuforums.org/showthread.php?p=6353911)

---

### Post by menschtx on 2009-02-21
thank you - got firefox back

---

### Post by phorgan1 on 2009-12-30
I had problems with firefox after I built gcc.  Took me forever to find it.  The problem was that firefox didn't have permissions to load libraries from /usr/local/lib!  I just had to add a line in /etc/apparmor.d/firefox-3.5 (in my case) that said /usr/local/lib/** rm,  I put it right after the one for /usr/lib/** and everything works fine now.  I also couldn't download into the directory /usr/local/downloads, and added a line that said /usr/local/downloads/** rw, and everything was perfect!

---

