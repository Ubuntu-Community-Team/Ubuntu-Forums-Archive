---
title: "5 login attempt failed without user invoking"
date: 2009-12-13
forum: Security
---

### Post by r3kdoob on 2009-12-13
Hi, i'm using karmic.
Recently my karmic logout automatically and it happened twice.
On the first time, i know when i'm shutting down my laptop. Usually it will switch to console (same as press ctrl-alt-F1), thus i saw about 6 login attempt for a few second.

I checked the log files /var/log/auth.log and noticed some entries as below and the time is exactly same as the 'automatic logout' happened. it also same when the 2nd time occured. Could anyone tell me what actuall happened.
Thanks in advance :)

```

Dec 13 19:33:53 rekdoob login[1265]: pam_unix(login:auth): auth could not identify password for [9*+9"9!1 HH-.92 9**************************************************************9+'. 94&HHH. &&9&KKKKKKKKKKKKKKKKKMMMMMMMMMMMMMMMMMM1 4&&9&9******9*************&9&**H6SPMMMPKKKPMMHMMPPPMMMHHPKKKHPPPMM..MMPPM//MMPK!!.1!&.1!&.1!"&H&KKKKKKKKKKK&9]
Dec 13 19:33:53 rekdoob gdm-session-worker[1903]: pam_unix(gdm:session): session closed for user rek
Dec 13 19:33:53 rekdoob gnome-keyring-daemon[1936]: dbus failure unregistering from session: Connection is closed
Dec 13 19:33:56 rekdoob login[1265]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Dec 13 19:33:56 rekdoob login[1265]: pam_securetty(login:auth): unexpected response from failed conversation function
Dec 13 19:33:56 rekdoob login[1265]: pam_securetty(login:auth): cannot determine username
Dec 13 19:33:59 rekdoob login[1265]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Dec 13 19:33:59 rekdoob login[1265]: pam_securetty(login:auth): unexpected response from failed conversation function
Dec 13 19:33:59 rekdoob login[1265]: pam_securetty(login:auth): cannot determine username
Dec 13 19:34:02 rekdoob login[1265]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Dec 13 19:34:02 rekdoob login[1265]: pam_securetty(login:auth): unexpected response from failed conversation function
Dec 13 19:34:02 rekdoob login[1265]: pam_securetty(login:auth): cannot determine username
Dec 13 19:34:03 rekdoob gdm-session-worker[7059]: pam_unix(gdm:session): session opened for user rek by (uid=0)
Dec 13 19:34:03 rekdoob gdm-session-worker[7059]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :1
Dec 13 19:34:06 rekdoob seahorse-daemon[7168]: init gpgme version 1.1.8
Dec 13 19:34:06 rekdoob login[1265]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Dec 13 19:34:06 rekdoob login[1265]: pam_securetty(login:auth): unexpected response from failed conversation function
Dec 13 19:34:06 rekdoob login[1265]: pam_securetty(login:auth): cannot determine username
Dec 13 19:34:09 rekdoob login[1265]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Dec 13 19:34:09 rekdoob login[1265]: TOO MANY LOGIN TRIES (5) on '/dev/tty2' FOR 'UNKNOWN'
Dec 13 19:34:09 rekdoob login[1265]: pam_mail(login:session): cannot determine username
Dec 13 19:34:09 rekdoob login[1265]: pam_unix(login:session): close_session - error recovering username

```

---

### Post by f00buntu on 2010-01-22
Hello,

I've been running karmic for a few months now. I've experienced the exact same automatic logout event you described twice.

From /var/log/auth.log:
```
Jan 21 10:05:14 - login[2412]: pam_unix(login:auth): auth could not identify password for [5 9PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP92/9209&.!&1.401&S. 9*&&9&2/9445* *****21429445* *!29!9445* 2 /.HG 929445* *. 9445* &. 494429!9. 9-&. 9442/9-9445****************. 92&.9*. 944292H9]
Jan 21 10:05:16 - gdm-session-worker[1660]: pam_unix(gdm:session): session closed for user foo
Jan 21 10:05:18 - login[2412]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Jan 21 10:05:18 - login[2412]: pam_securetty(login:auth): unexpected response from failed conversation function
Jan 21 10:05:18 - login[2412]: pam_securetty(login:auth): cannot determine username
Jan 21 10:05:21 - login[2412]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Jan 21 10:05:21 - login[2412]: pam_securetty(login:auth): unexpected response from failed conversation function
Jan 21 10:05:21 - login[2412]: pam_securetty(login:auth): cannot determine username
Jan 21 10:05:23 - login[2412]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Jan 21 10:05:23 - login[2412]: pam_securetty(login:auth): unexpected response from failed conversation function
Jan 21 10:05:23 - login[2412]: pam_securetty(login:auth): cannot determine username
Jan 21 10:05:27 - login[2412]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Jan 21 10:05:27 - login[2412]: pam_securetty(login:auth): unexpected response from failed conversation function
Jan 21 10:05:27 - login[2412]: pam_securetty(login:auth): cannot determine username
Jan 21 10:05:30 - login[2412]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Jan 21 10:05:30 - login[2412]: TOO MANY LOGIN TRIES (5) on '/dev/tty2' FOR 'UNKNOWN'
Jan 21 10:05:30 - login[2412]: pam_mail(login:session): cannot determine username
Jan 21 10:05:30 - login[2412]: pam_unix(login:session): close_session - error recovering username
Jan 21 10:05:40 - gdm-session-worker[2902]: pam_unix(gdm:session): session opened for user foo by (uid=0)
Jan 21 10:05:40 - gdm-session-worker[2902]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :1
Jan 21 10:05:44 - seahorse-daemon[3034]: init gpgme version 1.1.8

```

The last time it occurred i noticed the event coincides with an (involuntary) graphics mode change to a lower resolution just before logging me out of my desktop session. 

From /var/log/messages
```
Jan 21 10:05:15 - kernel: [ 3746.743401] [drm] LVDS-8: set mode 1400x1050 19
Jan 21 10:05:17 - kernel: [ 3749.127655] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:18 - kernel: [ 3749.257725] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:18 - kernel: [ 3749.513854] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:18 - kernel: [ 3749.679558] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:18 - kernel: [ 3749.849181] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:18 - kernel: [ 3749.978986] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:19 - kernel: [ 3750.235061] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:19 - kernel: [ 3750.401831] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:24 - kernel: [ 3755.543981] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:24 - kernel: [ 3755.675021] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:24 - kernel: [ 3755.932009] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:24 - kernel: [ 3756.098452] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:25 - kernel: [ 3756.284677] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:25 - kernel: [ 3756.416612] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:25 - kernel: [ 3756.674031] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:25 - kernel: [ 3756.839153] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:25 - kernel: [ 3757.011566] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:25 - kernel: [ 3757.142105] [drm] DAC-6: set mode 640x480 0
Jan 21 10:05:26 - kernel: [ 3757.399703] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:26 - kernel: [ 3757.564956] [drm] TV-16: set mode NTSC 480i 0
Jan 21 10:05:41 - pulseaudio[3000]: pid.c: Stale PID file, overwriting.

```

Graphics hardware is an onboard intel 915GM.

At the time of the last occurrence i was using firefox and moving some files to my ubuntu one cloud storage thingy.

---

### Post by P.T. on 2010-05-27
Does someone have an explanation for this, as this also happens to me at 10.04.

It really is an annoying thing, as my screen goes black no matter what I'm working on.

---

