---
title: "RK Hunter Warning advisor"
date: 2018-02-19
forum: Security
---

### Post by fascinus on 2018-02-19
I am a new linux user, I have been using linux 3 months and I found this  program called RK Hunter so I decide to use it to what happend with my  system, but when I check my system:

sudo rkhunter -c

I found 6 warnings, this is the log that I got:

[https://paste.ubuntu.com/p/hR7Rnrhmnv/](https://paste.ubuntu.com/p/hR7Rnrhmnv/)

Someone can help me? :confused:

I don't know what to do, I am using Ubuntu 16.04 
I don't know what other kind of information about my system did you need to help me better, but you can ask without compromise.

---

### Post by yetimon_64 on 2018-02-19
The 6 warnings in the top section you are getting are for applications that have been replaced with a script. I am on 14.04 and when I first used rkhunter those same warnings appeared here as well. This is normal for ubuntu installs.

You can get rid of those warnings by whitelisting them in the file /etc/rkhunter.conf. You will need to open that file as root in a text editor and look for the "SCRIPTWHITELIST" entries. To do so ...
```
sudo -H gedit /etc/rkhunter.conf
```
Normally you don't use sudo with graphical apps however the "-H" switch in use in the above code makes it safe to do so. 
**Edit2:** a better option than "sudo -H" is to use pkexec eg.
```
pkexec gedit /etc/rkhunter.conf
```

When you open the rkhunter.conf file look for the "SCRIPTWHITELIST" entries further down in the file and as a guide I will include my current entries for you to work off ...
> #
# Allow the specified commands to be scripts.
#
# This is a space-separated list of filenames. The option may
# be specified more than once. The option may use wildcard
# characters.
#
SCRIPTWHITELIST=/bin/egrep
SCRIPTWHITELIST=/bin/fgrep
SCRIPTWHITELIST=/bin/which
SCRIPTWHITELIST=/usr/bin/groups
SCRIPTWHITELIST=/usr/bin/ldd
SCRIPTWHITELIST=/usr/bin/lwp-request
SCRIPTWHITELIST=/usr/sbin/adduser
SCRIPTWHITELIST=/usr/sbin/prelink
SCRIPTWHITELIST=/usr/bin/unhide.rb


You can see the 6 entries that appeared in your output are included in my rkhunter.conf file as whitelisted entries. This stops them showing up as they do in your output. Remove (delete) the # symbol at the start of any line required to enable the whitelisting of the entry or add in any lines in the same manner as above for any that don't have a supplied entry.

You also have two more lots of warnings for suspicious /dev files and suspicious shared memory segments further down the report you link to.

The suspicious /dev/ files relate to pulseaudio eg. "/dev/shm/pulse-shm-756206663: data" and 13 more similar entries. Those warnings can be removed by altering the section for "ALLOWDEVFILE".
From my rkhunter.conf file ...
> # Allow the specified files to be present in the /dev directory,
# and not regarded as suspicious.
#
# This is a space-separated list of pathnames. The option may
# be specified more than once. The option may use wildcard
# characters.
#
#ALLOWDEVFILE="/dev/shm/pulse-shm-*"
#ALLOWDEVFILE="/dev/shm/sem.ADBE_*"
ALLOWDEVFILE="/dev/.udev/rules.d/root.rules*"

IF you uncomment the entry **ALLOWDEVFILE="/dev/shm/pulse-shm-*"** by deleting the # symbol at the start of the line then those warnings won't show either. I have not needed to do so on this install yet (Xfce desktop in use NOT unity). I did have a udev related warning for /dev/.udev/rules.d/root.rules* so you can see I've removed the # symbol at the start of the line to remove the warnings in my output.

On 14.04 i do not have the "ipc_shared_mem" test available and do not  know about it and how to remove those warnings. Someone else may have  better advice on that one.


**Edit:** after altering the /etc/rkhunter.conf file remember to save the file, then rerun the rkhunter test to check for any more warnings. Also note at the top of the report you have ...
> No mail-on-warning address configured
From my rkhunter.conf file ...
> # Email a message to this address if a warning is found when the
# system is being checked. Multiple addresses may be specified
# simply be separating them with a space. Setting this option to
# null disables the option.
#
# NOTE: This option should be present in the configuration file.
#
#MAIL-ON-WARNING=me@mydomain   root@mydomain
MAIL-ON-WARNING=root@**<my-installs-hostname>**
I have removed my actual hostname for privacy reasons, put in your system hostname there instead of "<my-installs-hostname>" for the warning regarding mail-on-warning to be removed.

Regards, yeti.

---

### Post by deadflowr on 2018-02-19
*Thread moved to **Security***

---

### Post by fascinus on 2018-02-20
OMG, thank you very much! 
I was pretty worried about it :o

---

### Post by yetimon_64 on 2018-02-20
> **fascinus said:**
> OMG, thank you very much! 
I was pretty worried about it :o

You're welcome, definitely a good idea to configure the program after first use so it gives no further warnings on the second use. Once configured you will get warnings from the top executable section after system updates; the command "**sudo rkhunter --propupd**" will reset such update related warnings.

Warnings from the lower sections (after initial configuration) should be investigated as to what causes them a bit more carefully than the top executables section.

Doesn't seem anything too bad in your results from what I can see. Though as I note in my first post, I am unfamiliar with the "ipc_shared_mem" test in your results. I suspect not running firefox or nautilus and such programs while running rkhunter may improve those particular warnings. 

Regards, yeti.

---

### Post by vasa1 on 2018-02-20
> **yetimon_64 said:**
>  ...
```
sudo -H gedit /etc/rkhunter.conf
```
Normally you don't use sudo with graphical apps however the "-H" switch in use in the above code makes it safe to do so. 
**Edit2:** a better option than "sudo -H" is to use pkexec eg.
```
pkexec gedit /etc/rkhunter.conf
```
...
Hi, why do you prefer *pkexec* over *sudo -H*? I read [here]("https://askubuntu.com/a/961978") that forgetting to include "-H" was one possible drawback.

---

### Post by yetimon_64 on 2018-02-20
> **vasa1 said:**
> Hi, why do you prefer *pkexec* over *sudo -H*? I read [here]("https://askubuntu.com/a/961978") that **forgetting to include "-H" was one possible drawback.**

The OP noted Ubuntu 16.04 in use and forgetting or omitting the "-H"switch with sudo usage is a bit of a risk so I thought under the circumstance pkexec may be a better/safer option to suggest for a graphical app. 

Normally in the past I'd suggest the use of gksu for graphical applications but it is now deprecated in newer releases and has to be specifically installed by the user in 16.04 (no longer in the default installation as far as I'm aware). I've seen it noted elsewhere pkexec is installed by default in 16.04, though I am currently booted into 14.04 when posting in this thread. Cheers, yeti.

---

### Post by vasa1 on 2018-02-20
Thanks, @yeti :)

---

