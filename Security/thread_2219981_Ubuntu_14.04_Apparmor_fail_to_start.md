---
title: "Ubuntu 14.04 Apparmor fail to start"
date: 2014-04-26
forum: Security
---

### Post by Laiquendi on 2014-04-26
Hey there, I didn't find it to be posted yet, so if you have any idea on how to deal with this, I'm grateful:

When I try to start one profile at a time, it works.
When I try to start more than one at a time, it gives me this, and stops:
```
# sudo aa-complain /etc/apparmor.d/usr.bin.*
Setting /etc/apparmor.d/usr.bin.chromium-browser to complain mode.
Traceback (most recent call last):
  File "/usr/sbin/aa-complain", line 30, in <module>
    tool.cmd_complain()
  File "/usr/lib/python3/dist-packages/apparmor/tools.py", line 171, in cmd_complain
    apparmor.read_profiles()
  File "/usr/lib/python3/dist-packages/apparmor/aa.py", line 2564, in read_profiles
    read_profile(profile_dir + '/' + file, True)
  File "/usr/lib/python3/dist-packages/apparmor/aa.py", line 2590, in read_profile
    profile_data = parse_profile_data(data, file, 0)
  File "/usr/lib/python3/dist-packages/apparmor/aa.py", line 2843, in parse_profile_data
    store_list_var(filelist[file]['lvar'], list_var, value, var_operation)
  File "/usr/lib/python3/dist-packages/apparmor/aa.py", line 3274, in store_list_var
    raise AppArmorException(_('An existing variable redefined: %s') % list_var)
apparmor.common.AppArmorException: 'An existing variable redefined: @{TFTP_DIR}'
```

When I try ALL at a time, it shows the same error but starts with additional one:
```
Profile for /etc/apparmor.d/abstractions not found, skipping
```

It happens with both complain and enforce modes, with sudo and from root console.

Ideas are welcome, thank you.

---

