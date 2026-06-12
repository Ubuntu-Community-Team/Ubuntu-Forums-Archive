---
title: "Show me what you got."
date: 2006-03-19
forum: The Cafe
---

### Post by virgule on 2006-03-19
Come one guys help me as I am lost!

```

 [virgule @ ~ ]# time ps -ely
S   UID   PID  PPID  C PRI  NI   RSS    SZ WCHAN  TTY          TIME CMD
S     0     1     0  0  76   0   612   426 select ?        00:00:03 init
S     0     2     1  0  94  19     0     0 ksofti ?        00:00:00 ksoftirqd/0
S     0     3     1  0  70  -5     0     0 worker ?        00:00:03 events/0
S     0     4     1  0  71  -5     0     0 worker ?        00:00:00 khelper
S     0     5     1  0  80  -5     0     0 worker ?        00:00:00 kthread
S     0    17     5  0  70  -5     0     0 worker ?        00:00:00 kblockd/0
S     0    49     5  0  80   0     0     0 pdflus ?        00:00:00 pdflush
S     0    50     5  0  75   0     0     0 pdflus ?        00:00:00 pdflush
S     0    52     5  0  80  -5     0     0 worker ?        00:00:00 aio/0
S     0    51     1  0  85   0     0     0 kswapd ?        00:00:00 kswapd0
S     0   244     1  0  75   0     0     0 scsi_s ?        00:00:00 scsi_eh_0
S     0   256     1  0  83   0     0     0 scsi_e ?        00:00:00 scsi_eh_1
S     0   309     1  0  75   0     0     0 hub_th ?        00:00:00 khubd
S     0  1878     1  0  75   0     0     0 kjourn ?        00:00:00 kjournald
S     0  2262     1  0  71  -4   636   487 select ?        00:00:00 udevd
S     0  3091     1  0  75   0     0     0 hpsbpk ?        00:00:00 khpsbpkt
S     0  3404     1  0  75   0     0     0 kjourn ?        00:00:00 kjournald
S     0  3682     1  0  75   0     0     0 nodemg ?        00:00:00 knodemgrd_0
S   101  4347     1  0  73  -2  1260   730 select ?        00:00:00 dhclient3
S   102  4719     1  0  76   0   840   542 select ?        00:00:00 syslogd
S   105  4732     1  0  76   0  1204   677 poll   ?        00:00:00 dbus-daemon
S   111  4745     1  0  75   0  3024  1354 poll   ?        00:00:01 hald
S   111  4762  4745  0  76   0   752   565 nanosl ?        00:00:00 hald-addon-stor
S   111  4765  4745  0  76   0   752   565 nanosl ?        00:00:01 hald-addon-stor
S     0  4791     1  0  76   0  3336  3776 poll   ?        00:00:00 gdm
S   107  4863     1  0  76   0  1496  3479 tcp_ac ?        00:00:00 hpiod
S   107  4867     1  0  76   0  6476  3029 select ?        00:00:00 python
S     0  4975     1  0  78   0   940   582 poll   ?        00:00:00 hcid
S     0  4981     1  0  78   0   644   459 select ?        00:00:00 sdpd
S     0  4991     1  0  70 -10     0     0 rfcomm ?        00:00:00 krfcommd
S     1  5035     1  0  84   0   736   539 nanosl ?        00:00:00 atd
S     0  5048     1  0  76   0   940   590 nanosl ?        00:00:00 cron
S     0  5059     1  0  76   0   556   425 read_c tty1     00:00:00 getty
S     0  5060     1  0  76   0   556   425 read_c tty2     00:00:00 getty
S     0  5061     1  0  76   0   556   425 read_c tty3     00:00:00 getty
S     0  5062     1  0  76   0   556   425 read_c tty4     00:00:00 getty
S     0  5067     1  0  76   0   556   425 read_c tty5     00:00:00 getty
S     0  5070     1  0  76   0   556   425 read_c tty6     00:00:00 getty
S     0  5568  4791  0  76   0  3860  3957 select ?        00:00:00 gdm
R     0  5573  5568  9  76   0 15920  4579 -      ?        00:02:59 Xorg
S  1000  5595  5568  0  76   0  6736  3261 select ?        00:00:08 openbox
S  1000  5634  5595  0  76   0  1148   985 select ?        00:00:00 ssh-agent
S  1000  5637     1  0  83   0   848   831 select ?        00:00:00 dbus-launch
S  1000  5638     1  0  82   0   868   599 poll   ?        00:00:00 dbus-daemon
S  1000  5639  5595  1  76   0 16948 11811 poll   ?        00:00:23 gnome-terminal
S  1000  5641     1  0  76   0  3976  2038 poll   ?        00:00:01 gconfd-2
S  1000  5643     1  0  80   0  3104  2108 poll   ?        00:00:00 bonobo-activati
S  1000  5644  5639  0  79   0   812   731 unix_s ?        00:00:00 gnome-pty-helpe
S  1000  5645  5639  0  76   0  2308  1346 wait   pts/0    00:00:00 bash
S  1000  5655  5595  1  75   0  9512  4879 poll   ?        00:00:22 gkrellm
S  1000  5660  5645  0  76   0  7672  4065 select pts/0    00:00:11 pypanel
S  1000  5663  5595  8  75   0 29144 12414 select ?        00:02:27 opera
S  1000  5705  5645  0  76   0  2460  1762 select pts/0    00:00:00 xcalc
R  1000  5709  5645  0  77   0   952   971 -      pts/0    00:00:00 ps

real    0m2.289s
user    0m0.038s
sys     0m0.036s

```
This computer is waaaaaaay too slow I know it can do much better then that.  WHAT exactly cause such a gap between 'real' and the other two values? Xorgs is set to use 16-bits only and I ran this from openbox. That takes **57 times** longer to display some TEXT on screen than it takes the computer to gather the datas!  :-k 

