---
title: "Deluge headless issue"
date: 2017-12-01
forum: Server Platforms
---

### Post by timonoj on 2017-12-01
Hi guys,

I installed deluged and set it up on my headless server so it's handled by the clients. But I'm not sure what did I do wrong: If I launch it via $deluged, then it works as expected, and I can login with the client. There's the auth file in the expected place, /home/myuser/.config/deluge/auth, but if I launch it in service mode "sudo service deluged start", it seems to also launch, but I can't connect to it. If I query it with sudo service deluged status, it seems to keep running, but I'm unable to connect via client. I'm thinking the path to the auth might be different if it's done as a service, but I don't seem to find where is it supposed to be looking.

Anyone can help me?

Thanks a lot!

---

