---
title: "Mutant Hidden Ports"
date: 2014-08-11
forum: Security
---

### Post by actionmystique on 2014-08-11
Hello guys,

Bad news on my system; I've been discovering 4 weird hidden ports which **mutate on system reboot**. Below is an example:

[https://drive.google.com/file/d/0B5fXyIn0-GDFTTFQYW5DajZ6bGc/edit?usp=sharing](https://drive.google.com/file/d/0B5fXyIn0-GDFTTFQYW5DajZ6bGc/edit?usp=sharing)

So far, I've been unable to catch some network communication with them.

**How can a process open some ports and hide its name to various root commands such as netstat, fuser and lsof**?

---

### Post by cogset on 2014-08-11
Maybe wireshark or nmap could be used to see what is going on?

---

### Post by ventrical on 2014-08-11
Go to:

[www.grc.com](www.grc.com)

and run "Shields Up!" and see of there are any ports open or if you are running in stealth mode.

Regards..

---

### Post by ian-weisser on 2014-08-11
> **actionmystique said:**
> How can a process open some ports and hide its name to various root commands such as netstat, fuser and lsof?

A well-behaved service should not do that.
I saw listening ports that shifted sneakily and hid like you describe, I would suspect that my system had been compromised and promptly reinstall.
Hooray for backups.

---

### Post by actionmystique on 2014-08-12
Thanks for all your replies.

@**ventrical**: [stealth mode is a myth]("http://ubuntuforums.org/showthread.php?t=2215873&p=12982045#post12982045")!

@**cogset**: I'm already running wireshark whenever I can, but I have to check and change the port numbers as they shift; so far, the fishing expedition has had no catch!

@**ian-weisser**: I have a strong suspicion over my... ESET antivirus software! What? On linux? Yes I know how it sounds... but I run almost exclusively as root.
I have 2 Android devices which also have ESET antivirus and it's easy to uninstall and reinstall it. So I have been able to confirm that a special feature in this product (namely the "anti-theft") opens a hidden port on the smartphones. And this seems a normal procedure regarding the functionality being set.
However, on the Linux product, there's no such "anti-theft" feature; when I contacted ESET support about this case and clearly asked the question about these hidden ports, they made no comment, which sounds like a... confession! I will try later to uninstall it to check if my suspicion can be confirmed by a fact.

Regarding the backups, they are quite useless until you discover the source of the "infection"...

---

### Post by ian-weisser on 2014-08-12
Glad you seem to have figured it out.

---

### Post by Habitual on 2014-08-12
See [http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/)
for how some processes can hide themselves.

---

### Post by actionmystique on 2014-08-16
Thanks [**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341") for the link. I did not have time to try the advices on my system yet.

However, I have found 2 interesting facts:
- installing ESET NOD32 on a fresh Ubuntu VM shows that the **trial version** of the antivirus is **NOT responsible for the hidden open ports**. My strong suspicion was misleading. I apologize for that.
- running **netstat -tulpe** with the -e option gives some interesting intel on the infection:
[https://drive.google.com/file/d/0B5fXyIn0-GDFbTZJWWVsVXNfLXM/edit?usp=sharing](https://drive.google.com/file/d/0B5fXyIn0-GDFbTZJWWVsVXNfLXM/edit?usp=sharing)

All the ionode numbers are consecutive.

**"ffind -a /dev/sda2 12953"** does not give any result! (ffind comes from sleuthkit).
"File name not found for inode"

 "**ls -iR | grep <inode-number>**" from the root directory with the root credentials gives the following results:
12953 **reserved**
12954 **slabs_cpu_partial**
12955 **total_objects**
12956 **slabs**

Then **"find -name "filename"" >> Malware.txt**" from the root gives several hundreds of files, all within **/sys/kernel/slab**:
Then "**ls -iRl1 < /Malware.txt >> /Malware-2.txt**". A search inside "/Malware-2.txt" with the correct inode numbers gives the following results:

**[B]/sys/kernel/slab**/hugetlbfs_inode_cache: 
12953 -r-------- 1 root root 4096 Aug 16 15:30 reserved
12954 -r-------- 1 root root 4096 Aug 16 15:30 slabs_cpu_partial
12955 -r-------- 1 root root 4096 Aug 16 15:30 total_objects
12956 -r-------- 1 root root 4096 Aug 16 15:30 slabs[/B]

What are these files for and how can they open ports?

---

### Post by uRock on 2014-08-16
> **actionmystique said:**
> Thanks for all your replies.

@**ventrical**: [stealth mode is a myth]("http://ubuntuforums.org/showthread.php?t=2215873&p=12982045#post12982045")!

No, it has been properly defined. 
[http://support.kaspersky.com/anti_hacker/ids?qid=193238713](http://support.kaspersky.com/anti_hacker/ids?qid=193238713)
[http://technet.microsoft.com/en-us/library/dd448557(v=ws.10).aspx](http://technet.microsoft.com/en-us/library/dd448557(v=ws.10).aspx)
[http://www.websense.com/content/support/library/web/v75/wws_install_guide/config_stealth_configuring_for_stealth_mode_linux.aspx](http://www.websense.com/content/support/library/web/v75/wws_install_guide/config_stealth_configuring_for_stealth_mode_linux.aspx)

---

### Post by fugu2 on 2014-08-16
are you runnig avahi-daemon by any chance? I've always seen this exihibate this kinda behavior that your talking about.  if you are running this service, and your not using it you can stop this service:
```

# service avahi-daemon stop

```
(as root)

---

### Post by actionmystique on 2014-08-17
Stopping this service does not close the hidden ports. And I have other simple Ubuntu systems with that service running but not showing this strange behavior.

It must be another demon ;)

---

### Post by fugu2 on 2014-08-17
I had another thought, have you tried the ubuntu package unhide?
```
sudo apt-get install unhide
```

---

### Post by actionmystique on 2014-08-18
Thanks for the tip, fugu2.

_**Unhide**_
[I]unhide -dfmv sys procall brute reverse: no warning
unhide -dfmvr sys procall brute reverse: *no warning*[/I]

_**chkrootkit**_
*chkrootkit*
**suckit** found, but seems to be a false positive (not found by rkhunter)

The following suspicious files and directories were found:  
/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit
[I]Comparing with a healthy comparable system, the same file has been found.
[/I]
_**rkhunter**_
[I]rkhunter --update
rkhunter -c[/I]
Checking for preloaded libraries                [ Warning ]
Warning: Found preloaded shared library: libesets_pac.so, *ESET NOD32*
Checking /dev for suspicious file types         [ Warning ]
Warning: Suspicious file types found in /dev:
          **/dev/.udev/rules.d/root.rules**: ASCII text
          SUBSYSTEM=="block", ENV{MAJOR}=="8", **ENV{MINOR}=="2"**, SYMLINK+="root"
          [I]On healthy system:
          SUBSYSTEM=="block", ENV{MAJOR}=="8", **ENV{MINOR}=="1"**, SYMLINK+="root"[/I]
Checking for hidden files and directories       [ Warning ]
Warning: Hidden directory found: /etc/.java: directory, *but /etc/.java/deployment empty*
Warning: Hidden directory found: /dev/.udev: directory, *also found in healthy system*
Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs', , *also found in healthy system*

**The only suspicious point is within root.rules: I don't know what a minor device number  "2" means.**

---

### Post by actionmystique on 2014-08-19
I have just found the source of therse hidden ports: **NFS Server**!
I have installed **nfs-kernel-server** and all its dependencies on a healthy Ubuntu 14.04 VM, configured the exported filesystems inside /etc/exports, rebooted, and boom: the 4 mysterious ports appeared!

Well, it does not make sense:
[LIST=1]
[*]there already is a port reserved for NFS, 2049: why would there be other ports open for the same purpose, inside non-reserved port range? 
[*]these ports are open on all IP addresses, whereas I have exported the FS to only one local subnet 
[/LIST]

Any suggestions or comments?

---

### Post by actionmystique on 2014-08-20
Epilogue:

No one needs some dynamic/random service ports to be open on his/her system.
The way to make these ports static is explained [here]("https://wiki.debian.org/SecuringNFS").
**_These guidelines should be natively configured on Ubuntu_**.
On top of that, you'll be able to allow in/out all NFS communications with ufw/gufw or any other firewall.

---

### Post by ian-weisser on 2014-08-20
I think you should probably file a bug report for this behavior.
Please subscribe the Ubuntu Security Team to the bug.
I suspect they will take a rather dim view of NFS opening random ports.

---

### Post by Habitual on 2014-08-20
Sorry. it's a little late, but worth the wait... in the future you can see what process has a port open by using
```
lsof -i :<port_number>
```

Skype for instance:
```
lsof -i :63606
COMMAND  PID USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
skype   1941   jj   96u  IPv4 1587782      0t0  TCP *:63606 (LISTEN)
skype   1941   jj   97u  IPv4 1587783      0t0  UDP *:63606 
```

Glad you figured it out!

---

### Post by actionmystique on 2014-08-21
@[**[COLOR=#000000]ian-weisser[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841707"): this strange behavior is not exactly considered as a bug, but I filed a report [here]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1359587").
@[**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341"): the command opening the port remains undisclosed; in fact, "lsof -i  :<port_number" does not return any information at all on these particular ports.
_**Net Activity viewer**_ run as root returns the same kind of information for all ports at once.

---

### Post by Habitual on 2014-08-21
> **actionmystique said:**
> @[**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341"): the command opening the port remains undisclosed; in fact, "lsof -i  :<port_number" does not return any information at all on these particular ports. That is bizarre.

maybe your lsof is a different version?
```
lsof -v
lsof version information:
    revision: 4.86
``` and for comparison...
```

for i in md5sum sha1sum sha256sum ; do $i /usr/bin/lsof  ; done
8bd620061c15e87cce55aec1aa0d7ab6  /usr/bin/lsof
a09e74f493b075c6febaa4fbeb0a59445f404937  /usr/bin/lsof
dd8553477e01410b5f8e955603510ee70c48b679bef6a611b135049bb1cd2080  /usr/bin/lsof
```

---

### Post by matt_symes on 2014-08-21
Hi

NFS was developed back it the '80's when security issues were not so much of an issue for NFS. 

To quote the debian wiki 

> The SunRPC system was designed around the *"trust the remote system"* and the *"make it simple for the admin, use dynamic ports"* paradigm.

This is why is uses dynamic ports.

It very simple to configure it to use static ports that will play nice with a stateful firewall and for further security you have NFSv4 and Kerberos. That's why, in part, Kerberos was developed; although Kerberos can be a pain in the butt to set up.

Have you tried using sudo with lsof and netstat ?

Kind regards

---

### Post by actionmystique on 2014-08-21
@[**[COLOR=#000000]Habitual[/COLOR]**]("http://ubuntuforums.org/member.php?u=504341"): same release and checksums:
root@MSI-GE60-Ubuntu-14:/# lsof -v
lsof version information:
    revision: 4.86

root@MSI-GE60-Ubuntu-14:/# for i in md5sum sha1sum sha256sum ; do $i /usr/bin/lsof  ; done
8bd620061c15e87cce55aec1aa0d7ab6  /usr/bin/lsof
a09e74f493b075c6febaa4fbeb0a59445f404937  /usr/bin/lsof
dd8553477e01410b5f8e955603510ee70c48b679bef6a611b135049bb1cd2080  /usr/bin/lsof

@[**[COLOR=#DD4814][B]matt_symes**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1067998"): we have a different vision of simplicity ;) And yes, all my commands are run as root.

---

### Post by Habitual on 2014-08-21
I thought matt's [answer]("http://ubuntuforums.org/showthread.php?t=2238950&p=13104165#post13104165") explained this anomaly?

---

