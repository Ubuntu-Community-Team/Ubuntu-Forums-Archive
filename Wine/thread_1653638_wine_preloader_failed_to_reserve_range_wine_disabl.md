---
title: "wine preloader failed to reserve range: wine disabled"
date: 2010-12-27
forum: Wine
---

### Post by magnus07 on 2010-12-27
I've been using wine for quite a while but in the last few days it stopped.

As an example this is the output of the winecfg line command:
winecfg
preloader: Warning: failed to reserve range 00010000-00110000
preloader: Warning: failed to reserve range 00110000-68000000
preloader: Warning: failed to reserve range 7f000000-82000000
Segmentation fault

Since in 2008 a security bug solution was posted I also tried to run "sudo winecfg" but the result is the same.

I cannot run any wine program. It looks broken deep inside.
I tried to wipe wine (I had 1.2) and reinstall. No change
I tried to load latest beta 1.3.9, no change.

Help apreciated.

---

### Post by magnus07 on 2010-12-27
I forgot to mention that "wine --version" works

---

### Post by cogadh on 2010-12-27
First of all, never *ever* run Wine with sudo or a root account, doing so breaks the permissions on your .wine directory and gives Wine, along with any potentially malicious software it may be running (Windows viruses, other malware) unrestricted and damaging access to your entire system.

Given that you have run Wine using sudo, I would recommend you re-name the .wine directory and try running Wine again to create a new one. If that doesn't correct the problem, then do a complete purge of Wine, then re-install.

---

### Post by magnus07 on 2010-12-28
I tried to run as root just as a proof it wasn't the old bug.

I've tried to find my .wine directory but didn't find it  !!??

As said, I already tried to wipe and reinstall. Before this problem all was working just fine, including my .wine directory that was feeling well ;-)

Any other command/info I can try/provide to understand what's happening?

I use ubuntu 10.04 with all fixes applied.

---

### Post by magnus07 on 2010-12-30
Anyone has ideas?

---

### Post by cogadh on 2010-12-30
Its fine that you were trying to prove that, but doing it that way will still break Wine and add another layer of problems on top of the one you already had. Those problems do not go away simply because you are no longer using sudo to run Wine, they are persistent.

The .wine directory is a hidden directory, you will need to show hidden files and folders in order to see it in your home directory.

Did you do a simple uninstall or an uninstall and purge of Wine? Simply uninstalling is often not enough, you need to run "sudo apt-get remove --purge wine" to be sure that everything left over from the old Wine installation is really gone.

---

### Post by magnus07 on 2010-12-30
I did remove and purge.
Just for fun I did the command again and autoremoved 3 requirements no longer needed.

I've nautilus set to show hidden directories. There's no .wine dir.

In the meantime I did notice that something wrong happens during the installation.

Here is the dpkg log

