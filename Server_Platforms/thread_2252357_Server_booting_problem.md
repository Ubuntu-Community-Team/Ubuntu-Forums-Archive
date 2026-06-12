---
title: "Server booting problem"
date: 2014-11-11
forum: Server Platforms
---

### Post by rouvalis on 2014-11-11
We have our web page in a virtual ubuntu server in Germany. We had to restart the server yesterday and since then the server is not starting. The problem is that our administrator had an terrible accident and he is not capable to solve anything. I am not an experienced linux user but a have an idea. The server disk is spliced in thee partitions the first is swap the second the boot and grub and the third the main linux.

From yesterday when the server restarted stops in this point.
The company our server is can give us a vnc console to our server and a resque linux distribution that runs in memory temporarily.
With this tools can we solve the problem; 
```
[COLOR=#3C3B37][FONT=Lucida Grande][    8.0986951 EXT3-fs (sda3): mounted filesystem with ordered data mode[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]Begin: Running /scripts/loca1-bottom ... done, done .[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]Begin: Running /scripts/init-bottom ... done.[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]Target filesystem doesn't have requested /sbin/init.[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]/bin/sh: &#920;: Can't open ro[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.74&#920;5331 Kernel panic - not syncing: Attempted to kill in it![/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7410241    Pid: 1, comm:    sh Not tainted 3.2.&#920;-38-generic-pae #61-Ubuntu[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7415171    Call Trace:[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7418881    [<cl592426>l    ? printk+0x2d/0x2f[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7423361    [<cl5922f4>l    panic+0x5c/0xl61[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7427351    [<cl05e0a4>l    forget_original_parent+0xle4/0xlf0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7432351    [<cl0eb070>l    ? perf_cgroup_attach_task+0x20/0x20[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7437911    [<cl05e0c3>l    exit_notify+0x13/0x100[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7445131    [<cl05e85e>l    do_exit+0xlae/0x3c0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7449711    [<cl05ebc8>l    do_group_exit+0x38/0xa0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7454011    [<cl05ec48>l    sys_exit_group+0xl8/0x20[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande][    8.7458391    [<cl5a8394>l    sysca1l_ca11+0x7/0xb[/FONT][/COLOR]

```
The company our server is can give us a vnc console to our server and a resque linux distribution that runs in memory temporarily.
With this tools can we solve the problem without loosing anything?

---

### Post by slickymaster on 2014-11-12
[I]
Moved to the [/I]**Server Platforms*** sub-forum*

Hi rouvalis, welcome to the forums.

I've edit your post, adding code tags to it. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by tgalati4 on 2014-11-12
Looks like a disk problem:

```
sudo smartctl -a /dev/sda
```

Review the SMART parameters of the drive to see if there is a mechanical problem.

The kernel panic output is not helpful at this point.

I do hope your administrator gets  back on his feet soon.

---

### Post by Jonathan L on 2014-11-12
Hi Rouvalis

| The server disk is spliced in thee partitions the first is swap the second the boot and grub and the third the main linux.

Just wondering if you're quite sure you know which partition is which?  I'd suggest trying to mount the partitions (read-only, of course) and having a look to see which have grub, which have sensible looking /bin /sbin /boot and so on, just to double check.

Wishing a speedy recovery to your data, and more importantly to your colleague.

Kind regards,
Jonathan.

---

