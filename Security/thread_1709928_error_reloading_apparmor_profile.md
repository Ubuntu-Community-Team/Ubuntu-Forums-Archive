---
title: "error reloading apparmor profile"
date: 2011-03-19
forum: Security
---

### Post by TheNewbieGeek on 2011-03-19
Hi I just got through reading the tutorial on apparmor and decided to use a profile provided by someone else while learning more about apparmor or for good. 

I used

sudo gedit /etc/apparmor.d/user.lib.firefox-3.6.3.firefox.sh

to copy and paste a profile provided elsewhere and save it.

I then tried to reload it with the following command:

/etc/init.d/apparmor restart

I received this error message:

* Reloading AppArmor profiles   
  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

Also another question I had on my mind is apparmor running on computer startup? So you would have protection all the time?

Thanks for the replies dudes.

---

### Post by CandidMan on 2011-03-19
That's not an error per se, you just need to run this command

```
sudo rm -v /etc/apparmor.d/disable/usr.bin.firefox ;sudo apparmor_parser -va /etc/apparmor.d/usr.bin.firefox
```

Any profile entry you enter in disable/ is automatically skipped when apparmor loads during the boot process

Don't know what that entry would be doing in disable/ if you haven't been adjusting apparmor

---

### Post by TheNewbieGeek on 2011-03-19
> **CandidMan said:**
> That's not an error per se, you just need to run this command

```
sudo rm -v /etc/apparmor.d/disable/usr.bin.firefox ;sudo apparmor_parser -va /etc/apparmor.d/usr.bin.firefox
```Any profile entry you enter in disable/ is automatically skipped when apparmor loads during the boot process

Don't know what that entry would be doing in disable/ if you haven't been adjusting apparmor

That didn't work...why would I want to remove it or skip it....what is disable/???

---

### Post by CandidMan on 2011-03-19
Well, any profile that's in /etc/apparmor.d/disable/ is skipped when apparmor is being started.

That's usually done by using the ln command to make a hard-link so the profile is in the apparmor.d/ profile and disable folder at the same time

Maybe it would help if you posted the output from 
```
ls -l /etc/apparmor.d/
```

and 
```

ls -l /etc/apparmor.d/disable/
```

and lastly

```
sudo apparmor_status
```

---

### Post by TheNewbieGeek on 2011-03-19
> **CandidMan said:**
> Well, any profile that's in /etc/apparmor.d/disable/ is skipped when apparmor is being started.

That's usually done by using the ln command to make a hard-link so the profile is in the apparmor.d/ profile and disable folder at the same time

Maybe it would help if you posted the output from 
```
ls -l /etc/apparmor.d/
```and 
```

ls -l /etc/apparmor.d/disable/
```and lastly

```
sudo apparmor_status
```

First Code:

total 152
drwxr-xr-x 2 root root 4096 2010-04-29 05:26 abstractions
drwxr-xr-x 2 root root 4096 2011-03-18 23:00 apache2.d
-rw-r--r-- 1 root root  696 2011-01-20 09:43 bin.ping
drwxr-xr-x 2 root root 4096 2011-03-18 23:48 cache
drwxr-xr-x 2 root root 4096 2010-04-29 05:22 disable
drwxr-xr-x 2 root root 4096 2010-04-01 10:48 force-complain
-rw-r--r-- 1 root root  967 2010-04-14 16:24 gdm-guest-session
drwxr-xr-x 2 root root 4096 2011-03-18 23:00 program-chunks
-rw-r--r-- 1 root root 1944 2010-04-01 10:46 sbin.dhclient3
-rw-r--r-- 1 root root  755 2011-01-20 09:43 sbin.klogd
-rw-r--r-- 1 root root 1052 2011-01-20 09:43 sbin.syslogd
-rw-r--r-- 1 root root 1147 2011-01-20 09:43 sbin.syslog-ng
drwxr-xr-x 3 root root 4096 2010-04-29 05:26 tunables
-rw-r--r-- 1 root root 2052 2010-03-29 15:10 usr.bin.evince
-rw-r--r-- 1 root root 8337 2010-04-23 07:54 usr.bin.firefox
-rw-r--r-- 1 root root  509 2011-01-20 09:43 usr.lib.dovecot.deliver
-rw-r--r-- 1 root root  561 2011-01-20 09:43 usr.lib.dovecot.dovecot-auth
-rw-r--r-- 1 root root  447 2011-01-20 09:43 usr.lib.dovecot.imap
-rw-r--r-- 1 root root  445 2011-01-20 09:43 usr.lib.dovecot.imap-login
-rw-r--r-- 1 root root  476 2011-01-20 09:43 usr.lib.dovecot.managesieve-login
-rw-r--r-- 1 root root  427 2011-01-20 09:43 usr.lib.dovecot.pop3
-rw-r--r-- 1 root root  459 2011-01-20 09:43 usr.lib.dovecot.pop3-login
-rw-r--r-- 1 root root 8867 2011-03-18 23:43 usr.lib.firefox-3.6.3.firefox.sh
-rw-r--r-- 1 root root  713 2011-01-20 09:43 usr.sbin.avahi-daemon
-rw-r--r-- 1 root root 4050 2010-04-09 08:12 usr.sbin.cupsd
-rw-r--r-- 1 root root  518 2011-01-20 09:43 usr.sbin.dnsmasq
-rw-r--r-- 1 root root  937 2011-01-20 09:43 usr.sbin.dovecot
-rw-r--r-- 1 root root  802 2011-01-20 09:43 usr.sbin.identd
-rw-r--r-- 1 root root  814 2011-01-20 09:43 usr.sbin.mdnsd
-rw-r--r-- 1 root root  471 2011-01-20 09:43 usr.sbin.nmbd
-rw-r--r-- 1 root root 1215 2011-01-20 09:43 usr.sbin.nscd
-rw-r--r-- 1 root root  987 2011-01-20 09:43 usr.sbin.smbd
-rw-r--r-- 1 root root  827 2010-03-23 12:29 usr.sbin.tcpdump
-rw-r--r-- 1 root root  677 2011-01-20 09:43 usr.sbin.traceroute

