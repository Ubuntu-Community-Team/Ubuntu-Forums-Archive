---
title: "Frequent Kernel Panics"
date: 2010-07-11
forum: System76 Support
---

### Post by jamesrl on 2010-07-11
Hi,
My month old system76 serp6 has been doing an abnormal number of kernel panics under low stress conditions (e.g., only 10% of memory used, just light web browsing, or ssh-ing into another machine).  Sometimes it will run for a few days with no issues, frequently going to sleep (suspend) and waking up.

Every now and then it kernel panics (not necessarily daily).  I reboot and then in less than 10 minutes it kernel panics again (while only using a web browser, a terminal, ssh, and background applications).  And sometimes this repeats a few more times (never more than 6) and then it works fine with no problem (for a few days).  The kernel panic does do the flashing caps/num lock lights and doesn't respond to the magic sysrq keys.

I do not think it is heat related; I am inside with air conditioning and the CPU temperature seems reasonable (/proc/acpi/thermal_zone/TZ0/temperature is 47C)

Attached is a tarball of a few log files showing a panic at 19:25:44 and 19:31:10 today.  I think it may be associated with the network card and waking up/going to sleep, but don't know if the messages in the log relating are normal.

Thanks for any help.

---

### Post by marshmallow1304 on 2010-07-12
Are you using a wireless connection?  Also, are you doing any sort of port forwarding with ssh?  Several months ago, I had kernel panics while forwarding ports with ssh over my college's wireless connection.  Apparently, the connection was being reset by the router while HTTP data was traveling across ssh, somehow causing a kernel panic.  I started using a wired connection instead, and the problem disappeared.

---

### Post by thomasaaron on 2010-07-12
For some reason, I can't see syslog in that archive.

The next time it happens, please reboot your machine and make note of the time when your system is all the way up, or the time on the clock when the freeze occurs. Then, please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

---

### Post by jamesrl on 2010-07-12
> **marshmallow1304 said:**
> Are you using a wireless connection?  Also, are you doing any sort of port forwarding with ssh?  Several months ago, I had kernel panics while forwarding ports with ssh over my college's wireless connection.  Apparently, the connection was being reset by the router while HTTP data was traveling across ssh, somehow causing a kernel panic.  I started using a wired connection instead, and the problem disappeared.

I am using wireless and do use ssh & ssh port forwarding.  My linksys router sends incoming connections to my routers ip address on an specific port (call it 3701) to my desktop machine's port 3701, which is used for ssh on the desktop.  (The desktop is not a sys76 machine, also runs 10.04, and is not having kernel panics.)  So whenever I ssh into my desktop from my sys76 laptop, I ssh in through port 3701.  I also use an rsa public/private keypair for ssh authentication (with a passphrase I unlock before first use).  I do frequently ssh into my desktop from my laptop, e.g., to sync my svn repository, alter my MPD playlist, sync files, etc.  Most of the time that I have crashes its while I am sshing into my desktop (which is what I was doing the last two times it kernel panicked).  I very rarely ssh into my laptop; though the laptop is running sshd but incoming connections aren't correlated with kernel panics.

And to further complicate things, I often use a SOCKS 5 proxy for browsing the web through this my desktop connection; e.g., start a ssh SOCKS connection to port 13701 on my laptop to my desktop by launching "ssh -fND localhost:13701 desktop" (where desktop is in my ~/.ssh/config with port 3701 defined), and configure a web browser to use a SOCKS proxy).  I do not always launch this SOCKS connection every time I get a kernel panic (though possibly always before the first kernel panic, as it is frequently on).  I will note that I had this same setup on my old laptop, and I can't recall ever getting kernel panics from this.  (I only very rarely had my old laptop kernel panic; probably less than once every 3 months had a kernel panic on my old laptop, and that was almost always related to suspend/hibernate issues).

