---
title: "Can Ubuntu help this Conficker infected Windows network?"
date: 2009-11-13
forum: Security
---

### Post by Roasted on 2009-11-13
I work in a large Windows network with Conficker hiding here and there. I'm curious if there's a utility I can load up on my Ubuntu machine and somehow pinpoint which systems are infected so I can run the appropriate scans on those computers and handle them accordingly.

I've heard nmap can handle this, but only the absolute newest version, which comes in a tarball and I'm not overly familiar with how to install them - but I tried make, make install, configure, whatever and nothing worked.

I tried zenmap but I'm not entirely sure I understand how to use it.

What (if anything) can I use to nail this sucker with an Ubuntu system?

---

### Post by Agent ME on 2009-11-14
The version of nmap in Ubuntu 9.10's repository is new enough.

This command will do the trick, replacing <hosts> with the host(s) to scan:
```
nmap -PN -p139,445 -v --script=smb-check-vulns <hosts>
```

---

### Post by Roasted on 2009-11-14
> **Agent ME said:**
> The version of nmap in Ubuntu 9.10's repository is new enough.

This command will do the trick, replacing <hosts> with the host(s) to scan:
```
nmap -PN -p139,445 -v --script=smb-check-vulns <hosts>
```

If 9.10 liked my computer, we'd be golden, but it doesn't - so I'm stickin with 9.04. :(

Is there any way I can mass-scan the hosts instead of using one IP? Can I use the IP range of like 10.0.0.1-255?

---

### Post by withjigs on 2009-11-14
i guess you can use slash notation i.e. 10.0.0.0/24

---

### Post by Agent ME on 2009-11-14
> **Roasted said:**
> I've heard nmap can handle this, but only the absolute newest version, which comes in a tarball and I'm not overly familiar with how to install them - but I tried make, make install, configure, whatever and nothing worked.
What didn't work? Installing nmap shouldn't take anything more than ./configure, make, sudo make install.
> **Roasted said:**
> Is there any way I can mass-scan the hosts instead of using one IP? Can I use the IP range of like 10.0.0.1-255?
You can type in the ip range exactly like that to nmap.

---

