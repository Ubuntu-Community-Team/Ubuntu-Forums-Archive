---
title: "firestarter service won't run"
date: 2007-02-15
forum: Server Platforms
---

### Post by nilsja on 2007-02-15
**Hi,**

i have a problem getting firestarter start automaticly. i'm not interrested in the gui, but the service also doesn't run and i don't know how to fix this. when i look at tty8 i see red [fail] of trying firestarter to run. i'm running feisty, installed firestarter through synaptics and when i manually start it and enter the password it works perfectly fine. i also tried to edit sudoers, but that also didn't work.

when i put the gksu firestarter line into rc.local, my desktop freezes after bootup. :confused: 

any ideas?

---

### Post by nilsja on 2007-02-17
shouldn't the service start automaticly in standard installation? what could i have done wrong or are there any logs that could help anybody to help me? 

i feel such naked without my firewall...

---

### Post by benson444 on 2007-02-17
I believe that the firewall in Ubuntu is called iptables and is built into the kernel. Firestarter is just one GUI for configuring the firewall. You only need to run Firestarter when you need to change iptable's settings. You don't need to have it running to enable a firewall.

---

### Post by nilsja on 2007-02-17
that is what i also thought, but my ports are not closed when i reoot my computer. that just works, when the firestarter daemon is running and by that configureing iptables. or am i getting sth really wrong?

---

### Post by meng on 2007-02-17
This is not normal behavior. How do you know that your ports are open?

---

### Post by benson444 on 2007-02-17
Google for "shields up" and test your ports. Having Firestarter running should make no difference.

---

### Post by nilsja on 2007-02-17
hi,

i tested my ports on [http://www.grc.com/default.htm](http://www.grc.com/default.htm) and the ShieldsUP! link. when i start firestarter manually, it works fine, everything stealth. But on startup, the service does not start. i'm repeating me, but after bootup on tty8 i see the [[COLOR="Red"]fail[/COLOR]] behind the line: starting the firestarter firewall...

---

### Post by meng on 2007-02-17
Sorry to repeat myself, but you didn't explicitly state that you had evidence of your ports being open without firestarter, so I just want to check - how do you know the firewall is inactive? This is an important question to answer because it suggests a completely different and serious problem to not being able to start firestarter itself.
The point is that firestarter is not a firewall.

---

### Post by nilsja on 2007-02-17
sorry for not making clear what i mean.

i know it, because when i run firestarter through terminal with sudo and than test my ports online (as described above), they are stealthed, but a scan after a reboot everything is like before even installing firestarter. the ports are not open, oh my..., but they are present, they answer closed. (at the first time i ran the scan, i found an open ssh port, which i closed through services manager in gnome)

---

### Post by nilsja on 2007-02-17
a little more significant is perhaps the sudo ps -A, no firestarter appears...

where in ubuntu the bootup daemons get loaded and with which rights, or is there another way to start sth that needs root rights without entering the password?

edit: another interesting thing: once started and closed the gui, the ports are still stealthed.

---

### Post by meng on 2007-02-17
Hope this helps.
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by Prognatus on 2007-02-18
I have the same problem as the thread starter. I've already tried the recipe outlined in that link, without success. BTW, it says "Edit your /etc/sudoers file in your favorite text editor ". This is wrong. You must edit this file with...

[color=green]$ export EDITOR=gedit && sudo visudo[/color] <--- optional
[color=green]$ sudo visudo[/color]

...or you can't issue any sudo commands anymore after reboot. The file will not be readable by Linux and you'll have to re-edit it from a Live-CD or something to fix it again.

The problem I have is that even after adding...

**%**username ALL= NOPASSWD: /usr/**s**bin/firestarter

...firestarter still doesn't run after reboot. Nothing happens at all. No errors, nothing.

If I try...

[color=green]$ sudo -K
$ sudo /usr/sbin/firestarter[/color]

...I get this error:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

(firestarter:14930): Gtk-WARNING **: cannot open display:
```

BTW, here's a link that explains the same topic a little better I think, although it made no difference for me to solve my problem: **[http://ubuntu-tutorials.blogspot.com/2007_02_01_archive.html](http://ubuntu-tutorials.blogspot.com/2007_02_01_archive.html)**  (look a little down the page, in the Feb 5th. entry).

**So, does anyone know what this error means?**

---

### Post by nilsja on 2007-02-18
meng: i also aready tried the sudoers way, but that didn't work.


@Prognatus
have you tried to not start the gui, but the daemon with
gksu /etc/init.d/firestarter start

?

---

### Post by Prognatus on 2007-02-18
No, not directly, but indirectly I think by enabling the preference option

[x] Start/restart firewall on program startup.

Isn't that the same?

If so, this doesn't work either. I end up with a "Insufficient privileges" prompt after reboot. So the added line in /etc/sudoers clearly doesn't work in this case.

---

### Post by maulattu on 2007-02-18
mmhhh... do you have recompiled your kernel with the latest one (2.6.20)?
in this case, take a look at:
[http://www.ubuntuforums.org/showthread.php?t=359298](http://www.ubuntuforums.org/showthread.php?t=359298)

---

### Post by Prognatus on 2007-02-18
No, I'm using the default kernel in Dapper - 2.6.15-28 I think it is now.

---

### Post by nilsja on 2007-02-18
> nils@nils:~$ cat /proc/version
Linux version 2.6.20-8-generic (root@vernadsky) (gcc version 4.1.2 20070129 (prerelease) (Ubuntu 4.1.1-31ubuntu2)) #2 SMP Tue Feb 13 05:18:42 UTC 2007i don't know who vernadsky is, but i'm running the latest updates.

---

### Post by nilsja on 2007-02-18
i don't remember to have changed anything (apart from todays feisty updates), but now i get a password prompt (this gui one) while booting up. because "/etc/firestarter 'start'" could change my system...:confused: my xfce autostart and my rc.local don't contain any firestarter entrys...

---

### Post by nilsja on 2007-02-18
and this password prompt still appears after a not working remove --purge of firestarter.. HELP!

---

### Post by nilsja on 2007-02-18
here is the error of a again installed and then remove --purge of firestarter> Lösche Konfigurationsdateien von firestarter ...
dpkg: Fehler beim Bearbeiten von firestarter (--purge):
 Unterprozess post-removal script gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)translated to my bad english:> deleting config files of firestarter
dpkg: Error while working on firestarter (--purge):
subprocess post-removal script gave errorvalue 1 back
Error appeared while working on:
firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)

@maulattu
i would be so happy to have the prblem described in the thread of your link...

---

### Post by maulattu on 2007-02-20
> **nilsja said:**
> here is the error of a again installed and then remove --purge of firestartertranslated to my bad english:

@maulattu
i would be so happy to have the prblem described in the thread of your link...

The same for me. when i recompiled the kernel (2.6.20) I was unable to remove firestarter because it didn't stop.
Now i recompiled that kernel with all the option active (as module -> "M") in the "Network filtering" subsection and firestarter works well.

---

### Post by Prognatus on 2007-02-25
(( Bump! ))

See post #12.

---

