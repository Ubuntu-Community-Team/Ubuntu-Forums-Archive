---
title: "Dual Booting with Burg"
date: 2012-05-07
forum: The Cafe
---

### Post by phosphide on 2012-05-07
I thought it would be appropriate to post this here, since it's not necessarily a Ubuntu issue. Though, I tried to install Burg following this tutorial.

[http://howtoubuntu.org/how-to-make-your-dual-boot-better-with-burg/](http://howtoubuntu.org/how-to-make-your-dual-boot-better-with-burg/)

Though, when I attempt to run grub-customizer, I get this error:

```
burg-mkconfig couldn't be executed successfully. error message:
 /usr/sbin/burg-mkconfig: 8: /etc/default/burg: Syntax error: "(" unexpected
```

Here is the output in the terminal when I run from the terminal:

```
(grub-customizer:11639): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.82Z7DW': No such file or directory

(grub-customizer:11639): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

Any suggestions on what's going on here?

Edit: Should have provided a little bit more information. Running 10.04 and 12.04 on the dual boot. In addition, grub-customizer won't run at all when I select to configure the Burg option, but does work in the standard grub options.

---

