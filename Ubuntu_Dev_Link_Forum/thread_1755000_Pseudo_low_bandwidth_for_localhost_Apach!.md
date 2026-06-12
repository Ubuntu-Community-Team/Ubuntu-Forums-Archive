---
title: "Pseudo low bandwidth for localhost Apach?!"
date: 2011-05-10
forum: Ubuntu Dev Link Forum
---

### Post by saidbakr on 2011-05-10
Hi,
Is there any way to make localhost Apache seems to be connecting at low speed? I develop some web applications locally, and I want to see how do it work with users connected to the Internet with low speed, let we say 64 Kbs!

---

### Post by saidbakr on 2011-05-10
Thank you. I found the solution. It is **iprelay** try from the command to do the following:

```

iprelay -b64000 8000:localhost:80

```

I supposed that your localhost is running as default at port 80, so we assigned port 8000 to access it @ 64 kbs. So you just need to access it from your browser as [http://localhost:8000](http://localhost:8000), so everything will be loaded as you connected to the net @ 64kbs.

If there is no iprelay installed on your system, the command line will tell you how to get it!

---

