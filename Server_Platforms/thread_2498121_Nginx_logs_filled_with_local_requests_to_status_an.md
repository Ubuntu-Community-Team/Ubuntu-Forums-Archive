---
title: "Nginx logs filled with local requests to /status and /server_status"
date: 2024-05-31
forum: Server Platforms
---

### Post by oneseventeen2 on 2024-05-31
I have a dedicated host at IONOS running Ubuntu 22.04 (it came with 20.04 and I did a dist-upgrade), installed nginx from the repo's, enabled let's encrypt with certbot, and installed sematext log monitoring agent.

Everything seems to be going well, but I'm get a request every few seconds to /status and /server status from 127.0.0.1 which makes me think there is a monitoring service installed that I would like to disable or configure properly.

I know I can just create an empty file at the appropriate address, but since I don't know what process is doing this, I don't want to feed bad data to something or open myself to an issue. I also don't want invalid data in my log file.

Should I just add a location block for those paths in my nginx config and disable logging?

---

### Post by currentshaft on 2024-06-03
You could enable user-agent logging or take a packet capture on localhost to see if a UA string is included in the request to determine the application making it.

---

