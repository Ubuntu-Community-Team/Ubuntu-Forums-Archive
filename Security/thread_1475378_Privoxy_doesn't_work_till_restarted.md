---
title: "Privoxy doesn't work till restarted?"
date: 2010-05-06
forum: Security
---

### Post by directedition on 2010-05-06
I'm using Ubuntu 10.04 and for some reason, privoxy just won't start properly on startup. I see privoxy is there when I run 'ps -A', but Firefox says that it is refusing connections. When I run 'sudo /etc/init.d/privoxy restart', it restarts and everything is peachy. But for some reason, it just won't start properly on boot. Has anyone run into this?

---

### Post by directedition on 2010-05-06
Appeared to have trouble resolving 'localhost' weird.... anyway, Switched all privoxy config (/etc/privoxy/config) options use 127.0.0.1 instead and it works just fine now. Thanks anyway!

---

