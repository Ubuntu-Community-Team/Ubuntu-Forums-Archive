---
title: "Apt-cacher and sources.list - Same Box"
date: 2008-08-06
forum: Server Platforms
---

### Post by ardugh on 2008-08-06
Hi there,

I'm busy installing apt-cacher on a 8.04.1 server.
Hopefully my question is relevant and understandable.

I understand I must change sources.list on my **clients**.
Is the server on which apt-cacher is running **also a client**? In other words, do I change the apt-cacher server sources.list (in /etc/apt) as well, or leave it as default?

Thanks for reading this and looking forward to a response,
Regards,

---

### Post by Rhubarb on 2008-08-06
Yes, I'm quite sure the apt-cacher machine would also be a client.
That way when the server updates itself, those updates that can be used for other clients can be made available.

I can't quite remember where I read it, but it was on one apt-cacher tutorial that I followed somewhere.

I've configured my play-test server at home this way, and it works very well.

---

### Post by ardugh on 2008-08-06
In other words apt-cacher will pull in the repository regardless of how I set the same box's sources.list?

---

