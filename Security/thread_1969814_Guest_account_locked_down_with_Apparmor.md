---
title: "Guest account locked down with Apparmor?"
date: 2012-04-30
forum: Security
---

### Post by Paqman on 2012-04-30
I've just upgraded my netbook to Precise. The guest account is no longer able to access assets mounted by another user. I'd like to switch that back to the previous behaviour, where the guest accoutn could access something mounted to /media by another user.

Is this done through Apparmor? I've had a quick look at the guest account profile at /etc/apparmor.d/lightdm-guest-session but I'm not sure what I'm doing.

---

### Post by bodhi.zazen on 2012-05-01
Check the logs and add a rule

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by Paqman on 2012-05-03
> **bodhi.zazen said:**
> Check the logs and add a rule

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

Since the default behaviour for users is to allow this, surely it'd be a matter of deleting the rule that precludes it in the special case of the guest account?

The guest account profile is here:
```

# vim:syntax=apparmor
# Profile for restricting lightdm guest session 
# Author: Martin Pitt <martin.pitt@ubuntu.com>

#include <tunables/global>

/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper {
  #include <abstractions/authentication>
  #include <abstractions/nameservice>
  #include <abstractions/wutmp>
  /etc/compizconfig/config rw, # bug in compiz https://launchpad.net/bugs/697678
 
  / r,
  /bin/ rmix,
  /bin/fusermount Px,
  /bin/** rmix,
  /cdrom/ rmix,
  /cdrom/** rmix,
  /dev/ r,
  /dev/** rmw, # audio devices etc.
  owner /dev/shm/** rmw,
  /etc/ r,
  /etc/** rmk,
  /etc/gdm/Xsession ix,
  /lib/ r,
  /lib/** rmixk,
  /lib32/ r,
  /lib32/** rmixk,
  /lib64/ r,
  /lib64/** rmixk,
  owner /media/ r,
  owner /media/** rmwlixk,  # we want access to USB sticks and the like
  /opt/ r,
  /opt/** rmixk,
  @{PROC}/ r,
  @{PROC}/* rm,
  @{PROC}/asound rm,
  @{PROC}/asound/** rm,
  @{PROC}/ati rm,
  @{PROC}/ati/** rm,
  owner @{PROC}/** rm,
  # needed for gnome-keyring-daemon
  @{PROC}/*/status r,
  /sbin/ r,
  /sbin/** rmixk,
  /sys/ r,
  /sys/** rm,
  /tmp/ rw,
  owner /tmp/** rwlkmix,
  /usr/ r,
  /usr/** rmixk,
  /var/ r,
  /var/** rmixk,
  /var/guest-data/** rw, # allow to store files permanently
  /var/tmp/ rw,
  owner /var/tmp/** rwlkm,
  /{,var/}run/ r,
  # necessary for writing to sockets, etc.
  /{,var/}run/** rmkix,
  /{,var/}run/shm/** wl,

  capability ipc_lock,

  # silence warnings for stuff that we really don't want to grant
  deny capability dac_override,
  deny capability dac_read_search,
  #deny /etc/** w, # re-enable once LP#697678 is fixed
  deny /usr/** w,
  deny /var/crash/ w,
}

```

But I don't understand why this is blocking access to /media, since everything in /media seems to be listed as rmwlixk.

---

### Post by Hungry Man on 2012-05-03
The /media/ has an owner conditional attached. That means that the program/ user can only access files that it has created. Removing the owner conditional would likely fix this issue, though obviously it is less secure.

---

### Post by bodhi.zazen on 2012-05-03
> **Hungry Man said:**
> The /media/ has an owner conditional attached. That means that the program/ user can only access files that it has created. Removing the owner conditional would likely fix this issue, though obviously it is less secure.

Nice one ^^

---

### Post by Paqman on 2012-05-03
> **Hungry Man said:**
> The /media/ has an owner conditional attached. That means that the program/ user can only access files that it has created. Removing the owner conditional would likely fix this issue, though obviously it is less secure.

Thanks a lot, that has indeed done the trick!

---

### Post by Hungry Man on 2012-05-03
You might want to consider a 

/media/ r, 
rule

and a 
owner /media/ rmwlixk,

rule

That way anyone can read but only the owner of the files can perform other actions.

This is safer.

If you need it to be anyone modifying the data though you can just leave it as is.

---

