---
title: "Wireshark"
date: 2010-04-17
forum: Security
---

### Post by Xeneth on 2010-04-17
I just installed wireshark, and I believe I got it together correctly, but I thing I have a permission issue.  I am unable to see any interfaces to capture from them in which it's due to permissions.  I don't want to run as root, so is there a way to give permissions to my current user so that it can run packet sniffing?

---

### Post by rudihawk on 2010-04-17
> **Xeneth said:**
> I just installed wireshark, and I believe I got it together correctly, but I thing I have a permission issue.  I am unable to see any interfaces to capture from them in which it's due to permissions.  I don't want to run as root, so is there a way to give permissions to my current user so that it can run packet sniffing?

Try running: 

```
sudo wireshark
```

---

### Post by Rubi1200 on 2010-04-17
Hi,
as suggested by another forum user:

sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap

run each command separately and then you should have no problems; worked on my machine very nicely.
Good luck

---

### Post by Xeneth on 2010-04-17
Making a group for it worked like a charm  Thanks Rubi

---

### Post by Rubi1200 on 2010-04-17
No problem!
That is how we learn, by helping each other.
:)

---

