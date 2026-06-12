---
title: "Vidalia is now Broken"
date: 2014-02-19
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2014-02-19
Clean install todays daily iso.
```
 vidalia

(process:6317): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
An AppArmor policy prevents this sender from sending this message to this recipient, 0 matched rules; type="method_call", sender="(null)" (inactive) interface="org.
freedesktop.DBus" member="Hello" error name="(unset)" requested_reply="0" destination="org.freedesktop.DBus" (bus)

(<unknown>:6317): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
An AppArmor policy prevents this sender from sending this message to this recipient, 0 matched rules; type="method_call", sender="(null)" (inactive) interface="org.
freedesktop.DBus" member="Hello" error name="(unset)" requested_reply="0" destination="org.freedesktop.DBus" (bus)

(<unknown>:6317): IBUS-WARNING **: Unable to load /var/lib/dbus/machine-id: Failed to open file '/var/lib/dbus/machine-id': Permission denied

(<unknown>:6317): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory
 '/usr/share/gvfs/remote-volume-monitors': Permission denied


```
Worked up until today.

---

### Post by ventrical on 2014-02-19
Tried it on an install from last week. Rough shape.

---

### Post by ventrical on 2014-02-19
Won't let me send bug.

---

### Post by ventrical on 2014-02-19
Doing fresh install of todays daily now . Will test   and see if I can replicate that.

---

### Post by ventrical on 2014-02-19
Pretty well the same thing on todays daily.

---

### Post by QDR06VV9 on 2014-02-19
> **ventrical said:**
> Pretty well the same thing on todays daily.
Thanks Vent.;) Quite the Enigma isn't it.:D

---

### Post by ventrical on 2014-02-19
Yes. Even to get it to come up you have to uninstall it and then reinstall it. After the first run and then restart will not bring up the GUI. It gets ready to send all the data for a bug .. then tells you  it cannot send bug .. ?  etc... that's breakage here in U+1 :)

---

### Post by QDR06VV9 on 2014-02-19
> **ventrical said:**
> that's breakage here in U+1 :)

```
AppArmor policy prevents this sender from sending this message to this recipient
```

Happy Here in Testing Land:)
I think I'm narrowing in on something, I will report back if it pans out.
I really must be bored:lolflag: to do this!
I know I can hear it now. CLI

---

### Post by QDR06VV9 on 2014-02-20
No Joy:mad:
So wanted to see if tor-browser would even show vidalia but no go there either.
It dose work as tor without Vidalia GUI.

---

### Post by johnd03 on 2014-03-09
confirmed :(

[https://bugs.launchpad.net/ubuntu/+source/vidalia/+bug/1290107](https://bugs.launchpad.net/ubuntu/+source/vidalia/+bug/1290107)

---

### Post by hackan2 on 2014-10-06
Yes, it's broken but here is the solution, it worked for me ([#32]("https://bugs.launchpad.net/ubuntu/+source/vidalia/+bug/680192/comments/32") is me).
[#31]("https://bugs.launchpad.net/ubuntu/+source/vidalia/+bug/680192/comments/31") is the solution:

> I edited my /etc/apparmor.d/usr.bin.vidalia to look like this:
 #include <tunables/global>
 /usr/bin/vidalia {
  #include <abstractions/kde>
  #include <abstractions/nameservice>
   #include <abstractions/dbus-session>
  #include <abstractions/dconf>
  #include <abstractions/ibus>
  #include <abstractions/tor>
   owner @{HOME}/.vidalia/ rw,
  owner @{HOME}/.vidalia/** rwmk,
   /{var/,}run/tor/control rw,
  /{var/,}run/tor/control.authcookie r,
   /usr/share/icons/*/index.theme k,
   /etc/** rmk,
  /usr/** rmixk,
  @{PROC}/ r,
  @{PROC}/* rm,
  owner /{,var/}run/user/*/** rw,
  owner @{PROC}/** rm,
   owner @{HOME}/.tor/ rw,
  owner @{HOME}/.tor/** rwmk,
   # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.bin.vidalia>
}
 Then I just issued the following command to replace apparmor definitions:
 sudo apparmor_parser --replace /etc/apparmor.d/usr.bin.vidalia
 Now vidalia runs, I have tor connectivity & /var/log/syslog is clean of AppArmor messages.



---

### Post by cariboo on 2014-10-06
Problems with 14.04 should be posted in the main parts of the Forum. We are discussing utopic here. Thread closed.

---

