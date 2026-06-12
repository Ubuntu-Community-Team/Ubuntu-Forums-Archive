---
title: "[SOLVED] RKhunter-Multiple File Permissions Changed-/bin/su"
date: 2008-11-15
forum: Security
---

### Post by randy78 on 2008-11-15
Alright, there was an update yesterday that had something to do with passwd (assuming it was to do with the VMbuilder vulnerability posted here: [http://www.ubuntu.com/usn/usn-670-1]("http://www.ubuntu.com/usn/usn-670-1"))

I ran an RKhunter scan today and had multiple warnings come up...
I'm assuming this is because RKhunter was ran after the update, and I understand that the file hash would change because of the new file, but I want to know how to correct this and update the system so these errors don't persist.

I've already ran: sudo updatedb
But after that, I ran RKhunter again, and the errors were still present.

Here are the errors:
```
[15:45:56] /bin/su                                           [ Warning ]
[15:45:56] Warning: The file properties have changed:
[15:45:56]          File: /bin/su
[15:45:56]          Current hash: 48a5cab28938bf1203f390854583b61a3a21d377
[15:45:56]          Stored hash : fb0641d828a93ab17df08e733262d6db1fe4c517
[15:45:56]          Current inode: 690173    Stored inode: 688240
[15:45:56]          Current file modification time: 1226559294
[15:45:56]          Stored file modification time : 1213035031

[15:46:04] /usr/bin/lastlog                                  [ Warning ]
[15:46:04] Warning: The file properties have changed:
[15:46:04]          File: /usr/bin/lastlog
[15:46:04]          Current hash: 40027e152c4592f482a731e90eb5415cf31484ca
[15:46:04]          Stored hash : a559592a93fc50f3660d90b9fc1974f8994602f9
[15:46:04]          Current inode: 158758    Stored inode: 156231
[15:46:04]          Current file modification time: 1226559294
[15:46:04]          Stored file modification time : 1213035031

[15:46:07] /usr/bin/newgrp                                   [ Warning ]
[15:46:08] Warning: The file properties have changed:
[15:46:08]          File: /usr/bin/newgrp
[15:46:08]          Current hash: 243e49e5cc0d4870cd1a425291056f09f3b565f0
[15:46:08]          Stored hash : 863fb21f9e4cc33553778012fd22ba4cf50c4449
[15:46:08]          Current inode: 158759    Stored inode: 156345
[15:46:08]          Current file modification time: 1226559294
[15:46:08]          Stored file modification time : 1213035031

[15:46:08] /usr/bin/passwd                                   [ Warning ]
[15:46:08] Warning: The file properties have changed:
[15:46:08]          File: /usr/bin/passwd
[15:46:08]          Current hash: a20df24d8a8b7970be0081167dcd0663d09ce1da
[15:46:08]          Stored hash : e0f1aaa29d21fde2b63c18129a267b5b326163a9
[15:46:09]          Current inode: 159384    Stored inode: 156406
[15:46:09]          Current file modification time: 1226559291
[15:46:09]          Stored file modification time : 1213035028

[15:46:27] /usr/sbin/groupadd                                [ Warning ]
[15:46:27] Warning: The file properties have changed:
[15:46:27]          File: /usr/sbin/groupadd
[15:46:27]          Current hash: 1cf5376f629acb6393eb920120d7ba4a778ec403
[15:46:27]          Stored hash : c779a59c49f83c8c503a9fc960448253f21d4ca4
[15:46:27]          Current inode: 159388    Stored inode: 158253
[15:46:28]          Current file modification time: 1226559291
[15:46:28]          Stored file modification time : 1213035028

[15:46:28] /usr/sbin/groupdel                                [ Warning ]
[15:46:28] Warning: The file properties have changed:
[15:46:28]          File: /usr/sbin/groupdel
[15:46:28]          Current hash: e1567e1051b2ad21923b48bf49e5ffa2fc4b92ea
[15:46:28]          Stored hash : 25c5a23047c12bab286c0240246f4b12e1a4a7dd
[15:46:28]          Current inode: 159389    Stored inode: 158254
[15:46:28]          Current file modification time: 1226559291
[15:46:28]          Stored file modification time : 1213035028

[15:46:28] /usr/sbin/groupmod                                [ Warning ]
[15:46:29] Warning: The file properties have changed:
[15:46:29]          File: /usr/sbin/groupmod
[15:46:29]          Current hash: 7a82ce60545ddbf3dddfac0fb8503c502f230624
[15:46:29]          Stored hash : 6970642c6d6f6b447f6ac883bf749aa95942c0f9
[15:46:29]          Current inode: 159390    Stored inode: 158255
[15:46:29]          Current file modification time: 1226559291
[15:46:29]          Stored file modification time : 1213035028

[15:46:29] /usr/sbin/grpck                                   [ Warning ]
[15:46:29] Warning: The file properties have changed:
[15:46:29]          File: /usr/sbin/grpck
[15:46:29]          Current hash: 71a2f30f88cd2b45b2738c2728dee2bbc0e5b7c8
[15:46:29]          Stored hash : bad92a89ed925cd04c51d57f7be28475bda663c2
[15:46:29]          Current inode: 159391    Stored inode: 158256
[15:46:30]          Current file modification time: 1226559291
[15:46:30]          Stored file modification time : 1213035028

[15:46:30] /usr/sbin/nologin                                 [ Warning ]
[15:46:30] Warning: The file properties have changed:
[15:46:30]          File: /usr/sbin/nologin
[15:46:30]          Current hash: c77ff7059bb28b299e26e120c7b2f5c16997bc2c
[15:46:31]          Stored hash : 8a9070374223b8fb9836d790ce35669e614a8509
[15:46:31]          Current inode: 158756    Stored inode: 158320
[15:46:31]          Current file modification time: 1226559294
[15:46:31]          Stored file modification time : 1213035031

[15:46:31] /usr/sbin/pwck                                    [ Warning ]
[15:46:31] Warning: The file properties have changed:
[15:46:31]          File: /usr/sbin/pwck
[15:46:31]          Current hash: 8ce0a3042cb92ba5095068c0f7bf946f640d7488
[15:46:31]          Stored hash : 127d9d06265d7758dad7672f95eedf2208266379
[15:46:31]          Current inode: 159395    Stored inode: 158348
[15:46:31]          Current file modification time: 1226559291
[15:46:31]          Stored file modification time : 1213035028

[15:46:33] /usr/sbin/useradd                                 [ Warning ]
[15:46:33] Warning: The file properties have changed:
[15:46:33]          File: /usr/sbin/useradd
[15:46:33]          Current hash: a836bf82da6f1e8d33735ef677107312ba0b235b
[15:46:33]          Stored hash : c06843dcb0aa247baa50f64b53dd92e8c2134a86
[15:46:33]          Current inode: 159398    Stored inode: 158417
[15:46:33]          Current file modification time: 1226559291
[15:46:33]          Stored file modification time : 1213035028

[15:46:33] /usr/sbin/userdel                                 [ Warning ]
[15:46:33] Warning: The file properties have changed:
[15:46:33]          File: /usr/sbin/userdel
[15:46:34]          Current hash: 3f6802229e013d59e9ca76729af2fd27a1ece04e
[15:46:34]          Stored hash : 36bdbf3447087e27795e07197812ad8940e09ecb
[15:46:34]          Current inode: 159399    Stored inode: 158418
[15:46:34]          Current file modification time: 1226559291
[15:46:34]          Stored file modification time : 1213035028

[15:46:34] /usr/sbin/usermod                                 [ Warning ]
[15:46:34] Warning: The file properties have changed:
[15:46:34]          File: /usr/sbin/usermod
[15:46:34]          Current hash: 616aec6adf64cd037b41082505dc3d34047d9773
[15:46:34]          Stored hash : 0e3694793d0b22b384e9b70f57f3e3ee4188b490
[15:46:34]          Current inode: 159400    Stored inode: 158419
[15:46:34]          Current file modification time: 1226559291
[15:46:34]          Stored file modification time : 1213035028

[15:46:35] /usr/sbin/vipw                                    [ Warning ]
[15:46:35] Warning: The file properties have changed:
[15:46:35]          File: /usr/sbin/vipw
[15:46:35]          Current hash: bee92da96d5ab2f37b489d0cb73fabc4c4a62ba2
[15:46:35]          Stored hash : 7f6d6bb3b2a99e41b759b61121ea7fa14e1e19ca
[15:46:35]          Current inode: 159401    Stored inode: 158427
[15:46:35]          Current file modification time: 1226559291
[15:46:35]          Stored file modification time : 1213035028
```

I ran the 'last' command in a terminal, and didn't notice anything out of the norm, other than a 'guest' login on Nov. 3rd, but I have been using the new Guest account feature in Ibex and am assuming that this is related to that.

Also, I don't have anything in my 3rd party repos other than the Intrepid Partner repos, the official VLC nightlies, the medibuntu repo and the Google Picasa repo.

Thanks

---

### Post by lovinglinux on 2008-11-15
I'm afraid I have more warnings than you.

```

[02:16:15] Warning: The file properties have changed:
[COLOR="Red"]**[02:16:15]          File: /bin/login**[/COLOR]
[02:16:15]          Current inode: 612049    Stored inode: 612055
[02:16:15]          Current file modification time: 1226559073
[02:16:15]          Stored file modification time : 1207184931

[02:16:16] /bin/lsmod                                        [ Warning ]
[02:16:16] Warning: The file properties have changed:
[COLOR="Red"]**[02:16:16]          File: /bin/lsmod**[/COLOR]
[02:16:16]          Current hash: be5bd1d2d0e00b4f999cacaa0e47a75db7431976
[02:16:16]          Stored hash : 56f23aee856a79d9bfe663303945cf700323951b
[02:16:16]          Current inode: 612027    Stored inode: 612057
[02:16:16]          Current size: 3952    Stored size: 4344
[02:16:16]          Current file modification time: 1223297493
[02:16:16]          Stored file modification time : 1203974432

[02:16:20] Warning: The file properties have changed:
[02:16:20]          File: /bin/su
[02:16:20]          Current inode: 612051    Stored inode: 612105
[02:16:20]          Current file modification time: 1226559073
[02:16:20]          Stored file modification time : 1207184931

[02:16:30] /usr/bin/lastlog                                  [ Warning ]
[02:16:30] Warning: The file properties have changed:
[02:16:30]          File: /usr/bin/lastlog
[02:16:30]          Current inode: 83382    Stored inode: 82179
[02:16:30]          Current file modification time: 1226559073
[02:16:30]          Stored file modification time : 1207184931

[02:16:33] /usr/bin/newgrp                                   [ Warning ]
[02:16:34] Warning: The file properties have changed:
[02:16:34]          File: /usr/bin/newgrp
[02:16:34]          Current inode: 83535    Stored inode: 82292
[02:16:34]          Current file modification time: 1226559073
[02:16:34]          Stored file modification time : 1207184931

[02:16:34] /usr/bin/passwd                                   [ Warning ]
[02:16:34] Warning: The file properties have changed:
[02:16:34]          File: /usr/bin/passwd
[02:16:34]          Current inode: 85387    Stored inode: 82354
[02:16:34]          Current file modification time: 1226559071
[02:16:34]          Stored file modification time : 1207184929

[02:16:46] /sbin/depmod                                      [ Warning ]
[02:16:46] Warning: The file properties have changed:
[COLOR="Red"]**[02:16:46]          File: /sbin/depmod**[/COLOR]
[02:16:46]          Current hash: 203ea97ff492f25e275bfb0d73bae82fa9b834eb
[02:16:47]          Stored hash : 6ca5c21e2f3a78105f0b9609f85fcd23e2bdc3fb
[02:16:47]          Current inode: 791603    Stored inode: 791542
[02:16:47]          Current size: 31448    Stored size: 45216
[02:16:47]          Current file modification time: 1223297493
[02:16:47]          Stored file modification time : 1203974432

[02:16:49] /sbin/insmod                                      [ Warning ]
[02:16:49] Warning: The file properties have changed:
[COLOR="Red"]**[02:16:49]          File: /sbin/insmod**[/COLOR]
[02:16:49]          Current hash: d0f772ef77188de05edc0076c350e25474eb2450
[02:16:49]          Stored hash : 014396614120829f88a0c82610c13144d8d2c02e
[02:16:49]          Current inode: 791595    Stored inode: 791575
[02:16:49]          Current size: 4632    Stored size: 5740
[02:16:49]          Current file modification time: 1223297493
[02:16:49]          Stored file modification time : 1203974432

[02:16:50] /sbin/lsmod                                       [ Warning ]
[02:16:50] Warning: The file properties have changed:
[COLOR="Red"]**[02:16:50]          File: /sbin/lsmod**[/COLOR]
[02:16:50]          Current hash: be5bd1d2d0e00b4f999cacaa0e47a75db7431976
[02:16:50]          Stored hash : 56f23aee856a79d9bfe663303945cf700323951b
[02:16:50]          Current inode: 791609    Stored inode: 791610
[02:16:50]          Current file modification time: 1226499261
[02:16:50]          Stored file modification time : 1223673775

[02:16:50] /sbin/modinfo                                     [ Warning ]
[02:16:50] Warning: The file properties have changed:
[COLOR="Red"]**[02:16:50]          File: /sbin/modinfo**[/COLOR]
[02:16:50]          Current hash: a04124962db6deecf777ddc35f93b02ec60992e6
[02:16:50]          Stored hash : 313a170da05a5ee9d10e46967f1f472275b46b53
[02:16:50]          Current inode: 791604    Stored inode: 791629
[02:16:50]          Current size: 8652    Stored size: 10872
[02:16:50]          Current file modification time: 1223297493
[02:16:51]          Stored file modification time : 1203974432

[02:16:51] /sbin/modprobe                                    [ Warning ]
[02:16:51] Warning: The file properties have changed:
[COLOR="Red"]**[02:16:51]          File: /sbin/modprobe**[/COLOR]
[02:16:51]          Current hash: da098e64bfe6f64850e49eafa7c46220a52564ca
[02:16:51]          Stored hash : 1fb9823287322bf64584b77d4a91ebf59c74e75a
[02:16:51]          Current inode: 791596    Stored inode: 791630
[02:16:51]          Current size: 19876    Stored size: 26860
[02:16:51]          Current file modification time: 1223297493
[02:16:51]          Stored file modification time : 1203974432

[02:16:51] /sbin/rmmod                                       [ Warning ]
[02:16:52] Warning: The file properties have changed:
[COLOR="Red"]**[02:16:52]          File: /sbin/rmmod**[/COLOR]
[02:16:52]          Current hash: 97de214a061471c80c6ebc9b6cdd0caf77d3467a
[02:16:52]          Stored hash : 45a718f89bdf296e3f68fd4a1a5debd2305cf040
[02:16:52]          Current inode: 791599    Stored inode: 791653
[02:16:52]          Current size: 6672    Stored size: 7800
[02:16:52]          Current file modification time: 1223297493
[02:16:52]          Stored file modification time : 1203974432

[02:16:55] /usr/sbin/groupadd                                [ Warning ]
[02:16:55] Warning: The file properties have changed:
[02:16:55]          File: /usr/sbin/groupadd
[02:16:55]          Current inode: 86070    Stored inode: 86049
[02:16:55]          Current file modification time: 1226559071
[02:16:55]          Stored file modification time : 1207184929

[02:16:56] /usr/sbin/groupdel                                [ Warning ]
[02:16:56] Warning: The file properties have changed:
[02:16:56]          File: /usr/sbin/groupdel
[02:16:56]          Current inode: 86087    Stored inode: 86050
[02:16:56]          Current file modification time: 1226559071
[02:16:56]          Stored file modification time : 1207184929

[02:16:56] /usr/sbin/groupmod                                [ Warning ]
[02:16:56] Warning: The file properties have changed:
[02:16:56]          File: /usr/sbin/groupmod
[02:16:56]          Current inode: 86103    Stored inode: 86051
[02:16:56]          Current file modification time: 1226559071
[02:16:56]          Stored file modification time : 1207184929

[02:16:56] /usr/sbin/grpck                                   [ Warning ]
[02:16:57] Warning: The file properties have changed:
[02:16:57]          File: /usr/sbin/grpck
[02:16:57]          Current inode: 86548    Stored inode: 86052
[02:16:57]          Current file modification time: 1226559071
[02:16:57]          Stored file modification time : 1207184929

[02:16:57] /usr/sbin/nologin                                 [ Warning ]
[02:16:57] Warning: The file properties have changed:
[02:16:57]          File: /usr/sbin/nologin
[02:16:57]          Current inode: 83281    Stored inode: 86103
[02:16:57]          Current file modification time: 1226559073
[02:16:57]          Stored file modification time : 1207184931

[02:16:58] /usr/sbin/pwck                                    [ Warning ]
[02:16:58] Warning: The file properties have changed:
[02:16:58]          File: /usr/sbin/pwck
[02:16:58]          Current inode: 86552    Stored inode: 86128
[02:16:58]          Current file modification time: 1226559071
[02:16:58]          Stored file modification time : 1207184929

[02:16:59] /usr/sbin/useradd                                 [ Warning ]
[02:16:59] Warning: The file properties have changed:
[02:16:59]          File: /usr/sbin/useradd
[02:16:59]          Current inode: 87001    Stored inode: 86191
[02:16:59]          Current file modification time: 1226559071
[02:16:59]          Stored file modification time : 1207184929

[02:16:59] /usr/sbin/userdel                                 [ Warning ]
[02:16:59] Warning: The file properties have changed:
[02:16:59]          File: /usr/sbin/userdel
[02:16:59]          Current inode: 87039    Stored inode: 86192
[02:16:59]          Current file modification time: 1226559071
[02:16:59]          Stored file modification time : 1207184929

[02:17:00] /usr/sbin/usermod                                 [ Warning ]
[02:17:00] Warning: The file properties have changed:
[02:17:00]          File: /usr/sbin/usermod
[02:17:00]          Current inode: 87044    Stored inode: 86193
[02:17:00]          Current file modification time: 1226559071
[02:17:00]          Stored file modification time : 1207184929

[02:17:00] /usr/sbin/vipw                                    [ Warning ]
[02:17:00] Warning: The file properties have changed:
[02:17:00]          File: /usr/sbin/vipw
[02:17:00]          Current inode: 87045    Stored inode: 86200
[02:17:00]          Current file modification time: 1226559071
[02:17:00]          Stored file modification time : 1207184929
```

---

### Post by simonbonner on 2008-11-15
Hi Randy and Loving,

I had the same thing occur and was a little worried at first, before I realized that it was caused by the updates.

You can run `rkhunter --propupd` option to update the file information. This will clear the stored information about the files that rkhunter checks and then replace it with the current information from your system. There is a warning in the man page for rkhunter not to do this unless you are certain that your system has not been compromised.

I reran `rkhunter --check` after doing this and got no warnings.

Cheers...

---

### Post by lovinglinux on 2008-11-16
Thank you very much. But how do I know for sure my system wasn't compromised?

I have a few more warnings then randy78, which is by itself suspicious. Nevertheless, I have installed/configured lirc and other stuff this week and didn't used rkhunter until today.

---

### Post by randy78 on 2008-11-16
Thanks Simon :)

I'm certain enough that my system hasn't been compromised, as I have no services listening for connections and I use strong system passwords.
I was concerned, however, after noticing a dramatic increase in port-scans in my gateway security logs over the past week, but the firewall is enabled and is set to block everything except for web traffic. I'm chalking it up to skiddies who've just discovered Nmap, or a bot-net scanning for victims.

I've also ran Wireshark several times now and haven't noticed any strange activity either.

Take Care :popcorn:

---

### Post by Kinstonian on 2008-11-16
> **lovinglinux said:**
> Thank you very much. But how do I know for sure my system wasn't compromised?

I have a few more warnings then randy78, which is by itself suspicious. Nevertheless, I have installed/configured lirc and other stuff this week and didn't used rkhunter until today.

You could check for all the usual signs of compromise, but if you really are infected with a rootkit then it would obviously make detecting it more difficult.  Some options of determining whether it's a real incident or not are:

1.  Perhaps you could look at the time stamps, for example if /bin/login was modified at the same time you installed lirc then it's probably a false positive.

2.  You could try chkrootkit to see if that finds anything.

3.  You could also check your logs to see if there are any recent suspicious entries.

4.  Since you can't trust a compromised computer (i doubt that's the case) you could remotely monitor network traffic from another computer to see if there are any suspicious connections relating to your computer.

