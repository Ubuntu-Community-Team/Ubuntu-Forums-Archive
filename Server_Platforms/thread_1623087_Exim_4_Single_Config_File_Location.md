---
title: "Exim 4 Single Config File Location"
date: 2010-11-16
forum: Server Platforms
---

### Post by humankind135 on 2010-11-16
Okay, so I have a nice little interface that generates an exim config file and a script on the server to check for changes. Unfort I cant find where to set the config file location.

E.G. I have my script generate the file to /etc/exim/exim4.conf (could be /usr/share/foo/bar.conf just as easily)

How can I point exim in the direction of that file?

Thanks in advance

---

### Post by TSJason on 2010-11-16
Last time I looked at this I think it was /etc/exim4/exim4.conf and I think the config has to be set to not use the split files method.

This page might tell more: [https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4)

---

