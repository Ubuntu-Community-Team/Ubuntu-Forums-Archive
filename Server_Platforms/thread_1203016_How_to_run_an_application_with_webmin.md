---
title: "How to run an application with webmin"
date: 2009-07-02
forum: Server Platforms
---

### Post by user328 on 2009-07-02
Hey,

I am running HLDS (Half Life Dedicated Server), and I want to be able to start it via Webmin. So in order to do that i go to **System>Running** **Processes>Run**. I realize I have to put in the command, but I do not know what exactly I should put.
Here is the command I need to run:
Dir: /home/hlds/hlds_4
Command: ./hlds_run -game cstrike +maxplayers 32

Can anyone tell me what the command should look like?
Thanks

---

### Post by user328 on 2009-07-03
Anyone knows?

---

### Post by windependence on 2009-07-03
Why don't you just ssh in to the server and do:

```
cd /home/hlds/hlds_4

./hlds_run -game cstrike +maxplayers 32
```

Learn a little CLI, it won't hurt you at all, I promise :-)

-Tim

---

### Post by user328 on 2009-07-03
Thanks. I could but I needed someone else to do it using webmin.
Thanks again

---

