---
title: "Wireshark Interfaces"
date: 2012-08-09
forum: Security
---

### Post by jacobroecker on 2012-08-09
```
jacobroecker@MooseFlix:~$ sudo chgrp admin /usr/bin/dumpcap
chgrp: invalid group: `admin'
jacobroecker@MooseFlix:~$ sudo chmod 750 /usr/bin/dumpcap
jacobroecker@MooseFlix:~$ sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap

```

I'm running 12.04.  Any help would be appreciated.

Because of the error above I get:
```
Couldn't run /usr/bin/dumpcap in child process: Permission denied
```

---

### Post by uRock on 2012-08-10
Bump for move to its own thread.

---

### Post by Soul-Sing on 2012-08-10
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
sudo chgrp admin /usr/bin/dumpcap
sudo -s
groupadd -g wireshark
groupadd -l wireshark
sudo usermod -a -G wireshark <yourname>

---

### Post by jacobroecker on 2012-08-10
Thanks folks.  I changed this line from
```
jacobroecker@MooseFlix:~$ sudo chgrp admin /usr/bin/dumpcap
```
to 
```
jacobroecker@MooseFlix:~$ sudo chgrp myusername /usr/bin/dumpcap
```
and it works just fine.  So, complete code for me

```
sudo apt-get install libcap2-bin wireshark
sudo chgrp myusername /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```

Hope this helps anyone else with the same problem in the future

Thanks folks.

---

