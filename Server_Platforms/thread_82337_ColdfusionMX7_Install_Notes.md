---
title: "ColdfusionMX7 Install Notes:"
date: 2005-10-26
forum: Server Platforms
---

### Post by Z3K3 on 2005-10-26
Hi,

I've been working on installing CFMX7 on ubuntu-server, I've been having some difficulties, and have worked through a few so I thought I would add a few notes:

- I had to run the installer from within the /tmp directory, when I ran the installer from an outside directory I had some permission errors while it tried to create a folder within /tmp.

-The following library files were required for the "Graphics" service to start, this service is required so the administration interface works after the installation is complete.

apt-get install libxtst6 libxt6 libxp6 libxext6

Agree to any dependancies.

So far thats where I'm at.

---

