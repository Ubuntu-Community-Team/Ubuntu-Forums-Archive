---
title: "sudo dpkg-scanpackages DOES NOT work??WHY?"
date: 2008-09-09
forum: Security
---

### Post by hammer v2 on 2008-09-09
Hey Guys,

I'm trying to make a BASH script that makes metapackages.

I've hit a problem

I get permission errors when trying to run;
sudo dpkg-scanpackages . /dev/null | sudo gzip -9c > Packages.gz

If I run sudo su or sudo -i first it will work great in the terminal but not in a BASH script (The script stops).

Any Ideas how to get around this? I'm stumped. Thanks!
H.

---

### Post by Titan8990 on 2008-09-09
You can't use sudo in a script. Instead you must run the script with sudo. Remove sudo from your scripts and execute like so (assuming that it is test.sh)

sudo ./test.sh

---

