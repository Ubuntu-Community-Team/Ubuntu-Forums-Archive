---
title: "Automatic Logout - auth log indicates Failed Login Attempt"
date: 2010-03-02
forum: Security
---

### Post by ajacx on 2010-03-02
A few minutes ago I was using google chrome when suddenly the scroll-lock indicator on my keyboard turned on... I pressed the scroll-lock key, but nothing happened, the light remained. I opened a terminal and ran "top" to find what processes were running when I was automatically logged out. I logged back and checked the logs and found the following entries in my auth.log:

```

CRON[2971]: pam_unix(cron:session): session opened for user root by (uid=0)
CRON[2971]: pam_unix(cron:session): session closed for user root
login[1106]: pam_unix(login:auth): auth could not identify password for [9.1"9&""999$/.39&39.**KKK******]
gdm-session-worker[1942]: pam_unix(gdm:session): session closed for user (myusername)
gnome-keyring-daemon[1959]: dbus failure unregistering from session: Connection is closed
login[1106]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
login[1106]: pam_securetty(login:auth): unexpected response from failed conversation function
login[1106]: pam_securetty(login:auth): cannot determine username
login[1106]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
login[1106]: pam_securetty(login:auth): unexpected response from failed conversation function
login[1106]: pam_securetty(login:auth): cannot determine username

```

I googled this and found that one or two other people have been automatically logged out before, but noone has replied to those threads. Does anyone have any idea why this happened and how I can look further to find out exactly what triggered it?

---

### Post by P.T. on 2010-05-28
I have the same problem. I get logged out randomly. After googling for quite some time I've found a couple of links:
 
[Gentoo Forums:]("http://forums.gentoo.org/viewtopic-p-6286779.html?sid=8f9ec0c24cfa1a5448efc7c2fe85861b") Some people seem to have had the same problem. Apparently the input from tty7 goes to tty2 for some odd reason. I suppose this makes the random logouts.

[Ubuntu Forums:]("http://ubuntuforums.org/showthread.php?t=1354428") This thread is a little old, but there are also people with this problem. None of them seem to have solved it or ever spoke about it again :(.

[Ubuntu Forums:]("http://ubuntuforums.org/showthread.php?t=1481956&highlight=failed+login+tty2") This link might lead to the solution. I'm about to try this thing, so hopefully this may solve it for you as well :).

Edit:
[Arch Forums:]("http://bbs.archlinux.org/viewtopic.php?pid=698626") They seem to have had the exact same problem as I had.

I've edited sysv-rc-conf today. GDM was turned off completely, so I set 2,3,4,5... hoping this will help. I'll let it know if it failed.
Allright, that didn't help after all.. I got logged out just a few minutes ago.

Well I'll just keep updating until I find the solution :p: [Similar bug report]("https://bugs.launchpad.net/ubuntu/+bug/511774"). I've executed the commands I found there:
```

cd /etc/apparmor.d/
sudo ufw enable
sudo ufw default deny
sudo ufw logging high
sudo apt-get install apparmor apparmor-profiles
for i in *; do sudo aa-enforce $i; done

```
No good... It's just not my lucky day I suppose...

---

