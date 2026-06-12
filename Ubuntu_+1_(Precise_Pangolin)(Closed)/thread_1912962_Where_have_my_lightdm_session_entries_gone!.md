---
title: "Where have my lightdm session entries gone?!"
date: 2012-01-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-01-21
I don't realise this had happened until GS broke (temporarily) earlier today and I wanted to choose another type of session (e.g. gnome classic) from the lightdm login screen.

The little cog widget is no longer there.

In precise I (still) have:

```
paul@precise-64:~$ ls -la /usr/share/xsessions
total 40
drwxr-xr-x   2 root root  4096 Dec  7 01:15 .
drwxr-xr-x 234 root root 12288 Jan 20 20:04 ..
-rw-r--r--   1 root root   233 Dec  6 19:19 gnome-classic.desktop
-rw-r--r--   1 root root   205 Dec  6 19:19 gnome.desktop
-rw-r--r--   1 root root   277 Dec  6 19:19 gnome-fallback.desktop
-rw-r--r--   1 root root   188 Dec  6 19:19 gnome-shell.desktop
-rw-r--r--   1 root root   208 Dec  6 19:19 ubuntu-2d.desktop
-rw-r--r--   1 root root   185 Dec  6 19:19 ubuntu.desktop
paul@precise-64:~$ 
```

but (unlike oneiric) no **/etc/lightdm/Xsession** file.

**oneiric**:

```
paul@precise-64:~$ ls -la /mnt/etc/lightdm
total 28
drwxr-xr-x   2 root root 4096 Dec 12 22:32 .
drwxr-xr-x 116 root root 4096 Jan 21 19:46 ..
-rw-r--r--   1 root root 3478 Dec 12 22:32 lightdm.conf
lrwxrwxrwx   1 root root   55 Oct  5 01:05 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r--   1 root root  683 Nov 24 06:01 lightdm-gtk-greeter-ubuntu.conf
-rw-r--r--   1 root root  715 Sep  6 16:43 unity-greeter.conf
-rw-r--r--   1 root root  456 Oct 27 05:09 users.conf
-rwxr-xr-x   1 root root 2044 Jul 13  2011 Xsession
```

```
cat /mnt/etc/lightdm/lightdm.conf
#
# General configuration
#
# xserver = X server to run (FIXME)
# default-xserver-command = Default X server command (FIXME)
# authorization-directory = Directory to store X authorization files
# log-directory = Directory to log information to
# theme-directory = Directory to load themes from
# theme-engine-directory = Directory to load theme engines from
# default-greeter-theme = Default greeter theme to use
# cache-directory = Directory to cache to
# xsessions-directory = Directory to find X sessions
# default-xsession Default X session to use
# session-wrapper = Program to run sessions through
# minimum-vt = First VT to run displays on
# seats = list of seats to start displays on
#

[LightDM]
#xserver=default-xserver
#default-xserver-command=
#authorization-directory=/var/cache/lightdm/authority
#log-directory=/var/log/lightdm
#theme-directory=/usr/share/lightdm/themes
#theme-engine-directory=/usr/libexec/lightdm
#default-greeter-theme=
#cache-directory=/var/cache/lightdm
#xsessions-directory=/usr/share/xsessions
#default-xsession=
**[COLOR="Red"]session-wrapper=/etc/lightdm/Xsession[/COLOR]**
minimum-vt=7
seats=seat-0

#
# X server configuration
# layout = ServerLayout to use
# config-file = Configuration file to use
#
#[default-xserver]
#command=/usr/bin/X
#layout=
#config-file=

#
# Seat configuration
#
# vt = Virtual terminal to start on (0-n)
# greeter-theme = Greeter theme
# greeter-user = User to run greeter process as
# session = Default session
# default-user = Username of default user to log in as
# default-user-timeout = Delay before logging in in seconds (use 0 for automatic login)
# pam-service = PAM service to use
# display-number = Display number to use (overrides automatic display number selection)
# xserver = X server to use
# xdmcp-manager = XDMCP manager to connect to
# xdmcp-port = XDMCP UDP/IP port to communicate on
# key = Authentication key to use
#
[seat-0]
#vt=0
#greeter-theme=example-gtk-gnome
#greeter-user=lightdm
#session=gnome
#default-user=bob
#default-user-timeout=5
#default-user-session=
#pam-service=lightdm
#display-number=2
#xserver=
#xdmcp-manager=
#xdmcp-port=177
#key=0x0123456789ABCD

#
# User manager configuration
#
# load-users = true if can provide user list to greeter
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserManager]
#load-users=true
#minimum-uid=500
#hidden-users=nobody nobody4 noaccess
#hidden-shells=/bin/false /usr/sbin/nologin

#
# Guest account configuration
#
# enabled = true if guest account is enabled
# username = username of guest account
# setup-script = script to be run to setup guest account
# cleanup-script = script to be run to cleanup guest account
#
[GuestAccount]
enabled=true
username=guest
setup-script=/usr/share/lightdm/guest-session/guest-session-setup.sh
cleanup-script=/usr/share/lightdm/guest-session/guest-session-cleanup.sh

#
# XDMCP Server configuration
#
# enabled = true if XDMCP connections should be allowed
# port = UDP/IP port to listen for connections on
# key = Authentication key to use for XDM-AUTHENTICATION-1 or blank to not use authentication
#
# The authentication key is a 56 bit DES key specified in hex as 0xnnnnnnnnnnnnnn.  Alternatively
# it can be a word and the first 7 characters are used as the key.
#
[xdmcp]
#enabled=true
#port=177
#key=0x0123456789ABCD

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
```