5.  You could also remotely port scan your computer to see if there are any backdoors that a rootkit has hidden.

6.  You could list all of the files on your computer saving it to a file, then boot to Knoppix and list all the files on your HD again and compare the results.  I don't know of any software that lets you do that, but if you find files on your HD from a trusted OS like Knoppix, that didn't show up when you listed all the files on your real OS, that could indicate a rootkit is hiding them. 

The last three options don't rely on a potentially compromised OS, so they are perhaps more trustworthy.

---

### Post by lovinglinux on 2008-11-16
> **randy78 said:**
> Thanks Simon :)

I'm certain enough that my system hasn't been compromised, as I have no services listening for connections and I use strong system passwords.
I was concerned, however, after noticing a dramatic increase in port-scans in my gateway security logs over the past week, but the firewall is enabled and is set to block everything except for web traffic. I'm chalking it up to skiddies who've just discovered Nmap, or a bot-net scanning for victims.

I've also ran Wireshark several times now and haven't noticed any strange activity either.

Take Care :popcorn:

Since you are certain enough that your system hasn't been compromised, I will hijack or thread if you don't mind.

> **Kinstonian said:**
> 1.  Perhaps you could look at the time stamps, for example if /bin/login was modified at the same time you installed lirc then it's probably a false positive.

Unfortunately, I don't have log files of that day, but Synaptic has a record of installed applications, so I compared the time stamps of all files with warnings with the files modified by the update of "login" and "passwd" packages.

