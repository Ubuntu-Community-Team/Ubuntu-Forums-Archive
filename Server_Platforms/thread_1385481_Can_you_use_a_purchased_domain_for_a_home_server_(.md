---
title: "Can you use a purchased domain for a home server (dynamic address)"
date: 2010-01-19
forum: Server Platforms
---

### Post by Morrad on 2010-01-19
I currently have a home server set up with dyndns.org for use as a blog and remote file server.  I want to change this so that I'm on my own domain (which I could purchase through Godaddy or similar).  Is there a way to do this despite being on a dynamic ip address?  I haven't been able to find any solutions that don't involve using some kind of hosted setup.

---

### Post by BobVila on 2010-01-19
You're already doing most of the heavy lifting here. Just go to zone edit or some other free DNS site and register your domain's DNS listing (after you've bought it) to be hosted on their NSes. Once that's done, set up a dynamic update client on your box to update the site in the event that your IP were to change.

---

### Post by Morrad on 2010-01-19
Thank you.  A service such as zone edit is exactly what I was looking for.

---

