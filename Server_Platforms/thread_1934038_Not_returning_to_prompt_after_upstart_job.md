---
title: "Not returning to prompt after upstart job"
date: 2012-03-01
forum: Server Platforms
---

### Post by ja27 on 2012-03-01
Hi all,

having several keyboards on my desk and being used to using the Ctrl-Alt-Del combination to call up the login window of Windows XP, several times I quite unintentionally succeeded in restarting the ubuntu server I'm experimenting with :D

A bit of googling revealed I should edit the /etc/inittab, but there is no such file in ubuntu 11.10 (Oneric). Further googling revealed the more ubuntu specific file /etc/event.d/control-alt-delete, which also didn't exist. But looking through /etc I discovered that the init directory contained a file named control-alt-delete.conf.

So I edited this file to look as follows:

```
# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed, and performs a safe reboot of the machine.

description "emergency keypress handling"
author      "Scott James Remnant <scott@netsplit.com>"

start on control-alt-delete

# task
# exec shutdown -r now "Control-Alt-Delete pressed"
console output
script
    echo "Shutdown / restart with Ctrl-Alt-Del is disabled!"
end script
```It works fine, except for one small irritation. After output of the message "Shutdown / restart with Ctrl-Alt-Del is disabled!" it seems to hang, and the user is forced to press ENTER to return to the normal bash or login input prompt.

Is there any way to change this behavior? Or is this the normal behavior of upstart scripts?

Thanks.

---

