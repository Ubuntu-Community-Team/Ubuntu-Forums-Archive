---
title: "Does SSHD attach to shared Memory?"
date: 2014-03-07
forum: Security
---

### Post by Empire-Phoenix on 2014-03-07
Well now this is a little complicated I guess,

Short question before the text wall:

"ipcs -mp" returns
> 
------ Shared Memory Creator/Last-op PIDs --------
shmid      owner      cpid       lpid
0          syslog     2492       25996
32769      gnats      2492       25996
65538      114        2492       25996

Now 25996 is a ssh session, is sshd attaching to shared memory normally? this kinda makes me curious.

Doing a full grep 25996 /proc/*/maps does not result in anything at all, so no more infos available

-------------------------------

Now for the long version:
I'm blacklisted at CBL because of a ebury trojan, since a few hours ago I never was before.

> 
IP Address XXX.XXX.XXX.X is listed in the CBL. It appears to be infected with a spam sending trojan, proxy or some other form of botnet.
It was last detected at 2014-03-06 19:00 GMT (+/- 30 minutes), approximately 17 hours ago.
The host at this IP address is infected with the Ebury Rootkit/Backdoor trojan.
Ebury is a SSH rootkit/backdoor trojan for Linux and Unix-style operating systems. It is installed by attackers on root-level compromised hosts by either replacing SSH related binaries or a shared library used by SSH.
 Ebury infected hosts are used for criminal activities, such as sending out spam emails or hosting exploit kits.


My mailserver is a vm, a few ports like 25 are forwared via iptables
Do I assume right, that if the physical machine is clean, a netstat-nat should see all kind of strange traffic from any infected VM?

How comes that they have not the offending mail? All other blacklist I know can show you the mail that caused the blacklisting, or are there other reasons for the blacklisting possible?

Other stuff done on the physical server:
running rkhunter chkrootkit reveals no infections.
testing the filesize with  "find /lib* -type f -name libkeyutils.so* -exec ls -la {} \;" return "-rw-r--r-- 1 root root 14360 Oct 17  2011 /lib/x86_64-linux-gnu/libkeyutils.so.1.4" so below 15kb wich should be clean.

---

### Post by tomearp on 2014-03-07
Please paste the output of:
```
sudo ipcs -m
```

---

### Post by unspawn on 2014-03-08
> **Empire-Phoenix said:**
> "ipcs -mp" returns
Almost all texts tell you to run 'ipcs -m' and 'ipcs -p' separately because else you can't see the required details like permissions and segment size?..


> **Empire-Phoenix said:**
>  Now 25996 is a ssh session, is sshd attaching to shared memory normally?
SSH'ing from one known clean machine to another should tell you if it does (and no, it doesn't).


> **Empire-Phoenix said:**
>  Doing a full grep 25996 /proc/*/maps does not result in anything at all, so no more infos available
- is it the "real" binary?: 'readlink -f /proc/25996/exe',
- what libs does it use?: ldd `readlink -f /proc/25996/exe`,
- any interesting text embedded?: strings `readlink -f /proc/25996/exe`,
- what does its startup environment tell you?: 'cat -v /proc/25996/environ',
plus check all OpenSSH binaries and related libraries not only for matching hashes but also modification times. 
...plus check your system and daemon logs for anomalies. After all if this is Ebury then root-owned files will have to be replaced.


> **Empire-Phoenix said:**
> testing the filesize with  "find /lib* -type f -name libkeyutils.so* -exec ls -la {} \;" return "-rw-r--r-- 1 root root 14360 Oct 17  2011 /lib/x86_64-linux-gnu/libkeyutils.so.1.4" so below 15kb wich should be clean.
With Linux Security there's no "thinking", "worrying", "maybe" or "should": just *ensure* everything is OK using your package management tools to *verify* integrity. 


> **Empire-Phoenix said:**
> running rkhunter chkrootkit reveals no infections.
Apart from well-documented tell-tale signs and using your package  management tools to verify integrity  [RKH  has signatures]("http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/files/signatures/") (highly experimental tho) since its most recent  release you can run using ClamAV. Note CRT hasn't been updated in years, maybe its developer has abandoned it?..

---

### Post by Empire-Phoenix on 2014-03-10
Hi, sorry for the late answer, first all information asked for/ suggested to do.

> 
XXX@YYY:~$ sudo ipcs -m

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x000016b0 0          news       666        2824816    0                       
0x0000151b 32769      nobody     666        2657776    0                       
0x00001756 65538      backup     666        3014632    0


> 
sudo ipcs -p

------ Shared Memory Creator/Last-op PIDs --------
shmid      owner      cpid       lpid      
0          news       4145       4145      
32769      nobody     4145       4145      
65538      backup     4145       4145      


------ Message Queues PIDs --------
msqid      owner      lspid      lrpid


The 4145 is a sshd with owner root, 



> 
sudo readlink -f /proc/4145/exe
/usr/sbin/sshd





This does not work with the readlink -f in quotes, but without it outputs this
> 
sudo ldd /proc/4145/exe
readlink:
ldd: ./readlink: No such file or directory
-f:
ldd: ./-f: No such file or directory
/proc/4145/exe:
	linux-vdso.so.1 =>  (0x00007fffcdfd7000)
	libwrap.so.0 => /lib/x86_64-linux-gnu/libwrap.so.0 (0x00007f0c0cd81000)
	libpam.so.0 => /lib/x86_64-linux-gnu/libpam.so.0 (0x00007f0c0cb73000)
	libcrypto.so.1.0.0 => /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 (0x00007f0c0c797000)
	libutil.so.1 => /lib/x86_64-linux-gnu/libutil.so.1 (0x00007f0c0c594000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f0c0c37d000)
	libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007f0c0c143000)
	libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007f0c0bf05000)
	libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f0c0bc37000)
	libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f0c0ba32000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f0c0b672000)
	libnsl.so.1 => /lib/x86_64-linux-gnu/libnsl.so.1 (0x00007f0c0b458000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f0c0b253000)
	libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f0c0b02b000)
	libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007f0c0ae23000)
	libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007f0c0ac1e000)
	libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f0c0aa02000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f0c0a7e5000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f0c0cf98000)