All files with warnings that are common between my rkhunter report and the one from randy78, plus "/bin/login" are related to the update of "login" and "passwd" packages and have the same time stamp. So I guess we can trust them.

I still can't verify why the other files have warnings (list below). 

```
/bin/lsmod
/sbin/depmod
/sbin/insmod
/sbin/lsmod
/sbin/modinfo
/sbin/modprobe
/sbin/rmmod
```

They all have the same time stamp:

```
Mon 06 Oct 2008 09:51:33 AM BRT
```

So, is there a way of checking the time stamps of those files in the Ubuntu repository to see if they match?

---

### Post by digitalbrain on 2008-11-16
> **lovinglinux said:**
> 

```
/bin/lsmod
/sbin/depmod
/sbin/insmod
/sbin/lsmod
/sbin/modinfo
/sbin/modprobe
/sbin/rmmod
```

They all have the same time stamp:

```
Mon 06 Oct 2008 09:51:33 AM BRT
```

So, is there a way of checking the time stamps of those files in the Ubuntu repository to see if they match?

Hi. I have the same rkhunter scan results and besides I have  2 or 3 more warnings.  I got worried too when I saw 25 warnings after my scan. I checked the time stamps of those files and i found out that they have been modified at the same time too. I don't know if there is a way to check the time stamps in ubuntu repository but I don't think there is something to worry about. Chkrootkit found nothing extraordinary. So, scan with chkrootkit too if you'd like to. These warnings occurred after the login and password updates as mentioned above. I consider them  false positives as I am a home user and got nothing to do with servers. Nmap scan and netstat results are all clean. But if someone would like to add more information about this issue, it will be appreciated.

