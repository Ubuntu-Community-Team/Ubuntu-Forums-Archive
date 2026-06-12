---
title: "Almost locked out of my ubuntu server 8.10"
date: 2009-02-22
forum: Server Platforms
---

### Post by lyssion on 2009-02-22
Hello everyone,
for almost one month i've been running my server smoothly
and had installed samba,ftp,cups,mailserver etc, everything being ok.
Since last night though i cannot connect to my server either through samba, or ssh or ftp...
i get messages like network path not found, server unexpectedly closed connection, The network link was interrupted while negotiating a connection,and once from my laptop running vista(everything else was tested from win xp) i got a msg that the port to use smb wasnt allowing that computer to login...
Which is strange considering i've been doing everything i wanted from any computer so far...

The only bright side is that i can connect to webmin normally and do anything i want there.. I can also login cups and phpmyadmin, and apache... It's strange :S

I first noticed all those problems when i tried to install a 2nd printer to my network using cups, but i have no idea if it could have caused all of this.
I hope everything i wrote makes sense...
And that someone out there could give me a hand to fix this problem as i cannot do anything at all :(

---

### Post by koenn on 2009-02-22
sounds like an authentication problem, which could be caused by anything between you using wrong user names or passwords, over someone has modified the accounts on your server, to your hard disks failing which has rendered the password file unreadable.
Of course it could also be a networking problem.

Maybe if you post accurate descriptions and real error messages, in stead of playing charades, someone might be able to help.

Your log files probably have accurate information on why these services refuse your login. Do you have console access ?

---

### Post by ikonia on 2009-02-22
the fact that your running webmin is a concern, webmin is not compatible or supported through ubuntu.

If webmin is working, but your generic auth isn't, I'd be very concerned about what webmin has done in general.

---

### Post by lyssion on 2009-02-22
> **koenn said:**
> sounds like an authentication problem, which could be caused by anything between you using wrong user names or passwords, over someone has modified the accounts on your server, to your hard disks failing which has rendered the password file unreadable.
Of course it could also be a networking problem.

Maybe if you post accurate descriptions and real error messages, in stead of playing charades, someone might be able to help.

Your log files probably have accurate information on why these services refuse your login. Do you have console access ?

thank you both for your answers.
okay one by one,
i am certainly not using wrong usernames and passwords and i tested with multiple accounts of family. The only case someone else has modified it is if i've been hacked:S (hope its not that).

I would very much like to view the logs too but i don't know where i can find them :(
I can connect my screen to the server and hope i'll be able to authenticate that way, although i can also run any command through webmin (which authenticates me just fine).

Now let's get to the actual error messages:

1) When I try to log in the ftp i have set up first of all i am prompted to enter username and password, and after i do that, no matter which account i try i get the following message:

"The connection to the server was reset while the page was loading.
The network link was interrupted while negotiating a connection. Please try again."

2) When i try to login my mail server through thunderbird, after trying to authenticate again i get:
"Sending of password did not succeed. Mail server 192.168.0.10 responded: Temporary authentication failure."

3) Now when i try to get to my samba shares, first of all i can't even see my server pc at my workgroup's computers anymore and when i manage to do the name has been altered from Homeserver (samba, ubuntu)(homeserver) to just Homeserver. Anyway..when i click on the icon, or type \\192.168.0.10  (i have set it to have static ip)
i get the following message:
" \\Homeserver is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found. "

This time though i wasn't even asked to authenticate.

4) When i try to login with root or any account using putty and connecting via ssh, after i am asked for the password i get the specific message:
"Server unexpectedly closed network connection."

