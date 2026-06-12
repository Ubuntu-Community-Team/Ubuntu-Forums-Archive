---
title: "ubuntu server 11.04 and ltsp server kicks the session"
date: 2011-07-25
forum: Server Platforms
---

### Post by mobius7 on 2011-07-25
use with HP t5335 thin clients
boot normaly, loging in, BUT  kicks back out to the login

i cant understand WHY :(

log
=================
File: auth.log          Line 474 Col 267   61344 bytes                               100%

Jul 25 14:40:09 userver sshd[12527]: Server listening on 0.0.0.0 port 22.
Jul 25 14:40:09 userver sshd[12527]: Server listening on :: port 22.
Jul 25 14:40:14 userver sshd[12527]: Received signal 15; terminating.
Jul 25 14:40:14 userver sshd[12541]: Server listening on 0.0.0.0 port 22.
Jul 25 14:40:14 userver sshd[12541]: Server listening on :: port 22.
Jul 25 14:40:54 userver sshd[12569]: Accepted password for test from 192.168.1.102 port 4
5170 ssh2
Jul 25 14:40:54 userver sshd[12569]: pam_unix(sshd:session): session opened for user test
 by (uid=0)
Jul 25 14:40:55 userver sshd[12660]: subsystem request for sftp by user test
Jul 25 14:40:57 userver polkitd(authority=local): Registered Authentication Agent for uni
x-session:/org/freedesktop/ConsoleKit/Session31 (system bus name :1.289 [/usr/lib/policyk
it-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/Authen
ticationAgent, locale ru_UA.UTF-8)
Jul 25 14:40:57 userver dbus-daemon: [system] Rejected send message, 2 matched rules; typ
e="method_call", sender=":1.292" (uid=1001 pid=12756 comm="nautilus ") interface="org.fre
edesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destinat
ion=":1.5" (uid=0 pid=851 comm="/usr/sbin/console-kit-daemon --no-daemon "))
Jul 25 14:41:00 userver dbus-daemon: [system] Rejected send message, 2 matched rules; typ
e="method_call", sender=":1.296" (uid=1001 pid=12851 comm="/usr/lib/indicator-datetime/in
dicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error
name="(unset)" requested_reply=0 destination=":1.5" (uid=0 pid=851 comm="/usr/sbin/consol
e-kit-daemon --no-daemon "))
Jul 25 14:41:35 userver polkitd(authority=local): Unregistered Authentication Agent for u
nix-session:/org/freedesktop/ConsoleKit/Session31 (system bus name :1.289, object path /o
rg/gnome/PolicyKit1/AuthenticationAgent, locale ru_UA.UTF-8) (disconnected from bus)
Jul 25 14:41:35 userver sshd[12660]: Received disconnect from 192.168.1.102: 11: disconne
cted by user
Jul 25 14:41:35 userver sshd[12569]: pam_unix(sshd:session): session closed for user test
Jul 25 14:41:35 userver gnome-keyring-daemon[12737]: dbus failure unregistering from sess
ion: Connection is closed
Jul 25 14:41:35 userver gnome-keyring-daemon[12737]: dbus failure unregistering from sess
ion: Connection is closed

---

### Post by newbie-user on 2011-10-10
I'm having the exact same problem, except with 10.04.  I'm using HP t5135 and Intel Atom 230 boards and I get booted back to the login screen.  Interestingly enough, if I use a higher-powered machine as a thin client, it logs in just fine.  As an example, I used a computer with a Pentium D 805 and 4GB of ram and it logs in as a thin client without any problems.  The lower-powered machines, t5135 and machines with Intel Atoms, get stuck at the login screen.

---

