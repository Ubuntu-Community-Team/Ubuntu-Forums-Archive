---
title: "virtualbox vm now DOA"
date: 2009-10-10
forum: Virtualisation
---

### Post by kaligus on 2009-10-10
I have not had problems with one now broken vbox since at least hardy...


 
 the error I get on trying to start that box now is:
 
 Failed to start the virtual machine win2k_encore.
 Failed to open host device '/dev/ttyS0' (VERR_FILE_NOT_FOUND).
 Unknown error creating VM (VERR_FILE_NOT_FOUND).
 
 Result Code: 
 NS_ERROR_FAILURE (0x80004005)
 Component: 
 Console
 Interface: 
 IConsole {0a51994b-cbc6-4686-94eb-d4e4023280e2}




 
 Due to a hardware issue I had to reinstall my / partition but not /home or /storage where the good stuff lives.


 
 After reinstall (just before the updates) I had no call for this one vbox until after the most recent two kernel updates so the problem could be something I forgot since the reinstall or it could be kernel issues.


 
 [http://ubuntuforums.org/showthread.php?t=846915](http://ubuntuforums.org/showthread.php?t=846915)
 yields below...  I can't see anything obviously broken but obviously I did break something. Any idea(s) what is broken?




 
 
 
 Linux bigwill 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux (9.04 jaunty)


 ******demsg
 [    0.004000] console [tty0] enabled
 [    1.292230] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 [    1.292451] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


 ******setserial
 /dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4


 ******proc/tty
 /dev/tty             /dev/tty        5       0 system:/dev/tty
 /dev/console         /dev/console    5       1 system:console
 /dev/ptmx            /dev/ptmx       5       2 system
 /dev/vc/0            /dev/vc/0       4       0 system:vtmaster
 rfcomm               /dev/rfcomm   216 0-255 serial
 serial               /dev/ttyS       4 64-111 serial
 pty_slave            /dev/pts      136 0-1048575 pty:slave
 pty_master           /dev/ptm      128 0-1048575 pty:master
 unknown              /dev/tty        4 1-63 console


 ******stty
 speed 38400 baud; rows 43; columns 194; line = 0;
 intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
 eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;
 werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
 -parenb -parodd cs8 -hupcl -cstopb cread -clocal -crtscts
 -ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon ixoff
 -iuclc -ixany -imaxbel iutf8
 opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
 isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
 echoctl echoke


 ******ls
 crw-rw---- 1 root dialout 4, 64 2009-10-09 22:15 /dev/ttyS0


 ******id
 uid=1000(will) gid=1000(will) groups=4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),127(vboxusers),1000(will)

---

### Post by kaligus on 2009-10-10
hmmmm... looks like I may also need to rollback an update I had not noticed before...  news at 11

---

