---
title: "How to remove orphaned network interfaces from Landscape (non-local server)?"
date: 2024-09-27
forum: Server Platforms
---

### Post by cmmrandau on 2024-09-27
Ubuntu Server 24.04.1 LTS. Landscape non-local Cannical server.  


 The Nextcloud AIO docker image backups at midnight and creates new  docker network interfaces, e.g., veth30869f3. Even though the orphaned  interfaces are removed on the server itself, they are still present on  the Landscape network monitoring section in an ever-increasing list of  unused interfaces. How can I remove these? I fear the page will grow to  infinity.

---

