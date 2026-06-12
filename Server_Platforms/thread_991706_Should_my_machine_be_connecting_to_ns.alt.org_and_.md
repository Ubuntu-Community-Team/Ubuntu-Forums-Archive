---
title: "Should my machine be connecting to ns.alt.org and am.net?"
date: 2008-11-24
forum: Server Platforms
---

### Post by phylae on 2008-11-24
I have a file server on my network that is running Ubuntu 7.10. I ignore it for the most part because it just serves my files (and does that quite well). However, today I logged into the server via SSH, and I ran iftop. I had just moved my router and I wanted to see if I was still getting the same network speed.

I saw that my fileserver was connecting to ns.alt.org and am.net. I couldn't figure out from going to those websites why my machine would be connecting to them. I do have it configured to update a dynamic DNS every once in a while, but I didn't tell it to use those websites.

Has someone hijacked my server? Why would my machine be connecting to these sites??

Thanks

---

### Post by spinanicky on 2009-02-02
block the ip's that relate to those two servers. Should anything start acting up on your server then you know a program needs it. If everything stays ok then just leave them blocked.

---

### Post by jerome1232 on 2009-02-02
Does iftop show what program is making the connection?

If not have a peak at netstat, knowing what program is making the connection can help alot in figuring out why there's a connection there.
```
sudo netstat -tap
```

---

### Post by phylae on 2009-02-02
Thanks! It turns out it was clamav. I've got this machine servering files to windows, so I keep that running in the background. I guess it updates itself more often than I thought.

---

