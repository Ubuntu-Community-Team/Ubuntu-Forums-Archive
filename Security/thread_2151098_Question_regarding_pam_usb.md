---
title: "Question regarding pam_usb"
date: 2013-06-03
forum: Security
---

### Post by kenhuman on 2013-06-03
Firstly, my goal is to cause my machine to lock any time a usb key is removed, and then open and present a password prompt when the usb key is replaced.

I've downloaded and installed the pam_usb module to accomplish this.  The following is a snippet from /etc/pam.d/common-auth:

```
auth    required     pam_usb.so
auth    [success=1 default=ignore]    pam_unix.so nullok_secure try_first_pass

```

pam_usb correctly checks for the presence of the usb key and I'm allowed to sudo after entering a password as expected.  However, I've found that upon restarting the machine, with the usb key installed and using my correct password, the machine claims that my password is invalid.  Relevant parts of /var/log/auth.log follow:

```
Jun  3 09:56:59 ken-MS-7681 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jun  3 09:56:59 ken-MS-7681 lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Jun  3 09:57:02 ken-MS-7681 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ken"
Jun  3 09:57:02 ken-MS-7681 pam_usb[2034]: pam_usb v0.5.0
Jun  3 09:57:02 ken-MS-7681 pam_usb[2034]: Authentication request for user "ken" (lightdm)
Jun  3 09:57:02 ken-MS-7681 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ken"
Jun  3 09:57:02 ken-MS-7681 pam_usb[2037]: pam_usb v0.5.0
Jun  3 09:57:02 ken-MS-7681 pam_usb[2037]: Authentication request for user "ken" (lightdm)
Jun  3 09:57:02 ken-MS-7681 dbus[1269]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=110 pid=2042 comm="/usr/lib/indicator-session/indicator-session-servi") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1687 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jun  3 09:57:02  dbus[1269]: last message repeated 3 times
Jun  3 09:57:02 ken-MS-7681 pam_usb[2037]: Device "Key" is connected (good).
Jun  3 09:57:02 ken-MS-7681 pam_usb[2037]: Performing one time pad verification...
Jun  3 09:57:03 ken-MS-7681 pam_usb[2037]: Pad checking failed !
Jun  3 09:57:03 ken-MS-7681 dbus[1269]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.26" (uid=0 pid=1980 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.7" (uid=0 pid=1552 comm="NetworkManager ")
Jun  3 09:57:03 ken-MS-7681 pam_usb[2037]: Access denied.
Jun  3 09:57:03 ken-MS-7681 dbus[1269]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.39" (uid=110 pid=2044 comm="/usr/lib/x86_64-linux-gnu/indicator-datetime-servi") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1687 comm="/usr/sbin/console-kit-daemon --no-daemon ")

```

I assumed that perhaps pam_usb is unable to check the pad because my home directory is encrypted, so I swapped the two rules in /etc/pam.d/common-auth as so:

```
auth    [success=1 default=ignore]    pam_unix.so nullok_secure try_first_pass
auth    required     pam_usb.so

```

This leads to sudo telling me that my password is invalid, and if I break or pass 3 tries, pam_usb authentication succeeds (however I am not granted access).

If anyone is able to assist, it'd be greatly appreciated.

---