2010-12-30 17:24:19 startup archives unpack
2010-12-30 17:24:19 install ttf-symbol-replacement <non definita> 1.2-1ubuntu1~lucidppa1
2010-12-30 17:24:19 status half-installed ttf-symbol-replacement 1.2-1ubuntu1~lucidppa1
2010-12-30 17:24:19 status triggers-pending fontconfig 2.8.0-2ubuntu1
2010-12-30 17:24:19 status half-installed ttf-symbol-replacement 1.2-1ubuntu1~lucidppa1
2010-12-30 17:24:20 status unpacked ttf-symbol-replacement 1.2-1ubuntu1~lucidppa1
2010-12-30 17:24:20 status unpacked ttf-symbol-replacement 1.2-1ubuntu1~lucidppa1
2010-12-30 17:24:20 install wine1.2 <non definita> 1.2-1ubuntu1~lucidppa1
2010-12-30 17:24:20 status half-installed wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:22 status triggers-pending python-gmenu 2.30.0-0ubuntu4
2010-12-30 17:27:22 status half-installed wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:22 status triggers-pending desktop-file-utils 0.16-0ubuntu2
2010-12-30 17:27:22 status half-installed wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:22 status triggers-pending man-db 2.5.7-2ubuntu1
2010-12-30 17:27:22 status half-installed wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:22 status triggers-pending hicolor-icon-theme 0.11-1
2010-12-30 17:27:22 status half-installed wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:25 status unpacked wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:26 status unpacked wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:26 install wine1.2-gecko <non definita> 1.0.0-0ubuntu4
2010-12-30 17:27:26 status half-installed wine1.2-gecko 1.0.0-0ubuntu4
2010-12-30 17:27:27 status unpacked wine1.2-gecko 1.0.0-0ubuntu4
2010-12-30 17:27:27 status unpacked wine1.2-gecko 1.0.0-0ubuntu4
2010-12-30 17:27:27 install winetricks <non definita> 0.0+20101106-0ubuntu1~lucidppa1
2010-12-30 17:27:27 status half-installed winetricks 0.0+20101106-0ubuntu1~lucidppa1
2010-12-30 17:27:28 status unpacked winetricks 0.0+20101106-0ubuntu1~lucidppa1
2010-12-30 17:27:28 status unpacked winetricks 0.0+20101106-0ubuntu1~lucidppa1
2010-12-30 17:27:28 install wisotool <non definita> 0.0+20101106~lucidppa1
2010-12-30 17:27:28 status half-installed wisotool 0.0+20101106~lucidppa1
2010-12-30 17:27:28 status unpacked wisotool 0.0+20101106~lucidppa1
2010-12-30 17:27:28 status unpacked wisotool 0.0+20101106~lucidppa1
2010-12-30 17:27:28 trigproc fontconfig 2.8.0-2ubuntu1 2.8.0-2ubuntu1
2010-12-30 17:27:28 status half-configured fontconfig 2.8.0-2ubuntu1
2010-12-30 17:27:30 status installed fontconfig 2.8.0-2ubuntu1
2010-12-30 17:27:30 trigproc python-gmenu 2.30.0-0ubuntu4 2.30.0-0ubuntu4
2010-12-30 17:27:30 status half-configured python-gmenu 2.30.0-0ubuntu4
2010-12-30 17:27:31 status installed python-gmenu 2.30.0-0ubuntu4
2010-12-30 17:27:31 status triggers-pending python-support 1.0.4ubuntu1
2010-12-30 17:27:31 trigproc desktop-file-utils 0.16-0ubuntu2 0.16-0ubuntu2
2010-12-30 17:27:31 status half-configured desktop-file-utils 0.16-0ubuntu2
2010-12-30 17:27:31 status installed desktop-file-utils 0.16-0ubuntu2
2010-12-30 17:27:31 trigproc man-db 2.5.7-2ubuntu1 2.5.7-2ubuntu1
2010-12-30 17:27:31 status half-configured man-db 2.5.7-2ubuntu1
2010-12-30 17:27:32 status installed man-db 2.5.7-2ubuntu1
2010-12-30 17:27:32 trigproc hicolor-icon-theme 0.11-1 0.11-1
2010-12-30 17:27:32 status half-configured hicolor-icon-theme 0.11-1
2010-12-30 17:27:32 status installed hicolor-icon-theme 0.11-1
2010-12-30 17:27:33 trigproc python-support 1.0.4ubuntu1 1.0.4ubuntu1
2010-12-30 17:27:33 status half-configured python-support 1.0.4ubuntu1
2010-12-30 17:27:33 status installed python-support 1.0.4ubuntu1
2010-12-30 17:27:34 startup packages configure
2010-12-30 17:27:34 configure ttf-symbol-replacement 1.2-1ubuntu1~lucidppa1 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:34 status unpacked ttf-symbol-replacement 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:34 status half-configured ttf-symbol-replacement 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:34 status installed ttf-symbol-replacement 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:34 configure wine1.2 1.2-1ubuntu1~lucidppa1 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:34 status unpacked wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:34 status unpacked wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:34 status half-configured wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:35 status installed wine1.2 1.2-1ubuntu1~lucidppa1
2010-12-30 17:27:35 status triggers-pending libc-bin 2.11.1-0ubuntu7.6
2010-12-30 17:27:35 configure wine1.2-gecko 1.0.0-0ubuntu4 1.0.0-0ubuntu4
2010-12-30 17:27:35 status unpacked wine1.2-gecko 1.0.0-0ubuntu4
2010-12-30 17:27:35 status half-configured wine1.2-gecko 1.0.0-0ubuntu4
2010-12-30 17:27:35 status installed wine1.2-gecko 1.0.0-0ubuntu4
2010-12-30 17:27:35 configure winetricks 0.0+20101106-0ubuntu1~lucidppa1 0.0+20101106-0ubuntu1~lucidppa1
2010-12-30 17:27:35 status unpacked winetricks 0.0+20101106-0ubuntu1~lucidppa1
2010-12-30 17:27:35 status half-configured winetricks 0.0+20101106-0ubuntu1~lucidppa1
2010-12-30 17:27:35 status installed winetricks 0.0+20101106-0ubuntu1~lucidppa1
2010-12-30 17:27:35 configure wisotool 0.0+20101106~lucidppa1 0.0+20101106~lucidppa1
2010-12-30 17:27:35 status unpacked wisotool 0.0+20101106~lucidppa1
2010-12-30 17:27:35 status half-configured wisotool 0.0+20101106~lucidppa1
2010-12-30 17:27:35 status installed wisotool 0.0+20101106~lucidppa1
2010-12-30 17:27:35 trigproc libc-bin 2.11.1-0ubuntu7.6 2.11.1-0ubuntu7.6
2010-12-30 17:27:35 status half-configured libc-bin 2.11.1-0ubuntu7.6
2010-12-30 17:27:35 status installed libc-bin 2.11.1-0ubuntu7.6

