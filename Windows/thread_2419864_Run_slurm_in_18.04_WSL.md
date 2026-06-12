---
title: "Run slurm in 18.04 WSL"
date: 2019-05-26
forum: Windows
---

### Post by pri2698 on 2019-05-26
I am following the above instructions to run SLURM. I am using Ubuntu-18.04 on WSL(Windows Subsystem for Linux). However I get the following error:
 * Starting slurm central management daemon slurmctld                                                                                                                                                       [fail]
slurmctld: error: _parse_next_key: Parsing error at unrecognized key: SlurmctldHost slurmctld: error: Parse error in file /etc/slurm-llnl/slurm.conf line 5: "SlurmctldHost=LAPTOP-KKM6C1SN" slurmctld: fatal: Unable to process configuration file
The hostname provided is the output of the command 'hostname -s'. What may be causing this issue ?

---

### Post by howefield on 2019-05-26
Post moved to it's own thread.

---

