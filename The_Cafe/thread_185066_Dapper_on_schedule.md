---
title: "Dapper on schedule?"
date: 2006-05-31
forum: The Cafe
---

### Post by Axier on 2006-05-31
I am just about to choose if we are changing distribution on our next system. I have seen Ubuntu around for a while. My choice stands between RHEL or something else. We went with RH9 earlier. Is Dapper considered stable and do we know en exact date for release?

Is it possible to use RC1 and upgrade to the final release without reinstalling?

Thanks for your time

---

### Post by siimo on 2006-05-31
sure it is possible without reinstalling!

when dapper is out update manager will notify you and you just point and click :KS 

or if you prefer the old fashoned way then run this command as root/sudo:
apt-get update && apt-get upgrade


and you will have final.

---

### Post by GreyFox503 on 2006-05-31
The final release for Dapper Drake is supposed to be June 1st.

---

### Post by Axier on 2006-05-31
[QUOTE=GreyFox503]The final release for Dapper Drake is supposed to be June 1st.[/QUOTE]

Reading in the developer corner, it seem to be quite messy at this time, or is it the normal stage of finalising a shipment? 

1 of June is tomorrow. We are looking for something production stable, is Ubuntu in general stable enough for enterprise running? Does it exist a list of known hardware which has been tested with Ubuntu?

---

### Post by ssam on 2006-05-31
its not perfect on all hardware (but i think its better on more hardware than breezy).

there should be some official release notes tomorrow documenting known bugs and regressions, which will hopefully be fixed soon.

the aim of dapper is that it will be suitable for enterprise grade stuff. but for mission critical you would not want to install on the day of release. you might also be interested in the paid for support.

---

### Post by drogoh on 2006-05-31
[QUOTE=siimo]
or if you prefer the old fashoned way then run this command as root/sudo:
apt-get update && apt-get upgrade
[/QUOTE]

It should be noted that 'dist-upgrade' should be used and not 'upgrade'.  'dist-upgrade' will pull in uninstalled dependencies if need be.

---

