---
title: "syscp webui?"
date: 2009-10-12
forum: Server Platforms
---

### Post by kpholmes on 2009-10-12
i just installed syscp from the repositories on a headless server, but how do i get to the the web ui?

---

### Post by kpholmes on 2009-10-12
never mind, i found a fix. for anyone who might have the same problem.

make sure to install all the dependencies, then download the .deb file to the /var/www/ file then insall the .deb file like this

dpkg -i syscp_1.4.2.1_all.deb


then go to the [http://serverip/syscp](http://serverip/syscp) and configure syscp


well i hope this help anyone who might be stuck in the situation i was in
:P

---

