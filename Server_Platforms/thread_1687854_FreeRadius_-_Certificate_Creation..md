---
title: "FreeRadius - Certificate Creation."
date: 2011-02-14
forum: Server Platforms
---

### Post by Roasted on 2011-02-14
So I'm setting up FreeRadius on Ubuntu 10.04.1 and I'm at the point where I'm trying to create a certificate. Evidently if you run sudo make when you're CD'd into the appropriate directory (/usr/share/doc/freeradius/examples/certs) you generate it automatically. I was told I have to edit the client.cnf file, so I edited the bottom of it with the countryName entries, etc. When I ran sudo make it came back with default settings, so I checked server.cnf, bingo. It had generated info from server.cnf in the output I saw in terminal.

SO... I edited server.cnf AND client.cnf accordingly. I ran into another error, saying the countryName field needed to be the same in the CA certificate (FR) and the request(US).

Now I'm lost.

HOW DO I GET FREERADIUS WORKING? :confused::confused::confused:

---

