---
title: "Suspect port (at least to me)"
date: 2012-10-03
forum: Security
---

### Post by youngunix on 2012-10-03
Hello all, 

From time to time, I do a netstat run to check for suspicious connections.  Yesterday, found this ```
localhost:44952 -> localhost:44952 == ESTABLISHED
```.
Looked up the port number, didn't find helpful info, except it's TCP/UDP.

Does anyone have any info to share about this matter?

Thank you.

---

### Post by 0011235813 on 2012-10-03
> **youngunix said:**
> Hello all, 

From time to time, I do a netstat run to check for suspicious connections.  Yesterday, found this ```
localhost:44952 -> localhost:44952 == ESTABLISHED
```.
Looked up the port number, didn't find helpful info, except it's TCP/UDP.

Does anyone have any info to share about this matter?

Thank you.
It looks like the computer connected with itself. There are some reasons why it may do this, but I doubt it would be anything malicious, since malicious programs have to connect to EXTERNAL addresses to do harm- connecting to yourself isn't putting yourself in any danger.

---

### Post by mr-woof on 2012-10-03
run sudo netstat -lnp, anything interesting/suspect showing?

---

### Post by youngunix on 2012-10-03
> **mr-woof said:**
> run sudo netstat -lnp, anything interesting/suspect showing?

No, just the usual (ssh, avahi, cups,...) my guess is that it just looked outta place. 

Thanks guys

---

