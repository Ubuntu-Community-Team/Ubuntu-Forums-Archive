---
title: "OpenVZ boot container control"
date: 2009-07-04
forum: Server Platforms
---

### Post by Chafnan on 2009-07-04
Anyone know how to define what openvz containers can start when the server is booted?

I am running Ubuntu 8.04 LTS

---

### Post by gombadi on 2009-07-04
> 
Anyone know how to define what openvz containers can start when the server is booted?


You can set the onboot option to yes or no for each container you want to or don't want to start when the machine boots.

```

vzctl set <container number> --onboot yes --save

```

---

### Post by Chafnan on 2009-07-04
Thank you.

---

