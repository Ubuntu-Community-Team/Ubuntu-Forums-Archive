---
title: "Apache upgrade in Ubuntu 9.04"
date: 2012-09-24
forum: Server Platforms
---

### Post by rafaelvieira96 on 2012-09-24
Dear, I need to perform the installation of the latest version of apache2. In the current repositories, it was not possible to do this.
 The current version is: 2.2.11, and need for version 2.2.22. what is the way to do that for this distribution.
 thanks

---

### Post by Bachstelze on 2012-09-24
You can look [here](https://launchpad.net/ubuntu/+ppas?name_filter=apache2) to see if a PPA provides it. Otherwise, upgrade to Quantal or install from source.

---

### Post by Cheesemill on 2012-09-25
If you are running a public facing server then you really shouldn't be running 9.04.

9.04 reached end-of-life in Oct 2010 and is no longer supported, you will have received no security updates for all of this time and therefore be wide open to all of the many exploits that have been discovered in the last 2 years.

Please, please, upgrade to a supported version of Ubuntu (either 10.04 or 12.04) instead of continuing to run a vulnerable server.

---

