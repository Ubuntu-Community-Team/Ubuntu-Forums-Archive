---
title: "Recommend an easy web filter or firewall"
date: 2012-08-07
forum: Security
---

### Post by bzd454 on 2012-08-07
was hoping to find an easy web filter or firewall that could download a bunch of different blacklists in various forms (hosts file type, Adblocker Plus type, whatever others, etc) and also allow me to easily block countries like Russia and China, allow to blacklist additional sites i choose in form like *.google.com, and lastly has an easy whitelist that will override the autoupdates of the blacklists.

i've tried hosts file but there don't appear to be any good managers on the linux side (with GUI) and i would like to be able to use various adblocker plus lists and malware blacklists as well.

also looked at one of the firewall frontend GUI's and it was still too complicated. guess i'm a dimbulb :)

---

### Post by SeijiSensei on 2012-08-07
The [Squid web proxy]("https://help.ubuntu.com/community/Squid") will do all this, but I wouldn't necessarily call it "easy" to install.  Most of the configuration requires editing the plain-text file /etc/squid/squid.conf.  

There's an extensive system of "access control lists" that let you write filters to match URLs based on a variety of criteria.  There are also pre-built block lists for squid like the one from [Malware Patrol]("http://www.malware.com.br/cgi/submit-agressive?action=list_squid&type=agressive").

---

### Post by bzd454 on 2012-08-07
Thanks.  Sounds like the program i'm looking for. :)

---

### Post by rukiaEnix on 2012-08-08
Squid is the best

---

### Post by Bubbelgum on 2012-08-09
Iam going to hijack this thread for a question, do i need a firewall in Ubuntu or is the threat level so low it's not needed?

*edit* found an answer to my question.

---

### Post by wacky_sung on 2012-08-10
I will suggest you to use [opendns]("http://www.opendns.com/") which is much better to filter out and it can be configured within your router.

---

### Post by mr-woof on 2012-08-12
if you have some old hardware lying around you could use the firewall based distro smoothwall, I've used it for a little while now in front of an windows xp rdp based machine.

---

