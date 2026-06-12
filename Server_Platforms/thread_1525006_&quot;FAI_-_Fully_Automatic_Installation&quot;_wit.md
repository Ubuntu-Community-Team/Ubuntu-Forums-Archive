---
title: "&quot;FAI - Fully Automatic Installation&quot; with ubuntu lucid"
date: 2010-07-06
forum: Server Platforms
---

### Post by surfer on 2010-07-06
i'm trying to install serveral HP Blades using [FAI - Fully Automatic Installation]("http://www.informatik.uni-koeln.de/fai/").

i did some tests and had no problems installing a dell latitude laptop (i386) with FAI.

but i don't get the blades to install. the installation process fails in the initrd already...

did anybody manage to get FAI running with ubuntu lucid on amd64?

---

### Post by surfer on 2010-09-07
i got FAI working now! ...and can recommend it!

---

### Post by HeWhoE on 2010-09-15
What was the issue before, and how did you resolve it? 

I'm preparing to deploy 15 Ubuntu workstations for an public school. Do you recommend FAI for such a deployment?

---

### Post by surfer on 2010-09-15
it took me a very long time to resolve all issues (mostly networking problems). fai is poorly documented, i have to say!

i'm not sure if it's worth he effort for 15 machines... the basic install is quickly done. you might benefit more by installing [puppet]("http://www.puppetlabs.com/") (or something similiar) to keep the configuration of the machines in sync after the install.

---