While this is synaptic output (see bold)

Preconfigurazione dei pacchetti in corso
Selezionato il pacchetto ttf-symbol-replacement.
(Lettura del database... 254585 file e directory attualmente installati.)
Estrazione di ttf-symbol-replacement (da .../ttf-symbol-replacement_1.2-1ubuntu1~lucidppa1_all.deb)...
Selezionato il pacchetto wine1.2.
Estrazione di wine1.2 (da .../wine1.2_1.2-1ubuntu1~lucidppa1_i386.deb)...
Selezionato il pacchetto wine1.2-gecko.
Estrazione di wine1.2-gecko (da .../wine1.2-gecko_1.0.0-0ubuntu4_i386.deb)...
Selezionato il pacchetto winetricks.
Estrazione di winetricks (da .../winetricks_0.0+20101106-0ubuntu1~lucidppa1_i386.deb)...
Selezionato il pacchetto wisotool.
Estrazione di wisotool (da .../wisotool_0.0+20101106~lucidppa1_i386.deb)...
Elaborazione dei trigger per fontconfig...
Elaborazione dei trigger per python-gmenu...
Rebuilding /usr/share/applications/desktop.it_IT.utf8.cache...
Elaborazione dei trigger per desktop-file-utils...
Elaborazione dei trigger per man-db...
Elaborazione dei trigger per hicolor-icon-theme...
Elaborazione dei trigger per python-support...
Configurazione di ttf-symbol-replacement (1.2-1ubuntu1~lucidppa1)...
Configurazione di wine1.2 (1.2-1ubuntu1~lucidppa1)...
[B]start: Job failed to start
start: Job failed to start[/B]
update-binfmts: warning: current package is wine, but binary format already
installed by wine1.0 

Configurazione di wine1.2-gecko (1.0.0-0ubuntu4)...
Configurazione di winetricks (0.0+20101106-0ubuntu1~lucidppa1)...
Configurazione di wisotool (0.0+20101106~lucidppa1)...
Elaborazione dei trigger per libc-bin...
ldconfig deferred processing now taking place

This is in kern.log after I tried "wine winecfg" but the problem is possibly in the installation.

kernel: [28468.619757] wine-preloader[9417]: segfault at 7bf0306c ip 7c000618 sp bfec07a0 error 6 in wine-preloader[7c000000+2000]


I've also found this on wineHQ but look like nobody really cared about...
[http://bugs.winehq.org/show_bug.cgi?id=20061](http://bugs.winehq.org/show_bug.cgi?id=20061)

---

### Post by cogadh on 2010-12-30
Did you ever install a custom compiled version of Wine in the past?

---

### Post by magnus07 on 2010-12-30
None that I'm aware of...

---

### Post by magnus07 on 2011-01-02
Any new idea brought by 2011? :confused:

---

### Post by philnice on 2011-02-13
> **magnus07 said:**
> Any new idea brought by 2011? :confused:
Hi, i've being having the same problem for quite long. After checking several folders and files, i found one named wine 1.0 in var/lib/binfmts. I trashed it, and then removed and reinstalled wine, and suddenly terminal did not gave me any update-binfmts errors.
I don't know if this is the right way to go with this though. Just worked for me.
I do use wine compiled with git, and possibly i upgraded to a newer compiled version once in the past, without removing the older official release first.

---

### Post by magnus07 on 2011-02-14
Thanks a lot.
I'll give it a try even if I don't need it anymore. Moved to a similar linux app.
I'll let the forum know my results.

---

### Post by philnice on 2011-02-14
> **magnus07 said:**
> Thanks a lot.
I'll give it a try even if I don't need it anymore. Moved to a similar linux app.
I'll let the forum know my results.
You're welcome. I hope it 'll work for you also. 
I did this trick a couple of hours before my response here, and as i've being searching a lot for a solution, i came back to post the results right after since i had seen this thread.

---

### Post by magnus07 on 2011-02-15
Philnice, you were very right.
That was the problem and your solution worked!!!

I found in /var/lib/binfmts a file named "wine" with the following content (without -------):

-----------------------
wine1.0
magic
0
MZ

/usr/bin/wine
-----------------------

I'll update also the wine bug that was "closed" as a packaging problem.

I owe you a beer !!!

---

### Post by philnice on 2011-02-15
**magnus07**, happy to hear that!!! may i ask for a kaiser since it's my favorite? :lolflag:
Make sure to mark the thread as solved so it would help others too.

---