As a reference, this computer can play StarCraft BroodWar on battle.net with 8 players rushing zerglings at each others without a single hint of LAG. Good luck explaining to me WHY AND HOW printing a couple lines of TEXT takes so long?:evil: [-(

---

### Post by taurus on 2006-03-19
You never care to include the spec of your machine so one should guess on that!!!  :-k

---

### Post by virgule on 2006-03-19
Its old and 'slow' according to today's standards but that is not the point. I see no rational explanation for such poor performance. Compared to a 8-way zergling rush on battle.net, an handsome lines of text should be next to nothing for this computer. That is my point: How comes it seam hard to print text when this computer 'scream' (for lack of a better work) at running an action-packed video game? This piss me off a little I know you understand my concern.

300Mhz PowerPC G3 - 1024k L2 backside cache
320Mb RAM, 40G ATA, 8MB VRAM (ATI RageII+DVD)

---

### Post by erikpiper on 2006-03-19
I got (Relitavely) long results also- BUT its a nice machine- So I say just ignore it..

I have an IBM T23- 1.2 Ghz PIII, 756 MB RAM.


Results:
real    0m0.326s
user    0m0.016s
sys     0m0.015s

---

### Post by s|k on 2006-03-19
Why is this in community chat? Why not post it in Support Forums and get better help and beans to boot.

---

### Post by virgule on 2006-03-19
Sorry :( I actually get quite confused about searching and finding the right places to.. anyway I learned a few tricks from Fedora guys and I am laughing at my own angriness now. 
1- I did that: [How to make Ubuntu responsive]("http://www.ubuntuforums.org/showthread.php?t=119220"). Both the script and bootloader argument
2- renice 'events\0' to -19. 

Life is good now. See for yourself: The same command as before but ran from KDE 3.5.1 with loaded apps instead of openbox with not much going on. That cfq trick is worth a buck or two ;)

Before:
real    0m2.289s
user    0m0.038s
sys     0m0.036s

After:
real    0m0.382s
user    0m0.053s
sys     0m0.037s

---

