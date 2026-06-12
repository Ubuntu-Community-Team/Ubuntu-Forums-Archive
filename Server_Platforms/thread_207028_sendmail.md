---
title: "sendmail"
date: 2006-07-01
forum: Server Platforms
---

### Post by [pl]ice on 2006-07-01
hey, am i correct that i can safely disable sendmail on a unix box? or really does it need running to support the insystem delivery??
thanks

---

### Post by lamego on 2006-07-03
There needs to be an MTA (Mail Transfer Agent) to do the local delivery, but you can set it up binded to the localhost so that it will not be able to get data from the network.

---

### Post by faultyCPU on 2006-07-03
in system delivery wont require any MTA. procmail will do.

---

### Post by [pl]ice on 2006-07-03
yeh, that's what i really need, bind it to the localhost, i.e. to the lo or my eh0 ? would it matter? now i bloody configured it for fake domain, so it's trying to connect on boot up to it, slows everything down, any easy way to configure it?
thanks guys

---