Second Code:

total 0
lrwxrwxrwx 1 root root 31 2011-02-15 09:41 usr.bin.firefox -> /etc/apparmor.d/usr.bin.firefox

Third Code:

apparmor module is loaded.
33 profiles are loaded.
13 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox-3.6.3/firefox-*bin
   /usr/lib/firefox-3.6.3/firefox-*bin//firefox_java
   /usr/lib/firefox-3.6.3/firefox-*bin//firefox_openjdk
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
20 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
5 processes have profiles defined.
3 processes are in enforce mode :
   /sbin/dhclient3 (1026) 
   /usr/lib/firefox-3.6.3/firefox-*bin (1592) 
   /usr/sbin/cupsd (910) 
2 processes are in complain mode.
   /usr/sbin/avahi-daemon (656) 
   /usr/sbin/avahi-daemon (658) 
0 processes are unconfined but have a profile defined.

---

### Post by CandidMan on 2011-03-20
Hmmm, from the looks of it you need to get rid of that hard link to usr.bin.firefox in /etc/apparmor.d/disable/.

Also, I don't know why this is but I've found confining the shell script (ending in .sh) for some programs instead of the executable just makes apparmor go screwy. So I'd stick to the usr.bin.firefox profile unless someone has a reason not to...

Could you try this command one more time and post the terminal's output?

```
sudo rm -v /etc/apparmor.d/disable/usr.bin.firefox
```

That tends to work for me, but if it doesn't for you might want to check the file or folder's not immutable with 
```
lsattr /etc/apparmor.d/
``` and ```
lsattr /etc/apparmor.d/disable/usr.bin.firefox
```

---

### Post by TheNewbieGeek on 2011-03-20
> **CandidMan said:**
> Hmmm, from the looks of it you need to get rid of that hard link to usr.bin.firefox in /etc/apparmor.d/disable/.

Also, I don't know why this is but I've found confining the shell script (ending in .sh) for some programs instead of the executable just makes apparmor go screwy. So I'd stick to the usr.bin.firefox profile unless someone has a reason not to...

Could you try this command one more time and post the terminal's output?

```
sudo rm -v /etc/apparmor.d/disable/usr.bin.firefox
```That tends to work for me, but if it doesn't for you might want to check the file or folder's not immutable with 
```
lsattr /etc/apparmor.d/
``` and ```
lsattr /etc/apparmor.d/disable/usr.bin.firefox
```

I tried the first line of code and the file was removed this time.

second code: 

