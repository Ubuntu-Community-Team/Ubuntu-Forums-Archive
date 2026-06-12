---
title: "busy resources on aireplay"
date: 2009-01-28
forum: Security
---

### Post by joebrueske on 2009-01-28
I've already looked up onto how to test my new wireless router for security breaches with packet injections with aireplay-ng. I was able to successfully patch the Intel IWP driver just fine, and I can switch back and forth between old and patched using the rmmod and insmod commands.

I've been following the directions [here]("http://www.ubuntu-unleashed.com/2007/08/howto-aircrack-ng-quick-and-simple.html") to attempt to break through my security keys. I got up to step 4 when stuff didn't go as it should.

This is my iwconfig when I'm connected to the router return:
```
$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:A4  
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/100  Signal level=-59 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rtap0     no wireless extensions.

```
Of course the Access Point is my wireless router.

I opened a new terminal and started monitoring on channel 11.
```
$ sudo airmon-ng start eth1 11
```
I know the instructions don't specify the interface, but it errors out if I don't.

Then in a new terminal I start capturing with airodump-ng
```
$ sudo airodump-ng --channel 11  --write secondtry eth1
 CH 11 ][ Elapsed: 1 hour ][ 2009-01-28 08:02                                  
                                                                               
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ES
                                                                               
 00:00:00:00:C6  186 100    33947   289914  208  11  11 OPN              N
 00:00:00:00:A4  184 100    33959    28925    0  11  54. WEP  WEP         t 
 00:00:00:00:18  185  84    23863       18    0  11  54. WEP  WEP         B 
 00:00:00:00:81  186   0       95        0    0  11  11  WEP  WEP         < 
 00:00:00:00:13  199   0       69        0    0   6  48  WEP  WEP         S 
 00:00:00:00:A2  206   0       82        0    0   6  48  WPA  TKIP   PSK  l 
                                                                               
 BSSID              STATION            PWR   Rate  Lost  Packets  Probes       
                                                                               
 00:00:00:00:C6  00:00:00:00:27  186  11-11    35   311126  NETGEAR      
 00:00:00:00:C6  00:00:00:00:0A    0  11- 0     0     3068               
 (not associated)   00:00:00:00:2B  187   0- 1    47      332  Scott        
 (not associated)   00:00:00:00:AB  185   0- 1     0      435  NETGEAR  
```
The BSSID that ends in C6 is the open connection that my wireless card defaults to if not connected to my router, which ends in A4.

The deauthenticating attack. 1 little error
```
$ sudo aireplay-ng -0 5 -a 00:00:00:00:A4 -c 00:00:00:00:0A eth1
No source MAC (-h) specified. Using the device MAC (00:00:00:00:0A)
07:43:00  Waiting for beacon frame (BSSID: 00:00:00:00:A4)
07:43:00  Sending DeAuth to station   -- STMAC: [00:00:00:00:0A]
07:43:00  Sending DeAuth to station   -- STMAC: [00:00:00:00:0A]
07:43:01  Sending DeAuth to station   -- STMAC: [00:00:00:00:0A]
07:43:01  Sending DeAuth to station   -- STMAC: [00:00:00:00:0A]
07:43:02  Sending DeAuth to station   -- STMAC: [00:00:00:00:0A]
```

I went to the [airckrack-ng site]("http://www.aircrack-ng.org/doku.php?id=injection_test&s=injection%20test") and ran the test.
```
sudo aireplay-ng -9 eth1
07:11:29  Trying broadcast probe requests...
07:11:30  No Answer...
07:11:30  Found 3 APs

07:11:30  Trying directed probe requests...
07:11:30  00:00:00:00:C6 - channel: 11 - 'tai'
07:11:37   0/30:   0%

07:11:37  00:00:00:00:18 - channel: 11 - 'Bailey'
07:11:43   0/30:   0%

07:11:43  00:00:00:00:A4 - channel: 11 - 'NETGEAR'
07:11:50   0/30:   0%
```

This is what I go to do the packet re-injection
```
$ sudo aireplay-ng -3 -b 00:00:00:00:A4 -h 00:00:00:00:0A eth1
open(/dev/rtc) failed: Device or resource busy
07:48:03  Waiting for beacon frame (BSSID: 00:00:00:00:A4)
Saving ARP requests in replay_arp-0128-074803.cap
You should also start airodump-ng to capture replies.
```
And then nothing happens. No packets are read and no ARP requests come through. Any thoughts? 

My router is setup with a WEP, and when I disconnect from it my wireless card does connect to a different router that's in the building. Is that why I'm getting a "busy signal?"

I know it works because I was able to get it to go once, but that was on the open C6 router. That doesn't help me any of course. :) And yes, I did zero out the mac ids. I have no doubt my neighbors would like having their equipment ids winding up on a forum. :P

---

### Post by cariboo on 2009-01-28
As far as I know you can't directly check your wireless network, you have to have at least one other wireless device connected, to be able to check packets  going between your router and a wireless device.

Jim

---

### Post by teddks on 2009-01-28
Are you sure your drivers are patched? You failed the injection test.

The aircrack forums would be a better place than this, though.

---

### Post by joebrueske on 2009-02-02
Thanks for the direction teddks, I'll check those out.

For whatever reason when I tried it today it worked just fine. So I don't know what was different.

---

### Post by teddks on 2009-02-02
> **joebrueske said:**
> Thanks for the direction teddks, I'll check those out.

For whatever reason when I tried it today it worked just fine. So I don't know what was different.

Did you reboot between patching the drivers? If you didn't unload the modules (you have to do this even after installing them) then the old drivers would have been in effect.

---

