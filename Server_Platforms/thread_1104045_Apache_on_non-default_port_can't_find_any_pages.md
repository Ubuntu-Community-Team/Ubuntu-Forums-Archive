---
title: "Apache on non-default port can't find any pages"
date: 2009-03-23
forum: Server Platforms
---

### Post by FiberOptix on 2009-03-23
Hey all,

I've set up my apache service to run on a high, unused port number, and also set up Snort/BASE as per the instructions linked to in the security forum. After restarting apache and confirming the service is listening on the desired port (and setting up BASE) I navigate to [http://localhost:](http://localhost:)[port#]/ and see a message that "/" was not found (as opposed to the "It works!" that I should see), and similarly when I visit [http://localhost:](http://localhost:)[port#]/base/ saying that base wasn't found. 

Does anybody know how to fix this? It seems as though after changing the port number I should make some sort of change to the directory tree? I'm not sure.

---