--------e- /etc/apparmor.d/sbin.klogd
-----------------e- /etc/apparmor.d/usr.sbin.dnsmasq
-----------------e- /etc/apparmor.d/sbin.dhclient3
-----------------e- /etc/apparmor.d/usr.lib.dovecot.imap-login
-----------------e- /etc/apparmor.d/sbin.syslogd
-----------------e- /etc/apparmor.d/usr.lib.dovecot.deliver
-----------------e- /etc/apparmor.d/usr.lib.dovecot.pop3
-----------------e- /etc/apparmor.d/usr.sbin.cupsd
-----------------e- /etc/apparmor.d/bin.ping
-----------------e- /etc/apparmor.d/abstractions
-----------------e- /etc/apparmor.d/usr.lib.dovecot.dovecot-auth
-----------------e- /etc/apparmor.d/usr.lib.dovecot.managesieve-login
-----------------e- /etc/apparmor.d/usr.lib.dovecot.imap
-----------------e- /etc/apparmor.d/usr.sbin.avahi-daemon
-----------------e- /etc/apparmor.d/usr.sbin.nscd
-----------------e- /etc/apparmor.d/usr.sbin.identd
-----------------e- /etc/apparmor.d/usr.bin.firefox
-----------------e- /etc/apparmor.d/usr.bin.evince
-----------------e- /etc/apparmor.d/program-chunks
-----------------e- /etc/apparmor.d/gdm-guest-session
-----------------e- /etc/apparmor.d/disable
-----------------e- /etc/apparmor.d/usr.lib.firefox-3.6.3.firefox.sh
-----------------e- /etc/apparmor.d/sbin.syslog-ng
-----------------e- /etc/apparmor.d/tunables
-----------------e- /etc/apparmor.d/apache2.d
-----------------e- /etc/apparmor.d/cache
-----------------e- /etc/apparmor.d/usr.sbin.dovecot
-----------------e- /etc/apparmor.d/usr.lib.dovecot.pop3-login
-----------------e- /etc/apparmor.d/usr.sbin.mdnsd
-----------------e- /etc/apparmor.d/usr.sbin.smbd
-----------------e- /etc/apparmor.d/usr.sbin.tcpdump
-----------------e- /etc/apparmor.d/usr.sbin.nmbd
-----------------e- /etc/apparmor.d/usr.sbin.traceroute
-----------------e- /etc/apparmor.d/force-complain


Third Code:

lsattr: No such file or directory while trying to stat /etc/apparmor.d/disable/usr.bin.firefox


How do I know if the firefox profile is working?

---

### Post by TheNewbieGeek on 2011-03-20
> **CandidMan said:**
> Hmmm, from the looks of it you need to get rid of that hard link to usr.bin.firefox in /etc/apparmor.d/disable/.

Also, I don't know why this is but I've found confining the shell script (ending in .sh) for some programs instead of the executable just makes apparmor go screwy. So I'd stick to the usr.bin.firefox profile unless someone has a reason not to...

Could you try this command one more time and post the terminal's output?

```
sudo rm -v /etc/apparmor.d/disable/usr.bin.firefox
```That tends to work for me, but if it doesn't for you might want to check the file or folder's not immutable with 
```
lsattr /etc/apparmor.d/
``` and ```
lsattr /etc/apparmor.d/disable/usr.bin.firefox
```

A quick question...how do you test to see if the profile works?

---

### Post by CandidMan on 2011-03-20
Okay, good.

You need to make/find a profile for /usr/bin/firefox. If you want to make your own I'd recommend using this command

```
sudo aa-autodep /usr/bin/firefox
```
You need the apparmor-utils package for that.

As for testing, just put a deny entry in the profile, 
something like "deny /home/*/.ssh/ r,"
put firefox into enforce mode 

```
sudo enforce firefox
```

and try to open said file/directory using CTRL-O in firefox

You should get a big fat permission denied, even as root

---

### Post by TheNewbieGeek on 2011-03-21
> **CandidMan said:**
> Okay, good.

You need to make/find a profile for /usr/bin/firefox. If you want to make your own I'd recommend using this command

```
sudo aa-autodep /usr/bin/firefox
```You need the apparmor-utils package for that.

As for testing, just put a deny entry in the profile, 
something like "deny /home/*/.ssh/ r,"
put firefox into enforce mode 

```
sudo enforce firefox
```and try to open said file/directory using CTRL-O in firefox

You should get a big fat permission denied, even as root

I don't understand...another profile...I already did...did you see the OP? I copy and pasted someone elses.

---

### Post by CandidMan on 2011-03-21
> I don't understand...another profile...I already did...did you see the OP? I copy and pasted someone elses.
Sorry, I missed that. According to apparmor_status, firefox was already confined. But I can't tell if that's due to the usr.bin.firefox profile or usr.lib.firefox-3.6.3.firefox.sh.

So yeah, I'd just add a denial for any file or folder into the usr.bin.firefox profile, reload apparmor, using this code
```
sudo service apparmor restart
```
then see if you can open that file/folder with firefox

Like I mentioned before, I found Apparmor to act a bit when I accidentally confined the script and not the program.

Also, make sure any version numbers referenced in the profile match the actual locations and versions of any programs you want to confine.

Maybe, you could post the contents of your usr.bin.firefox profile. Remove any identifying information if you feel more comfortable :-)

---

### Post by TheNewbieGeek on 2011-03-21
> **CandidMan said:**
> Sorry, I missed that. According to apparmor_status, firefox was already confined. But I can't tell if that's due to the usr.bin.firefox profile or usr.lib.firefox-3.6.3.firefox.sh.

So yeah, I'd just add a denial for any file or folder into the usr.bin.firefox profile, reload apparmor, using this code
```
sudo service apparmor restart
```then see if you can open that file/folder with firefox

