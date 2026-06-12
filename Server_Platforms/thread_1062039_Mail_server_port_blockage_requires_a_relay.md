---
title: "Mail server port blockage requires a relay?"
date: 2009-02-06
forum: Server Platforms
---

### Post by EvilTchnlgy on 2009-02-06
Although I am relatively well versed in linux and most of the intricacies of running a server, I have had limited exposure to mail server administration. I run a poweredge 6650 server from home running 8.0.4. I was trying to install a groupware server and recently discovered the Comcast must have started blocking port 25 here in south Florida. What are my options to get around this? I don't have access to any servers with the port unblocked to use as a relay and I would really rather not pay for a relay service as it sort of defeats the purpose of running my own mail server...
Thank you in advance =)
I apologize if I posted this in the wrong section

---

### Post by joebeasley on 2009-02-06
You can use the comcast email servers as a relay.  It will require authentication, which means you'll have to read your postfix/sendmail documentation to find out how to set this up.

---