**precise**:

```
paul@precise-64:~$ ls -la /etc/lightdm
total 32
drwxr-xr-x   2 root root  4096 Jan 20 19:37 .
drwxr-xr-x 130 root root 12288 Jan 21 20:52 ..
-rw-r--r--   1 root root    66 Jan 20 19:37 lightdm.conf
lrwxrwxrwx   1 root root    55 Sep 28 17:54 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r--   1 root root   683 Nov 22 02:03 lightdm-gtk-greeter-ubuntu.conf
-rw-r--r--   1 root root   776 Jan 19 04:33 unity-greeter.conf
-rw-r--r--   1 root root   456 Nov 10 06:34 users.conf
paul@precise-64:~$ 
```

```
cat /etc/lightdm/lightdm.conf
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
paul@precise-64:~$
```

so (for example) the precise lightdm.conf has no "session-wrapper=/etc/lightdm/Xsession" line, but maybe that's not needed/used any more in precise.

---

### Post by mc4man on 2012-01-21
The session-chooser menu (cog) is not displayed for the default user until you move to another user or guest session & then back to that user.

If you only have the one user (have disabled the guest session) then from the greeter login screen atm you're sol

The whole thing is weird & hopefully a bug rather than a "Design"

edit:
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918657](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918657)

---

### Post by paul_in_london on 2012-01-21
> **mc4man said:**
> The session-chooser menu (cog) is not displayed for the default user until you move to another user or guest session & then back to that user.

If you only have the one user (have disabled the guest session) then from the greeter login screen atm you're sol

The whole thing is weird & hopefully a bug rather than a "Design"

edit:
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918657](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/918657)

Oh I see. Thanks! That is weird, yes. I'd be surprised/disappointed if this was deliberate!

My precise lightdm.conf has no **allow-guest** entry and it's a single user setup, but I'm sure I still saw an option to log in as a guest. I didn't bother selecting that because it never occurred to me that it might being the session chooser menu back.

I am using unity-greeter so apparently it's related to the bug you just posted - albeit a slightly more recent version than the one referred to in the bug report:

```
apt-cache policy unity-greeter
unity-greeter:
  Installed: 0.2.0-0ubuntu4
  Candidate: 0.2.0-0ubuntu4
  Version table:
 *** 0.2.0-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by mc4man on 2012-01-21
unity-greeter has updated a couple of time in the last few days though they were for relatively insignificant things

> unity-greeter (0.2.0-0ubuntu4) precise; urgency=low

  * debian/patches/drop_keyboard_indicator.patch:
    - Back out the keyboard layout indicator for now, until we can properly
      fix the bugs with detecting user layouts.  (LP: #915468)

 -- Michael Terry <mterry@ubuntu.com>  Fri, 20 Jan 2012 07:05:31 -0500

unity-greeter (0.2.0-0ubuntu3) precise; urgency=low

  * Add versioned Breaks on edubuntu-artwork to allow edubuntu-artwork
    to fix its unity-greeter.conf to match the new options.

 -- Stéphane Graber <stgraber@ubuntu.com>  Thu, 19 Jan 2012 14:07:30 -0500

unity-greeter (0.2.0-0ubuntu2) precise; urgency=low

---

### Post by paul_in_london on 2012-01-21
> **mc4man said:**
> unity-greeter has updated a couple of time in the last few days though they were for relatively insignificant things

Does this suggest their bug triaging isn't working very well?! I imagine it'll be fixed at some stage of course.

EDIT: I see there are 3 duplicate bugs listed on the page you posted. Nothing more than a couple of days old though, so I can't really complain too much!

---

### Post by mc4man on 2012-01-21
Yeah, it's only a few days & not a show stopper at all. For those that are using a single user only they can for the moment simply  add an account back, change greeters or if bored figure some way to change sessions outside of the unity-greeter

(I have no clue where the previous (exiting) session is stored for a user, likely not the same as previously, maybe something with accountservices, curiosity will probably not get the best of me here..

---

### Post by paul_in_london on 2012-01-21
> **mc4man said:**
> Yeah, it's only a few days & not a show stopper at all. For those that are using a single user only they can for the moment simply  add an account back, change greeters or if bored figure some way to change sessions outside of the unity-greeter

(I have no clue where the previous (exiting) session is stored for a user, likely not the same as previously, maybe something with accountservices, curiosity will probably not get the best of me here..

The funny thing is if GS hadn't broken today for a while (in such a way that I didn't have a usable desktop session) I still might not have noticed at all! As you say, though, it's not a major problem.

Thanks again for your input.

---

### Post by bmbaker on 2012-01-23
its still wking

"Re: Where have my lightdm session entries gone?!
The session-chooser menu (cog) is not displayed for the default user until you move to another user or guest session & then back to that user.

If you only have the one user (have disabled the guest session) then from the greeter login screen atm you're sol

The whole thing is weird & hopefully a bug rather than a "Design"

or in other words it will automatically select your last desktop session and to change you have to toigle usr accouts! bit strange but there you go :-)

---

