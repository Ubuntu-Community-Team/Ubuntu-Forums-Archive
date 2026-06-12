---
title: "gconftool"
date: 2012-09-04
forum: Ubuntu Dev Link Forum
---

### Post by mikemike1232 on 2012-09-04
hello i need to bind a hot key, i use gconftool and it works, not in postinst script in deb package. i use command like```
 gconftool-2 -s /apps/metacity/keybinding_commands/command_1 -t string /path/to/file
gconftool-2 -s /apps/metacity/global_keybings/run_command_1 -t string <some><keys>

``` 
but in postinst script it calls under sudo so it doesn't work(work's but on another user), so what i can do ( i read somethink about --config-source but it doesn't work too) mb it's possible to use sudo -u $SUDO_USER but it doesn't help.
so how it's possible to this.
Thanks.

---

