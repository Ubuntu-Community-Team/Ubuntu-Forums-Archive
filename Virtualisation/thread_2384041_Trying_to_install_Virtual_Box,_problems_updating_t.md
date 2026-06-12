---
title: "Trying to install Virtual Box, problems updating the registry (I think)"
date: 2018-02-01
forum: Virtualisation
---

### Post by joesalmon1985 on 2018-02-01
I get the below error message

```

W: The repository 'https://download.virtualbox.org/virtualbox/debian Xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [https://download.virtualbox.org/virtualbox/debian/dists/Xenial/contrib/binary-amd64/Packages](https://download.virtualbox.org/virtualbox/debian/dists/Xenial/contrib/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

After I run
```
wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add -
wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add - 
```
then
```
sudo apt-get update
```
What am I doing wrong do you think?

---

### Post by QIII on 2018-02-01
Hello!

The URL you are trying to connect to is returning a 404 -- not found.  There is something wrong with that URL, or perhaps the page is down for maintenance.  It does not resolve to an existing resource.

Did you follow the instructions [here]("https://www.virtualbox.org/wiki/Linux_Downloads")?

---

### Post by joesalmon1985 on 2018-02-01
yeah to the letter

---

### Post by coffeecat on 2018-02-01
> **joesalmon1985 said:**
> yeah to the letter

No you didn't. Hint - Xenial &#8800; xenial

---

### Post by joesalmon1985 on 2018-02-02
Okay, now how do I stop anybody ever finding this thread and uncovering what an idiot I am?

---

### Post by QIII on 2018-02-02
Everyone makes human errors.  We wouldn't want to bury this because that would rob the next person with a similar issue of an experience to learn from.

---

