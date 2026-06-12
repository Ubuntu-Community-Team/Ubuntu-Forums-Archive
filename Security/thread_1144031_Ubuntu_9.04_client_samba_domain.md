---
title: "Ubuntu 9.04 client samba domain"
date: 2009-04-30
forum: Security
---

### Post by pigna on 2009-04-30
I changed the configuration of pam to authenticate in the domain with winbind and I have enabled caching of user and password of the domain, I log the domain user (both online and offline) and mount the shared, but I have a problem when Working offline and use of certain programs that require user authentication to be run. 

Example: When I try to launch the System -> Admin -> Users and Group " from local user and I click Unlock I request the password, but when I enter the program freezes for a few minutes and then tells me:

[HTML]Unable to authenticate
An unexpected error occurred[/HTML]

And in the file auth.log I appear the following messages:

[HTML]dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.29" (uid=1001 pid=4573 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.91" (uid=1000 pid=6714 comm="/usr/lib/policykit-gnome/polkit-gnome-manager "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=5593 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.91" (uid=1000 pid=6714 comm="/usr/lib/policykit-gnome/polkit-gnome-manager "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.29" (uid=1001 pid=4573 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.92" (uid=1000 pid=6715 comm="/usr/lib/policykit/polkit-grant-helper 6706 org.fr"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=5593 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.92" (uid=1000 pid=6715 comm="/usr/lib/policykit/polkit-grant-helper 6706 org.fr"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.29" (uid=1001 pid=4573 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.93" (uid=1000 pid=6718 comm="/usr/lib/policykit/polkit-grant-helper 6706 org.fr"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=5593 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.93" (uid=1000 pid=6718 comm="/usr/lib/policykit/polkit-grant-helper 6706 org.fr"))
polkit-grant-helper-pam[6721]: pam_mount(rdconf1.c:667): path to luserconf set to /home/user1/.pam_mount.conf.xml 
polkit-grant-helper-pam[6721]: pam_winbind(polkit:auth): getting password (0x00000010)
polkit-grant-helper-pam[6721]: pam_winbind(polkit:auth): pam_get_item returned a password
polkit-grant-helper-pam[6721]: pam_winbind(polkit:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTHINFO_UNAVAIL (9), NTSTATUS: NT_STATUS_NO_LOGON_SERVERS, Error message was: No logon servers
polkit-grant-helper-pam[6721]: pam_winbind(polkit:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'user1')
polkit-grant-helper-pam[6721]: pam_unix(polkit:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=user1 rhost=  user=user1[/HTML]

And if you use a domain  user I have these messages appear:

[HTML]dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
57" (uid=1001 pid=4645 comm="users-admin "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
58" (uid=0 pid=4648 comm="/usr/bin/perl /usr/share/system-tools-backends-2.0"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
59" (uid=0 pid=4654 comm="/usr/bin/perl /usr/share/system-tools-backends-2.0"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
60" (uid=0 pid=4656 comm="/usr/bin/perl /usr/share/system-tools-backends-2.0"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
61" (uid=0 pid=4658 comm="/usr/bin/perl /usr/share/system-tools-backends-2.0"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
62" (uid=1001 pid=4666 comm="/usr/lib/policykit-gnome/polkit-gnome-manager "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
63" (uid=1001 pid=4667 comm="/usr/lib/policykit/polkit-grant-helper 4645 org.fr"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
64" (uid=1001 pid=4670 comm="/usr/lib/policykit/polkit-grant-helper 4645 org.fr"))
polkit-grant-helper-pam[4673]: pam_mount(rdconf1.c:667): path to luserconf set to /home/user2/.pam_mount.conf.xml
polkit-grant-helper-pam[4673]: pam_winbind(polkit:auth): getting password (0x00000210)
polkit-grant-helper-pam[4673]: pam_winbind(polkit:auth): pam_get_item returned a password
polkit-grant-helper-pam[4673]: pam_winbind(polkit:auth): user 'user2' granted access
polkit-grant-helper-pam[4673]: pam_winbind(polkit:account): user 'user2' granted access[/HTML]

This is my configuration files:

```
[common-account]
account sufficient pam_winbind.so
account required pam_unix.so

[common-auth]
auth required pam_mount.so
auth sufficient pam_winbind.so use_first_pass
#auth sufficient pam_winbind.so
auth required pam_unix.so nullok_secure use_first_pass

[common-password]
password sufficient pam_winbind.so use_authtok
#password sufficient pam_winbind.so
password required pam_unix.so nullok obscure min=4 max=9 md5

[common-session]
session required pam_unix.so nullok_secure
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
session optional pam_mount.so

[pam_winbind.conf]
[global]
#debug
cached_login = yes

[smb.conf]
workgroup = DOM1
server string = %h
security = domain
encrypt passwords = true
wins server = xxx.xxx.xxx.xxx
password server = *
domain master = false
preferred master = false
local master = no
lm announce = false
hosts allow = xxx.xxx.xxx.xxx, 127.0.0.1
hosts deny = all
socket options = TCP_NODELAY IPTOS_LOWDELAY
log file = /var/log/samba/log.%U
log level = 2
pam password change = yes
interfaces = eth0, lo
winbind uid = 1000-10000
winbind gid = 1000-10000
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
winbind cache time = 15
winbind offline logon = yes
template shell = /bin/bash
template homedir = /home/%U

```

	
Suggestions?

---

### Post by travis.wenks on 2009-08-03
im getting the same issue my computer just pauses for a sec or so and when i look in the logs its full of those events

hmm

---

