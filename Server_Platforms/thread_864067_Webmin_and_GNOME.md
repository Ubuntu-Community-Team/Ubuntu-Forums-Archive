---
title: "Webmin and GNOME"
date: 2008-07-19
forum: Server Platforms
---

### Post by sirdeltalot on 2008-07-19
Hi
I have several questions
I have installed ubuntu server 8.04 on my mac using vmware.
I have downloaded webmin and unpacked it but i don't now how to access it. How do i open it from the command line?

also, i downloaded the GNOME desktop but don't know how to start it. Apparently startx works but i typed it in and it couldn't work.

Any answers
Thanks
Iz

---

### Post by windependence on 2008-07-20
```
sudo apt-get install webmin

```

Then, in your browser on another machine:

[https://yourIPaddress:10000](https://yourIPaddress:10000)

Or if you have a GUI on your server, from that machine:

[https://localhost:10000](https://localhost:10000)

You can't just download these packages, you also have to install them. Read up on apt-get. Google is your friend here.

-Tim

---

