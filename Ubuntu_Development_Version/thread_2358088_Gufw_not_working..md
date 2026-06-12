---
title: "Gufw not working."
date: 2017-04-09
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-04-09
Tried running gufw from desktop, but only an invisible window pops up and closes.

This is what I get from terminal:

```
 gufw
Traceback (most recent call last):
  File "/usr/share/gufw/gufw/gufw.py", line 30, in <module>
    gufw = Gufw(controler.get_frontend())
  File "/usr/share/gufw/gufw/gufw/view/gufw.py", line 81, in __init__
    self.winadd = Add(self)
  File "/usr/share/gufw/gufw/gufw/view/add.py", line 43, in __init__
    self._set_initial_values()
  File "/usr/share/gufw/gufw/gufw/view/add.py", line 101, in _set_initial_values
    for ifaceName in self.gufw.fw.get_net_interfaces():
  File "/usr/share/gufw/gufw/gufw/model/frontend.py", line 126, in get_net_interfaces
    return self.firewall.get_net_interfaces(exclude_iface)
  File "/usr/share/gufw/gufw/gufw/model/firewall.py", line 251, in get_net_interfaces
    all_faces = self.backend.get_net_interfaces()
  File "/usr/share/gufw/gufw/gufw/model/ufw_backend.py", line 462, in get_net_interfaces
    cmd = self._run_cmd(cmd_ifaces)
  File "/usr/share/gufw/gufw/gufw/model/ufw_backend.py", line 37, in _run_cmd
    proc = subprocess.Popen(cmd, shell=False, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
  File "/usr/lib/python3.5/subprocess.py", line 676, in __init__
    restore_signals, start_new_session)
  File "/usr/lib/python3.5/subprocess.py", line 1282, in _execute_child
    raise child_exception_type(errno_num, err_msg)
FileNotFoundError: [Errno 2] No such file or directory: 'netstat'
```

---

### Post by mc4man on 2017-04-09
Install net-tools

---

### Post by Hewjr100 on 2017-04-09
Ok will do.

Henry

---

### Post by Hewjr100 on 2017-04-09
it's working now.  Thanks for your help.

Henry

---

### Post by jbicha on 2017-04-09
Please file a bug for this issue.

---

### Post by mc4man on 2017-04-09
> **jbicha said:**
> Please file a bug for this issue.

[https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1681250](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1681250)

---

