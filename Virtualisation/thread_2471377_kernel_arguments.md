---
title: "kernel arguments"
date: 2022-01-28
forum: Virtualisation
---

### Post by jcross009 on 2022-01-28
root=/dev/vda ro vdso=0 showopts vga=normal console=tty1 console=ttyS0,115200 3

Under KVM the above parameters are fed to the kernel?

I get the root part. and the VGA part.

But I don't know what 

[LIST=1]
[*]vdso=0
[*]showopts
[*]and what the 3 is doing after the serial configuration.  I have another that has 2 instead.
[/LIST]

Obviously I googled these but I can't find the correct term for what I'm looking for, as its inconsistently referred to as kernel arguments, command line, args, boot arguments etc.  Sometimes its the same thing sometimes not.  I found man pages with vdso defined but I am none the wiser at all.
I have read various sources for console= but none of them have a 2 or 3 after them, and its hard to know if its part of the console parameter or something else.  I thought it may be pipe messages to that device after we reach a certain run level or something.

---

### Post by schragge on 2022-01-28
The primary source of documentation for kernel boot parameters is the kernel itself. See [The kernel&#8217;s command-line parameters]("https://www.kernel.org/doc/html/latest/admin-guide/kernel-parameters.html") in *The Linux kernel user&#8217;s and administrator&#8217;s guide*. The **console=** parameter is described in [Linux Serial Console]("https://www.kernel.org/doc/html/latest/admin-guide/serial-console.html").

That **3** at the end has nothing to do with **console=**. It's not a *kernel* boot parameter at all. Rather a systemd command line parameter specifying runlevel. From the [systemd(1)]("https://www.mankier.com/1/systemd#Kernel_Command_Line-3") man page:
> [FONT=monospace]2[/FONT], [FONT=monospace]3[/FONT], [FONT=monospace]4[/FONT], [FONT=monospace]5[/FONT][INDENT]Boot into the specified legacy SysV runlevel. These are equivalent to [FONT=monospace]systemd.unit=runlevel2.target[/FONT], [FONT=monospace]systemd.unit=runlevel3.target[/FONT], [FONT=monospace]systemd.unit=runlevel4.target[/FONT], and [FONT=monospace]systemd.unit=runlevel5.target[/FONT], respectively, and provided for compatibility reasons and to be easier to type.[/INDENT]


The **showopts** option lists boot options on the GRUB command line.
> Actually what this keyword does is to hide the options that are listed before it and show those that appear after it.

If you remove [FONT=monospace]showopts[/FONT] from the default entry line [...], then at the next boot you will see exactly which boot parameters are being passed to the kernel when it loads. You will also be able to edit these parameters in the initial boot screen

---

