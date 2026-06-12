---
title: "Ubuntu SDK IDE does not start"
date: 2017-11-29
forum: Ubuntu Application Development
---

### Post by adhdluke on 2017-11-29
Hi, I am running Ubuntu MATE 16.04 64-bit.
I installed Ubuntu SDK from the software boutique.
When I start it up, it tells me container backend is not completely initialized, and asks if I want to create a new one. Clicking no doesn't do anything, and when I hit yes, (after inputting root password) it says immediately afterwards:
```
 Stopping containers: All containers stopped. Creating default network bridge .....
 FAILED 
 [COLOR=#ff0000]error: Creating the bridge failed with: not implemented [/COLOR]
 [COLOR=#ff0000]---Task exited with errors, please check the output---[/COLOR]


```
Hitting close brings up an error that says Setting up the container backend failed.
Please help. The account is in the lxd group, and the lxd service is configured and running.
If needed, lshw output is: [https://pastebin.com/V96dtXri](https://pastebin.com/V96dtXri)

---

