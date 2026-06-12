---
title: "Hard disk is failing...Can't run commands"
date: 2009-12-07
forum: Server Platforms
---

### Post by volkswagner on 2009-12-07
Hi, all.

I believe my hard disk is failing on Ubuntu Server 8.04.

From messages log.

```
Dec  7 06:07:52 atom kernel: [568512.815310]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  7 06:07:57 atom kernel: [568517.853392] ata3: port is slow to respond, please be patient (Status 0xd0)
Dec  7 06:08:02 atom kernel: [568522.826605] ata3: device not ready (errno=-16), forcing hardreset
Dec  7 06:08:02 atom kernel: [568522.826615] ata3: soft resetting link
Dec  7 06:08:24 atom kernel: [568544.717844] ata3: failed to recover some devices, retrying in 5 secs
Dec  7 06:08:29 atom kernel: [568549.723475] ata3: soft resetting link
Dec  7 06:08:30 atom kernel: [568550.305084] ata3.00: configured for UDMA/133
Dec  7 06:08:30 atom kernel: [568550.305120] ata3: EH complete
Dec  7 06:08:30 atom kernel: [568550.354950] sd 2:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
Dec  7 06:08:30 atom kernel: [568550.355137] sd 2:0:0:0: [sda] Write Protect is off
Dec  7 06:08:30 atom kernel: [568550.355482] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  7 06:25:15 atom -- MARK --
Dec  7 06:26:23 atom kernel: [569603.216923]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  7 06:26:23 atom kernel: [569608.252496] ata3: port is slow to respond, please be patient (Status 0xd0)
Dec  7 06:26:23 atom kernel: [569612.688670] ata3: soft resetting link
Dec  7 06:26:23 atom kernel: [569622.302049] ata3.00: configured for UDMA/133
Dec  7 06:26:23 atom kernel: [569622.302084] ata3: EH complete
Dec  7 06:26:23 atom kernel: [569622.343318] sd 2:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
Dec  7 06:26:23 atom kernel: [569622.343501] sd 2:0:0:0: [sda] Write Protect is off
Dec  7 06:26:23 atom kernel: [569622.344075] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  7 06:32:29 atom kernel: [569987.885702]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  7 06:32:34 atom kernel: [569992.921276] ata3: port is slow to respond, please be patient (Status 0xd0)
Dec  7 06:32:39 atom kernel: [569997.896992] ata3: device not ready (errno=-16), forcing hardreset
Dec  7 06:32:39 atom kernel: [569997.897005] ata3: soft resetting link
Dec  7 06:33:09 atom kernel: [570028.081019] ata3.00: qc timeout (cmd 0xec)
Dec  7 06:33:09 atom kernel: [570028.081033] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec  7 06:33:09 atom kernel: [570028.081071] ata3: failed to recover some devices, retrying in 5 secs
Dec  7 06:33:19 atom kernel: [570038.122356] ata3: port is slow to respond, please be patient (Status 0xd0)
Dec  7 06:33:24 atom kernel: [570043.098072] ata3: device not ready (errno=-16), forcing hardreset
Dec  7 06:33:24 atom kernel: [570043.098082] ata3: soft resetting link
Dec  7 06:33:54 atom kernel: [570073.282101] ata3.00: qc timeout (cmd 0xec)
Dec  7 06:33:54 atom kernel: [570073.282115] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec  7 06:33:54 atom kernel: [570073.282149] ata3: failed to recover some devices, retrying in 5 secs
Dec  7 06:34:04 atom kernel: [570083.323435] ata3: port is slow to respond, please be patient (Status 0xd0)
Dec  7 06:34:09 atom kernel: [570088.299152] ata3: device not ready (errno=-16), forcing hardreset
Dec  7 06:34:09 atom kernel: [570088.299162] ata3: soft resetting link
Dec  7 06:34:39 atom kernel: [570118.483183] ata3.00: qc timeout (cmd 0xec)
Dec  7 06:34:39 atom kernel: [570118.483197] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Dec  7 06:34:39 atom kernel: [570118.483235] ata3.00: disabled
Dec  7 06:34:45 atom kernel: [570124.028387] ata3: port is slow to respond, please be patient (Status 0xd0)
Dec  7 06:34:50 atom kernel: [570129.004105] ata3: device not ready (errno=-16), forcing hardreset
Dec  7 06:34:50 atom kernel: [570129.004116] ata3: soft resetting link

```

When I try to run any commands I get the following errors.

```
eric@atom:~$ netstat
-bash: /bin/netstat: Input/output error
eric@atom:~$ su
Password: 
bash: /usr/bin/groups: Input/output error
bash: /root/.bashrc: Input/output error

```

I can FTP into server, apache seems to be running.

I can't access Webmin, I get the following error.

```
Error - Missing Headers

```

Any suggestions?

---