---

### Post by lovinglinux on 2008-11-16
> **digitalbrain said:**
> Hi. I have the same rkhunter scan results and besides I have  2 or 3 more warnings.  I got worried too when I saw 25 warnings after my scan. I checked the time stamps of those files and i found out that they have been modified at the same time too. I don't know if there is a way to check the time stamps in ubuntu repository but I don't think there is something to worry about. Chkrootkit found nothing extraordinary. So, scan with chkrootkit too if you'd like to. These warnings occurred after the login and password updates as mentioned above. I consider them  false positives as I am a home user and got nothing to do with servers. Nmap scan and netstat results are all clean. But if someone would like to add more information about this issue, it will be appreciated.

Since you have the same file warnings and time stamps, I guess is safe to assume its update related. Thanks.

---

### Post by cariboo on 2008-11-16
One way to find out if any new users have been logging on is to check lastlog, in a terminal type:

```
last
```

If you see any users logging in that you don't recognize, or you get no results at all, then you may have something to worry about.

Jim

---

### Post by digitalbrain on 2008-11-16
Thank you for the information Jim.  All I can see is my user name and reboot times. No other suspicious or unknown user names. So, everything looks normal.

---

### Post by jmi on 2008-11-18
Hi, 

Apologies if I'm missing something, but this thread is marked as [SOLVED] but I'm not seeing a solution. 