(Why the SOCKS proxy you ask?  For anonymity/security when my laptop is on another network; e.g., don't want admin at a coffee place to be able to monitor my unencrypted traffic or if the DNS servers have been messed with.  One of my two web browsers (firefox/google-chrome) is permanently setup with this proxy for more sensitive stuff; e.g., finances/online ordering).

---

### Post by jamesrl on 2010-07-12
> **thomasaaron said:**
> For some reason, I can't see syslog in that archive.

The next time it happens, please reboot your machine and make note of the time when your system is all the way up, or the time on the clock when the freeze occurs. Then, please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

Thanks for the quick response; I really appreciate it.  Will do the System76 Driver/support create, the next time it happens.  I guess I forgot to put syslog in the tarball and have attached it (I copied it into my home dir to put it in the archive but guess I left it out).  The two crashes yesterday were at 19:25:44 (1st kernel panic) 19:28:56 (1st reboot) and 19:31:10 (2nd kernel panic), 19:32:33 (2nd reboot).

---

### Post by thomasaaron on 2010-07-13
OK, it's definitely networking-related. The key messages appear to be...

Jul 11 19:30:29 celtics2010 kernel: [  116.703705] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 11 19:30:30 celtics2010 kernel: [  118.249918] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 11 19:31:10 celtics2010 kernel: [  157.976433] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 11 19:31:24 celtics2010 kernel: [  171.956561] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again

In other words, the wireless card is going to sleep, but it is unable to wake up. 

Does this happen when you're *not* using ssh?

---

### Post by jamesrl on 2010-07-13
> **thomasaaron said:**
> OK, it's definitely networking-related. The key messages appear to be...

Jul 11 19:30:29 celtics2010 kernel: [  116.703705] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 11 19:30:30 celtics2010 kernel: [  118.249918] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 11 19:31:10 celtics2010 kernel: [  157.976433] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 11 19:31:24 celtics2010 kernel: [  171.956561] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again

In other words, the wireless card is going to sleep, but it is unable to wake up. 

Does this happen when you're *not* using ssh?

Yes.  I just rebooted and haven't used ssh at all (just firefox with no SOCKS proxy), via wifi (using WPA2).  But my syslog is still giving:
> 
Jul 13 16:22:58 celtics2010 kernel: [  829.249549] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 13 16:22:59 celtics2010 kernel: [  830.751276] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 13 16:23:14 celtics2010 kernel: [  845.221908] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 13 16:23:40 celtics2010 kernel: [  871.196972] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 13 16:24:58 celtics2010 kernel: [  949.089414] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 13 16:24:58 celtics2010 kernel: [  949.089495] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 13 16:24:59 celtics2010 kernel: [  950.680429] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 13 16:25:08 celtics2010 kernel: [  959.078949] rtl8192_hw_sleep_down(): RF Change in progress!


---

### Post by thomasaaron on 2010-07-14
OK. Good info.

Can you set your wifi to no encryption? Just for testing?

Or, can you test with ethernet enabled but wireless disabled?

---

### Post by jamesrl on 2010-07-14
Sorry didn't get a chance to test the unencrypted/wifi disabled network yet (other people on the network).  I did just have another kernel panic though and made a logs.tar that is attached.  I was using ssh at the time; e.g., just signed into my other computer and was launching ncmpc (a terminal MPD player) from the other computer when it froze.  Had been working for a while so the ssh SOCKS proxy was also open too, while using wifi with encryption.  (Kernel panic at Jul 14 14:39:38).

---

### Post by jamesrl on 2010-07-14
So I reset my router to have no encryption (just MAC address filtering).  (I would rather prefer to encrypt as a long term solution though, as I am in an apartment building with lots of neighbors and MAC spoofing isn't too difficult.)  

That said I do not seem to see the frequent "Change in progress! Schedule wake up task again".  E.g., recent syslog messages:

> 
Jul 14 16:57:34 celtics2010 kernel: [   40.482900] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 16:57:35 celtics2010 kernel: [   42.036571] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 16:58:14 celtics2010 kernel: [   80.504786] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 16:58:14 celtics2010 kernel: [   80.504858] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 16:58:15 celtics2010 kernel: [   82.023038] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 16:59:14 celtics2010 kernel: [  140.529412] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 16:59:15 celtics2010 kernel: [  142.057810] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 16:59:42 celtics2010 kernel: [  168.829218] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
Jul 14 17:00:34 celtics2010 kernel: [  220.558607] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:00:34 celtics2010 kernel: [  220.558684] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:00:35 celtics2010 kernel: [  222.120779] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:01:53 celtics2010 kernel: [  300.168084] ========>too long to sleep:22, fffffff4, 3e8
Jul 14 17:01:53 celtics2010 kernel: [  300.271101] ========>too long to sleep:2c, fffffffe, 3e8
Jul 14 17:02:16 celtics2010 kernel: [  322.799470] __ratelimit: 9 callbacks suppressed
Jul 14 17:02:16 celtics2010 kernel: [  322.799479] npviewer.bin[2512]: segfault at 418 ip 00000000f60b5a56 sp 00000000fffdab48 error 6 in libflashplayer.so[f5e67000+b04000]
Jul 14 17:02:24 celtics2010 kernel: [  330.616934] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:02:24 celtics2010 kernel: [  330.617011] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:02:25 celtics2010 kernel: [  332.156088] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:04:14 celtics2010 kernel: [  440.653273] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:04:14 celtics2010 kernel: [  440.653352] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:04:15 celtics2010 kernel: [  442.202078] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:05:01 celtics2010 kernel: [  487.673530] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:05:20 celtics2010 kernel: [  506.962915] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
Jul 14 17:06:14 celtics2010 kernel: [  560.670497] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:06:14 celtics2010 kernel: [  560.670595] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:06:15 celtics2010 kernel: [  562.207676] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:07:39 celtics2010 kernel: [  645.989371] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:08:14 celtics2010 kernel: [  680.655777] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:08:14 celtics2010 kernel: [  680.655866] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:08:15 celtics2010 kernel: [  682.287097] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:10:00 celtics2010 kernel: [  786.938240] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
Jul 14 17:10:04 celtics2010 kernel: [  790.937871] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
Jul 14 17:10:14 celtics2010 kernel: [  800.649035] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:10:14 celtics2010 kernel: [  800.649124] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:10:15 celtics2010 kernel: [  802.216523] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:12:14 celtics2010 kernel: [  920.638873] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 17:12:14 celtics2010 kernel: [  920.638952] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 17:12:15 celtics2010 kernel: [  922.155952] ===>rtl8192se_link_change():ieee->iw_mode is 2


I haven't been using ssh yet, for the above messages.

---

### Post by jamesrl on 2010-07-14
Just had two more kernel panics one at 18:10 and another at 18:12.  

Attached is the logs.tar after the second one.

The first one happened while I was using ssh.  I had ssh'd into my desktop probably an hour earlier, was still connected, started ncmpc (to manage mpd), then fired up alsamixer to change the volume level, then I tried switching back to ncmpc, and my laptop kernel panicked instead of starting ncmpc up the second time).

The second one happened right after I rebooted, I made a logs.tar via the sys76 app, went to firefox to fire it up, and got another kernel panic.  I wasn't using ssh.

Both occurred when I wasn't using encryption on my wifi connection.

I also note, I haven't used ssh yet and am on the unencrypted wifi, but have frequent messages of the sort:

> 
Jul 14 18:34:03 celtics2010 kernel: [ 1161.708099] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 18:34:04 celtics2010 kernel: [ 1163.247383] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 18:34:36 celtics2010 kernel: [ 1195.574643] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 14 18:35:16 celtics2010 kernel: [ 1235.570383] rtl8192_hw_sleep_down(): RF Change in progress!
Jul 14 18:35:18 celtics2010 kernel: [ 1237.561563] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
Jul 14 18:36:03 celtics2010 kernel: [ 1281.697637] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 18:36:03 celtics2010 kernel: [ 1281.697719] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 18:36:04 celtics2010 kernel: [ 1283.267360] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 18:36:26 celtics2010 kernel: [ 1305.557322] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 14 18:37:06 celtics2010 kernel: [ 1345.552317] rtl8192_hw_sleep_down(): RF Change in progress!
Jul 14 18:37:26 celtics2010 kernel: [ 1365.560514] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 14 18:37:40 celtics2010 kernel: [ 1379.552363] rtl8192_hw_sleep_down(): RF Change in progress!
Jul 14 18:38:03 celtics2010 kernel: [ 1401.688259] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 18:38:03 celtics2010 kernel: [ 1401.688336] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 18:38:04 celtics2010 kernel: [ 1403.307410] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 18:38:08 celtics2010 kernel: [ 1407.547460] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
Jul 14 18:38:48 celtics2010 kernel: [ 1447.546757] rtl8192_hw_sleep_down(): RF Change in progress!
Jul 14 18:39:01 celtics2010 CRON[3689]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jul 14 18:39:16 celtics2010 kernel: [ 1475.541798] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
Jul 14 18:39:46 celtics2010 kernel: [ 1505.548862] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 14 18:40:03 celtics2010 kernel: [ 1521.677785] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 14 18:40:03 celtics2010 kernel: [ 1521.677860] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 18:40:04 celtics2010 kernel: [ 1523.287445] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 14 18:41:04 celtics2010 kernel: [ 1583.538687] rtl8192_hw_sleep_down(): RF Change in progress!


---

### Post by jamesrl on 2010-07-14
Another kernel panic at 10:40.  This time as I was starting up the ssh SOCKS proxy to my desktop while connected to WPA2 wifi (re-enabled as roommate came home and didn't want to have to pull MAC address.  

While writing this message, not ssh-ing or doing anything else besides having booting, creating sys76 log tarball (and closing), opening firefox to go here, there was another kernel panic at about 10:44.

Attached are the most recent logs.tar.

I also have a question; so far the kernel panics seem related to the wifi card.  I probably have an extra internal wifi card lying I could swap in that I know has worked in ubuntu 7.04 - 9.04 with no problems or configuration issues (I think atheros or intel 3945, not sure).  My questions are (a) if I open the system up do I void a warranty or anything, and (b) is there a guide somewhere (e.g., instructions how to remove the keyboard or where the wifi card is)?

Thanks.

---

### Post by thomasaaron on 2010-07-15
OK, I'll have a look at the logs. But could you define exactly what you're seeing. Kernel panics usually have flashing LED's. Is that what you're getting?

---

### Post by jamesrl on 2010-07-16
> **thomasaaron said:**
> OK, I'll have a look at the logs. But could you define exactly what you're seeing. Kernel panics usually have flashing LED's. Is that what you're getting?

Yes, all the kernel panics (except one) had the two flashing LEDs (num lock/scroll lock), and doesn't respond the magic sysrq keys (Alt-SysRq-R,E,I,S,U,B) or restarting X (Ctrl-Alt-Bksp).  

The one kernel panic without the flashing LEDs had the same symptoms (screen froze; e.g., system monitor in gnome panel stopped scrolling, no response to mouse, keyboard, or magic SysRq keys).  

The kernel panics have happened on battery power and plugged in.  The cpu reports a normal temperature (under 50C).  I've fully checked the memory with memtest86 and no errors were reported.

The first kernel panic is usually associated with ssh usage (without X11 forwarding) to my desktop that I connect (using port forwarding); e.g., often after I try loading a terminal application through ssh (e.g., alsamixer, ncmpc).  However, doing the exact same thing works most of the time w/o kernel panic.  Normally, I have wpa2 encryption on the network card, but the last set of kernel panics did not have wpa2 enabled.  The computer I am ssh-ing to continues to run fine and reports no errors.  Sometimes I get several kernel panics in a row, and the subsequent ones will happen when doing nothing ssh related.

If this had no warranty/support the next step I would do is swap out the wifi card to see if that's the issue; however I don't want to void any warranties.  (I have working linux friendly mini-PCI express wifi cards lying around from old laptops, so its not like I am trying to get new hardware and I know how to safely install hardware without static discharges.)

---

### Post by jamesrl on 2010-07-18
Another kernel panic at 8:05pm today, but no subsequent crashes.  Was using ssh to edit a few files (e.g., nano) and crashed right after typing ls.  I've been trying to use ssh less when its not necessary.  Syslog showed the usual error messages related to the wifi card going to sleep:
```

Jul 17 19:56:46 celtics2010 kernel: [10840.504493] ===>rtl8192se_link_change():
ieee->iw_mode is 2
Jul 17 19:58:45 celtics2010 kernel: [10958.701218] LPS leave: notify AP we are 
awaked ++++++++++ SendNullFunctionData
Jul 17 19:58:45 celtics2010 kernel: [10958.701288] ===>rtl8192se_link_change():
ieee->iw_mode is 2
Jul 17 19:58:46 celtics2010 kernel: [10960.329120] ===>rtl8192se_link_change():
ieee->iw_mode is 2
Jul 17 20:00:45 celtics2010 kernel: [11078.527524] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 17 20:00:46 celtics2010 kernel: [11080.151261] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 17 20:01:28 celtics2010 sudo: pam_sm_authenticate: Called
Jul 17 20:01:28 celtics2010 sudo: pam_sm_authenticate: username = [jledoux]
Jul 17 20:02:45 celtics2010 kernel: [11198.348644] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 17 20:02:46 celtics2010 kernel: [11199.974720] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 17 20:04:12 celtics2010 kernel: [11285.298984] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Jul 17 20:04:45 celtics2010 kernel: [11318.175652] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 17 20:04:45 celtics2010 kernel: [11318.175737] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 17 20:04:46 celtics2010 kernel: [11319.798016] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 17 20:07:50  ; rebooted.

```


Earlier last week, I had switched my ssh port back to 22 on my desktop to try and see if that would have changed anything (as [marshmellow1304 suggested here]("http://ubuntuforums.org/showpost.php?p=9578462&postcount=2") that it could have something to do with ssh port forwarding.  He also suggested switching to wired internet connection, which is not an option with the layout of my apartment.  Anyhow I'm pretty convinced its a wireless card issue, and may just try swapping it out (likely Tuesday night; as I'm busy with other stuff in the meantime).

EDIT: here's the relevant output from `sudo lshw | grep -20 wlan0`:
```
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:3000(size=4096) memory:f0900000-f09fffff ioport:f0000000(size=2097152)
           *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 10
                serial: e0:91:53:17:55:5c
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=802.11bg
                resources: irq:16 ioport:3000(size=256) memory:f0900000-f0903fff

```

---

