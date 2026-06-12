---
title: "Server constantly Downloading"
date: 2009-02-12
forum: Server Platforms
---

### Post by neomaximus2k on 2009-02-12
Hey guys need some major help here, my ubuntu server for some reason is constantly downloading, I know this as the server is on a virgin media line and they do traffic monitoring, while all other machines are off the line is downloading and then the traffic management kicks in, also if another machine tries to do anything it only has 5Kb to play with its like being on dialup!

I looked at TOP and had a load of dansguardian instances open so i'm thinking this may be the cause but as for removing the software, well their website says it cant be done (typical)

is there any way I can isolate what exactly is causing it? the internet is managed by a wireless router so the server isn't acting as a gateway, need to get it sorted asap as the server is off-line until I can fix it

---

### Post by cdenley on 2009-02-12
If you're not using the server as a gateway, what were you using dansguardian for? If you want to remove it, did you try:
```

sudo apt-get remove dansguardian

```
Are you running a proxy server?
```

sudo netstat -tlnp

```

---

### Post by neomaximus2k on 2009-02-12
No idea i havn't even installed dans guardian myself!! It must have come down with another piece of software.

The server isn't setup to be a proxy server either sadly not at home at present and I dont think the wake on lan is enabled on the server so cant turn it on either

---

