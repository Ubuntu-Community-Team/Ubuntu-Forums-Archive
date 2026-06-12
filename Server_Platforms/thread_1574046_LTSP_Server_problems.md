---
title: "LTSP Server problems"
date: 2010-09-13
forum: Server Platforms
---

### Post by Ensign_Expendable on 2010-09-13
I am trying to test a thin client setup. The server is running Ubuntu 10.04 and is located inside a private vlan, without access to the outside world. There is a mirror inside this vlan that it can use, and updating everything works fine. The problem occurs when I try to build an ltsp-client. Even though I specify the local mirror as the default mirror and the security mirror, the client builder insists on contacting archive.ubuntu.com to get what looks like localization files. Of course it can't succeed, and the client build fails.

Is there a way for me to make it pull this data from the local mirror? Unfortunately, there is no --archive-mirror switch like the --security-mirror one.

---

### Post by bmathis on 2010-09-13
Just a shot in the dark here, but you can try and set a dns entry to point archive.ubuntu.com to the local IP address of your mirror.

---

### Post by Ensign_Expendable on 2010-09-14
Thanks. I've already thought of that, and it won't work due to the rather wonky way the mirror is built. Turns out that redoing the network a bit was the easiest way to handle this. Odd that building an LTSP client locally isn't possible.

---