I'm seeing the same rkhunter errors as others on this thread and I've used debsums and dlocate in  conjunction with another installation to 'prove' the files are actually OK[0]. However, what I don't understand is why the warnings have started showing up. Regardless of whether or not the files on everybody's installations are OK, why are the warnings there?

Cheers,
jmi

[0] - Yes, this assumes that the Ubuntu repositories I'm running against haven't been compromised but let's not get ahead of ourselves. We're not all running against gb.archive.ubuntu.com, are we?

---

### Post by digitalbrain on 2008-11-18
Rkhunter understands that the file properties have been changed but does not understand that the changes come from official ubuntu repositories or trusted servers. That is the problem I suppose. If there was a rootkit, then rkhunter would find that rootkit and report it. These are only warnings about the file properties.

---

### Post by Cato2 on 2008-11-23
jmi - I think the reason for the warnings is that rkhunter only checks a very few vulnerable files such as /bin/login, and this is the first time in ages that these files have been updated.

For those who would like to know how to check if a change is OK, here is a "mini HOWTO to investigate rkhunter file-changed warnings".

Here's how to check, with output from my Gutsy 7.10 system - yours may vary but should be similar. This requires dlocate, which itself requires updatedb (normally runs every day on your system, but some people might have uninstalled).

First, install the required packages - best to do this BEFORE you suspect an intrusion, i.e. do it now.  If you are really suspicious, boot from an Ubuntu live CD, though that's more complex to do and will require different commands.  Assuming you are not on a live CD, use:
```
apt-get install updatedb dlocate
```