Like I mentioned before, I found Apparmor to act a bit when I accidentally confined the script and not the program.

Also, make sure any version numbers referenced in the profile match the actual locations and versions of any programs you want to confine.

Maybe, you could post the contents of your usr.bin.firefox profile. Remove any identifying information if you feel more comfortable :-)

I copy and pasted the profile I found on the net into usr.lib.firefox-3.6.3.firefox.sh and enforced it. I am new to apparmor so I'm trying to follow what you're saying...is "confined" the same as enforcing the script?...so you're saying I should make a profile and enforce it for the app too? What is the difference between usr.bin.firefox and usr.lib.firefox-3.6.3.firefox.sh don't they both control the app?

I checked the version numbers they are the same.

---

### Post by CandidMan on 2011-03-21
'Confined' just means that Apparmor is keeping an eye on the program.

[LIST]
[*]'Enforcing' means Apparmor is keeping an eye on the program and making it stick to the rules in the  profile
[*]Then you've got 'Complain' mode, same again but Apparmor just keeps a log of what the program does
[/LIST]
So whenever you start up Apparmor, any profiles in /etc/apparmor.d/ will confine the corresponding.

Confined programs are either being just monitored or monitored and locked down

Scripts(.sh) are 'just' executable text files that make use of programs. They usually just set conditions and parameters when you're using programs.
I think of it like this: Programs=Functionality, Scripts=Parameters

As an experiment you could start any program 

and then,
create a profile for said program using ```
sudo aa-autodep /path/to/program
```.

Check its status with ```
sudo apparmor_status
``` and you should see that the program is unconfined until you start it next time
P.S. Sorry if any of that's condescending, just have to be sure + posterity :-)

---

### Post by TheNewbieGeek on 2011-03-21
> **CandidMan said:**
> 'Confined' just means that Apparmor is keeping an eye on the program.

[LIST]
[*]'Enforcing' means Apparmor is keeping an eye on the program and making it stick to the rules in the  profile
[*]Then you've got 'Complain' mode, same again but Apparmor just keeps a log of what the program does
[/LIST]
So whenever you start up Apparmor, any profiles in /etc/apparmor.d/ will confine the corresponding.

Confined programs are either being just monitored or monitored and locked down

Scripts(.sh) are 'just' executable text files that make use of programs. They usually just set conditions and parameters when you're using programs.
I think of it like this: Programs=Functionality, Scripts=Parameters

As an experiment you could start any program 

and then,
create a profile for said program using ```
sudo aa-autodep /path/to/program
```.

Check its status with ```
sudo apparmor_status
``` and you should see that the program is unconfined until you start it next time
P.S. Sorry if any of that's condescending, just have to be sure + posterity :-)

It's cool...actually I don't find it condescending a bit because I'm such a newbie with linux. I understood everything but I don't know where programs are kept in linux...if you could tell me I do know what to based on your last post. thanks dude.

---

### Post by CandidMan on 2011-03-21
Okay, cool
In general the core programs are in /bin/
the core system daemons(background programs) are in /sbin/ 

And there are the sort of optional programs and daemons in /usr/bin/ and /usr/sbin/
Things like firefox and GUI stuff goes in there

But really important stuff like cp(copy), mv(move),kill(despatch with extreme prejudice) are all in /bin/

Oh, and then you have share libraries in /lib/ and /usr/lib/

That's general pattern
If you type "env" in a terminal it will tell you where it looks for programs when you type a command

---

### Post by TheNewbieGeek on 2011-03-21
> **CandidMan said:**
> Okay, cool
In general the core programs are in /bin/
the core system daemons(background programs) are in /sbin/ 

And there are the sort of optional programs and daemons in /usr/bin/ and /usr/sbin/
Things like firefox and GUI stuff goes in there

But really important stuff like cp(copy), mv(move),kill(despatch with extreme prejudice) are all in /bin/

Oh, and then you have share libraries in /lib/ and /usr/lib/

That's general pattern
If you type "env" in a terminal it will tell you where it looks for programs when you type a command

It is in enforce mode...One last question...how do you set a denial for a folder in the profile?

---

### Post by CandidMan on 2011-03-21
Here's the beginning of my firefox profile 
```
# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

#include <tunables/global>

/usr/lib/firefox-3.6.15/firefox-*bin {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/private-files>

  deny /bin/dash rx,
  deny @{HOME}/.* mrwlk,
  deny @{HOME}/.*/ mrwlk,
  deny @{HOME}/.gnupg/ mrwlk,
  deny @{HOME}/.gnupg/** mrwlk,
```The rest is some more denials followed by all of the allows. The denials are quite handy because if you use lots of wildcards like me, you can use 'deny' to stop a program reading/writing stuff it otherwise would be able to because of the wildcards

Hope that helps

---