I hope it helps to find a solution..
If you can think of anything else that might help tell me (and perhaps the way to find it, if it's kinda complicated)
Thanks again for your time.

---

### Post by lyssion on 2009-02-22
```
Feb 23 02:20:01 homeserver /USR/SBIN/CRON[9946]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Feb 23 02:20:01 homeserver /USR/SBIN/CRON[9963]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 23 02:30:01 homeserver /USR/SBIN/CRON[10039]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 23 02:39:01 homeserver /USR/SBIN/CRON[10099]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 23 02:40:01 homeserver /USR/SBIN/CRON[10138]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Feb 23 02:40:01 homeserver /USR/SBIN/CRON[10155]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 23 02:50:01 homeserver /USR/SBIN/CRON[10231]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 23 02:58:14 homeserver kernel: [28901.057916] sshd[10340]: segfault at 0 ip 00007f160f5d2dbc sp 00007fff1b861060 error 4 in pam_smbpass.so[7f160f56b000+149000]
Feb 23 03:00:01 homeserver /USR/SBIN/CRON[10351]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Feb 23 03:00:01 homeserver /USR/SBIN/CRON[10365]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 23 03:02:13 homeserver kernel: [29139.069835] proftpd[10437]: segfault at 0 ip 00007fd4ee71bdbc sp 00007ffffb8dd6a0 error 4 in pam_smbpass.so[7fd4ee6b4000+149000]
Feb 23 03:03:17 homeserver kernel: [29203.830554] dovecot-auth[10441]: segfault at 0 ip 00007f187053edbc sp 00007fff7d8a3940 error 4 in pam_smbpass.so[7f18704d7000+149000]
Feb 23 03:03:17 homeserver dovecot: child 10441 (auth-worker) killed with signal 11
Feb 23 03:03:19 homeserver kernel: [29205.361816] dovecot-auth[10444]: segfault at 0 ip 00007fcbec619dbc sp 00007ffff997ea10 error 4 in pam_smbpass.so[7fcbec5b2000+149000]
Feb 23 03:03:19 homeserver dovecot: child 10444 (auth-worker) killed with signal 11
Feb 23 03:04:18 homeserver dovecot: pop3-login: Disconnected (auth failed, 2 attempts): user=<alekos>, method=PLAIN, rip=192.168.0.2, lip=192.168.0.10, TLS
Feb 23 03:09:01 homeserver /USR/SBIN/CRON[10454]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 23 03:10:01 homeserver /USR/SBIN/CRON[10492]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 23 03:11:10 homeserver kernel: [29676.533441] sshd[10545]: segfault at 0 ip 00007f1500b78dbc sp 00007fff0ce050a0 error 4 in pam_smbpass.so[7f1500b11000+149000]
Feb 23 03:13:28 homeserver kernel: [29814.872294] proftpd[10549]: segfault at 0 ip 00007fd4ee71bdbc sp 00007ffffb8dd6a0 error 4 in pam_smbpass.so[7fd4ee6b4000+149000]

```

I found some logs that seem to be from the tests i did just now.. do you think they help at all? will try to dig some more around

---

### Post by lyssion on 2009-02-22
and this is the syslog of the time everything started (or at least when i noticed it):

```


Feb 21 22:18:28 homeserver kernel: [1484444.220043] usb 5-8: new high speed USB device using ehci_hcd and address 3
Feb 21 22:18:28 homeserver kernel: [1484444.377855] usb 5-8: configuration #1 chosen from 1 choice
Feb 21 22:18:28 homeserver kernel: [1484444.385475] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x083A
Feb 21 22:18:28 homeserver kernel: [1484444.608833] usbcore: registered new interface driver libusual
Feb 21 22:18:28 homeserver kernel: [1484444.639266] Initializing USB Mass Storage driver...
Feb 21 22:18:28 homeserver kernel: [1484444.639379] scsi2 : SCSI emulation for USB Mass Storage devices
Feb 21 22:18:28 homeserver kernel: [1484444.639476] usbcore: registered new interface driver usb-storage
Feb 21 22:18:28 homeserver kernel: [1484444.639479] USB Mass Storage support registered.
Feb 21 22:18:28 homeserver kernel: [1484444.641492] usb-storage: device found at 3
Feb 21 22:18:28 homeserver kernel: [1484444.641496] usb-storage: waiting for device to settle before scanning
Feb 21 22:18:33 homeserver kernel: [1484449.640286] usb-storage: device scan complete
Feb 21 22:18:33 homeserver kernel: [1484449.642650] scsi 2:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
Feb 21 22:18:33 homeserver kernel: [1484449.648695] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Feb 21 22:18:33 homeserver kernel: [1484449.648810] sd 2:0:0:0: Attached scsi generic sg2 type 0
Feb 21 22:19:37 homeserver kernel: [1484513.892914] ppdev0: registered pardevice
Feb 21 22:19:37 homeserver kernel: [1484513.930059] ppdev0: unregistered pardevice
Feb 21 22:20:01 homeserver /USR/SBIN/CRON[27119]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Feb 21 22:20:01 homeserver /USR/SBIN/CRON[27142]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 21 22:20:02 homeserver /USR/SBIN/CRON[27156]: (root) CMD (/etc/webmin/cron/tempdelete.pl)
Feb 21 22:20:14 homeserver kernel: [1484550.816169] type=1503 audit(1235247614.697:5): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4343 profile="/usr/sbin/cupsd"
Feb 21 22:20:14 homeserver kernel: [1484550.830605] type=1503 audit(1235247614.717:6): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4343 profile="/usr/sbin/cupsd"
Feb 21 22:20:20 homeserver kernel: [1484556.249637] type=1503 audit(1235247620.127:7): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4343 profile="/usr/sbin/cupsd"
Feb 21 22:20:20 homeserver kernel: [1484556.250409] type=1503 audit(1235247620.137:8): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4343 profile="/usr/sbin/cupsd"
Feb 21 22:20:21 homeserver kernel: [1484557.270735] type=1503 audit(1235247621.157:9): operation="inode_permission" requested_mask="x::" denied_mask="x::" fsuid=0 name="/usr/share/samba/panic-action" pid=27184 profile="/usr/sbin/cupsd"
Feb 21 22:20:21 homeserver kernel: [1484557.272274] cupsd[4343]: segfault at 0 ip 00007faca15c8dbc sp 00007fffae9684c0 error 4 in pam_smbpass.so[7faca1561000+149000]
Feb 21 22:24:20 homeserver kernel: [1484796.605518] sshd[27194]: segfault at 0 ip 00007f6809981dbc sp 00007fff15c0feb0 error 4 in pam_smbpass.so[7f680991a000+149000]
Feb 21 22:24:34 homeserver kernel: [1484810.821525] sshd[27227]: segfault at 0 ip 00007f2444117dbc sp 00007fff503a3640 error 4 in pam_smbpass.so[7f24440b0000+149000]
Feb 21 22:24:56 homeserver kernel: [1484832.311489] sshd[27231]: segfault at 0 ip 00007f853fb64dbc sp 00007fff4bdf3090 error 4 in pam_smbpass.so[7f853fafd000+149000]
Feb 21 22:30:01 homeserver /USR/SBIN/CRON[27300]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 21 22:32:56 homeserver kernel: [1485312.668797] sshd[27359]: segfault at 0 ip 00007fb8d5c5ddbc sp 00007fffe1eec180 error 4 in pam_smbpass.so[7fb8d5bf6000+149000]

```

---

### Post by hictio on 2009-02-22
The segmentation fault errors doesn't look any promising.

- What is this box?
- Does it have outside (internet) access to which services?
- Does it have a firewall running?
- Did you tried running [Root Kit Hunter](http://www.rootkit.nl/projects/rootkit_hunter.html) on it?

---

### Post by lyssion on 2009-02-22
What do you mean what is this box ? :P
It's a home made server, with a gigabyte motherboard and intel celeron cpu.
Yeah it has various services exposed to internet..
ftp, apache, sendmail, voice communication are exposed.
I do have my router's hardware firewall and NAT, no software firewall.
Nope i didn't run rootkit hunter, didn't even know of its existence and thanks for the link :)
I will take a look when i wake up :)

