---
title: "Tandberg Quickstor RDX USB drive causes Ubuntu server to hang"
date: 2015-04-30
forum: Server Platforms
---

### Post by morningstar.fallen on 2015-04-30
Hi everyone, 

I have an instance of server 14.4.2 running without gui. When I connect my Tandberg Quickstor RDX USB drive to it and insert a cartridge, the system hangs on the following error:

[I][   224.480196] sd 3:0:0:0: [sdb] No Caching mode page found
[   224.480495] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   224.530020] sd 3:0:0:0: [sdb] No Caching mode page found
[   224.530310] sd 3:0:0:0: [sdb] Assuming drive cache: write through[/I]

When I eject the cartridge the system starts working again.

---

### Post by morningstar.fallen on 2015-04-30
It looks like this might help, but I am not sure what to do with it.
[https://onebytetoomany.co.uk/linux-preventing-no-caching-mode-page-present-errors-from-showing-up-on-boot.html](https://onebytetoomany.co.uk/linux-preventing-no-caching-mode-page-present-errors-from-showing-up-on-boot.html)

Do I just add **loglevel=2** as a new line anywhere in the grub?

---

### Post by morningstar.fallen on 2015-04-30
After adding GRUB_CMDLINE_LINUX_DEFAULT="loglevel=2" to the grub, the error still appears, but the tty starts to work normally when I press enter.

---

