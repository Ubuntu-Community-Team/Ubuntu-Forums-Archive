---
title: "Netgear Wireless Adaptor( WNA-3100) with Broadcom driver will not connect to Wi-Fi"
date: 2016-07-27
forum: Ubuntu/Debian BASED
---

### Post by dr3wst3r on 2016-07-27
Ubuntu Noob Here-

Problem- Can not connect to network wirelessly
Bonus problem :)- Wireless adaptor(USB) requires manual plug and unplug after restart to be recognized 

I followed the tutorial here to install the correct driver for my n300 Wireless Adaptor Netgear WIFI Adaptor-wna3100 ([COLOR=#000000]Broadcom BCM43231)
[/COLOR][HTML]https://ubuntuforums.org/showthread.php?t=2221251&highlight=bcm43231[/HTML] 

I can now see all of the wireless connections and it appears that the driver is installed, but when I try to connect to a network it fails after about 1 min and asks me for the password. I have 3x checked to make sure that I am entering the correct WPA/WPA2 password. I have tried the following. 
[LIST]
[*]Deleting the network connection settings
[*]Manually entering the network connection settings
[*]Creating a guest network without password protection- I was able to fully connect to this network but after 2mins if failed and would no longer load pages.
[/LIST]

Thanks for any help and let me know if I committed any forum faux pas. It has been a while 


Here are my Logs.
[http://paste.ubuntu.com/21195709/](http://paste.ubuntu.com/21195709/)

```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
493
494
495
496
497
498
499
500
501
502
503
504
505
506
507
508
509
510
511
512
513
514
515
516
517
[/TD]
[TD="class: code"][COLOR=#000000]########## wireless info START ##########

Report from: 27 Jul 2016 14:24 PDT -0700

Booted last: 27 Jul 2016 13:03 PDT -0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS - KODIbuntu
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-92-generic #139-Ubuntu SMP Tue Jun 28 20:42:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 006: ID 045e:07b2 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0718:0065 Imation Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              496328  0 
ndiswrapper           283985  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.0.154  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6693 errors:0 dropped:10 overruns:0 frame:0
          TX packets:3598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7762705 (7.7 MB)  TX bytes:453566 (453.5 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.7.114  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1230839 (1.2 MB)  TX bytes:103240 (103.2 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dlink-guest"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'dlink-guest' [AC1]>   
          Bit Rate=130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-25 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:21  Invalid misc:38026   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.7.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.wa.comcast.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1037     1  0 13:03 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [dlink-guest] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-AFCE-2.4:   Infra, <MAC 'HOME-AFCE-2.4' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    CenturyLink2697: Infra, <MAC 'CenturyLink2697' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Guan:            Infra, <MAC 'Guan' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2
    MoralesNetwork-2.4: Infra, <MAC 'MoralesNetwork-2.4' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Annyeong:        Infra, <MAC 'Annyeong' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *dlink-guest:    Infra, <MAC 'dlink-guest' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100

  IPv4 Settings:
    Address:         192.168.7.114
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.7.1

    DNS:             192.168.7.1

- Device: eth0  [Ethernet connection 1] ----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.154
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Annyeong | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dlink-guest]] (600 root)
[connection] id=dlink-guest | type=802-11-wireless
[802-11-wireless] ssid=dlink-guest | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'dlink-guest' [AC1]>
                    ESSID:"dlink-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-25 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: <MAC 'Annyeong' [AC2]>
                    ESSID:"Annyeong"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-26 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HOME-AFCE-2.4' [AC3]>
                    ESSID:"HOME-AFCE-2.4"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xfinitywifi' [AC4]>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: <MAC 'CenturyLink2697' [AC5]>
                    ESSID:"CenturyLink2697"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Guan' [AC6]>
                    ESSID:"Guan"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'MoralesNetwork-2.4' [AC7]>
                    ESSID:"MoralesNetwork-2.4"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-92-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-92-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2A:48:00:B9:4D:C7:83:D0:53:26:FA:E6:7B:01:B0:BE:B7:3B:B8:11
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.13.0-92-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-92-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules ######################

coretemp
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist floppy

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/99lirc-resume] (744 root)
. /usr/lib/pm-utils/functions
case "$1" in
        hibernate|suspend)
                /etc/init.d/lirc stop
                echo "Unloading lirc kernel modules"
                rmmod ir-lirc-codec
                rmmod lirc_dev
                ;;
        thaw|resume)
                echo "Loading lirc kernel modules"
                modprobe ir-lirc-codec
                modprobe lirc_dev
                /etc/init.d/lirc start
                ;;
        *)
                ;;
esac
exit $?

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   19.737582] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   19.737659] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   22.512210] r8169 0000:02:00.0 eth0: link up
[   22.512221] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  316.000625] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  377.574262] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  378.092526] wlan0: ethernet device <MAC 'wlan0' [IF2]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[  378.094768] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  378.172701] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  812.510318] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1183.408367] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003) (repeated 7 times)

########## wireless info END ############[CODE]
```[/COLOR]
[/TD]
[/TR]
[/TABLE]
[/CODE]

---

### Post by jeremy31 on 2016-07-27
*Thread moved to **Ubuntu/Debian BASED**.*

I would look for a TP-Link W722N 150Mbps USB adapter, read about your adapter [http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

Anything that needs ndiswrapper is going to have issues

---

### Post by john_d3 on 2017-04-24
good info but ""Drat"" I still cant get mine to work with any stability.  I bought  a new Linksys or Asus refurb. still working well. just plugs in. netgear consumed an hour and still didnt connect ,till i remembered why it was available here...doesnt work in linux-fine in win7 however
john

---

### Post by reaver385 on 2017-04-26
DOWNLOAD the source code for your model and recompile.

---

### Post by QIII on 2017-04-26
Good night, dear thread.  Rest in peace.

By the way "Download the source and compile it" is not at all helpful.

Closed.

---

