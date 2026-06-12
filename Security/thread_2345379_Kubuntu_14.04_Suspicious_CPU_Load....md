---
title: "Kubuntu 14.04 Suspicious CPU Load..."
date: 2016-12-03
forum: Security
---

### Post by BlacklightHalo on 2016-12-03
I was diddling-around with my computer as usual today and noticed it was acting slower than usual. I added a CPU monitor widget to my desktop to get an idea of how much of that was in-use, and it appears that something is sucking-up at least 50-60% of the processor even when I'm not doing anything with the computer/desktop. This is suspicious to me.

I tried installing/using "chkrootkit" and "rkhunter" as per the advice of a web article about detecting malware, but while chkrootkit came back positive for "suckit," I did some investigating and it looks like that's a common false-positive. rkhunter was apparently not even installed, because when I use

```
sudo lynis audit system
```

I get 

```
sudo: lynis: command not found
```

Here is the [article]("https://www.howtoforge.com/tutorial/how-to-scan-linux-for-malware-and-rootkits/") I was following.

A little extra background: I've recently updated and tried upgrading to the newest Kubuntu LTS distro, but my system seems unable to do it in any of the ways I know. The disc drive is prioritized somewhere other than "first" so I can't run a LiveCD to do it. Saying "Yes, upgrade now" when auto-prompted by the system does apparently nothing, and I'm not sure how to do it with the terminal. Something could have gone wrong in a partially-completed upgrade process, but that's the only thing of which I can think besides "malware," etc.

---

### Post by deadflowr on 2016-12-03
*Thread moved to **Security**.*

lynis and rkhunter are two separate and different programs.
what happens when you run thr rkhunter commands?
basic rkhunter command:
```
sudo rkhunter -c -sk
```
-c checks the file system and -sk skips key press, allowing it to run through without you needing to key press for everytime it asks (which can be a few)
also run
```
rkhunter -h
```
for the rkhunter help overview.

---

### Post by BlacklightHalo on 2016-12-03
The output of

```
sudo rkhunter -c -sk
```

is

```
sudo: rkhunter: command not found.
```
> 
lynis and rkhunter are two separate and different programs.


Is the article to which I linked above then incorrect in saying that Lynis is "formerly rkhunter," or was I not supposed to infer that rkhunter is not the name of it anymore? Or something else? 

In any case, when I ran

```
cd /tmp
wget https://cisofy.com/files/lynis-2.1.1.tar.gz
tar xvfz lynis-2.1.1.tar.gz
mv lynis /usr/local/
ln -s /usr/local/lynis/lynis /usr/local/bin/lynis
```

as instructed by the linked page, I was told that Lynis could not be moved to /usr/local/lynis because permission is denied. After that point, running either the lynis or rkhunter commands are getting me a "command not found" error. I conclude that either neither one was installed, or the system doesn't know they were installed, or they weren't installed in a way that the system can use. I'm open to any other ideas about what may have gone wrong.

Thank you for relocating my thread to the proper section. I didn't know if this was necessarily a security issue, which is why I didn't post it there in the first place.

---

