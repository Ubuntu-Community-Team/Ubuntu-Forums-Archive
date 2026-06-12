---
title: "update question"
date: 2007-10-05
forum: Server Platforms
---

### Post by ibtexn on 2007-10-05
my ubuntu desktop gets updates seems every day...
what do I need to to to my server  ist is a ssh and web server
with no gui just text

---

### Post by netlogic on 2007-10-05
apt-get update && apt-get upgrade

---

### Post by p_quarles on 2007-10-05
It's also a good idea to open up the repository list,
```
sudo nano /etc/apt/sources.list
```
and comment out all the repos that don't have "security" in the URL. You want your server to be stable and secure, but it doesn't need to be bleeding edge. Commenting out the non-security repos is a good way to ensure you don't get an update that causes problems.

---

### Post by ibtexn on 2007-10-05
thanks guys  I got alot to learn...

---

### Post by netlogic on 2007-10-05
Remember, don't only rely on this site for help. Your search engine is your friend. Linux is going on 11yrs strong, there are insane amount of free documentation posted.

---