[QUOTE]


About the strings, as the list is very long, I cannot see anything unusual, but then I don't know what exactly I should be looking for.

[QUOTE]
sudo cat -v /proc/4145/environ
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@=^@



Well the problem using the package manager is, that ebury seems to modify some md5 and authentification related librarys, so I cannot trust a sucessfull validation
nonetheless I of course did it anyway , and I really don't like the results

> 
LC_ALL=C md5sum -c /var/lib/dpkg/info/*.md5sums | grep -v OK
usr/sbin/update-icon-caches: FAILED
md5sum: WARNING: 1 computed checksum did NOT match

usr/bin/ssh: FAILED
usr/bin/ssh-add: FAILED
md5sum: WARNING: 2 computed checksums did NOT match
usr/sbin/sshd: FAILED
md5sum: WARNING: 1 computed checksum did NOT match
usr/share/vim/vim73/doc/help.txt: FAILED
md5sum: WARNING: 2 computed checksums did NOT match
usr/share/vim/vim73/doc/tags: FAILED


So what I did then,
connect via ssh, kill sshd remove it, install it, change password, jsut to be save remove and install it again, restart server

-> after a restart those shared memory segments are back,

Is there some other way to force reinstall every binary from the repositorys?

I tried to follow this here:
[http://ubuntuforums.org/showthread.php?t=1646925](http://ubuntuforums.org/showthread.php?t=1646925)
but it does not say that any file is invalid. Wich i find a bit suprising seeing the other output.

So I'm still not sure if the server now is infected or not. Either my checks are done wrong or not. Usually I would just reinstall it and be happy, but in this case the server is collocated, and this is not done so easily. So any further suggestion what to do or how to determine if it is infected?

---

### Post by unspawn on 2014-03-10
> **Empire-Phoenix said:**
> ```
 XXX@YYY:~$ sudo ipcs -m
```  - Each segment has write bit set for all.  - Each segment is roughly 3 megs in size.  > **Empire-Phoenix said:**
> any further suggestion what to do or how to determine if it is infected? Please show output of these commands: ```
 stat  /lib/x86_64-linux-gnu/libkeyutils.so.1; debsums openssh-server; debsums openssh-client; debsums [whatever package contains  /lib/x86_64-linux-gnu/libkeyutils.so.1]; ssh -G 2>&1
```  *This may work if you have Rootkut Hunter 1.4.2 though false positives may occur: ```
clamscan -d /var/lib/rkhunter/signatures -r /lib /usr/sbin
```   > **Empire-Phoenix said:**
> Is there some other way to force reinstall every binary from the repositorys? We've only started to determine if the server was subverted so please don't get ahead of things. If it is then realize 0) Ebury is used to sniff credentials and 1) it requires root privileges to replace root-owned files. And apart from what misguided web log and forum posts tell you about "cleaning up" a root compromise basically means Game Over.

---

### Post by tomearp on 2014-03-10
[This page]("https://www.cert-bund.de/ebury-faq") has some methods for determining if you are infected. I don't like the look of your shared memory with 666 permissions. The rootkit is also known to change the owner of shared memory segments to users other than root, which appears consistent with your pasted output.
One is owned by backup; are there any backup-related processes currently running?

FWIW none of the servers I administrate with OpenSSH show any shared memory that can be related back to sshd by PID when I am logged in.

---

### Post by Empire-Phoenix on 2014-03-10
>  stat  /lib/x86_64-linux-gnu/libkeyutils.so.1; debsums openssh-server; debsums openssh-client; debsums [whatever package contains  /lib/x86_64-linux-gnu/libkeyutils.so.1]; ssh -G 2>&1 returns
Return s very long lists of OK so far 

The clamscan command does not work, as that signature file does not exist on my system. Do I have to do a special command to generate it?


The cert-bund page was what  I tried kinda in the beginning, wich is why I mentiond that the file is below 15kb, so maybee clean (or the system is compromised so bad that I cannot even see that anymore correctly :) )
Good thing is that this is just a host for some of my own vm's and it never has contact to the via ssh, so as long as there are no VNC + OCR tools out there they might be save. Well even then as each uses a different unique password, so to do this there must be a breach in the kvm supervisior, not impossible but so far it would be something new.)


Well I kinda feel like the server is screwed, did > ipcs -m | egrep "0x[0-9a-f]+ [0-9]+"|awk '{ if ($6 == 0) { print $2; } }'|xargs -n1 ipcrm -m then restarted, and there are exactly three shared memory segments again, same size but different owner :/

---

### Post by unspawn on 2014-03-12
> **Empire-Phoenix said:**
> returns Return s very long lists of OK so far  No, your output should show more than that. Since you're not posting actual output I can actually do something with there's nothing left to do or say. Good luck!

---

### Post by Empire-Phoenix on 2014-03-12
Well I just got blacklisted at cbl.abuseat.org for havinga rootkit/spammer trojan so I started reinstalling, guess my fears were valid after all.

---

