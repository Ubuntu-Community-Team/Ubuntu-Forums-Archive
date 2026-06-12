---
title: "Lynis Cron Job"
date: 2014-07-16
forum: Security
---

### Post by dunbrokin on 2014-07-16
I am trying to set up Lynis as Cron Job and have cobbled together a script from various places (this is my first script...so it is bound to be wrong!). I am running into Error 83 when I run it.

/usr/sbin/lynis: 83: .: Can't open /usr/share/lynis/include/consts


My script is as follows.....

#! /bin/sh

MYDATE=`date +%Y-%m-%d`
MYFILENAME="Lynis-pj-selfbuild"$MYDATE.txt
/bin/echo "Lynis check !! `date`" > /tmp/$MYFILENAME
/usr/sbin/lynis -c > /tmp/myLynis.txt
/bin/cat /tmp/myLynis.txt|/bin/grep -v failed >> /tmp/$MYFILENAME
/bin/echo "**************************************" >> /tmp/$MYFILENAME
/usr/bin/tail -20 /tmp/myLynis.txt >> /tmp/$MYFILENAME
/bin/echo "****************DONE******************" >> /tmp/$MYFILENAME
/bin/mail -s"$MYFILENAME `date`" [email]xxxxxxxx@gmail.com[/email] < /tmp/$MYFILENAME

The mail part does not work either....

lynis: 11: lynis: /bin/mail: not found

Which is peculiar because I have AIDE sending me emails when it finishes its analysis.

I am obviously on a steep learning curve. Any help much appreciated.

---

### Post by thnewguy on 2014-07-16
Regarding the first error, either the file [COLOR=#000000] /usr/share/lynis/include/consts does not exist or you do not have permission to access it. Which user account is trying to run the cron job? Does that user have access to the file?

Are you sure the mail program's path is /bin/mail and not somethign else like /usr/bin/mail? That would certainly cause the second error. Run the command "which mail" to get the correct path.[/COLOR]

---

### Post by dunbrokin on 2014-07-16
Thank you thnewguy, you are correct about the mail...it should indeed be usr/bin/mail.

As for the permissioning...see attached....both files seem, to my n00bie's eyes, to have the same set....I am obviously missing something here?! - see attached.

---

### Post by dunbrokin on 2014-07-17
OK, I think I have sorted the permissioning and the mail....I can get mail now...but it sends me a file called noname which I cannot open...when I look at the log in /var/log/ it says that the program did not run as you have to be root to run it....my question...how do you set up for root to run a cron,daily...do you have to put it in /root/etc/cron.daily/ as opposed to /Home/xx/etc/cron.daily?

---

### Post by thnewguy on 2014-07-17
To run a script as the root user you can either
A) Add your shell script to the /etc/cron.daily/ directory
B) Login to the root account (assuming it has been enabled) and add the script to the root user's cron file using the command "crontab -e".

---

### Post by dunbrokin on 2014-07-17
So, let me be sure I understand this, if I put the script in /etc/cron.daily/ it will automatically run with root privilege?

---

### Post by thnewguy on 2014-07-18
Yes, cron by default runs all cripts in the /etc/cron.daily folder once per day. Check the cron manual page for details.

---

### Post by dunbrokin on 2014-07-19
Thank you for the pointer....I missed that when I originally skimmed it...it pays to read it in more detail...in any event, I now have it working ...the following occurs in my output...what should I do about it?:

 [09:24:44] Warning: Invalid permissions on tests file tests_crypto [test:NONE]
[09:24:44] Exception: skipping test category virtualization, file /usr/share/lynis/include/tests_virtualization has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_virtualization [test:NONE]
[09:24:44] Exception: skipping test category mac_frameworks, file /usr/share/lynis/include/tests_mac_frameworks has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_mac_frameworks [test:NONE]
[09:24:44] Exception: skipping test category file_integrity, file /usr/share/lynis/include/tests_file_integrity has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_file_integrity [test:NONE]
[09:24:44] Exception: skipping test category hardening_tools, file /usr/share/lynis/include/tests_hardening_tools has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_hardening_tools [test:NONE]
[09:24:44] Exception: skipping test category malware, file /usr/share/lynis/include/tests_malware has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_malware [test:NONE]
[09:24:44] Exception: skipping test category file_permissions, file /usr/share/lynis/include/tests_file_permissions has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_file_permissions [test:NONE]
[09:24:44] Exception: skipping test category homedirs, file /usr/share/lynis/include/tests_homedirs has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_homedirs [test:NONE]
[09:24:44] Exception: skipping test category kernel_hardening, file /usr/share/lynis/include/tests_kernel_hardening has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_kernel_hardening [test:NONE]
[09:24:44] Exception: skipping test category hardening, file /usr/share/lynis/include/tests_hardening has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_hardening [test:NONE]

---

### Post by MBoelen on 2014-07-19
> **dunbrokin said:**
> Thank you for the pointer....I missed that when I originally skimmed it...it pays to read it in more detail...in any event, I now have it working ...the following occurs in my output...what should I do about it?:

 [09:24:44] Warning: Invalid permissions on tests file tests_crypto [test:NONE]
[09:24:44] Exception: skipping test category virtualization, file /usr/share/lynis/include/tests_virtualization has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_virtualization [test:NONE]
[09:24:44] Exception: skipping test category mac_frameworks, file /usr/share/lynis/include/tests_mac_frameworks has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_mac_frameworks [test:NONE]
[09:24:44] Exception: skipping test category file_integrity, file /usr/share/lynis/include/tests_file_integrity has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_file_integrity [test:NONE]
[09:24:44] Exception: skipping test category hardening_tools, file /usr/share/lynis/include/tests_hardening_tools has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_hardening_tools [test:NONE]
[09:24:44] Exception: skipping test category malware, file /usr/share/lynis/include/tests_malware has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_malware [test:NONE]
[09:24:44] Exception: skipping test category file_permissions, file /usr/share/lynis/include/tests_file_permissions has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_file_permissions [test:NONE]
[09:24:44] Exception: skipping test category homedirs, file /usr/share/lynis/include/tests_homedirs has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_homedirs [test:NONE]
[09:24:44] Exception: skipping test category kernel_hardening, file /usr/share/lynis/include/tests_kernel_hardening has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_kernel_hardening [test:NONE]
[09:24:44] Exception: skipping test category hardening, file /usr/share/lynis/include/tests_hardening has bad permissions (should be 640, 600 or 400)
[09:24:44] Warning: Invalid permissions on tests file tests_hardening [test:NONE]


Change the permissions of these files. Lynis tests them and they seem to be "loose".

Alter permissions for all files starting with tests_: chmod 640 /usr/share/lynis/include/tests_*

---

### Post by dunbrokin on 2014-07-19
Thanks for that suggestion, I have followed your advice...

---

