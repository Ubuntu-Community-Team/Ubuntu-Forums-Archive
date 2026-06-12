---
title: "Apparmor profile for firefox from repositories + aa-tools"
date: 2015-01-24
forum: Security
---

### Post by damatta2 on 2015-01-24
Hello,

I'm using the official apparmor profile for firefox in enforce mode but keep getting denial messages such as this:

> kernel: [ 3610.671282] audit: type=1400 audit(1421929442.220:69): apparmor="DENIED" operation="ptrace" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" pid=3063 comm="firefox" requested_mask="trace" denied_mask="trace" peer="/usr/lib/firefox/firefox{,*[^s][^h]}"
AND
> dbus[1696]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/gtk/vfs/mounttracker" interface="org.gtk.vfs.MountTracker" member="ListMountableInfo" mask="send" name=":1.5" pid=3066 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" peer_pid=1732 peer_profile="unconfined"

I was wondering if it is safe to allow ptrace for firefox profile itself by using -> > ptrace (trace) peer=@{profile_name}, and allowing dbus for mounttracker.

The second issue is aa-tools. I'm on Lubuntu and aa-genprof and aa-logprof are not working for me, it seems these tools are not reading the profile (even if I set it to read /var/syslog). Anyone else with this issue?

Thanks in advance.

---