### Post by deadflowr on 2016-12-04
> Is the article to which I linked above then incorrect in saying that Lynis is "formerly rkhunter," or was I not supposed to infer that rkhunter is not the name of it anymore? Or something else? 
The softwares (both actually) author's own words:
[https://linux-audit.com/tools-compared-rkhunter-vs-lynis/]("https://linux-audit.com/tools-compared-rkhunter-vs-lynis/")

That said...
> as instructed by the linked page, I was told that Lynis could not be moved to /usr/local/lynis because permission is denied. After that point, running either the lynis or rkhunter commands are getting me a "command not found" error. I conclude that either neither one was installed, or the system doesn't know they were installed, or they weren't installed in a way that the system can use. I'm open to any other ideas about what may have gone wrong.

It seems like you needed to be running as root to be able to move those extracted files over to the /usr/local folder.

(The linked article mentions needing to be root at the way way top pre-ramble section. But that part only says needed root to run the scanners, not to be root to install.
I can see where you might have not known that.
Articles tend to skip things that the posters take as common, even when they are not. Especially to new users.)

No matter, since as you should already have the files extracted, now you should only need to be root for two commands.
First is the move (mv) command, to make it run as root add sudo to the beginning of that command.
(Double check that you are in the /tmp directory, or the directory where the extracted files are):
```
cd /tmp
sudo mv lynis /usr/local/
```
then run the link creation command with sudo as well
```
sudo ln -s /usr/local/lynis/lynis /usr/local/bin/lynis
```
now it should work as intended.
Hope it helps.

---

### Post by BlacklightHalo on 2016-12-04
The response I get to

```
cd /tmp
sudo mv lynis /usr/local/

```

is

"mv: cannot stat 'lynis': no such file or directory"

*However, I have noticed that my Home directory currently contains a folder called "Lynis." Not sure if that means anything.

---

### Post by deadflowr on 2016-12-04
Oh, yeah, if you rebooted, then it might be gone.
It is the temporary directory...

Should be simple enough to re-wget it, get it?

---

### Post by BlacklightHalo on 2016-12-05
I'm assuming you mean follow the installation steps in the original article again, and then enter the codes you gave me just now?

---

### Post by deadflowr on 2016-12-05
> **BlacklightHalo said:**
> I'm assuming you mean follow the installation steps in the original article again, and then enter the codes you gave me just now?

Yeah, you can either follow the instructions and use the codes I posted (really I only added sudo to the two commands that required it)
```
cd /tmp
wget https://cisofy.com/files/lynis-2.1.1.tar.gz
tar xvfz lynis-2.1.1.tar.gz
**sudo** mv lynis /usr/local/
**sudo** ln -s /usr/local/lynis/lynis /usr/local/bin/lynis
```
Or you can run the whole instructions as root:
```
sudo su
cd /tmp
wget https://cisofy.com/files/lynis-2.1.1.tar.gz
tar xvfz lynis-2.1.1.tar.gz
mv lynis /usr/local/
ln -s /usr/local/lynis/lynis /usr/local/bin/lynis
exit
```
sudo su will switch you to the root user, and allow you to run as root, making it easier to do (no need to enter sudo when you run as root; so less to do).
exit exits the root user back to your normal user.

either method should do it.

Though you should always be extra careful when running as root.
Since being root gives you full unabated access to the entire system, allowing you to change anything on the system.

---

### Post by BlacklightHalo on 2016-12-05
Okay.

Having entered,

```
cd /tmp wget https://cisofy.com/files/lynis-2.1.1.tar.gz
tar xvfz lynis-2.1.1.tar.gz
```

I get this in the terminal...

```
Resolving cisofy.com (cisofy.com)... 2a01:7c8:aab2:209::1, 149.210.134.182
Connecting to cisofy.com (cisofy.com)|2a01:7c8:aab2:209::1|:443... failed: Connection timed out.
Connecting to cisofy.com (cisofy.com)|149.210.134.182|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181099 (177K) [application/octet-stream]
Saving to: &#8216;lynis-2.1.1.tar.gz&#8217;

100%[===================================================================================================>] 181,099      300KB/s   in 0.6s   

2016-12-05 01:13:36 (300 KB/s) - &#8216;lynis-2.1.1.tar.gz&#8217; saved [181099/181099]

(name of computer+my username):/tmp$ tar xvfz lynis-2.1.1.tar.gz
```

The ending appears to just be the name of the installation file for lynis. I've never seen this as a result before,
so I waited a few minutes to see if it had more processing to do. It didn't move, so I entered the next line of code,

```
sudo mv lynis /usr/local/
```

and

```
tar (child): lynis-2.1.1.tar.gzsudo: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
```

was the result. So I re-entered the code starting with the "cd /tmp" and got as far as the result that seems to be the
installation file's name. I hit "enter" thinking maybe it was a next step that I needed to approve in order to complete
installation. This returned,

```
lynis/CHANGELOG
lynis/CONTRIBUTIONS.md
lynis/CONTRIBUTORS                                                                                                                           
lynis/FAQ                                                                                                                                    
lynis/INSTALL                                                                                                                                
lynis/LICENSE                                                                                                                                
lynis/README                                                                                                                                 
lynis/db/                                                                                                                                    
lynis/db/integrity.db                                                                                                                        
lynis/db/sbl.db                                                                                                                              
lynis/db/fileperms.db                                                                                                                        
lynis/db/malware-susp.db                                                                                                                     
lynis/db/malware.db
lynis/db/hints.db
lynis/default.prf
lynis/extras/
lynis/extras/README
lynis/extras/files.dat
lynis/extras/lynis.spec
lynis/extras/systemd/
lynis/extras/systemd/lynis.service
lynis/extras/systemd/lynis.timer
lynis/extras/openbsd/
lynis/extras/openbsd/+CONTENTS
lynis/extras/check-lynis.sh
lynis/extras/bash_completion.d/
lynis/extras/bash_completion.d/lynis
lynis/extras/.bzrignore
lynis/extras/build-lynis.sh
lynis/include/
lynis/include/helper_audit_dockerfile
lynis/include/profiles
lynis/include/tests_malware
lynis/include/tests_containers
lynis/include/tests_accounting
lynis/include/parameters
lynis/include/tests_ssh
lynis/include/tests_time
lynis/include/tests_firewalls
lynis/include/tests_nameservices
lynis/include/binaries
lynis/include/tests_webservers
lynis/include/tests_squid
lynis/include/tests_storage_nfs
lynis/include/tests_insecure_services
lynis/include/tests_scheduling
lynis/include/tests_tooling
lynis/include/tests_hardening
lynis/include/tests_networking
lynis/include/tests_custom.template
lynis/include/report
lynis/include/tests_boot_services
lynis/include/functions
lynis/include/tests_memory_processes
lynis/include/tests_file_permissions
lynis/include/helper_update
lynis/include/tests_file_integrity
lynis/include/tests_shells
lynis/include/tests_databases
lynis/include/tests_homedirs
lynis/include/osdetection
lynis/include/tests_ldap
lynis/include/tests_ports_packages
lynis/include/tests_logging
lynis/include/tests_mail_messaging
lynis/include/tests_banners
lynis/include/tests_crypto
lynis/include/tests_kernel
lynis/include/tests_mac_frameworks
lynis/include/tests_solaris
lynis/include/tests_virtualization
lynis/include/tests_kernel_hardening
lynis/include/tests_snmp
lynis/include/tests_authentication
lynis/include/tests_filesystems
lynis/include/tests_storage
lynis/include/data_upload
lynis/include/tests_printers_spools
lynis/include/tests_php
lynis/include/consts
lynis/lynis
lynis/lynis.8
lynis/plugins/
lynis/plugins/README
lynis/plugins/custom_plugin.template
```

so I entered

```
sudo mv lynis /usr/local/
```

this seemed to execute without any formal confirmation, just returned me to the command-prompt. So I followed-up with

```
sudo ln -s /usr/local/lynis/lynis /usr/local/bin/lynis
```

and the same thing happened. So I entered,

```
sudo rkhunter -c -sk
```

which returned,

```
sudo: rkhunter: command not found
```

I'm starting to get really aggravated with this thing...

---

### Post by BlacklightHalo on 2016-12-05
It occurred to me to look-up a simple command that would show me basically the same thing I'd get for "Ctrl+Alt+Del" in Windows, so I did that and found the "top" command. I've been looking-over the result, and nothing seems to be using-up much of the processor, but then again CPU usage has recently mysteriously dropped back to the usual 6-20%. I don't know if this means the problem has resolved itself or if it tells us anything else useful, but I thought I would mention it.

---

### Post by deadflowr on 2016-12-05
Sorry.
I do not think I was particularly clear on this:
rkhunter and lynis are completely different things.

I originally posted the rkhunter commands because your original post ran:
> rkhunter was apparently not even installed, because when I use
```
sudo lynis audit system
```
I get 
```
sudo: lynis: command not found
```
So my original response was to actually run the rkhunter commands, to see if rkhunter was installed.
It was not...

But then we jumped down the rabbit hole to try to fix the installation problem for lynis.

You now seem to have lynis installed, so you can try running the lynis commands
```
 sudo lynis audit system
```
Installing lynis does not also install rkhunter.

If you also want to install rkhunter simply run
```
sudo apt-get install rkhunter
```
You should then be able to run the rkhunter commands.
Simple enough, I think.

That said,
Glad the cpu usage has/had dropped.
Kubuntu comes with a nice graphic system monitor usually call KDE system monitor, or system monitor (Not sure what it's called in the kubuntu menu)

(It's true name is ksysguard:[https://userbase.kde.org/KSysGuard]("https://userbase.kde.org/KSysGuard")
I find it easier for novice users to use and understand, rather then terminal monitors like top, which require a little more learning, in my opinion.)

Hopefully with the knowledge of the tools such as top and ksysguard you can more readily find any rogue processes next time.

Again sorry for any confusion.
I hope this makes more sense.

---

### Post by BlacklightHalo on 2016-12-05
I believe I have found the culprit. Using the "top" command during a time when the CPU was running unusually high, I found the process "clamscan" using 50-100% of the CPU. I had set Clam AV to scan the hard drive daily awhile ago, but always assumed that function wasn't working because I never saw any GUI pop up to show that it was carrying-out said task. I'm disabling daily scans, and if that solves the problem, then I'll mark this thread as solved.

Thank you for your help. No need to apologize. Actually, I'm sorry if my lack of understanding has been frustrating for you.

---

