---
title: "[SOLVED] sudo apt-get install openssh-server is teh failz"
date: 2008-06-18
forum: Server Platforms
---

### Post by dr.krap on 2008-06-18
*********EDIT************

I reinstalled again and everything is fine now. Go figure.


*************************


I just setup a new server and installed ubuntu server on it. That alone was quite the pain, because the install kept failing until I did "expert mode". I'm not sure why that was different, but it worked, so my gripes with that are null.

So anyway, I'm now trying to install the ssh server, which didn't seem to be that big of a problem from what I've read, but things aren't going that smoothly. When I type:

```
sudo apt-get install openssh-server
```

at the prompt, it's telling me that there is an unmet dependency. Some package called libck-connector0.

I've made sure the repositories are right and I've updated the package lists. It didn't help.

Am I being retarded or am I missing something? Any help will be very appreciated.

---

### Post by doogy2004 on 2008-06-18
try ```
sudo apt-get install -f
```

---

### Post by tubezninja on 2008-06-18
What processor architecture are you using (powerPC, x86, x86_64, Itanium, etc)?  And could you give us some details on your server's configuration?

---

### Post by dr.krap on 2008-06-18
> **doogy2004 said:**
> try ```
sudo apt-get install -f
```

no luck

---

### Post by dr.krap on 2008-06-18
> **scaredpoet said:**
> What processor architecture are you using (powerPC, x86, x86_64, Itanium, etc)?  And could you give us some details on your server's configuration?

It's just a P4 Dell Desktop. I had it laying around and I decided to use it to host my website. Currently, I host my site from my main box, but I wanted to move it to a separate machine. I basically just want a simple LAMP setup with ssh so I don't have to keep a monitor on it.

I don't know if that answers your question or not. There's nothing fancy about this "server". :)

---