---

### Post by hictio on 2009-02-22
> **lyssion said:**
> What do you mean what is this box ? :P
It's a home made server, with a gigabyte motherboard and intel celeron cpu.
Yeah it has various services exposed to internet..
ftp, apache, sendmail, voice communication are exposed.
I do have my router's hardware firewall and NAT, no software firewall.
Nope i didn't run rootkit hunter, didn't even know of its existence and thanks for the link :)
I will take a look when i wake up :)

JA JA Ja.
Sorry, what I meant by "what is this box?" Is if this is a production $erver, a home server, or a box you just build to learn a bit about Ubuntu :D

---

### Post by lyssion on 2009-02-23
to be honest at first i set it up to be a local file server, but then i got taken away by the multiple capabities of ubuntu (had never tried anything other than windows before), so i started testing everything i wanted :)

---

### Post by lyssion on 2009-02-23
i searched around and found both cause and solution...

in my case the error was caused by cups, somehow corrupting libpam_smbpass

here's a topic that might help others that will encounter the same problem:

[HTML]https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458[/HTML]

---

### Post by koenn on 2009-02-23
yep, I found something similar ( [http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg07505.html](http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg07505.html) ) but couldn't post it until I got home (don't remember my forum password :) )

did you get it fixed ?

---

### Post by lyssion on 2009-02-23
yeah it worked fine :) it was a really nasty bug :S
Thank you all for your time though !!

---

