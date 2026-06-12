---
title: "Will firefox-granparadiso be updated to the current beta release?"
date: 2007-11-21
forum: The Cafe
---

### Post by Old Pink on 2007-11-21
Hi there,

Firefox 3.0 Beta 1 was just released the other day. Will firefox-granparadiso gutsy packages, which are currently in alpha state, be upgraded?

- Matt

---

### Post by philinux on 2007-12-11
Anyone in the know?

---

### Post by Xbehave on 2007-12-11
i doubt it.
installing is fairly simple there may be a howto somewhere but basically
download a nightly (nightlies have come alot further than beta 1)
unpack into /opt/firefox/
sudo ln -s /opt/firefox/firefox /usr/bin/firefoxN
then either manually install you plugins to /opt/firefox/plugins 
or ln -s it to your plugins, mine is pointed at the files in /usr/lib/mozilla/plugins/ and a few others, but there may be a better way of doing
[COLOR="Red"][SIZE="3"]
**_CREATE A NEW PROFILE_**[/SIZE][/COLOR]
start firefox by typing
firefoxN **-P**

p.s it would be nice if canonical did abit more fore the backports repository, but its not really useful in the business work

---

