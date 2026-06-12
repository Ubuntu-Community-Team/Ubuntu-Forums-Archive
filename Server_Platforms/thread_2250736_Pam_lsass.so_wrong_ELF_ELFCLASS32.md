---
title: "Pam_lsass.so wrong ELF ELFCLASS32"
date: 2014-10-30
forum: Server Platforms
---

### Post by mreidiv on 2014-10-30
So i set up a Linux file server, this is the process; Ubuntu Server 14.04 (x64) clean install,
 set up samba share 
 enabled ssh disabled root login
 set up ufw firewall only ssh,http,and samba
 improve ip security <-- will not respond to ping (ICMP) request
 Install and configure rootkit checkers
 installed calm AV 
 Install Logwatch
 Enabled automatic security updates
 Enable process accounting
 Set up ad with Realm 
 Set up cron job to  rsync 

 I am getting the errors seen in the screen shot. I have googled for  days and tried every method i could find. Does anyone have and  suggestions? I will provide configs or other requested info to help me  solve this issue. Also when i reboot using "reboot" if fails to start  back up half of the time saying it cant mount "sdb1". Any help will be  appreciated.
[ATTACH=CONFIG]257645[/ATTACH]


[B]unable to dlopen:
    /lib/security/pam_lsass.so: Wrong ELF class: ELFCLASS32: 1 time(s)

CRON: Pam unable to dlopen(pam_lsass.so):  /lib/security/pam_lsass.so: Wrong ELF class: ELFCLASS32: 1 time(s)
smbd: Pam unable to dlopen(pam_lsass.so): /lib/security/pam_lsass.so: Wrong ELF class: ELFCLASS32: 117 time(s)
[/B]

---

### Post by Thirtysixway on 2014-11-02
Did you install everything through apt-get/aptitude?  The first thing I can see is that you're using a 64bit install of ubuntu, but it's using ELFCLASS32. Doing some Googling it appears that some 32bit libraries were installed instead of 64bit?

First thing I would try is running 'sudo apt-get install ia32-libs' that will install some 32bit library files that are needed when trying to run 32bit software on a 64bit install.

---

### Post by mreidiv on 2014-11-03
Ok thanks found the answer the server somehow had likewise installed i removed it since i was using realm and the errors are gone.

---

