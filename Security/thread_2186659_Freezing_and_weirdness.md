---
title: "Freezing and weirdness"
date: 2013-11-08
forum: Security
---

### Post by J_Me on 2013-11-08
Could someone tell me please what's going on. I've been having freezing issues with my netbook[http://ubuntuforums.org/showthread.php?t=2185601](http://ubuntuforums.org/showthread.php?t=2185601) and just after it happened again I searched for 'error' in the systemlog a few things popped up and so I tried to copy and paste some of the errors but highlighting the text and doing ctrl+c ctrl+v pasted this ```
RaspBMC loads first screen, but nothing after that
    5 
    94 
    linoskoczek
    by Phill Rymer
    Fri Nov 08, 2013 12:31 am 

```
and not the text that I highlighted[IMG][[IMG]http://s9.postimg.org/moajx8kff/error_message.jpg[/IMG]]("http://postimg.org/image/moajx8kff/")[/IMG] where did that come from? Anyway just happened again while writing this and this time I just printed out all the errors here
```

08/11/2013 13:55:49    n    kernel    [    5.152402] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
08/11/2013 13:55:53    n    NetworkManager[787]    <error> [1383918953.175281] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
08/11/2013 13:55:54    n    udevd[499]    error changing net interface name eth1 to eth2: Device or resource busy
08/11/2013 13:56:58    n    kernel    [   74.594660] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:56:58    n    kernel    [   74.594683] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:56:59    n    NetworkManager[787]    <error> [1383919019.89631] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
08/11/2013 13:56:59    n    NetworkManager[787]    <error> [1383919019.89863] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
08/11/2013 13:57:04    n    kernel    [   80.594299] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:04    n    kernel    [   80.594317] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:09    n    kernel    [   86.594646] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:09    n    kernel    [   86.594669] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:15    n    kernel    [   92.599956] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:15    n    kernel    [   92.599990] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:21    n    kernel    [   98.594619] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:21    n    kernel    [   98.594642] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:27    n    kernel    [  104.594752] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:27    n    kernel    [  104.594775] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:33    n    kernel    [  110.594294] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:33    n    kernel    [  110.594310] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:39    n    kernel    [  116.594973] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:39    n    kernel    [  116.594985] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:45    n    kernel    [  122.595203] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:45    n    kernel    [  122.595226] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:51    n    kernel    [  128.594424] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:51    n    kernel    [  128.594441] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:57:57    n    kernel    [  134.595689] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:57:57    n    kernel    [  134.595713] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:03    n    kernel    [  140.594659] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:03    n    kernel    [  140.594683] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:09    n    kernel    [  146.683090] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:09    n    kernel    [  146.683107] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:15    n    kernel    [  152.603572] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:15    n    kernel    [  152.603603] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:20    n    kernel    [  157.257920] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:20    n    kernel    [  157.257943] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:25    n    kernel    [  162.594619] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:25    n    kernel    [  162.594642] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:31    n    kernel    [  168.594710] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:31    n    kernel    [  168.594734] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:37    n    kernel    [  174.594585] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:37    n    kernel    [  174.594608] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:43    n    kernel    [  180.594623] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:43    n    kernel    [  180.594646] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:49    n    kernel    [  186.595972] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:49    n    kernel    [  186.596269] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:54    n    kernel    [  191.254198] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:54    n    kernel    [  191.254233] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:58:59    n    kernel    [  196.594562] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:58:59    n    kernel    [  196.594586] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:05    n    kernel    [  202.594593] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:05    n    kernel    [  202.594615] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:11    n    kernel    [  208.594635] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:11    n    kernel    [  208.594659] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:17    n    kernel    [  214.595153] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:17    n    kernel    [  214.595176] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:23    n    kernel    [  220.594562] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:23    n    kernel    [  220.594585] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:29    n    kernel    [  226.595174] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:29    n    kernel    [  226.595198] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:34    n    kernel    [  231.253853] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:34    n    kernel    [  231.253877] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:39    n    kernel    [  236.596406] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:39    n    kernel    [  236.596429] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:45    n    kernel    [  242.594527] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:45    n    kernel    [  242.594550] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:51    n    kernel    [  248.594093] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:51    n    kernel    [  248.594106] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 13:59:57    n    kernel    [  254.595678] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 13:59:57    n    kernel    [  254.595701] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:03    n    kernel    [  260.594475] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:03    n    kernel    [  260.594499] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:09    n    kernel    [  266.595162] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:09    n    kernel    [  266.595186] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:15    n    kernel    [  272.594634] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:15    n    kernel    [  272.594658] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:21    n    kernel    [  278.595117] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:21    n    kernel    [  278.595149] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:27    n    kernel    [  284.595885] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:27    n    kernel    [  284.595909] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:33    n    kernel    [  290.594202] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:33    n    kernel    [  290.594220] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:39    n    kernel    [  296.595356] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:39    n    kernel    [  296.595368] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:45    n    kernel    [  302.596342] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:45    n    kernel    [  302.596365] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:51    n    kernel    [  308.594967] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:51    n    kernel    [  308.594990] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:00:57    n    kernel    [  314.594497] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:00:57    n    kernel    [  314.594521] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:03    n    kernel    [  320.595213] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:03    n    kernel    [  320.595236] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:09    n    kernel    [  326.595283] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:09    n    kernel    [  326.595347] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:15    n    kernel    [  332.596279] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:15    n    kernel    [  332.596302] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:21    n    kernel    [  338.595782] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:21    n    kernel    [  338.595805] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:27    n    kernel    [  344.594757] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:27    n    kernel    [  344.594780] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:33    n    kernel    [  350.596428] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:33    n    kernel    [  350.596452] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:39    n    kernel    [  356.594505] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:39    n    kernel    [  356.594528] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:45    n    kernel    [  362.595152] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:45    n    kernel    [  362.595183] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:51    n    kernel    [  368.594987] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:51    n    kernel    [  368.595024] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:01:57    n    kernel    [  374.594776] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:01:57    n    kernel    [  374.594788] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
08/11/2013 14:02:03    n    kernel    [  380.594999] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
08/11/2013 14:02:03    n    kernel    [  380.595030] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
```

Is my netbook on it's last legs or should I be getting paranoid(joking).
P.S. freezing happened three times in a row, unplugged the power supply and it seems ok, maybe it's that.

---

### Post by houstonbofh on 2013-11-10
Before  you go to far, make sure you have a stable platform.  Boot into memtest, and hammer the memory overnight.  If you have bad ram, it will make all kinds of unhappy things happen.

---

### Post by J_Me on 2013-11-10
Thanks for the reply
Already did a overnight memtest but one thing I noticed was that it returned no results what so ever.

---

### Post by J_Me on 2013-11-11
I should have been more specific in my reply, what it shows when I start memtest is this
[http://postimg.org/image/dzzavu6nx/](http://postimg.org/image/dzzavu6nx/)
which doesn't change over time. Shouldn't it be printing out something as it goes through each cycle.
Thanks

---

### Post by houstonbofh on 2013-11-11
It is not correctly running.  If you have a newer system with a UEFI bios, you may need the Memtest 5.0.1

[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

---

### Post by J_Me on 2013-11-12
I tried booting from other distro's but they either do the same thing as before or won't boot(memtest86+, DSL). I used dd on memtest86+ should I have used something else.
What are my options.
Thanks
P.S. the computer is 4 years old and doesn't have a cd drive.

---

### Post by J_Me on 2013-11-12
Udate
I just swapped out the memory for one that was working before, so it should be good. I post back here if things go wrong again.

---

