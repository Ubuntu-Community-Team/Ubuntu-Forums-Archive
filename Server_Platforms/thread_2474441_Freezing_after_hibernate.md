---
title: "Freezing after hibernate"
date: 2022-04-29
forum: Server Platforms
---

### Post by marko0205 on 2022-04-29
Hi guys,

When I put my server to hibernate, shortly after the command:
```
systemctl hibernate
```
The pc freezes and I have to force a restart (when I return at home)

The last logs after the command execution are below:
```
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos NetworkManager[1065]: <info>  [1651242140.1856] manager: sleep: sleep requested (sleeping: no  enabled: yes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos NetworkManager[1065]: <info>  [1651242140.1857] device (p2p-dev-wlo1): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos NetworkManager[1065]: <info>  [1651242140.1861] manager: NetworkManager state is now ASLEEP[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd[1]: Reached target Sleep.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd[1]: Starting Record successful boot for GRUB...[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd[1]: Starting Hibernate...[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd[1]: grub-common.service: Succeeded.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd[1]: Finished Record successful boot for GRUB.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos kernel: [ 5526.423244] PM: Image not found (code -16)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd[1]: Starting GRUB failed boot detection...[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd[1]: grub-initrd-fallback.service: Succeeded.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd[1]: Finished GRUB failed boot detection.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos systemd-sleep[7387]: Suspending system...[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Apr 29 14:22:20 marcos kernel: [ 5526.466756] PM: hibernation entry[/FONT][/COLOR]

```

Could someone more experienced than me, figure out the problem? thanks anyway

SO [COLOR=#000000][FONT=Menlo]Ubuntu 20.04.4[/FONT][/COLOR], installed on SSD

Other "maybe" necessary info:
```
[COLOR=#000000][FONT=Menlo][COLOR=#39c026]**rack@marcos**[/COLOR]:[COLOR=#5620f4]**~**[/COLOR]$ cat /etc/default/grub[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# If you change this file, run 'update-grub' afterwards to update[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# /boot/grub/grub.cfg.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# For full documentation of the options in this file, see:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#   info -f grub -n 'Simple configuration'[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_DEFAULT=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_TIMEOUT_STYLE=hidden[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_TIMEOUT=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_CMDLINE_LINUX_DEFAULT=""[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GRUB_CMDLINE_LINUX=""[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# This works with Linux (no patch required) and with any kernel that obtains[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# Uncomment to disable graphical terminal (grub-pc only)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#GRUB_TERMINAL=console[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# The resolution used on graphical terminal[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# note that you can use only modes which your graphic card supports via VBE[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# you can see them in real GRUB with the command `vbeinfo'[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#GRUB_GFXMODE=640x480[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#GRUB_DISABLE_LINUX_UUID=true[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# Uncomment to disable generation of recovery mode menu entries[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#GRUB_DISABLE_RECOVERY="true"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# Uncomment to get a beep at grub start[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#GRUB_INIT_TUNE="480 440 1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#39c026]**rack@marcos**[/COLOR]:[COLOR=#5620f4]**~**[/COLOR]$ dmesg | grep "Command line"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][    0.000000] [COLOR=#ca3323]**Command line**[/COLOR]: BOOT_IMAGE=/vmlinuz-5.4.0-109-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro[/FONT][/COLOR]

```

---