Now, run the checks on each of the files reported by rkhunter as having changed.  Here I will start with /bin/login:
```

sudo dlocate /bin/login                     # Find which package /bin/login belongs to, package name is first in output lines
sudo aptitude show login | grep Version     # Get current package version
sudo grep ' login ' /var/log/dpkg.log       # Note the spaces

```
This shows the following output:
```

fred@valluga:~# sudo dlocate /bin/login
login: /bin/login
fred@valluga:~# sudo aptitude show login | grep Version
Version: 1:4.0.18.1-9ubuntu0.1
fred@valluga:~# sudo grep 'upgrade login ' /var/log/dpkg.log
2008-11-15 08:44:21 upgrade login 1:4.0.18.1-9 1:4.0.18.1-9ubuntu0.1

```
The date in the dpkg log file should correspond to when you saw the rkhunter warnings.

So far you have only checked /bin/login.  Now you should run the same checks for all the other files named - this isn't as hard as it sounds, as often a single package such as 'login' will have caused many file updates logged by rkhunter.  So you can usually do dlocate only for many files, or maybe do this:
```
cat files-to-be-checked.txt | sudo xargs -n1 dlocate
```
Create files-to-be-checked.txt with one filename on each line, and xargs will run dlocate once for every file.  Only packages not checked already need be checked with the other commands.

**Notes**
dpkg is the tool underlying apt-get, Synaptic, aptitude, etc.  I have used aptitude here because its output is a bit shorter and I normally use it.

To reset file hashes once you are OK about these changes, just run ```
rkhunter --propupd
``` as someone else mentioned.  This will ensure that any future change is flagged, i.e. it starts comparisons from the new files.

Incidentally, even if the Ubuntu archives were compromised, the attacker would also have to compromise the Ubuntu key used to sign packages - otherwise all the 'bad' package updates would be rejected by APT (includes apt-get, also used by aptitude and Synaptic).

---

