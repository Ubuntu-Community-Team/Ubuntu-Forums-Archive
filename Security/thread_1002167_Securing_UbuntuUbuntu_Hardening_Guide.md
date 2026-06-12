---
title: "Securing Ubuntu/Ubuntu Hardening Guide"
date: 2008-12-04
forum: Security
---

### Post by Vantrax on 2008-12-04
Ive built this up over a while as part of some personal documentation for work use and figured it may be of use to other people. I have no idea where half this came from, but if you recognize some tips of yours contact me at admin at matthewlye dot com and ill add some credits to this, I'm sure most of the tips are widely documented.

A more regularly updated version can be found here: [http://www.matthewlye.com/index.php/ubuntu-sec](http://www.matthewlye.com/index.php/ubuntu-sec)

For more general tips and ideas check the Ubuntu Security by that genius bodhi.zazen at [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

First things first if you just want something quick and fast here are the big three:

Reconfiguring shared memory
Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:
· tmpfs /dev/shm tmpfs defaults,ro 0 0

Disabling SSH root login
Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:
· PermitRootLogin yes to PermitRootLogin no

Limiting access to the "su" program (this is done by default in Ubuntu)
*****MAKE SURE YOU ARE PART OF THE ADMIN GROUP****
Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:
· sudo chown root:admin /bin/su sudo
· chmod 04750 /bin/su

System/Server Hardening Checklist

Here is the larger recommended list (although most are not necessary unless your looking at a server or lab environments).

1. Disk Partitions and Mounting

1. Separate /home, /tmp, /var/tmp from /root partitions (If only if the machine has frequent access from general user except administrator).
2. Change mount options in /etc/fstab to limit user access on appropriate filesystems.
· Using noexec instead prevents execution of binaries on a file system

This is not good if you have programs to be executed Data partitions are good for this. Its used often for partitions serving Apache.

· Using nosuid will prevent the setuid bit from having effect.

SUID stands for Set User ID. This means that if the SUID bit is set for any application then your user ID would be set as that of the owner of application/file rather than the current user, while running that application. That means in case I have an application whose owner is ' root ' and it has its SUID bit set, then when I run this application as a normal user, that application would still run as root. Since the SUID bit tells Linux that the the User ID root is set for this application and whenever this application executes it must execute as if root was executing it (since root owns this file). Disabling this for a drive prevents this operation.

· The nodev option prevents use of device files on the filesystem.

This option would be recommended for CDs and NTFS file systems generally speaking. But it can have options to lock down a system preventing breaching by simply creating hda1 or sda1 devices that are writable by all.

2. Physical Security
Typically used in lab environments or where a server in not in a completely secured location.

1. Configure BIOS.
· Disable booting from CDs/DVDs, floppies, and external devices.
· Set BIOS password to protect the settings.
2. Set a password for the GRUB bootloader.
· Generate a password hash using the command / /usr/sbin/grub-md5-crypt. Add the hash to the first line of /boot/grub/menu.lst as follows:
password --md5 passwordhash
· Remove rescue-mode boot section from /boot/grub/menu.lst

3. Keep Software Up to Date
Upgrade through the Ubuntu Repository Network to apply upgrade automatically. Security updates should be applied as soon as possible.
Create the file apt.cron, make it executable, place it in /etc/cron.daily or /etc/cron.weekly, and ensure that it reads as follows:

#!/bin/sh
/usr/bin/apt-get update

This can have a side effect of breaking some dependencies.

4. Detecting listening network ports & Closing open ports and services
Detecting listening network ports
For a list of network ports that are open you can use the following commands:

# netstat -tulp or lsof -i -n | egrep 'COMMAND|LISTEN|UDP' or just a port scanner (nmap) 9

Closing open ports and services
To get a list of running services you can execute the following command: sysv-rc-conf --list | grep on
To disable a running service you can execute the command: sysv-rc-conf service name off
and then you should stop this service from running by executing: /etc/init.d/service stop.

5. Disable SUID and SGID Binaries
To find SUID and SGID files on the system, use the following command:

# find / \( -perm -4000 -o -perm -2000 \) &#8211;print

SUID or SGID bits safely disabled (using chmod -s filename) unless required for other program.

6. Configure and Use TCP Wrapper
Configure the TCP Wrapper library to protect network daemons that support its use by adding appropriate rules to /etc/hosts.allow and /etc/hosts.deny.

NOTE: tcp wrappers only works for services that inetd starts. Sendmail, apache, and named do not use inetd, and so they are not protected via tcp wrappers.

7. Configure and Use AppArmor
AppArmor is installed and loaded by default in Hardy. Some packages will install their own enforcing profiles. Active profiles for LAM Server:
· usr.sbin.mysqld
· usr.sbin.apache2
All activity will be logged by auditd and saved to /var/log/audit/audit.log

Some excellent advice on this is available in the stickies threads here.


8. Rdate or NTP (To keep your server date up to date)
Create the file /etc/cron.d/rdate with the following line:
15 * * * * root /usr/sbin/rdate -s content

for NTP
Create the file /etc/cron.d/ntp with the following line:
15 * * * * root /usr/sbin/ntpdate server

9. Configure or Disable SSH
- Disable it when not required.
- If SSH is required, ensure the SSH configuration includes the following lines:

· PermitRootLogin no
· Protocol 2

- If possible, limit SSH access to a subset of users. Create a group called sshusers and only add the users that need remote access. Then, add the following line to /etc/ssh/sshd_config:

· AllowGroups sshusers

Edit /etc/group find sshusers and add allowed users.

10. Disable IPv6
- Disable it when not required.
Edit the following line from /etc/modprobe.d/aliases:

· Find the line: alias net-pf-10 ipv6
· Edit this to: alias net-pf-10 off ipv6
· Save the file and reboot

11. Disable Compile ·
Add compiler group: /usr/sbin/groupadd compiler
· Move to correct directory: cd /usr/bin
· Make most common compilers part of the compiler group

chgrp compiler *cc*
chgrp compiler *++*
chgrp compiler ld
chgrp compiler as

· Set access on mysqlaccess

chgrp root mysqlaccess

· Set permissions

chmod 750 *cc*
chmod 750 *++*
chmod 750 ld
chmod 750 as
chmod 755 mysqlaccess

· To add users to the group, modify /etc/group and change compiler:123: to compiler:123:username1,username2 ('123' will be different on your installation)

12. Root Notification
Edit .bashrc under /root to get notified by email when someone logs in as root and add the following:
echo 'ALERT - Root Shell Access (Server Name) on:' `date` `who` | mail -s "Alert: Root Access from `who | cut -d"(" -f2 | cut -d")" -f1`" [email]admin@myhost.com[/email]

13. Securing History
chattr +a .bash_history (append)
chattr +I .bash_history
Get your users know that their history is being locked and they will have to agree before they use your services.

14. Using Welcome Message
Edit /etc/motd and put the following banner to be displayed:

WARNING !!!
This computer system including all related equipment, network devices (specifically including Internet access), are provided only for authorized use.
Unauthorized use may subject you to criminal prosecution. By accessing this system, you have agreed to the term and condition of use and your actions will be monitored and recorded. &#9633;

15. Chmod dangerous files
chmod 700 /bin/ping
chmod 700 /usr/bin/who
chmod 700 /usr/bin/w
chmod 700 /usr/bin/locate
chmod 700 /usr/bin/whereis
chmod 700 /sbin/ifconfig
chmod 700 /bin/nano
chmod 700 /usr/bin/vi
chmod 700 /usr/bin/which
chmod 700 /usr/bin/gcc
chmod 700 /usr/bin/make
chmod 700 /usr/bin/apt-get
chmod 700 /usr/bin/aptitude

16. Specify TTY Devices Root is allowed
vi /etc/securetty
Leave only two connections:
tty1
tty2

17. Choose a secure password
This is generally a good tip, this fix however applies to people using pam to authenticate to LDAP or AD.

vi /etc/pam.d/common-password
change the detail from this:
password requisite pam_unix.so nullok obscure md5
to
password requisite pam_unix.so nullok obscure md5 min=8
Change min=8 with your company password policy length.

18. Checking for Rootkits
Install it from Ubuntu Repository:
# apt-get install chkrootkit
You can run it with the following command: ./chkrootkit
Now we are going to add it to contrab to schedule daily automatic scans in the system:
vi /etc/cron.daily/chkrootkit.sh and type
#!/bin/bash
# Enter the directory where the rootkit is installed
cd /root/chkrootkit/
# Enter your email address where you want to receive the report
./chkrootkit | mail -s "Daily chkrootkit from Server Name" [email]admin@myhost.com[/email]

Now change the file permissions so we can run it: chmod 755 /etc/cron.daily/chkrootkit.sh
To give it a try you can run the chkrootkit.sh file manually from /etc/cron.daily directory and you should receive a report to the email account you provided.

19. Hardening your Kernel (sysctl.conf)
Instead of doing this manually use a pre hardened kernel like selinux.

20. Disable unnecessary PHP variables
Edit /etc/php5/apache2/php.ini and /etc/php5/cli/php.ini

Turn off these variables:

allow_call_time_pass_reference = Off
magic_quotes_gpc = Off
register_long_arrays = Off
register_argc_argv = Off
allow_url_fopen = Off
expose_php = Off
disable_functions = symlink,shell_exec,proc_close,
proc_open,dl,passthru,
escapeshellarg,escapeshellcmd,openlog, apache_child_terminate,
apache_get_modules,apache_get_version,
apache_getenv,apache_note,apache_setenv,virtual, phpinfo

21. Apache Hardening
- Edit /etc/apache2/apache.conf

- Turn off these variables:
TraceEnable off
- (Disable apache root access)
[directory\]
Order deny,allow
Deny from all
[/directory]

- Enable Module ( /etc/apache2/mods-enable/ ):

alias, auth_basic, authn_file, authz_default, authz_groupfile, authz_host, authz_user, autoindex, dir, env, mime, mod-security2, negotiation, php5, rewrite, setenvif, ssl, unique_id

- Edit /etc/php.ini

Find disable functions and edit as below:
disable_functions = exec, passthru, shell_exec, system, proc_open, popen, curl_exec, curl_multi_exec, parse_ini_file, show_source

Hardened Kernel Variables ( /etc/sysctl.conf )

# Controls the System Request debugging functionality of the kernel
kernel.sysrq = 0

# Controls whether core dumps will append the PID to the core filename.
# Useful for debugging multi-threaded applications.
kernel.core_uses_pid = 1

#Prevent SYN attack
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_synack_retries = 2

# Disables IP source routing
net.ipv4.conf.lo.accept_source_route = 0
net.ipv4.conf.eth0.accept_source_route = 0
net.ipv4.conf.default.accept_source_route = 0

# Enable IP spoofing protection, turn on source route verification
net.ipv4.conf.eth0.rp_filter = 1

# Disable ICMP Redirect Acceptance
net.ipv4.conf.lo.accept_redirects = 0
net.ipv4.conf.eth0.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0

# Enable Log Spoofed Packets, Source Routed Packets, Redirect Packets
net.ipv4.conf.lo.log_martians = 1
net.ipv4.conf.eth0.log_martians = 1

# Disables IP source routing
net.ipv4.conf.lo.accept_source_route = 0
net.ipv4.conf.eth0.accept_source_route = 0
net.ipv4.conf.default.accept_source_route = 0

# Enable IP spoofing protection, turn on source route verification
net.ipv4.conf.eth0.rp_filter = 1

# Disable ICMP Redirect Acceptance
net.ipv4.conf.lo.accept_redirects = 0
net.ipv4.conf.eth0.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0

# Modify system limits for Ensim WEBppliance
fs.file-max = 65000

# Decrease the time default value for tcp_fin_timeout connection
net.ipv4.tcp_fin_timeout = 15

# Decrease the time default value for tcp_keepalive_time connection
net.ipv4.tcp_keepalive_time = 1800

# Turn off the tcp_window_scaling
net.ipv4.tcp_window_scaling = 0

# Turn off the tcp_sack ( Need to turn on for traffic to internet)
#net.ipv4.tcp_sack = 0

# Turn off the tcp_timestamps
net.ipv4.tcp_timestamps = 0

# Enable TCP SYN Cookie Protection
net.ipv4.tcp_syncookies = 1

# Set maximum amount of memory allocated to shm to 256MB
kernel.shmmax = 268435456

# Increase the maximum total TCP buffer-space allocatable
net.ipv4.tcp_mem = 57344 57344 65536

# Increase the maximum TCP write-buffer-space allocatable
net.ipv4.tcp_wmem = 32768 65536 524288

# Increase the maximum TCP read-buffer space allocatable
net.ipv4.tcp_rmem = 98304 196608 1572864

# Increase the maximum and default receive socket buffer size
net.core.rmem_max = 524280
net.core.rmem_default = 524280

# Increase the maximum and default send socket buffer size
net.core.wmem_max = 524280
net.core.wmem_default = 524280

# Increase the tcp-time-wait buckets pool size
net.ipv4.tcp_max_tw_buckets = 1440000

# Allowed local port range
net.ipv4.ip_local_port_range = 16384 65536

# Increase the maximum memory used to reassemble IP fragments
net.ipv4.ipfrag_high_thresh = 512000
net.ipv4.ipfrag_low_thresh = 446464

# Increase the maximum amount of option memory buffers
net.core.optmem_max = 57344

---

### Post by hyper_ch on 2008-12-05
> **Vantrax said:**
> Disabling SSH root login
    Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:
    · PermitRootLogin yes to PermitRootLogin no

Why? Root is not activated and UF recommends to not enable root.

> **Vantrax said:**
> 
Limiting access to the "su" program
    Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:
    · sudo chown root:admin /bin/su sudo
    · chmod 04750 /bin/su

This goes hand in hand with root/sudo above.


> **Vantrax said:**
> 
2. Physical Security

    1. Configure BIOS.
    · Disable booting from CDs/DVDs, floppies, and external devices.
    · Set BIOS password to protect the settings.
    2. Set a password for the GRUB bootloader.
    · Generate a password hash using the command / /usr/sbin/grub-md5-crypt. Add the hash to the first line of /boot/grub/menu.lst as follows:
    password --md5 passwordhash
    · Remove rescue-mode boot section from /boot/grub/menu.lst

If you're concerned about physical security the only thing that really works is encryption of you data or full-disk encryption.


> **Vantrax said:**
> 
3. Keep Software Up to Date
Upgrade through the Ubuntu Repository Network to apply upgrade automatically. Security updates should be applied as soon as possible.
Create the file apt.cron, make it executable, place it in /etc/cron.daily or /etc/cron.weekly, and ensure that it reads as follows:

    #!/bin/sh
    /usr/bin/apt-get update

I don't like auto-updates. It may remove somethign else because of dependencies.

---

### Post by x3roconf on 2008-12-05
> **Vantrax said:**
> 
20. Disable unnecessary PHP variable
Edit /etc/php5/apache2/php.ini and /etc/php5/cli/php.ini

Turn off some of this variable:

allow_call_time_pass_reference = Off
magic_quotes_gpc = Off
register_long_arrays = Off
register_argc_argv = Off
allow_url_fopen = Off
expose_php = Off
disable_functions = symlink,shell_exec,proc_close,
proc_open,dl,passthru,
escapeshellarg,escapeshellcmd,openlog, apache_child_terminate,
apache_get_modules,apache_get_version,
apache_getenv,apache_note,apache_setenv,virtual, phpinfo


system() is still allowed... so it's not very secure :D attacker can execute shell commands using system()

---

### Post by Vantrax on 2008-12-05
My particular version of this was not just related to Ubuntu:P so some of it comes from there.

Also its been used before to harden Linux labs in university computing environments.

If you have a specific addition ill add it in:P and ill make some comments on those bits that arent Ubuntu specific.

---

### Post by kevdog on 2008-12-05
Can you elaborate on #6.  There wasn't much explanation given.

---

### Post by Vantrax on 2008-12-07
Kinda complicated, but you create rules in there to deny or allow access, generally speaking you do a deny all, then allow specific connections your after. Its mainly used for SSH and can only be used for programs started by inetd.

Ive added a link to the redhat docco on it for further reading.

---

### Post by chrisrhode on 2008-12-11
Thank you for posting this useful information.  I've been looking for a document similar to this and am glad that someone was able to put it up for everyone to view! :)

---

### Post by jerremy-tamlin on 2008-12-16
Thanks for this info, you might also want to add a warning or disclaimer at the top for people like me who do silly things such as follow the instructions to only allow people in admin group to use sudo, without first checking THAT I'M IN GROUP ADMIN! Which I wasn't :-(
I managed to change it back using the live CD and after finding out how to mount my Logical volumes. Good learning experience but I'm sure I'm not the only person who thinks they understand more than they do. :p

Could you elaborate a bit more on which parts of the filesystem can be mounted noexec and/or ro?
> 1. Disk Partitions and Mounting

1. Separate /home, /tmp, /var/tmp from /root partitions (If only if the machine has frequent access from general user except administrator).
2. Change mount options in /etc/fstab to limit user access on appropriate filesystems.
· Using noexec instead prevents execution of binaries on a file system (though it will not prevent scripts from running).
· Using nosuid will prevent the setuid bit from having effect.
· The nodev option prevents use of device files on the filesystem.
I keep coming across this recommendation and have /boot /tmp /usr /var /home /var/www and /opt all on different partitions but I can't seem to find any info on what needs rw, exec or suid access. Obviously /dev needs the dev option (and I assume nothing else does), /usr needs exec, /tmp needs rw and lots needs to be changed when updating or installing more software but exactly what can I mount how while still allowing my system to function?

Cheers

---

### Post by Vantrax on 2008-12-17
> **jerremy-tamlin said:**
> Thanks for this info, you might also want to add a warning or disclaimer at the top for people like me who do silly things such as follow the instructions to only allow people in admin group to use sudo, without first checking THAT I'M IN GROUP ADMIN! Which I wasn't :-(
I managed to change it back using the live CD and after finding out how to mount my Logical volumes. Good learning experience but I'm sure I'm not the only person who thinks they understand more than they do. :p

Could you elaborate a bit more on which parts of the filesystem can be mounted noexec and/or ro?

I keep coming across this recommendation and have /boot /tmp /usr /var /home /var/www and /opt all on different partitions but I can't seem to find any info on what needs rw, exec or suid access. Obviously /dev needs the dev option (and I assume nothing else does), /usr needs exec, /tmp needs rw and lots needs to be changed when updating or installing more software but exactly what can I mount how while still allowing my system to function?

Cheers

Okies, I've added a warning there, and probably should have done so earlier but I made some silly assumptions. Im sorry you had a problem.

As before:
· Using noexec instead prevents execution of binaries on a file system 

This is not good if you have programs to be executed:P Data partitions are good for this. Its used often for partitions serving Apache.

· Using nosuid will prevent the setuid bit from having effect.

SUID stands for Set User ID. This means that if the SUID bit is set for any application then your user ID would be set as that of the owner of application/file rather than the current user, while running that application. That means in case I have an application whose owner is ' root ' and it has its SUID bit set, then when I run this application as a normal user, that application would still run as root. Since the SUID bit tells Linux that the the User ID root is set for this application and whenever this application executes it must execute as if root was executing it (since root owns this file). Disabling this for a drive prevents this operation.


· The nodev option prevents use of device files on the filesystem.

This option would be recommended for CDs and NTFS file systems generally speaking. But it can have options to lock down a system preventing breaching by simply creating hda1 or sda1 devices that are writable by all.

EDIT: I forgot to mention ro as its a read only lock. Its generally not used unless you have some archival data that cannot be changed or some documentation library htdocs kinda thing.

Generally speaking Google has all the answers and might be faster sometimes than waiting for a response. However I am happy to try and fill in gaps if you have questions.

---

### Post by jerremy-tamlin on 2008-12-21
Thanks for the explenation of nosuid, that's very useful.

Unfortunatly I've been searching google and can only find similar explenations as to those you've already given me. I understand what noexec, nodev, and ro do, but I want to know which parts of a filesystem can be mounted ro and/or noexec without affecting day to day functionality.

For instance at present I've mounted /usr ro and when I want to update software I remount it rw. Similarly I've mounted /home noexec and /var /tmp & /home nosuid

This seems to be working at the moment but I'm not sure if it means some applications won't function properly.

---

### Post by Vantrax on 2008-12-22
That should be ok, using the ro is a little unusual tho.

Basically you have to understand what the folders are ment to be used for, and what you are using them for. If you install things in odd spots then use these settings some things might not work. Just remember you made them so you can change them if you find a bug.

That being said this link will give you a short idea of what the folders do: [http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html](http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html)

If you think thats too simple read this:
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Edit: This one could help too: [http://kdubois.net/?p=25](http://kdubois.net/?p=25)

If you still want more info about what does what see the big one:
[http://rute.2038bug.com/node38.html.gz](http://rute.2038bug.com/node38.html.gz)

---

### Post by mang_ucup on 2009-01-09
Hey, your hardening guide exactly the same with mine. I think you just copy paste the guide from my blog. [http://boilinglinux.blogspot.com/2008/07/ubuntu-hardy-hardening.html](http://boilinglinux.blogspot.com/2008/07/ubuntu-hardy-hardening.html)

---

### Post by Vantrax on 2009-01-09
> **mang_ucup said:**
> Hey, your hardening guide exactly the same with mine. I think you just copy paste the guide from my blog. [http://boilinglinux.blogspot.com/2008/07/ubuntu-hardy-hardening.html](http://boilinglinux.blogspot.com/2008/07/ubuntu-hardy-hardening.html)

Some of the points are similar, and you have some good points I don't think I've included, with your permission I'd like to add them.

By and large this guide is a little larger and has a fair bit more detailed than yours. Ill make the correction on AppArmor instead of SE linux. If I'd read yours before I would have not made that mistake:P Ive never configured them together and did not realize they were mutually exclusive.

---

### Post by ProfDecoy on 2009-01-09
Out of curiosity, I noticed that in 8.10, the chkrootkit package does add a script to the daily cron list and references a config file (/etc/chkrootkit.conf) to enable the daily run.

The only significant difference between your recommended cron job and the one included is your's will mail out the logs to the specified address (provided one has set up sendmail on the system).  Was there any particular reason not to add on to that one?  I haven't checked an older Ubuntu system to see if that's a new addition with the 8.10 repository or not.

Both guides are a good starting point for hardening systems.  Thanks!

---

### Post by Vantrax on 2009-01-09
> **ProfDecoy said:**
> Out of curiosity, I noticed that in 8.10, the chkrootkit package does add a script to the daily cron list and references a config file (/etc/chkrootkit.conf) to enable the daily run.

I havent tested this process in 8.10, server/stable environments tend to only use LTS versions (and desktops the latest). Thanks for that info tho, I'm glad they are making it easier to secure systems.

---

### Post by mang_ucup on 2009-01-11
> **Vantrax said:**
> Some of the points are similar, and you have some good points I don't think I've included, with your permission I'd like to add them.

By and large this guide is a little larger and has a fair bit more detailed than yours. Ill make the correction on AppArmor instead of SE linux. If I'd read yours before I would have not made that mistake:P Ive never configured them together and did not realize they were mutually exclusive.

Yeah, i think you have copied the latest one. 
[http://boilinglinux.blogspot.com/2008/10/updated-ubuntu-hardy-804-hardening.htm](http://boilinglinux.blogspot.com/2008/10/updated-ubuntu-hardy-804-hardening.htm)
No offense for you but next time, at least please provide the source of your article.
Thanks.

For all readers, i just want to share the result from this hardening guide. I found something weird lately when i scan my "hardened" server with Nessus security scanner (brute force scan). It caused my "hardened" server down if i scan it several times. But it won't be happen in unhardened server. It looks like the kernel hardening part caused the problem. So please be more careful before you implement this guide because intruder my tried to use this scan method to bring down your "hardened" server.

Will post you guys an update how to solve this issue after i done with my research.

---

### Post by Vantrax on 2009-01-11
> **mang_ucup said:**
> Yeah, i think you have copied the latest one. 
[http://boilinglinux.blogspot.com/2008/10/updated-ubuntu-hardy-804-hardening.htm](http://boilinglinux.blogspot.com/2008/10/updated-ubuntu-hardy-804-hardening.htm)
No offense for you but next time, at least please provide the source of your article.
Thanks.

That link is broken, could you give me another link?

As I said at the start, I've pulled bit and pieces in a text file over the last year. No idea where half of it comes from. If there are significant matching bits ill put your site in a link up the top.

---

### Post by mang_ucup on 2009-01-11
> **Vantrax said:**
> That link is broken, could you give me another link?

As I said at the start, I've pulled bit and pieces in a text file over the last year. No idea where half of it comes from. If there are significant matching bits ill put your site in a link up the top.
[http://boilinglinux.blogspot.com/2008/10/updated-ubuntu-hardy-804-hardening.html](http://boilinglinux.blogspot.com/2008/10/updated-ubuntu-hardy-804-hardening.html)

Nevermind bro. I don't hesitate to share this with anyone. I just curious that how can your hardening guide just exactly the same with mine :)

Maybe we can start to make this guide more potent and solve one of the issue that just happen to me which i already posted it in my last reply.

Thank and be hardened :)

---

