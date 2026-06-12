---
title: "scp takes more time to copy and stalls"
date: 2010-09-28
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-28
I am using ubuntu os with 2Mbps link. I'll do scp to the ubuntu cloud servers to copy the .war file which is of 14MB. Before it takes only 2 mins to copy this war file under /tmp of cloud server. Now it takes more than 15 mins.
  While doing scp it is stalled and restarts again. the scp process may look like below

  app1.war                     15%    2320KB  61.3KB/s - stalled -^

  Any tips?. I'm asked to fix this soon. Plz need help.

---

### Post by arrrghhh on 2010-09-28
Have you made sure you're not taking any errors on the circuit?  Ensured that it is running clean?  Have you noticed any other downloads slow on the circuit?

It could also be the far end, but I doubt it.

---

### Post by Thyagaraj on 2010-10-06
sorry it was my ISP's uploading problem and thank you

---

