---
title: "SSH access problem"
date: 2006-02-28
forum: Server Platforms
---

### Post by dqsis on 2006-02-28
Hello Ubuntu friends! 

I am trying to access my laptop at home from my PC at work through SSH.

Then I immidiately get the warning "Port 22 Denied" (or something similar). :???: 

When I take my laptop somewhere else (place other than my home), then SSH works perfect. So I guess the problem has to do with my home port. :confused: 

Do you think port 22 is busy there? Is there a way to use SSH through another port?

Thank you!

---

### Post by mattheweast on 2006-02-28
If you have a router at your home, you'll need to set up port forwarding on port 22, to ensure that incoming packets go to your laptop. Have a look in the router interface and see if you can set it.

---

