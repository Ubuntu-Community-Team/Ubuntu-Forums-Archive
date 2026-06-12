---
title: "HowTo: WPA with wpa_supplicant"
date: 2006-09-22
forum: Tutorials
---

### Post by luca_linux on 2006-09-22
[Here was my first HowTo about this topic]("http://www.ubuntuforums.org/showthread.php?t=26623"). It made a success, but now it's a bit out-to-date, as it was written for Hoary.
This stuff has started getting easier to configure since Breezy and now it's really very easy to have it work.
This HowTo will help you get WPA to work, no matter what wireless card you have. (This HowTo has been tested with an ipw2200).
So, let's start:

1) Open a terminal window and type:
```
wpa_passphrase your_ssid your_psk
```
Note: your_ssid is the name of your wireless network (a.k.a. SSID) and your_psk is the password you want to use to protect your network. (Look below for an example).

2) Now copy the psk string you got as output.

3) Type:
```
sudo gedit /etc/wpa_supplicant.conf
```
Then paste this as follow:
```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=your_psk
}

```
Note: your_psk is the psk string you got from step 1.

Here is an example:
```

luca@laptop1:~$ wpa_passphrase mywlan thisisthepassword
network={
        ssid="mywlan"
        #psk="thisisthepassword"
        psk=[COLOR="Red"]b22ec921c254c73f99b31b76ff876692ecde36839a1f2d92150829e6afcb5515[/COLOR]
}

```
The red string is what you have to paste into /etc/wpa_supplicant.conf as your_psk (without quotes obviously). So you'll have something like this:
```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="mywlan"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=b22ec921c254c73f99b31b76ff876692ecde36839a1f2d92150829e6afcb5515

```

4) Save the file and close Gedit.

5) Now we have to make wpa_supplicant load when system boots, so go back to the terminal window and type:
```
sudo gedit /etc/network/interfaces
```

6) Add the following lines in the part regarding your wireless card, as in the example below:
```

pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```
Note: "eth0" is your wireless device and "wext" is the driver; this is a kind of generic driver, so it should work with most wireless cards. If it doesn't, please try another driver, such as hostap, ndiswrapper, etc.
Here is an example:
```

iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
wireless-essid my_essid
gateway 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

7) Now run wpa_supplicant:
```
sudo wpa_supplicant -Bw -Dwext -i eth0 -c/etc/wpa_supplicant.conf
```
You should be online!



**Troubleshooting:**

You can run wpa_supplicant with -dd flag for a detailed debug output.

1) If you don't manage to connect to the AccessPoint, try to uncomment line 2 in /etc/wpa_supplicant.conf.
2) If that doesn't help, try change its value to 0 or 1.
3) If you get troubles while authenticating, try removing "RSN" and/or "CCMP" strings from /etc/wpa_supplicant.conf.

---

### Post by yopnono on 2006-09-24
Only like to say that if you put the string in "/etc/network/interfaces" you will get an error if you try to reload the DHCP "sudo ifup -a --force"

I would go for a boot script in the /etc/init.d/your_own_script
And add it using 
```
update-rc.d -f your_own_script start 40 S .
```

---

### Post by luca_linux on 2006-09-25
If you use DHCP, your /etc/network/interfaces should look like the following:
```

auto eth0
iface eth0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```

Does this cause that error?

---

### Post by yopnono on 2006-09-25
I know you should not enter the IP etc if using DHCP.
I did get an error
```
/etc/network/interfaces:12: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

But what was because of this:
```
iface eth0 inet dhcp
auto eth0
```
Instead of:
```
auto eth0
iface eth0 inet dhcp
```
Strange this only happen if I enter the pre-up/down to the interface file

---

### Post by yopnono on 2006-09-25
Another thing is that if you use the interface file and you dis/enable you network interfaces, it over writes the interface file.

---

### Post by matthewboh on 2006-09-25
I am so close - I can almost taste it, but still not having luck.  Can someone direct me?

I am running a LAMP server with a Linksys card running the Broadcom chipset.  It can see the access point, but it won't hook up correctly.  Here's the output of iwlist

```
eth0      Scan completed :
          Cell 01 - Address: 00:0C:41:D0:46:A0
                    ESSID:"matthewboh"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=100/100  Signal level=-145 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 270ms ago


```

and here's what the iwconfig brings back

```
eth0      IEEE 802.11b/g  ESSID:"matthewboh"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

The contents of the wpa_supplicant.conf 

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
# network={
#         ssid=""
#         key_mgmt=NONE
# }


# reading passphrase from stdin
network={
	ssid="matthewboh"
	proto=WPA RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP TKPI
	group=CCMP TKPI
	psk=c43ae013621f4aa1db2d1127664349f425a2852c352c2c1d6913bfb056736b8d
}

```

---

### Post by luca_linux on 2006-09-25
@ mattewboh: Are you trying without any protection/encryption? Otherwise, could you post the output of
```
sudo wpa_supplicant -Bw -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd
```?

---

### Post by luca_linux on 2006-09-25
> **yopnono said:**
> I know you should not enter the IP etc if using DHCP.
I did get an error
```
/etc/network/interfaces:12: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

But what was because of this:
```
iface eth0 inet dhcp
auto eth0
```
Instead of:
```
auto eth0
iface eth0 inet dhcp
```
Strange this only happen if I enter the pre-up/down to the interface file
Yeah, that's a bit strange.

---

### Post by matthewboh on 2006-09-25
It just comes back with 

Daemonize...

---

### Post by luca_linux on 2006-09-25
> **matthewboh said:**
> It just comes back with 

Daemonize...
Oh sorry, my mistake, I meant:
```
sudo wpa_supplicant -w -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd
```

---

### Post by matthewboh on 2006-09-25
Got this

```
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 22 - start of a new network block
ssid - hexdump_ascii(len=10):
     6d 61 74 74 68 65 77 62 6f 68                     matthewboh      
proto: 0x3
key_mgmt: 0x2
Line 26: invalid cipher 'TKPI'.
Line 26: failed to parse pairwise 'CCMP TKPI'.
Line 27: invalid cipher 'TKPI'.
Line 27: failed to parse group 'CCMP TKPI'.
PSK - hexdump(len=32): [REMOVED]
Line 29: failed to parse network block.
Failed to read read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface eth0
Cancelling scan request

```

---

### Post by matthewboh on 2006-09-25
D'oh!  It's TKIP instead of TKPI - fixed that, but still having a bit of a problem.  Here's the new debug file

```
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 22 - start of a new network block
ssid - hexdump_ascii(len=10):
     6d 61 74 74 68 65 77 62 6f 68                     matthewboh      
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='matthewboh'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Could not set interface 'eth0' UP
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:18:39:15:1c:11
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth0
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'matthewboh'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 24 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=19
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth0
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request

```

---

### Post by yopnono on 2006-09-25
> **matthewboh said:**
> 

The contents of the wpa_supplicant.conf 

```

	proto=WPA RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP TKPI
	group=CCMP TKPI


```


Try to replace your code with this
```
scan_ssid=1
key_mgmt=WPA-PSK
proto=WPA
```

---

### Post by matthewboh on 2006-09-25
Okay - I've changed the wpa_supplicant.conf to 

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
# network={
#         ssid=""
#         key_mgmt=NONE
# }


# reading passphrase from stdin
network={
	ssid="matthewboh"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
#	pairwise=CCMP TKIP
#	group=CCMP TKIP
	psk=c43ae013621f4aa1db2d1127664349f425a2852c352c2c1d6913bfb056736b8d
}

```

and when I typed in the wpa_supplicant cmd with a redirect to a debug file, got 

```
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 22 - start of a new network block
ssid - hexdump_ascii(len=10):
     6d 61 74 74 68 65 77 62 6f 68                     matthewboh      
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='matthewboh'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Could not set interface 'eth0' UP
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:18:39:15:1c:11
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth0
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'matthewboh'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=19
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth0
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request

```

---

### Post by luca_linux on 2006-09-25
Try playing with the parameter "ap_scan", setting it to 0, 1 and 2 and see if something changes.
Anyway, what wireless card do you have? It should also be a matter of driver, that is you should change "wext" (in the wpa_supplicant run command) to something else such as hostap, ndiswrapper, etc.

---

### Post by yopnono on 2006-09-25
Yes, which driver/card are you using, does it support WPA. Is WPA on at the router. etc,etc. Is it the same password.

---

### Post by beetee2 on 2006-09-25
I don't understand -- why is it eth0 if your wireless device is by default eth1? 

I also get "Daemonize.." as the output of "sudo wpa_supplicant -Bw -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd"

---

### Post by luca_linux on 2006-09-26
> **beetee2 said:**
> I don't understand -- why is it eth0 if your wireless device is by default eth1? 

I also get "Daemonize.." as the output of "sudo wpa_supplicant -Bw -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd"
In the HowTo I supposed the wireless card was eth0, but you have to change this with your device (as I wrote in the HowTo itself).

As for your output of wpa_supplicant, it's right if you are running it (you have to get "Daemonize..."), while if you want to see a detailed output for debug, just take the "-B" flag out and add "-dd".

---

### Post by onioneater36 on 2006-09-26
luca_linux...  Thank you very much.  I have been fighting with this for a long time and I feel I am now really close.  WPA-PSK is linking and my interface (ath0) is receiving an IP address via DHCP.  The only problem is the networking drops off from time to time...  I opened a terminal window and let it "iwevent" to see what has been happening and here is the result...

```
onioneater36@dell-c840-linux:~$ iwevent
Waiting for Wireless Events from interfaces...
18:45:22.846118   ath0     New Access Point/Cell address:Not-Associated
18:45:22.950340   ath0     Set ESSID:"my_wlan"
18:45:25.190388   ath0     Scan request completed
18:45:25.190576   ath0     Set ESSID:"my_wlan"
18:45:25.194708   ath0     New Access Point/Cell address:00:0F:B5:10:F9:77
18:45:25.326064   ath0     Custom driver event:MLME-REPLAYFAILURE.indication(keyid=0 unicast addr=00:0f:b5:23:bd:15)
18:45:35.236426   ath0     New Access Point/Cell address:Not-Associated
18:45:35.236653   ath0     Set ESSID:off/any
18:45:37.475151   ath0     Scan request completed
18:45:37.475325   ath0     Set ESSID:"my_wlan"
18:45:37.479323   ath0     New Access Point/Cell address:00:0F:B5:10:F9:77
18:45:37.627722   ath0     Custom driver event:MLME-REPLAYFAILURE.indication(keyid=0 unicast addr=00:0f:b5:23:bd:15)

```

Anyone have any idea how I can correct this problem???  Your guide taught me alot about what is going on and I really appreciate it.

---

### Post by yopnono on 2006-09-27
Check if you have more then one "wpa_supplicant" running in the system monitor.
Or more then one "dhclient3"

---

### Post by onioneater36 on 2006-09-27
yopnono...

I assume you wanted me to check in gnome under SYSTEM > ADMINISTRATION > SYSTEM MONITOR and I did not see even 1 instance of either wpa_supplicant or dhclient.  Is there something at the command line you wanted me to execute to examine these processes?

---

### Post by yopnono on 2006-09-27
from terminal 
ps -A

---

### Post by luca_linux on 2006-09-27
Moreover, did you add the SSID also to the configuration of your wireless card in Gnome network-admin?

---

### Post by luca_linux on 2006-09-27
From what you have written, I see you have an Atheros-based wireless card, so in the wpa_supplicant run command you should change "-Dwext" into "-Dmadwifi".

---

### Post by matthewboh on 2006-09-27
Just wanted everyone to know that I got my WMP54GS card running WPA TKIP using ndiswrapper and wpa_supplicant - NOT the bcm43xx driver.  Thanks everyone for your help and assistance!

---

### Post by onioneater36 on 2006-09-27
> **luca_linux said:**
> From what you have written, I see you have an Atheros-based wireless card, so in the wpa_supplicant run command you should change "-Dwext" into "-Dmadwifi".

Woops.  Sorry.  I should have mentioned that I did use -Dmadwifi and I also used -iath0 as my interface has the different designation.  Thank you.

I will try the ps -A when I get home this evening.  Thanks.  I have also noticed that if I am using the network with heavy traffic over the wifi it seems to stay up.  Droppings seems to occur during no/low usage.

---

### Post by yopnono on 2006-09-27
I did have a problem like yours before. 
This was because the wpa_supplicant started after suspend, so I had more then one wpa_s running and conflicting.

So I did put a killall wpa_supplicant script in the /etc/acpi/suspend.d folder. On the other hand I don't start my wpa using the interface file, I use a boot script, so it may not be the same issue.

---

### Post by 00trav on 2006-09-27
Hi all,
Don't mean to go off on a little tangent, but i have a quick question.

First off, I have everything working.  I connect fine and its not problem.  My issue is with my laptop when i got to different networks.  its a pain to constantly change the config file and the interface.  when i am going back and forth from unsecured to secured its not that bad but then i go from WPA to WPA its just a pain having to change all the files.

basically all I do is change my /etc/network/interfaces from

```
auto eth1
iface eth1 inet dhcp
wireless-essid COVAD1
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

to

```
auto eth1
iface eth1 inet dhcp
wireless-essid COVAD1
#pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant
```

then i have to restart the computer.  I know that there is a way to restart the networking and i have tried ifdown and then ifup, but no luck. Is there a applet out there that I can create profiles for different locations so i can just switch locations and deal with changing the wpa_supplicant.conf file and the interfaces file?  i am running gnome and i have tried the network configuration but no luck, it just overwrites the ESSID and nothing else.

thanks in advance and sorry for being slightly off topic, but i thought it kinda pertained to this how to

---

### Post by yopnono on 2006-09-28
> **00trav said:**
> I connect fine and its not problem.  My issue is with my laptop when i got to different networks.  its a pain to constantly change the config file and the interface.  when i am going back and forth from unsecured to secured its not that bad but then i go from WPA to WPA its just a pain having to change all the files.


This wpa config used in this thread is not for you. You should use network-manager.
You will find it in synaptic, or use the terminal.
```
sudo aptitude install network-manager
```

---

### Post by luca_linux on 2006-09-28
Yeah, you should use network-manager. Anyway, if I'm not mistaken, it only works with DHCP.

---

### Post by 00trav on 2006-09-28
I have network manager installed, i even reinstalled it, and it still doesn't seem to work right.  It sees wired network but not wireless, maybe i am not useing it correctly,  i do see a signal strength up in the upper right, which when i open gives me some network into, i can click configure and then i can see my network configuration setting to which i can click on configure of my wireless device and then i can see a drop down list of networks in the area, but there is only a spot for a wep key, and WPA doesn't work.  

As this is getting way off topic, i am going to start a new thread in the noob section, but thanks to everyone here since i at least could connect by altering the interface file and wpa_supplicant.conf,

---

### Post by onioneater36 on 2006-09-28
I had looked everywhere and could not get WIFI working until I found this thread.

Therefore, I would vote to make this thread a sticky.

---

### Post by Magneto on 2006-09-29
great info luca
using a ipw2200 with wpa-psk ccmp here and couldnt get network manager to act reliably

I would connect and drop until I removed all TKIP references and the RSN for wpa_supplicant.conf which I thought was weird. Then I'd connect longer and die until I commented out the ap_scan command. I had it commented out originally but it still wouldnt connect for longer than a few seconds.

The essid parameter in network/interfaces has disappeared.
And now my connection has dropped again. :( 

I can see (network monitor) and hear (the minipci card buzzes when it scans) my adapter falling into scan mode. I think there was a bug in the ipw2200 driver that it defaulted to scanning constantly - that was patched in march so this kernel driver is old. Im gonna try to throw it an option that is supposed to stop it, i think it was hwcrypto=0  I have to check on that one

How do I set permanent ip,gateway and dns settings for my wireless adapter? If I set them using the network monitor(gnome panel) they reset the adapter and the adapter generally doesnt reauthenticate with the ap. If I set them in the etc/network/interfaces they are ignored in part when I throw an ifup/ifdown to the interface. My ip might get set but the route might not.


what overwrites the interfaces file?

---

### Post by Magneto on 2006-09-29
echo options ipw2200 hwcrypto=0 > /etc/modprobe.d/ipw2200

solved all my weird problems so far

---

### Post by onioneater36 on 2006-09-29
One thing worth noting, I mentioned that my network would work most of the time but would drop occasionally.  Referencing the wpa_supplicant.conf file here...

```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=your_psk
}
```

I changed the one line to "proto=WPA" instead of "proto=WPA RSN" and it has not dropped since.  I did this on a guess just trying things to see if it would work and it did.  I knew what WPA was, but not what RSN meant and that is why I removed it.  Is there someplace that explains some of these major configuration files like /etc/network/interfaces and /etc/X11/xorg.conf and all these major files a linux noob who wants to become a linux junkie should know about?  I keep trying to learn more about the boot process and what happens and take it a file at a time, but if someone has advice how to learn the system, I'd definately take it.  I digress.  If anyone can answer the WPA vs WPA RSN and what that means, and why it may have fixed my problem, I'd appreciate it.

Thanks

---

### Post by Magneto on 2006-09-30
> **onioneater36 said:**
> One thing worth noting, I mentioned that my network would work most of the time but would drop occasionally.  Referencing the wpa_supplicant.conf file here...

```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=your_psk
}
```

I changed the one line to "proto=WPA" instead of "proto=WPA RSN" and it has not dropped since.  I did this on a guess just trying things to see if it would work and it did.  I knew what WPA was, but not what RSN meant and that is why I removed it.  Is there someplace that explains some of these major configuration files like /etc/network/interfaces and /etc/X11/xorg.conf and all these major files a linux noob who wants to become a linux junkie should know about?  I keep trying to learn more about the boot process and what happens and take it a file at a time, but if someone has advice how to learn the system, I'd definately take it.  I digress.  If anyone can answer the WPA vs WPA RSN and what that means, and why it may have fixed my problem, I'd appreciate it.

Thanks
check out the wpa supplicant website it has alot of info and the readme files that break down all the wpa_supplicant.conf options

rsn is wpa2, listing it as a possible option shouldnt effect the connectivity of other encryption protocols but it did for me too 

[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain)
[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain)

if u want to learn about anything id suggest using google to research the program/technology etc that youre interested in learning

gentoo forums and wiki are jampacked with info - remember to omit words with less than 4 letters in your searches on many sites including ubuntuforums, they will turn up blank - google wont do that and has a fair amount of the info here and on other forums indexed

good luck

---

### Post by Magneto on 2006-09-30
looks like ifup/down is the best tool

here's my wireless section of /etc/network/interfaces

```
#wireless

iface 	eth1 inet static
	pre-up modprobe ipw2200
	pre-up wpa_supplicant -Bw -Dwext -ieth11 -c/etc/wpa_supplicant.conf
	address 192.168.98.71
	netmask 255.255.255.0
	gateway 192.168.89.178
	wireless-essid leper
	wireless-mode Managed
	post-down rmmod ipw2200
	post-down rmmod ieee80211
	post-down rmmod ieee80211_crypt_ccmp
	post-down rmmod ieee80211_crypt
	post-down killall -q wpa_supplicant

```

that way i dont have to hear the adapter scan and everything gets a restart  when I bring it back up

---

### Post by luca_linux on 2006-09-30
The "proto=WPA RSN" parameter does not cause any issue to me...that's strange. It could probably depend on how your routers handles the authentication.
Anyway, thanks for your feedback. I'll add that suggestion (that is removing the "RSN" string to the HowTo.

---

### Post by luca_linux on 2006-09-30
> **onioneater36 said:**
> I had looked everywhere and could not get WIFI working until I found this thread.

Therefore, I would vote to make this thread a sticky.
Oh, thanks so much. I'm glad to have helped you out.

---

### Post by onioneater36 on 2006-09-30
Sorry to report that I am still having problems.  This is really frustrating the heck out of me.  I won't report anything else unless I am sure what fixed it, but when I run "iwevent" in a terminal window, I still get...

> Waiting for Wireless Events from interfaces...
17:24:29.917329   ath0     New Access Point/Cell address:Not-Associated
17:24:30.022573   ath0     Set ESSID:"my_network_id"
17:24:32.262922   ath0     Scan request completed
17:24:32.263077   ath0     Set ESSID:"my_network_id"
17:24:32.266839   ath0     New Access Point/Cell address:00:0F:B5:10:F9:77
17:24:32.396782   ath0     Custom driver event:MLME-REPLAYFAILURE.indication(keyid=0 unicast addr=00:0f:b5:23:bd:15)
17:24:42.304204   ath0     New Access Point/Cell address:Not-Associated
17:24:42.304391   ath0     Set ESSID: off/any
17:24:44.543386   ath0     Scan request completed
17:24:44.543569   ath0     Set ESSID:"my_network_id"


It seems to come back soon enough, but sometimes it just keeps playing now you see me now you don't.  I have loosened up some things on my router (no Super-G, no MAC address address list, broadcast SSID=yes, etc).  I will keep pluggin' and chuggin' and will report if the problem is solved.  Any ideas are sincerely appreciated (especially based on the error messages I have listed above from "iwevent".

Should I maybe download the source for the latest version of madwifi and wpa_supplicant and try updating?  I have whatever comes with Ubuntu 6.06 LTS 32bit at present.  I am also considering trying the NDISWRAPPER method as well, but right now, this is the closest I have gotten, so I don't want to persue that yet.

---

### Post by luca_linux on 2006-09-30
Please, post the wpa_supplicant.conf you are using at the moment.

---

### Post by onioneater36 on 2006-09-30
Here is my current wpa_supplicant.conf

You will see that I put the RSN back in since taking it out was actually not the problem.

> ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
        ssid="my_network_id"
        scan_ssid=1
        proto=WPA RSN
#       proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=9ae6b101b503bedc93b2570b0c2d77e161932e752a82e0ffc5db9317fb390ee4
}


---

### Post by luca_linux on 2006-10-01
First of all, I suggest you removing the psk key from your post for your privacy. :p 
Then, as for your problem, try to uncomment the second line and rebooting wpa_supplicant. If that doesn't help, try changing its value to 0 and/or 1.
In the meanwhile, also try taking "CCMP" out, even though that shouldn't help as "RSN".

---

### Post by onioneater36 on 2006-10-01
Thanks luca...

Just so you know, I too was concerned about putting the psk key in there too, so I changed a few numbers in there.  I figured you wanted to make sure I had one in there, so left it in (altered) for demonstration purposes.

I assume by rebooting wpa_supplicant, you want me to either reboot the lappy or do a...

```
wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
```

at a terminal window prompt.  After I do the wpa_supplicant command, do I have to do an...

sudo ifconfig ath0 down
sudo ifconfig ath0 up

Thanks again.

---

### Post by Magneto on 2006-10-01
there is a bug in the 1.1.1 version of the ipw2200 driver that is included with ubuntu dapper/edgy etc and kernels (from linus) including 2.6.17

the bug will show you the following messages repeatedly
[4295722.986000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.

this bug causes connection problems like disconnects - its behind alot of my connection troubles
im compiling the new driver from source to try to solve my problems

---

### Post by luca_linux on 2006-10-01
> **onioneater36 said:**
> Thanks luca...

Just so you know, I too was concerned about putting the psk key in there too, so I changed a few numbers in there.  I figured you wanted to make sure I had one in there, so left it in (altered) for demonstration purposes.

I assume by rebooting wpa_supplicant, you want me to either reboot the lappy or do a...

```
wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
```

at a terminal window prompt.  After I do the wpa_supplicant command, do I have to do an...

sudo ifconfig ath0 down
sudo ifconfig ath0 up

Thanks again.
Yeah, that's what I meant.

---

### Post by luca_linux on 2006-10-01
> **Magneto said:**
> there is a bug in the 1.1.1 version of the ipw2200 driver that is included with ubuntu dapper/edgy etc and kernels (from linus) including 2.6.17

the bug will show you the following messages repeatedly
[4295722.986000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.

this bug causes connection problems like disconnects - its behind alot of my connection troubles
im compiling the new driver from source to try to solve my problems
Ok, good to know.
Then let us know how it goes.

---

### Post by Magneto on 2006-10-01
> **luca_linux said:**
> Ok, good to know.
Then let us know how it goes.
well I installed the latest ieee80211, wireless tools, ipw2200 firmware and ipw2200 drivers and its a big improvement

no more queue full problems , no more disconnects every time I attempt to use the network

its much more reliable now - no need for the hwcrypto=0 module option because the issue has been fixed

one thing I did have to do is re-enable the apscan option in wpa_supplicant.conf because my essid is hidden and without that option I have serious problems trying to authenticate

its pretty much the same process as your old howto although some make processes run the removal scripts automatically

for me its really worth it - i have no idea why stable drivers and tools that have been out more than 6 months havent been included in ubuntu
wireless tools is at 28  ubuntu is at 18
ipw2200 is at 1.2.0 ubuntu is at 1.1.1
ipw firmware is at 3.0 ubuntu is at 2.4
same with ieee
:(

---

### Post by almax00 on 2006-10-02
good to find this how-to. is it advisable to delete anything before trying this...ie network-manager, network-manager-gnome etc? thankyou.

---

### Post by luca_linux on 2006-10-02
No, they shouldn't be a problem.

---

### Post by onioneater36 on 2006-10-05
luca & magneto...

Having learned from one of your previous posts that the RSN in the WPA RSN line for "proto" meant WPA2, I re-did my WPA_supplicant.conf to use WPA2 and reconfigured my router as well.  Although it has not worked on WPA, it does seem to be working on WPA2.  Perhaps this could help someone else if they had the same problem.

---

### Post by bobbyone on 2006-10-15
matthewboh or anyone who can help ->  I have a bcm4311 wireless card using it with ndiswrapper.  I am trying to set up wpa_supplicant per the how-to but I get the following when running it with -dd option:  ```
Driver doesn't support WPA
``` I get this when using option -Dndiswrapper of wpa_supplicant.  If I use -Dwext I don't get that message but I can't connect to my network.  I know there is some info you might need but I am not sure what else to post here.  Oh yes, I am using AMD64 Dapper.  And I got a connection before when using WEP, but I want the stronger WPA security.

---

### Post by matthewboh on 2006-10-18
Bobbyone - I found out the drivers that come with Ubuntu don't support the stronger WPA security.  I ended up using the Windows drivers that came with the card.  I ended up using this HOWTO in order to set up my card - [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

### Post by Haiyadragon on 2006-10-21
I can connect to the internet with this method. However, for some reason the router detects it as a direct connection, not wireless. The router reports that it has given 192.168.2.3 as ip, but Ubuntu says 192.168.2.103. I can't access the local network, it doesn't find the computers it should find. And when I try to access the router on 192.168.2.1 it wants a login and password which I normally don't give in that manner (it should show the router login page).

Any ideas on how this weirdness is happening? Ofcourse, everything works as it should on Windows. I've tried this on Arch Linux also and it's the same. I may try a wep key with mac filtering later but only to test it.

---

### Post by luca_linux on 2006-10-22
> **Haiyadragon said:**
> I can connect to the internet with this method. However, for some reason the router detects it as a direct connection, not wireless. The router reports that it has given 192.168.2.3 as ip, but Ubuntu says 192.168.2.103. I can't access the local network, it doesn't find the computers it should find. And when I try to access the router on 192.168.2.1 it wants a login and password which I normally don't give in that manner (it should show the router login page).

Any ideas on how this weirdness is happening? Ofcourse, everything works as it should on Windows. I've tried this on Arch Linux also and it's the same. I may try a wep key with mac filtering later but only to test it.
I guess you are using DHCP, so just try using a Static IP.

---

### Post by Moseycd on 2006-10-24
I followed these steps and now my wireless card does not show up at all anywhere. I am using kubuntu, and my wireless card is an intel 3945ABG. Does anybody have any ideas on how I can at least get it to show up?

---

### Post by bodhi.zazen on 2006-10-31
Nice How-to luca_linux.

This thread has been added to the UDSF wiki.

[WPA with wpa_supplicant](http://doc.gwos.org/index.php/WPAwpa_suppicant)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by PartisanEntity on 2006-11-13
> **luca_linux said:**
> 

1) Open a terminal window and type:
```
wpa_passphrase your_ssid your_psk
```
Note: your_ssid is the name of your wireless network (a.k.a. SSID) and your_psk is the password you want to use to protect your network. (Look below for an example).

Hello,

I do not understand what is meant with 'your_psk'.

Is this something I choose locally on my computer in Ubuntu or is this supposed to be stored on the router?

My netgear router is set to use wpa-psk but i only have a passphrase, no psk.

And another question, is wpa_supplicant already installed in Dapper? Or do I have to download it manually?

---

### Post by peterbakker on 2006-11-13
pf...
as for me; i'd stick to WEP for a few more years8) until out of the box bla bla
No need to configure - concerning my state of health i prefer *no configure* to some neighbour-nerds trying to access me web

---

### Post by thele0pard on 2006-11-13
kewla.

this worked for me. i thought it was screwed, then checked my _passphrase output AND IT WAS WRONG. so, all changed and working perfectly ta.

thanks for the great work  =P

edit: actually, now i want to know how to script it so that i can run from my desktop or panel. i dont want it running at boot as im scared that it will be broadcasting my ssid and psk from boot, so i want to choose. Can i just chmod +x it?

PartisanEntity - follow the walkthru earlier in this post or browse the many links from here - you will find a solution, or closure.

---

### Post by daverave999 on 2006-11-14
I followed this set of instructions and it all went smoothly, bar forgetting to change eth0 to eth2 in my case. I'm using a Broadcomm chipset card, Belkin F5D7001UK, if that helps anyone who's unsure whether it will work or not.

---

### Post by giruzz on 2006-11-19
Hi,

I'm new with Linux...I'm trying to use my WPA-wifi connection with my notebook... the wifi card is a Intel 2200BG.

This is what I've done so far:

sudo kwrite /etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid=Sydney
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=370d97a2c2d4564c0c34647ac4d57f9b49b068f06aae32b2df243d48a74408771
}

(SSID and PSK aren't the one I use, just copy and pasted and changed a bit)

Then....

sudo kwrite /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
iface wlan0 inet dhcp
wireless-essid Sydney
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0

and last

sudo wpa_supplicant -Bw -Dwext -i eth0 -c/etc/wpa_supplicant.conf

....everything should work but it doesn't...

So...anyone can help me?

I'm not sure if this makes any difference but I receive this message when I'm running Kwrite...

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
giruzz@giruzz-laptop:~$ sudo kwrite /etc/network/interfaces
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Thanks for any help!

giruzz

---

### Post by somegayname on 2006-12-06
First off, thanks Luca. I used your previous how-to for an install about a year ago, and this one has me close to wireless.  My last problem is that for some reason it keeps dropping and picking up the access point
```

iablt:/home/iab# iwevent
Waiting for Wireless Events from interfaces...
23:25:57.780616   eth2     New Access Point/Cell address:Not-Associated
23:25:57.780856   eth2     New Access Point/Cell address:Not-Associated
23:26:00.882024   eth2     Set Mode:Managed
23:26:00.882091   eth2     Set ESSID:"WiFabu"
23:26:01.086865   eth2     New Access Point/Cell address:00:14:BF:39:40:EE
23:26:05.052726   eth2     New Access Point/Cell address:Not-Associated
23:26:05.053576   eth2     New Access Point/Cell address:Not-Associated
23:26:08.154450   eth2     Set Mode:Managed
23:26:08.154474   eth2     Set ESSID:"WiFabu"
23:26:08.333068   eth2     New Access Point/Cell address:00:14:BF:39:40:EE
23:26:12.296069   eth2     New Access Point/Cell address:Not-Associated
23:26:12.296097   eth2     New Access Point/Cell address:Not-Associated
23:26:15.399157   eth2     Set Mode:Managed
23:26:15.399184   eth2     Set ESSID:"WiFabu"
23:26:15.588405   eth2     New Access Point/Cell address:00:14:BF:39:40:EE
23:26:19.546805   eth2     New Access Point/Cell address:Not-Associated
23:26:19.547655   eth2     New Access Point/Cell address:Not-Associated

```

a similar symptom is seen with random hits from iwconfig:
```

iablt:/home/iab# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      unassociated  ESSID:"WiFabu"
          Mode:Managed  Channel=0  Access Point: 00:14:BF:39:40:EE
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

iablt:/home/iab# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11g  ESSID:"WiFabu"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:39:40:EE
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=98/100  Signal level=-28 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

You can see the Bit rate, signal level, noise level and the associated channel 0 then have values.

My wpa_supplicant.conf and interface files are cut and paste from your how-to, excepting for my ssid and psk.  The machine has a Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
I don't think this *should* make any difference, but I am running debian etch with kernel 2.6.17  Any ideas?

---

### Post by marcos.placona on 2006-12-08
You're amazing! uch a star! I followed your tutorial and it worked on the first time. After following step by step I just rebooted and off it went.

Thank you very much!

---

### Post by lcohen999 on 2006-12-09
i'm wondering if router affect this

I have two linksys routers, one a WRT54G and a WRT54GL
both with DD-WRT v23 SP2, both with the same SSID and PSK.

The 54GL likes wpa_supplicant, then WRT54G gives me this error:
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys


any thoughts?

---

### Post by mnisecky on 2006-12-16
> **matthewboh said:**
> D'oh!  It's TKIP instead of TKPI - fixed that, but still having a bit of a problem.  Here's the new debug file

```
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 22 - start of a new network block
ssid - hexdump_ascii(len=10):
     6d 61 74 74 68 65 77 62 6f 68                     matthewboh      
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='matthewboh'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Could not set interface 'eth0' UP
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:18:39:15:1c:11
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth0
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'matthewboh'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 24 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=19
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth0
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request

```
Can you tell me where is this debug or how command you use ? I need this information - I have a problem concerning WPA-TKIP.
Many thanks !

---

### Post by An_ant on 2006-12-17
L.S.,

After trying a number of different options I managed to get connection working. I will detail the options on a website in Dutch so other people who want to use wpa on a Dutch network can find help. Thanks for all the advise here on these pages.

---

### Post by RootsLINUX on 2006-12-18
I had wireless working with Ubuntu until I upgraded to Edgy (I did a clean wipe and install), but I am totally stumped at why I can't get it to work anymore. I've followed every post in this thread and tried playing around with many different configuration settings, but I've had absolutely no luck.

My main problem is that my wireless card can't find (scan?) my network (I have an Intel ipw2200 wireless card, and the device is eth1), nor any networks for that matter. My network's name is "dude wireless" and uses WEP encryption. My Debian desktop is connected to it just fine. I've tried both the wext and ipw drivers for wpa_supplicant, but neither of them worked.

Here is the output of a ton of commands/files, so if anyone can help me figure out what's wrong, I would appreciate it.


**$ /etc/network/interfaces**
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wireless-essid dude wireless
wireless-mode managed
wireless-key MYSECRET
pre-up wpa_supplicant -Bw -Dipw -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

#iface eth0 inet dhcp

```

**$ cat wpa_supplicant.conf**
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=0

network={
        ssid="dude wireless"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=SECRET :D
}

```

**$ iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"dude wireless"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

**$ ifconfig**
```

eth1      Link encap:Ethernet  HWaddr 00:12:F0:55:A8:4C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Memory:dcffd000-dcffdfff

```

**$ dmesg | grep ipw**
```

[17179590.608000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179590.608000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179590.608000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179590.608000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179591.332000] ipw2200: Radio Frequency Kill Switch is On:
[17179591.332000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

```

**$ sudo wpa_supplicant -dd -Dipw -ieth1 -c/etc/wpa_supplicant.conf**
```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=13):
     64 75 64 65 20 77 69 72 65 6c 65 73 73            dude wireless   
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='dude wireless'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:12:f0:55:a8:4c
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=13):
     64 75 64 65 20 77 69 72 65 6c 65 73 73            dude wireless   
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=13):
     64 75 64 65 20 77 69 72 65 6c 65 73 73            dude wireless   
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: SCANNING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Cancelling scan request

```

---

### Post by RootsLINUX on 2006-12-19
I don't have a clue why, but now suddenly it works. :confused: Its so weird, I didn't change anything from my post above! Oh well, I'm just happy to have it working finally. :D

---

### Post by PenguinEndre on 2006-12-23
First of all, I'm new to this so go easy on me. I have come to the part where I'm to paste that thread in to interfaces. But I'm not sure where, under the eth0 or wlan0? 

this is what interfaces says: 

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0 inet dhcp
iface wlan0 inet dhcp

auto eth1
iface eth1 inet dhcp
[/I]

And should I get any reply when I try to run Wpa_supplicant? I don't get any =S

Thanks in advance

---

### Post by MrNormS on 2006-12-27
I'm having problems.  I've confirmed that my Broadcom 4318 is working; [FONT="Courier New"]iwlist eth1 scan[/FONT] shows me both mine and my neighbour's networks.  Here's what my /etc/wpa_supplicant.conf looks like:
```

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
# network={
#         ssid=""
#         key_mgmt=NONE
# }


# reading passphrase from stdin
network={
        ssid="obcomputer"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
#       pairwise=CCMP TKIP
#       group=CCMP TKIP
        psk=792f89822002762c11thisnotmyrealpsk114236da73a3f7c9b
}
```

When I run [FONT="Courier New"]sudo wpa_supplicant -Dndiswrapper -ieth1 -c/etc/wpa_supplicant.conf -dd[/FONT] I see a few things that don't look right.  Here I've bolded them:

```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 22 - start of a new network block
ssid - hexdump_ascii(len=10):
     6f 62 63 6f 6d 70 75 74 65 72                     obcomputer      
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='obcomputer'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:14:a4:3b:7c:63
**Driver does not support WPA.**
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'obcomputer'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
**Association request to the driver failed**
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'obcomputer'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'obcomputer'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request
```

@matthewboh
I looks like you have similar hardware to mine.  Maybe you could post your wpa_supplicant.conf?

@all
Any help or suggestions would be greatly appreciated.  I'd love to get my new laptop online on linux.

EDIT: Nevermind, I have it working.  I changed the driver to wext and ap_scan to 1.  Though no one had a chance to help me directly, I'd like to thank you all for your help; this thread has really been helpful.

---

### Post by ZippyDaMCT on 2007-01-09
This seems a good thread, but after I do step one, and then Gedit /etc/wpa_supplicant.conf the file does not exist, why is this?](*,)

---

### Post by brandt on 2007-01-12
Thanks for the Howto.  I got it to work such that I can connect if I run

```

sudo /etc/init.d/networking restart

```

however, when the computer starts up, it doesn't seem to be getting an IP.  How do I configure it so I don't have to manually restart networking?  Thanks.

---

### Post by t_anjan on 2007-01-15
I've followed the HOW-TO exactly.
I've got a Netgear WG111v2 USB dongle that I have installed using NDISWRAPPER. 

'iwlist scan' shows me the available network:

```
anjan@supernal:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:F0:03:06
                    ESSID:"AnjanWireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality:17  Signal level:0  Noise level:2
                    Extra: Last beacon: 0ms ago
```

Output of 'iwconfig'
```
anjan@supernal:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"AnjanWireless"  
          Mode:Managed  Channel=11  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Contents of my 'interfaces' file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid AnjanWireless
wpa-driver wext
wpa-conf master
wpa-ssid AnjanWireless
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <hidden>
```


First, before reading this How-To, I had my 'interfaces' file without all the wpa config commands. Instead I had these two lines:

```
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Contents of my 'wpa_supplicant.conf' file:

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="AnjanWireless"
	scan_ssid=1
       	key_mgmt=WPA-PSK
	proto=WPA
       	#pairwise=CCMP TKIP
       	#group=CCMP TKIP
        #psk="<hidden>"
        psk=<hidden>
}
```

Everything seems OK to me. But I just cannot hook up to my wireless router, even after disabling my wired connection (eth0) and disconnecting my ethernet cable.

Please, I've spent three days on this now and Ubuntu is really starting to frustrate me. Someone help!

---

### Post by merry_meerkat on 2007-01-15
Just a thought:
Have you tried using NetworkManager? (choose network-manager-gnome in synaptic)
Once it is installed, comment out all the lines that refer to your wireless interface in your **interfaces **file
Then reboot

Some references: [1]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6") [2]("http://boff.wordpress.com/tag/wireless/")

---

### Post by t_anjan on 2007-01-15
> **merry_meerkat said:**
> Just a thought:
Have you tried using NetworkManager? (choose network-manager-gnome in synaptic)
Once it is installed, comment out all the lines that refer to your wireless interface in your **interfaces **file
Then reboot

Some references: [1]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6") [2]("http://boff.wordpress.com/tag/wireless/")

Yes, I've tried Network Manager. I've tried both the versions, one from the Synaptics Package Manager and the other from SVN. The Synaptics version has only WEP in it. The SVN version was supposed to display WPA, but gave me only one additional encryption option: LEAP.

Forgetting about encryption, both versions of Network Manager were unable to connect to even an unencrypted wireless network, as has been the case with all methods I've tried.

---

### Post by Skiboo on 2007-01-15
I finally managed to get it going thanks to this info after banging my head against a wall for a few hours. 

Like MrNormS, I was using -Dndiswrapper instead of -Dwext, in my case due to 
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) , I ran wpa_supplicant -h and saw the list of drivers, assuming ndiswrapper was the one.

Other than that, the only hard part was actually finding the right windows drivers for my card.

---

### Post by t_anjan on 2007-01-16
To heck with WPA. I've temporarily disabled all security on my router. I want Edgy to connect to my unsecured router. 

My "interfaces" file:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid AnjanWireless
wireless-channel 2
wireless-mode managed
```

Output of **sudo /etc/init.d/networking restart**

```
anjan@supernal:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 8963
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:08:c7:0e
Sending on   LPF/wlan0/00:18:4d:08:c7:0e
Sending on   Socket/fallback
[B][COLOR="Red"]Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.[/COLOR][/B]
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:08:c7:0e
Sending on   LPF/wlan0/00:18:4d:08:c7:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I think these two lines are the most important:
```
[B][COLOR="Red"]Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Operation not supported.[/COLOR][/B]
```

I have no idea why SET is not working. Any ideas? I can't even connect to an unsecured network!!!

---

### Post by aresgoddess on 2007-01-17
hi, i just had a few questions. I've been using Ubuntu for more than a year, but i don't understand a lot. In this thread, there was some stuff that was mentioned that I'm hoping can be clarified. 

1) when the code (like in Question 2) is entered into the terminal to start up the connection and the response is "Daemonizing", what does that mean?

2) What is the difference between
```
sudo wpa_supplicant -w -Dmadwifi -i eth0 -c/etc/wpa_supplicant.conf -dd
```
and
```
sudo wpa_supplicant -w -Dwext -i eth0 -c/etc/wpa_supplicant.conf -dd
```

3) what is the difference between eth0 and ath0?

4) Where does the ndiswrapper fit into all of this?

5) what is dhclient3?

Thank you in advance. I hope to understand using the codes better, and actually get my connection working with the new understanding of how it all works.

---

### Post by Hase on 2007-01-19
I finally got everything configured for wpa_supplicant.  It works beautifully, but, I always have to manually dhcp after the boot completes.
```
sudo dhclient
```
How do I get the system to do that after it starts wpa_supplicant?

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

/etc/wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
	ssid="xxxxxx"
	psk=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
	key_mgmt=WPA-PSK
	proto=WPA
	priority=5
}

network={
	ssid=""
	key_mgmt=NONE
	priority=2
}

```

---

### Post by aresgoddess on 2007-01-19
i figured out the answers to the questions i had above. though i still don't know what "dhclient3" is... anyways, i've almost got my computer connected to the wireless, but it still has the disconnection symbol on the icon. everything is fine until I run ```
sudo dhclient
``` and then the response is ```
No DHCPOFFERS received.
No working leases in the persistent database - sleeping.
```
there's more to the response, but it's too long to type out, and i can't copy and paste, as i am using a different computer than the one that's having problems. =(

It's been doing that every single time. So far, i've changed from automatic DHCP to a static IP, i've changed codes in the wpa_supplicant.conf AND the /etc/network/interfaces, and nothing seems to make a difference. It keeps getting stuck at that point.

this is what i have in my /etc/wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
    ssid="networkname"
    scan_ssid=0
    key_mgmt=WPA-PSK
    proto=WPA
#  pairwise=CCMP TKIP
#  group=CCMP TKIP
    psk=very long number/letter sequence
}
```

is it possible to have settings for two different wireless networks? if so, how do i do that? I assume that it would deal with the other dealies in the interfaces file, like eth0, eth1, eth2, wlan0, and lo, but what do all those mean?

---

### Post by 1975 on 2007-01-22
Hello

I'm trying to configure WPA using my ipw2200

My /etc/wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="senso-unico.nl"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=<<<CUT>>>
}

```

My /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```


Now when I run
```
$ sudo wpa_supplicant -w -Dwext -i eth1 -c/etc/wpa_supplicant.conf -dd
```
I get:
```
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=14):
     73 65 6e 73 6f 2d 75 6e 69 63 6f 2e 6e 6c         senso-unico.nl
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='senso-unico.nl'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:13:ce:d9:72:f3
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
Failed to add interface eth1
State: DISCONNECTED -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request

```

Anyone any ideas?

Thanks!

Bou

---

### Post by 1975 on 2007-01-23
I got by this problem by first deactivating my eth1 in System - Administration - Networking

Now I get the following problem:
```
bou@nlyehvsaq1nb0lf:~$ sudo wpa_supplicant -w -Dwext -i eth1 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=14):
     73 65 6e 73 6f 2d 75 6e 69 63 6f 2e 6e 6c         senso-unico.nl
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='senso-unico.nl'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:13:ce:d9:72:f3
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=14):
     73 65 6e 73 6f 2d 75 6e 69 63 6f 2e 6e 6c         senso-unico.nl
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.

```

What does that mean, "no suitable AP found"?

---

### Post by 1975 on 2007-01-23
> **luca_linux said:**
> From what you have written, I see you have an Atheros-based wireless card, so in the wpa_supplicant run command you should change "-Dwext" into "-Dmadwifi".

I have an Intel Pro Wireless 2200, and I now use -Dwext, is that ok?

---

### Post by Nugget21 on 2007-01-23
Hey guys.

So I just switched to Ubuntu from Fedora today and I'm trying to get my Intel 2200b/g going (as I couldn't on Fedora either!!!

Few questions:

1) Which driver should I be using for the 2200?  Dwext or Dipw?
2) No matter what I seem to do it doesn't even look like my wireless LED lights up at all!
3) Is this really what has to be done to connect to any WPA network?  Seems a bit long winded.

Thanks in advance guys...

---

### Post by ingo on 2007-01-24
I tried farting around with lots of code in my /etc/network/interfaces, Knet, KWlan, KwifiManager and what have you - all to no avail.

This little howto did it for me and my IBM T41 - bloody excellent work!

Thanks a million!

Ingo

---

### Post by ingo on 2007-01-25
ok, first it worked, then it didn't, then it did again...

worrisome!

switched to knetworkmanager ([https://wiki.ubuntu.com/DapperKNetworkmanager](https://wiki.ubuntu.com/DapperKNetworkmanager)) and it is the absolute killer when it comes to working with networks. 

there is a little configuration to be done (feel free to ask questions) but quite simply superb.

---

### Post by corax on 2007-01-29
Hi everyone !

First I' d like to congratulate to luca_linux for this very nice howto ! :-)

I have 3 minor problems ...

1,To luca: you also have ipw2200 why is it not working with

```
sudo wpa_supplicant -Bw -Dipw -i eth0 -c/etc/wpa_supplicant.conf
```

It works if I use -Dwext so it is not a big thing I'm just curious :-)

2,Any of you guys (and/or girls ;-) ) tried to use ipw2200 chip with WPA under M$ Windozer ? Because if I switch my network to WPA my other machines with ipw2200 (and XP) would not connect. :-(

I read some articles about ipw2200 + WPA under XP but none of them give straight and exact explanation (unlike this GREAT howto :-) )

3, Is WPA 2 possible somehow ? My router is capable for sure ... but I think ipw2200 will be not enough for that :)

Thanks for all !

---

### Post by s-bris on 2007-02-04
Hi ,

I have installed ubuntu 6.10 on my dell inspirion 6000 and love it (the LAN card works fine and I can get itnernet) - one glitch - quite major - I can't get the wireless inbuilt centrino adaptor to work - ultimatley I want it to work over my WPA TKIP connection that my existing windows boxes use.

As I want to transition away from Windows this is the only factor stopping me from making the switch on all my computers to Ubuntu - so please help if possible.

When I do an iwlist I can see that eth1 seems to be picking up my wireless access point SSID.  But it will not connect.  I have followed the above instructions except when I type in the wpa_passphrase your_ssid your_psk - nothing comes back.

Do I have to download the tar files suggested in [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623) , and then extract and install them to het wpa+passphrase to work or should they be there with 6.10 ?

So is the psk that needs to go into the psk part of the wpa_supplicant file ned to be generated by using the wpa_passphrase command ?


thanks heaps
steve

---

### Post by ingo on 2007-02-05
Hi s-bris,

even though I have never run Ubuntu (Kubuntu is my poison) I am certain that you might want to try this little beauty

[https://wiki.ubuntu.com/DapperKNetworkmanager](https://wiki.ubuntu.com/DapperKNetworkmanager)

Not only does it list all the networks your card can see, but it also takes care of wep and wpa for you. 

HTH

---

### Post by alessandrop65 on 2007-02-19
Luca... thank you so much!! I made my wireless work (Intel 2915abg work on XPS m170 laptop) doing everything outlined in your how-to. The last few suggestions did the trick for me after a quick reboot. Again thank you!!!! I have looked at a ton of other forum entries and yours did the trick!

Ciao,
Alex

---

### Post by zes on 2007-02-23
hi, i´m using a laptop with a broadcom wireless card, 4318, after trying first with ndiswrapper and was working fine, now i use bcm43xx-fwcutter and works +-, worst than ndiswrapper, but i was unable to activate wpa with ndiswrappper.

well, on Kubuntu, every time i boot my laptop i have to make 2 things to have wireless working and connected to my wpa protected home lan.

first: run kwlan, and wait for a message that says: "eth1 is connected"
second: after that message, run in terminal "sudo dhclient eth1".

i have to make those steps every boot.

there is any way to get always eth1 connected?, and get ip from dhcp automatically?

thx

---

### Post by webnetwiz on 2007-02-24
Question:

How do I set this up on a laptop (HP NC6220) with IPW2200 (Intel 2915ABG), but I have to use a certificate file vs PSK?

---

### Post by mondomunchies on 2007-02-27
I read somewhere that ctrl_interface does not work well with wpa_supplicant and you can probably sidestep the problem by removing the lines at the beginning of the config that start with ctrl_interface.

Hope that helps.

---

### Post by tel3caster on 2007-03-11
Sorry, I just recently switched to Ubuntu. I think I can connect to my network, or at least wpa_supplicant tells me I can but I'm still unable to access the internet for some odd reason. Any tips?

---

### Post by stenyak on 2007-03-15
> **somegayname said:**
> First off, thanks Luca. I used your previous how-to for an install about a year ago, and this one has me close to wireless.  My last problem is that for some reason it keeps dropping and picking up the access point
```

iablt:/home/iab# iwevent
Waiting for Wireless Events from interfaces...
23:25:57.780616   eth2     New Access Point/Cell address:Not-Associated
23:25:57.780856   eth2     New Access Point/Cell address:Not-Associated
23:26:00.882024   eth2     Set Mode:Managed
23:26:00.882091   eth2     Set ESSID:"WiFabu"
23:26:01.086865   eth2     New Access Point/Cell address:00:14:BF:39:40:EE
23:26:05.052726   eth2     New Access Point/Cell address:Not-Associated
23:26:05.053576   eth2     New Access Point/Cell address:Not-Associated
23:26:08.154450   eth2     Set Mode:Managed
23:26:08.154474   eth2     Set ESSID:"WiFabu"
23:26:08.333068   eth2     New Access Point/Cell address:00:14:BF:39:40:EE
23:26:12.296069   eth2     New Access Point/Cell address:Not-Associated
23:26:12.296097   eth2     New Access Point/Cell address:Not-Associated
23:26:15.399157   eth2     Set Mode:Managed
23:26:15.399184   eth2     Set ESSID:"WiFabu"
23:26:15.588405   eth2     New Access Point/Cell address:00:14:BF:39:40:EE
23:26:19.546805   eth2     New Access Point/Cell address:Not-Associated
23:26:19.547655   eth2     New Access Point/Cell address:Not-Associated

```

a similar symptom is seen with random hits from iwconfig:
```

iablt:/home/iab# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      unassociated  ESSID:"WiFabu"
          Mode:Managed  Channel=0  Access Point: 00:14:BF:39:40:EE
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

iablt:/home/iab# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11g  ESSID:"WiFabu"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:39:40:EE
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=98/100  Signal level=-28 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

You can see the Bit rate, signal level, noise level and the associated channel 0 then have values.

My wpa_supplicant.conf and interface files are cut and paste from your how-to, excepting for my ssid and psk.  The machine has a Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
I don't think this *should* make any difference, but I am running debian etch with kernel 2.6.17  Any ideas?

I have the same problem. Mine is a PCMCIA SMC card, and i'm using ndiswrapper.
Any idea what is causing the disconnections?

---

### Post by numa666 on 2007-03-16
I have exactly the same problem. I'm using IBM R50e laptop, Kubuntu 6.10, ipw2200 with latest drivers (1.2.1) and firmware (3.0).

I'm connecting to Linksys WRT54GS, firmware 1.5.2.

I tried manually configuring wpa_supplicant and KNetworkManager. Same problem. 

My Ralink card (desktop) connects just fine to my router using WPA, and my laptop connects without a problem to an open AP.

It seems the card associates and then tries to associate again, gets an error and disconnects.

---

### Post by matthewboh on 2007-03-17
I was having the same problem with an ipw card.  Network Manager now comes with 6.1, and I finally fixed the problem by going to /etc/network/interfaces file and commenting out everything except for lo - then ran network manager and it worked like a champ!

---

### Post by MrDetermination on 2007-03-18
This guide gets me up and running for a short time in Edgy, then nothing after any period of inactivity.  My network manager applet shows a "wired network RaLink RT2561/RT61 802.11g pc", or did before I implemented the things in the first post of this thread.  The card is actually a Linksys PCI card, WMP54g.  I drop after a few minutes of inactivity and can't figure out why or how to restore connection without restarting the machine.

interfaces:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid thisismyhouse
gateway 192.168.0.1
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

wpa_supplicant:
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="thisismyhouse"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
psk=404b8fb415XXXXXXXX90504acd10dbfcf
}

```

```
chip@Metallo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"thisismyhouse"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:A3:D1:E4   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

chip@Metallo:~$ sudo lshw
Password:
metallo                   
    description: Desktop Computer
    product: VT8367-8235
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: VT8367-8235
       physical id: 0
       slot: PS/2 Mouse
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/10/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.4.4
          slot: Socket A
          size: 1333MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 74
             serial: 00:0d:87:aa:42:96
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
             resources: ioport:e000-e0ff iomemory:ee10a000-ee10a0ff irq:11
chip@Metallo:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:A3:D1:E4
                    ESSID:"thisismyhouse"
                    Mode:Master
                    Frequency:2.412 GHz
                    Encryption key:on
                    Extra:wpa_ie=dd160050f201010000XXX
                    Extra:tsf=000000c6053221ca

chip@Metallo:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:f8:2d:fa:01
Sending on   LPF/wlan0/00:18:f8:2d:fa:01
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.101 -- renewal in 301942 seconds.

```

Any ideas?

---

### Post by JoeyJoeJoe on 2007-04-01
I tried the instructions and no joy at all with wpa_supplicant

I have a lot of questions about these instructions. I will go step by step

1. Ran the following in terminal window:
	```
wpa_passphrase 'MYSSID' 'MY_PSK'
```
Where 'MYSSID' and 'MY_PSK' correspond with that of my wireless router.

I got the resultant psk string and copied it

2. Ran 
```
sudo gedit /etc/wpa_supplicant.conf
```

A blank file opened. Is that normal? I followed the instructions adding the following to the .conf file:

> ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid='MYSSID'
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk='MY_PSK_STRING'
}

I saved this file.

3. I ran 
```
sudo gedit /etc/network/interfaces
```

Here is where things got kind of confusing. What you see below is what I currently have in that file. I placed what the instructions said under 'auto eth0' originally but that immediately dropped my wired connection when I ran wpa_supplicant in the final step. So I fixed it by placing the info from the instructions under auto eth1 since that is my wireless card when I run iwconfig. I am also using ndiswrapper to install my Windows driver so I changed that too.:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid "XBOXWAP"
pre-up wpa_supplicant -Bw -Dndiswrapper -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

4. when I run 
```
sudo wpa_supplicant -Bw -Dndiswrapper -i eth1 -c/etc/wpa_supplicant.conf
```

... nothing happens. Here are the results when I run it with the -dd switch

> joe@UbuntuLaptop:~$ sudo wpa_supplicant -Dndiswrapper -i eth1 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=7):
     58 42 4f 58 57 41 50                              XBOXWAP         
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='XBOXWAP'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:90:4b:b3:d6:d0
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface eth1
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Cancelling scan request

Anyone? I'm a total noob, so I may need some rudimentary instruction.

As another note, I have wifi radar running and it is at least seeing my neighbor's networks so I think the driver is working on some level.

Also, my SSID is hidden, if that is complicating things (??)

And the driver does support WPA. At least in Windows it does.

---

### Post by ingo on 2007-04-02
Have you tried installing knetworkmanager? This is a superb KDE networking tool, which took care of all my wpa1+wpa2 worries in a jiffy. > sudo apt-get install knetworkmanagerwill do the trick...

---

### Post by thebluejay on 2007-04-12
MY GOD!!! No wonder so few people are using Linux!

This is ridiculous! I've been trying for days to get my wireless network running with WEP and it won't work. Runs fine with no encryption but no connection if I enable WEP. Someone referred me to this thread which is a real laugh. Imagine having to write all that code to get it going and to figure out that it's not working because you missed a space or put a coma in the wrong place. Guess I'll just run the unprotected connection and hope for the best - or maybe go back to Windows.  ;)

Yes, yes, I know, WEP doesn't afford much protection, but it's better than nothing, so....

---

### Post by Ferri on 2007-04-15
Just wanted to thank you for this. I really think it's worth the small effort.
Incidentally, theblueray, if you don't want to miss a space or a coma (and save time and efforts), you can use copy+paste (just like in Windows).

---

### Post by almightybunghole on 2007-04-17
I too am having problems. I've read the thread and it feels like I'm close, but no cigar so far! The WLAN nic is an Intel 3945 which seems to be seeing the AP when using the wext driver (first I tried ipw3945 which didn't work at all).

Here are the two scripts: 

/etc/network/interfaces

auto eth1
iface eth1 inet dhcp
wireless-essid my_ssid
pre-up wpa_supplicant -Bw -Dwext -i eth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

/etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="my_ssid"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=**HEX SSID PSK HERE**
}


I have tried altering the ap_scan parameter to no effect. Below is the output I'm getting:

wpa_supplicant:

gmason@gmason-laptop:~$ sudo wpa_supplicant -w -D wext -i eth1 -c/etc/wpa_supplicant.conf
Trying to associate with 00:12:17:c6:d6:21 (SSID='my_ssid' freq=0 MHz)
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:12:17:c6:d6:21
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
Authentication with 00:12:17:c6:d6:21 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:12:17:c6:d6:21 (SSID='my_ssid' freq=0 MHz)
Associated with 00:12:17:c6:d6:21
WPA: Key negotiation completed with 00:12:17:c6:d6:21 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:12:17:c6:d6:21 completed (auth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:12:17:c6:d6:21 (SSID='my_ssid' freq=0 MHz)
Associated with 00:12:17:c6:d6:21
WPA: Key negotiation completed with 00:12:17:c6:d6:21 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:12:17:c6:d6:21 completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:12:17:c6:d6:21 (SSID='my_ssid' freq=0 MHz)
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Associated with 00:12:17:c6:d6:21
WPA: Invalid EAPOL-Key MIC - dropping packet
WPA: Invalid EAPOL-Key MIC - dropping packet
Authentication with 00:12:17:c6:d6:21 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:12:17:c6:d6:21 (SSID='my_ssid' freq=0 MHz)
Associated with 00:12:17:c6:d6:21


iwevent:

gmason@gmason-laptop:~$ iwevent
Waiting for Wireless Events from interfaces...
22:47:41.808334   eth1     Set Mode:Managed
22:48:18.692070   eth1     Set Mode:Managed
22:48:18.825691   eth1     Set Mode:Managed
22:48:18.825989   eth1     New Access Point/Cell address:Not-Associated
22:48:18.829216   eth1     Set ESSID:"my_ssid"
22:48:21.954493   eth1     Set Mode:Managed
22:48:21.954526   eth1     Set ESSID:"my_ssid"
22:48:24.168036   eth1     New Access Point/Cell address:00:12:17:C6:D6:21
22:48:34.182031   eth1     New Access Point/Cell address:Not-Associated
22:48:37.219635   eth1     Set Mode:Managed
22:48:37.219666   eth1     Set ESSID:"my_ssid"
22:48:37.289930   eth1     Set Mode:Managed
22:48:37.289969   eth1     Set ESSID:"my_ssid"
22:48:39.569407   eth1     New Access Point/Cell address:00:12:17:C6:D6:21
22:48:49.577559   eth1     New Access Point/Cell address:Not-Associated
22:48:52.602852   eth1     Set Mode:Managed
22:48:52.602886   eth1     Set ESSID:"my_ssid"
22:48:52.682934   eth1     Set Mode:Managed

Any help you could offer would be very gratefully received - I'm a new Linux convert and could really do with some wireless networking so I can stop using XP!! :D 

Thanks.

---

### Post by aminesay on 2007-04-20
I use a wpa-SPK wifi connection in my university and i have the same problem . I had followed many tutorials and links on the internet but havn't found yet the solution for the problem of connexion / deconnexion and this damn :   [COLOR="DarkOrange"]access point/cell adress not associated[/COLOR]

---

### Post by aminesay on 2007-04-20
Just a minute  after the previous post , And i don't really know exactly how but the connexion on my laptop is working again ( im writing this post on it). 
So i ll post my /etc/networks/interface , and the last things i have done , perhaps that will help :
```


auto eth1
wireless-essid ecole2007
wpa-proto WPA 
wpa-driver wext
wpa-ssid ecole2007
wpa-psk 84a4541e8458fa5a2c55erhdaadgt9d93823ebc62ecba40da2d9b5201d930cea1 
wpa-key-mgmt WPA-PSK
wpa-pairwise TKIP 
wpa-group TKIP 
        
   # wpa-auth-alg shared
iface eth1 inet static
address 192.168.1.193
netmask 255.255.255.0
gateway 192.168.1.1

```

and then i typed in the terminal :  sudo ifup eth1

```
16:40:44.476515   eth1     Set ESSID:"ecole2007"
16:40:47.524171   eth1     New Access Point/Cell address:Not-Associated
16:40:57.481198   eth1     Set Mode:Managed
16:40:57.481336   eth1     Set ESSID:"ecole2007"
16:40:58.102992   eth1     New Access Point/Cell address:00:08:A1:92:CE:A8
16:41:09.369986   eth1     New Access Point/Cell address:Not-Associated
16:41:12.374007   eth1     Set Mode:Managed
16:41:12.374140   eth1     Set ESSID:"ecole2007"
16:41:15.354509   eth1     New Access Point/Cell address:Not-Associated
16:41:25.375204   eth1     Set Mode:Managed
16:41:25.375350   eth1     Set ESSID:"ecole2007"
16:41:25.752524   eth1     New Access Point/Cell address:00:08:A1:92:CE:A8
16:41:36.868107   eth1     New Access Point/Cell address:Not-Associated
16:41:39.871704   eth1     Set Mode:Managed
16:41:39.871836   eth1     Set ESSID:"ecole2007"
16:41:42.803981   eth1     New Access Point/Cell address:Not-Associated
16:41:52.872471   eth1     Set Mode:Managed
16:41:52.872604   eth1     Set ESSID:"ecole2007"
16:41:53.219041   eth1     New Access Point/Cell address:00:08:A1:92:CE:A8
16:42:04.378317   eth1     New Access Point/Cell address:Not-Associated
```

Wich was the same damn output meaning no permanent connexion .I finally typed in the terminal :



finally typed in the terminal  
```
$  iwlist  eth1 scan ;sleep 2
```

And then the iwevent stopped and the connexion was finnaly established , but i don't really know if the last command i typed resolved the problem or it is simply by chance .Im now effrayed that if i shutdown my pc i l not be enabled to get reconnected :(

---

### Post by discord on 2007-05-13
here is my first attempt at getting wpa_supplicant working. Everytime I try using network-manager my computer crashed so I'm trying to get wpa_supplicant working. If you scroll down to the end I think I'm most sucessful there. I tried most of the hints on the post about removing RSN and changing the ap number from 0 to 1 etc. Anybody know how i can get this to work?

colin@multiX:~$ sudo wpa_supplicant -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
Password:
Trying to associate with 00:0f:b3:48:f4:65 (SSID='blarghjr' freq=2427 MHz)
Authentication with 00:00:00:00:00:00 timed out.

here i tried specifying ndiswrapper
colin@multiX:~$ sudo wpa_supplicant -Dndiswrapper -i wlan0 -c/etc/wpa_supplicant.conf
Trying to associate with 00:0f:b3:48:f4:65 (SSID='blarghjr' freq=2427 MHz)
Association request to the driver failed

here I started changing some of the settings suggested from 0 to 1 etc.
colin@multiX:~$ sudo wpa_supplicant -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
bind(PF_UNIX): Address already in use
Trying to associate with 00:0f:b3:48:f4:65 (SSID='blarghjr' freq=2427 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:00:00:00:00:00 (SSID='blarghjr' freq=2427 MHz)
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
WPA: EAPOL-Key Replay Counter did not increase - dropping packet


finally i changed some more settings inside wpa_supplicant.conf and now it associates but has that key replay counter message 

colin@multiX:~$ sudo wpa_supplicant -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
Trying to associate with 00:0f:b3:48:f4:65 (SSID='blarghjr' freq=2427 MHz)
Associated with 00:0f:b3:48:f4:65
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Authentication with 00:0f:b3:48:f4:65 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:0f:b3:48:f4:65 (SSID='blarghjr' freq=2427 MHz)
Associated with 00:0f:b3:48:f4:65
WPA: EAPOL-Key Replay Counter did not increase - dropping packet

---

### Post by eCartman on 2007-05-23
This thread is great.  However, I am trying to setup a WPA2 connection using an internal Cisco WLAN + ACS connection.  It woks fine with WIN***, but I can't get connected with Linux.

I have a Cisco B/G card (using the Atheros chipset = 'madwifi' driver)

My wpa_supplicant.conf file contains:

ssid="ap1"
auth_alg=OPEN
key_mgmt=WPA-EAP
proto=WPA2
eap=PEAP
identity="[username]"
password="[password]"
phase2="auth=MSCHAPV2"
scan_ssid=1

I am not able to connect.  Anyone have any suggestions for using WPA2 with EAP/PEAP?  Basically, the problem is that i am not able to associate with the AP.  The AP is able to see my connection attempt for about 1 second, then shows no connections.

**********************************************

Answering my own question (for anyone else who might be interested).

Looks like the madwifi driver (and probably wext also) doesn't support WPA2.  Time to try ndiswrapper?

---

### Post by phillipchandler on 2007-07-11
I wouldn't even bother with Gnome-Network-Manager, it seems only to work for the few privileged . Ive spent 40 hrs plus and got nowhere. I ended up giving Wicd a try (ver 1.3.1), and HEY BINGO !!!! WPA Encryption works everytime. And for a newbie (GUI Girlie) like me, it was easy as hell.
The guy who wrote the software has made a great piece of kit, can (X)buntu get this into the repos as standard, Id even be happy to write a howto for it as well.

---

### Post by tlg on 2007-07-24
> **phillipchandler said:**
> I wouldn't even bother with Gnome-Network-Manager, it seems only to work for the few privileged . Ive spent 40 hrs plus and got nowhere. I ended up giving Wicd a try (ver 1.3.1), and HEY BINGO !!!! WPA Encryption works everytime. And for a newbie (GUI Girlie) like me, it was easy as hell.
The guy who wrote the software has made a great piece of kit, can (X)buntu get this into the repos as standard, Id even be happy to write a howto for it as well.

I would like to second that. Network Manager (Fiesty) does not detect my Intel 2915ABG wireless (Dell 630M laptop). I did get it working by setting up wpa supplicant and the etc/network/interfaces file, but it was coded only for my home network  so roaming was a challenge!

Wicd installed and ran in a couple of minutes and everything just works!!!

A great piece of work.

T

---

### Post by maztech on 2007-09-05
This howto is awesome!! :guitar:

Installed ubuntu fiesty on my thinkpad t41 two days ago in which everything worked sweet except for the wireless connection.

struggled for hours as I'm using WPA TKIP on my 3com router until stumbled on this. Followed all the tips/options until it worked. Only prob is I have to manually set the route(route add) for my eth1.

Below are the details. If anybody has a same prob with a t41 

wifi card;
PRO/Wireless LAN 2100 3B Mini PCI

eth1      IEEE 802.11b  ESSID:"arlevien"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:14:7C:BD:FD:A4   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:97   Missed beacon:0



me@T41:/etc/network$ cat interfaces
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1


iface eth1 inet static
address 192.168.1.52
netmask 255.255.255.0
gateway 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -i eth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

my wpa_supplicant.conf
T41:/etc$ cat wpa_supplicant.conf
ctrl_interface=/var/run/wpa_suplicant
ap_scan=1

network={
        ssid="mysid"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        #pairwise=CCMP TKIP
        #group=CCMP TKIP
        psk=*mypskkeyfromstep1*
}


thanks!

---

### Post by Matsurosuka on 2007-10-12
my WPA passkey has an exlamation point in it and its causing an error with the wpa_passphrase command, is there anyway around this?

---

### Post by Natr0n on 2007-10-12
Nice HOWTO! Worked perfectly for me on Xubuntu 7.04 with an Atheros AR5005G wireless adapter.

---

### Post by jag on 2007-10-17
Hi there,

I think I tried all the tips and none took me to success... Maybe I am stupid, but I cannot make my WLAN WPA PSK running with Ubuntu 7.04
With WinXP no problem, this shows the router is ok.

MAC filter is off.

Anyone has an idea about the wpa_supplicant output?

olk@jagjit:/usr/share/doc/wpasupplicant/examples$ sudo wpa_supplicant -i eth1 -D ipw -c /etc/wpa_supplicant/wpa_supplicant.conf -dd >~/wpaerr
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported

less ~/wpaerr
Initializing interface 'eth1' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N
/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=2
Line: 11 - start of a new network block
ssid - hexdump_ascii(len=11):
     57 4c 41 4e 2d 37 37 45 41 30 33                  WLAN-77EA03     
proto: 0x1
key_mgmt: 0x2
pairwise: 0x18
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='WLAN-77EA03'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0e:35:9b:87:4f
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'WLAN-77EA03'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
wpa_driver_ipw_set_auth_alg: auth_alg=0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 04 01 00 
00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_ipw_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=19
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 1024 bytes of scan results (4 BSSes)
Scan results: 4
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 1024 bytes of scan results (4 BSSes)
Scan results: 4
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 1024 bytes of scan results (4 BSSes)
Scan results: 4
------
olk@jagjit:/usr/share/doc/wpasupplicant/examples$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:00:F0:92:C9:2C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:9B:87:4F  
          inet6 addr: fe80::20e:35ff:fe9b:874f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2913 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x6000 Memory:d0200000-d0200fff 

eth0:avah Link encap:Ethernet  HWaddr 00:00:F0:92:C9:2C  
          inet addr:169.254.7.151  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0xc800 

eth1:avah Link encap:Ethernet  HWaddr 00:0E:35:9B:87:4F  
          inet addr:169.254.5.241  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0x6000 Memory:d0200000-d0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22713 (22.1 KiB)  TX bytes:22713 (22.1 KiB)

olk@jagjit:/usr/share/doc/wpasupplicant/examples$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"WLAN-77EA03"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

olk@jagjit:~$ uname -a
Linux jagjit 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

olk@jagjit:~$ wpa_supplicant -v
wpa_supplicant v0.5.5

Thanks a lot

---

### Post by jag on 2007-10-18
got the solution by spending some hours trying again everything... and finally the solution was not looking at the ubuntu pages, but at debian...
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

This was the best and easiest ubuntu-like solution ever... clear the cfg files and it works :-)

---

### Post by Kazol on 2007-11-21
If I want to disable and remove wpa supplicant what should I do (besides restoring /etc/network/interfaces and deleting /etc/wpa_supplicant.conf, /etc/wpa_supplicant.conf~)? 
Should I delete /etc/wpa_supplicant? I head that it's necessary to leave the dir in place because it's used by a different WPA app-I'm not sure what it is, but it's initialized by these lines in /etc/network/interfaces:
```

wpa-psk <PSK key>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid <SSID>

```

---

### Post by jon_mark022 on 2008-01-10
HI! Guys

Am struggling a lot to configure my Ubuntu 7.10's WIRED ethernet with wpa.
At work they enabled the IEEE802.1x authentication with PEAP and encryption of MSCHAPv2 with windows domain account.
Can you help me with this configuration.
Desprately seeking help :( 


Thanks
Nischal

---

### Post by ingo on 2008-01-14
Encrypt a wired lan? Think you may have gotten something mixed up here - encryption, asfaik, is for wlans only.

---

### Post by MountainX on 2008-02-21
Thanks luca_linux

This helped me with my issues ([http://ubuntuforums.org/showthread.php?p=4377964](http://ubuntuforums.org/showthread.php?p=4377964))

---

### Post by northox on 2008-05-21
ingo, yes we can and should encrypt wired connection. Take a look at [http://en.wikipedia.org/wiki/802.1x](http://en.wikipedia.org/wiki/802.1x) and alike.

jon_mark022, I known some people have this kind of setup working. Here's a link about the process for wlan, which should not be really different from a lan setup. You'll have to go step by step: ensure data layer connectivity up to authentication to the domain.

[http://ubuntuforums.org/showthread.php?t=278603](http://ubuntuforums.org/showthread.php?t=278603)

---

### Post by ingo on 2008-05-23
Cheers, northox - I never knew!

---

### Post by Tyconic on 2008-12-11
Is anyone still checking this thread? I'm in a situation where I need a command-line wireless utility to work and this seems like a really good option, expect its not quite working :-/

Here is my configuration file:

```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
   ssid="rogue"
   scan_ssid=1
   proto=WPA RSN
   key_mgmt=WPA-PSK
   pairwise=CCMP TKIP
   group=CCMP TKIP
   psk=07860305771c588e6dd629021d2de1c7637a5ea05c52440a19c7fb85cd51cd8a
}
```

And here is a dump of the wpa_supplicant debug info:

```
Initializing interface 'wlan0' conf '/home/anton/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/home/anton/etc/wpa_supplicant.conf' -> '/home/anton/etc/wpa_supplicant.conf'
Reading configuration file '/home/anton/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     72 6f 67 75 65                                    rogue           
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='rogue'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0e:2e:de:db:82
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     72 6f 67 75 65                                    rogue           
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 674 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:58:f4:37:d5 ssid='rogue' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1e:58:f4:37:d5 ssid='rogue'
Try to find non-WPA AP
Trying to associate with 00:1e:58:f4:37:d5 (SSID='rogue' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=13
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=189
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE2432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIEdd0c00037f020101070002a44000)'
Association info event
req_ies - hexdump(len=47): 00 05 72 6f 67 75 65 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=30): 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 0c 00 03 7f 02 01 01 07 00 02 a4 40 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1e:58:f4:37:d5
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1e:58:f4:37:d5
No keys have been configured - skip key clearing
Associated with 00:1e:58:f4:37:d5
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1e:58:f4:37:d5
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 e0 e7 26 41 c9 3c 5d d8 cb ae ba 40 73 56 5d 88 b7 2a 3a 05 78 7a f3 b8 17 27 33 73 c8 e0 91 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): e0 e7 26 41 c9 3c 5d d8 cb ae ba 40 73 56 5d 88 b7 2a 3a 05 78 7a f3 b8 17 27 33 73 c8 e0 91 2c
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 e0 e7 26 41 c9 3c 5d d8 cb ae ba 40 73 56 5d 88 b7 2a 3a 05 78 7a f3 b8 17 27 33 73 c8 e0 91 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1e:58:f4:37:d5 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 9c 54 25 4a 98 86 f9 5d c5 30 4f 64 af dc 8a 75 33 31 fd b8 b6 83 23 e4 52 6f cc ec 2a da 11 e8
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 9c 54 25 4a 98 86 f9 5d c5 30 4f 64 af dc 8a 75 33 31 fd b8 b6 83 23 e4 52 6f cc ec 2a da 11 e8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cd a5 27 90 9c fd 0d f7 c9 97 0e 70 f9 3b 33 9f 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1e:58:f4:37:d5
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 e0 e7 26 41 c9 3c 5d d8 cb ae ba 40 73 56 5d 88 b7 2a 3a 05 78 7a f3 b8 17 27 33 73 c8 e0 91 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6b a9 6c 62 10 ca f2 7b fb 30 00 4a 37 b0 02 55 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): e0 e7 26 41 c9 3c 5d d8 cb ae ba 40 73 56 5d 88 b7 2a 3a 05 78 7a f3 b8 17 27 33 73 c8 e0 91 2c
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 6b a9 6c 62 10 ca f2 7b fb 30 00 4a 37 b0 02 55
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 e0 e7 26 41 c9 3c 5d d8 cb ae ba 40 73 56 5d 88 b7 2a 3a 05 78 7a f3 b8 17 27 33 73 c8 e0 91 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6b a9 6c 62 10 ca f2 7b fb 30 00 4a 37 b0 02 55 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1e:58:f4:37:d5 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 72 11 88 4e 01 b6 1c 67 a6 92 a1 33 23 95 8e 3d 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:1e:58:f4:37:d5
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 5e 19 0a db 4d 62 f6 d6 23 c8 d0 ad c4 16 cd 90 96 72 ec 03 c3 b9 13 55 ee 47 f4 05 94 2e bb 59 91 84 a5 2e f7 dc 3b ec 47 ed d6 ee 2f 72 75 a9 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5d e3 53 00 c2 90 a1 e4 5b 66 2f 49 f8 34 e4 7a 00 20 35 81 2f 7a f8 16 ec e0 fd ad ee 10 7c 5b e6 e3 3b 44 4d 16 10 18 d6 f5 eb d6 c9 7b a5 57 70 d8
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 5e 19 0a db 4d 62 f6 d6 23 c8 d0 ad c4 16 cd 90 96 72 ec 03 c3 b9 13 55 ee 47 f4 05 94 2e bb 59
  key_iv - hexdump(len=16): 91 84 a5 2e f7 dc 3b ec 47 ed d6 ee 2f 72 75 a9
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 5d e3 53 00 c2 90 a1 e4 5b 66 2f 49 f8 34 e4 7a
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 5e 19 0a db 4d 62 f6 d6 23 c8 d0 ad c4 16 cd 90 96 72 ec 03 c3 b9 13 55 ee 47 f4 05 94 2e bb 59 91 84 a5 2e f7 dc 3b ec 47 ed d6 ee 2f 72 75 a9 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5d e3 53 00 c2 90 a1 e4 5b 66 2f 49 f8 34 e4 7a 00 20 35 81 2f 7a f8 16 ec e0 fd ad ee 10 7c 5b e6 e3 3b 44 4d 16 10 18 d6 f5 eb d6 c9 7b a5 57 70 d8
WPA: RX message 1 of Group Key Handshake from 00:1e:58:f4:37:d5 (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f6 fc 21 0a 60 83 cd bc 60 5f 1a 5e 62 fb 71 2c 00 00
WPA: Key negotiation completed with 00:1e:58:f4:37:d5 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1e:58:f4:37:d5 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
```

There is life, it seems like there's communication taking place between the computer and router, but still no internet.

Any help would be greatly appreciated!

Anton

---

### Post by Tyconic on 2008-12-12
Never mind, problem was fixed by restarting...

---

### Post by Found on 2009-03-11
Hello guys...i'm havin' a problem connecting to WPA2 router
Firs thanks for such an informative howto to the author!!

wpa_supplicant says this
```
march@march-desktop:~$ sudo wpa_supplicant -Dwext -i ra0 -c/etc/wpa_supplicant.conf
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:22:69:2a:d0:ee (SSID='BTHomeHub2-3ZF4' freq=2437 MHz)
Associated with 00:22:69:2a:d0:ee
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:22:69:2a:d0:ee
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```
I removed -Bw parametet because otherwise it's not working...

interfaces config:
```
auto ra0
iface ra0 inet dhcp
pre-up wpa_supplicant -Dwext -ra0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

and wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="BTHomeHub2-3ZF4"
       	scan_ssid=1
       	proto=WPA RSN
       	key_mgmt=WPA-PSK
       	pairwise=CCMP TKIP
       	group=CCMP TKIP
	psk="my psk hex key"
}
```

I tried everything but still getting the same error :( 
If anyone can give me a hand with this, i will really appreciate that!

---

### Post by kevdog on 2009-03-12
Please post your wpa_supplicant.conf file and use the -dd flag to generate more output -- and post this!

---

### Post by Found on 2009-03-12
Yeah, here is the wpa_supplicant.conf file
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="BTHomeHub2-3ZF4"
       	scan_ssid=1
       	proto=WPA RSN
       	key_mgmt=WPA-PSK
       	pairwise=CCMP TKIP
       	group=CCMP TKIP
	psk='my key and it's 100% correct'
}
```

And that's wpa_supplicant -bb...

```
Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=15):
     42 54 48 6f 6d 65 48 75 62 32 2d 33 5a 46 34      BTHomeHub2-3ZF4 
scan_ssid=1 (0x1)
proto: 0x3
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='BTHomeHub2-3ZF4'
Initializing interface (2) 'ra0'
Interface ra0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=14 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1f:1f:18:0a:7a
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface ra0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=15):
     42 54 48 6f 6d 65 48 75 62 32 2d 33 5a 46 34      BTHomeHub2-3ZF4 
Trying to get current scan results first without requesting a new scan to speed up initial association
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
Scan timeout - try to get results
Received 540 bytes of scan results (5 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:74:a9:b2:e9 ssid='SKY45800' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 00:22:69:2a:d0:ee ssid='BTHomeHub2-3ZF4' wpa_ie_len=28 rsn_ie_len=24 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:22:69:2a:d0:ee ssid='BTHomeHub2-3ZF4'
Try to find non-WPA AP
Trying to associate with 00:22:69:2a:d0:ee (SSID='BTHomeHub2-3ZF4' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=30): dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 0c 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8c07 len=55
AssocReq IE wireless event - hexdump(len=47): 00 0f 42 54 48 6f 6d 65 48 75 62 32 2d 33 5a 46 34 01 08 82 84 8b 96 24 30 48 6c 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:22:69:2a:d0:ee
Association info event
req_ies - hexdump(len=47): 00 0f 42 54 48 6f 6d 65 48 75 62 32 2d 33 5a 46 34 01 08 82 84 8b 96 24 30 48 6c 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: clearing own WPA/RSN IE
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:22:69:2a:d0:ee
No keys have been configured - skip key clearing
Associated with 00:22:69:2a:d0:ee
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
EAPOL: startWhen --> 0
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
Authentication with 00:22:69:2a:d0:ee timed out.
Added BSSID 00:22:69:2a:d0:ee into blacklist
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=15):
     42 54 48 6f 6d 65 48 75 62 32 2d 33 5a 46 34      BTHomeHub2-3ZF4 
Scan requested (ret=0) - scan timeout 5 seconds
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: SCANNING -> DISCONNECTED
```

Then it's repeating lots of times. Thank you ;)

Oh yeah...also, i can connect to my friends router with no problem by WPA1 protocol, but unfortunately with my router i have to use WPA2...
```
march@march-desktop:~$ sudo wpa_supplicant -Dwext -i ra0 -c/etc/wpa_supplicant.conf
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:1e:74:a9:b2:e9 (SSID='SKY45800' freq=2412 MHz)
Associated with 00:1e:74:a9:b2:e9
WPA: Key negotiation completed with 00:1e:74:a9:b2:e9 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1e:74:a9:b2:e9 completed (auth) [id=0 id_str=]

```

---

### Post by kevdog on 2009-03-12
Just wondering if you can do TKIP with WPA2 and drop the CCMP (RSA) portion from your wpa_supplicant part and set router to use TKIP.  Also seems that your ESSID is incorrect?

---

### Post by Found on 2009-03-12
> **kevdog said:**
> Just wondering if you can do TKIP with WPA2 and drop the CCMP (RSA) portion from your wpa_supplicant part and set router to use TKIP.  Also seems that your ESSID is incorrect?

thanks for the tips, i'll try tomorrow morning, and post the results ;)

---

### Post by Found on 2009-03-13
Thank you! I removed RSA from confing and it's working now :)

---

### Post by kevdog on 2009-03-13
You wouldn't happen to be using a Broadcom card would you?

---

### Post by flyingsolow on 2009-03-18
Hello. So I have tried a number of things to get WPA encryption to work, but I'm at a loss and can't decipher the debug info for what is really going wrong. This thread and its previous suggestions have been great and if I can't get this working, I'm probably going to give wicd a try.

wpa_supplicant says:
```
rusty@rusty-ubuntu:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=13):
     44 41 56 45 53 20 4e 45 54 57 4f 52 4b            DAVES NETWORK   
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='DAVES NETWORK'
Initializing interface (2) 'wlan0'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xd
  capabilities: key_mgmt 0x5 enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:41:a6:56:dc
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=13):
     44 41 56 45 53 20 4e 45 54 57 4f 52 4b            DAVES NETWORK   
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 460 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:16:b6:60:9e:e8 ssid='DAVES NETWORK' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:16:b6:60:9e:e8 ssid='DAVES NETWORK'
Try to find non-WPA AP
Trying to associate with 00:16:b6:60:9e:e8 (SSID='DAVES NETWORK' freq=2447 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c07 len=59
AssocReq IE wireless event - hexdump(len=51): 00 0d 44 41 56 45 53 20 4e 45 54 57 4f 52 4b 01 04 02 04 0b 16 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 5a 11 0f 50 cb 4c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:16:b6:60:9e:e8
Association info event
req_ies - hexdump(len=51): 00 0d 44 41 56 45 53 20 4e 45 54 57 4f 52 4b 01 04 02 04 0b 16 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 5a 11 0f 50 cb 4c
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:16:b6:60:9e:e8 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
...Rinse and Repeat...
```

interfaces config:
```
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
wireless-essid 'DAVES NETWORK'
pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

and wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="DAVES NETWORK"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
	psk=myhexkey
}
```

I've tried static/dhcp, including the RSN/CCMP lines, ap_scan values 0/1/2, and emptying the values and allowing Network-Manager to do the work. Unencrypted works. Would be willing to WEP, but the consensus is Linksys WMP11v4 doesn't support it. I know WPA works with WMP11v4 as I've tried following [these instructions]("http://ubuntuforums.org/showthread.php?t=7319&highlight=WMP11v4&page=2").

I hope someone can give me some input, I'm willing to try anything. Thank you.

---

### Post by JF1980 on 2009-03-20
I've gotten most of this working.  One strange thing is that wpa_supplicant will not allow me to use ndiswrapper as the driver, only wext, which is strange as my WG111T driver is installed using ndiswrapper.

If I reboot, it hangs at 'Configuring network interfaces".  I can remove the WG111T, reboot and then re-insert the WG111T and manually bring the interface up with a '/etc/init.d/networking restart'.

Could it be that ndiswrapper is not starting before the networking comes up?

---

### Post by kevdog on 2009-03-23
wpa_supplicant newer releases from package or repository are only compiled with limited options such as using wext.  This is not a drawback, but an advantage, since it simplifies setup.  Everything should work with just specifying wext.  If you need to specifically have the ndiswrapper option (which I can't think off the top of my head any reason you should need this), you need to compile from source.

---

### Post by kevdog on 2009-03-23
flyingsolow

The space in your essid name may be what is causing problems.

---

### Post by flyingsolow on 2009-03-23
> **kevdog said:**
> flyingsolow

The space in your essid name may be what is causing problems.

Thanks for your help kevdog. I guess that's something I should've anticipated. Turns out that solves that initial problem. I've switched the ESSID to davesnetwork now.

I've been working on getting it working now, however, I've quickly hit another road block. I get an error that specifies the "pre-shared key may be incorrect" and I will admit, that's a very specific sounding error. However, I've attempted to use the wpa_passphrase and just the ASCII PSK and they both come up with the same result. My router is set to use WPA Personal, TKIP, and the PSK = mypresharedkey. I've attached the output I get and my wpa_supplicant.conf. Hopefully someone has some some ideas on possible things to solve the pre-shared key issue. Thanks.

```
rusty@rusty-ubuntu:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=12):
     64 61 76 65 73 6e 65 74 77 6f 72 6b               davesnetwork    
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='davesnetwork'
Initializing interface (2) 'wlan0'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
ioctl[SIOCSIWPMKSA]: Invalid argument
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xd
  capabilities: key_mgmt 0x5 enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0c:41:a6:56:dc
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
ioctl[SIOCSIWPMKSA]: Invalid argument
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=12):
     64 61 76 65 73 6e 65 74 77 6f 72 6b               davesnetwork    
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 459 bytes of scan results (2 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:16:b6:60:9e:e8 ssid='davesnetwork' wpa_ie_len=22 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:16:b6:60:9e:e8 ssid='davesnetwork'
Try to find non-WPA AP
Trying to associate with 00:16:b6:60:9e:e8 (SSID='davesnetwork' freq=2447 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
ioctl[SIOCSIWESSID]: Invalid argument
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c07 len=58
AssocReq IE wireless event - hexdump(len=50): 00 0c 64 61 76 65 73 6e 65 74 77 6f 72 6b 01 04 02 04 0b 16 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 81 42 3f 3f 78 a7
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:16:b6:60:9e:e8
Association info event
req_ies - hexdump(len=50): 00 0c 64 61 76 65 73 6e 65 74 77 6f 72 6b 01 04 02 04 0b 16 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 81 42 3f 3f 78 a7
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:16:b6:60:9e:e8
No keys have been configured - skip key clearing
Associated with 00:16:b6:60:9e:e8
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:16:b6:60:9e:e8
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 57 ee f4 89 00 00 00 01
  key_nonce - hexdump(len=32): c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:16:b6:60:9e:e8 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): ae 4e bc 51 58 47 7d 7d 05 70 1e 7f ff 58 60 3e 08 f0 0a d2 a5 20 ef 41 5e 4b ef 58 9c 58 d0 2c
WPA: PTK derivation - A1=00:0c:41:a6:56:dc A2=00:16:b6:60:9e:e8
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 57 ee f4 89 00 00 00 01 ae 4e bc 51 58 47 7d 7d 05 70 1e 7f ff 58 60 3e 08 f0 0a d2 a5 20 ef 41 5e 4b ef 58 9c 58 d0 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 aa 98 29 4c da 59 ba 86 69 0f aa 97 5c a7 b1 94 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:16:b6:60:9e:e8
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 57 ee f4 89 00 00 00 01
  key_nonce - hexdump(len=32): c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:16:b6:60:9e:e8 (ver=1)
WPA: PTK derivation - A1=00:0c:41:a6:56:dc A2=00:16:b6:60:9e:e8
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 57 ee f4 89 00 00 00 01 ae 4e bc 51 58 47 7d 7d 05 70 1e 7f ff 58 60 3e 08 f0 0a d2 a5 20 ef 41 5e 4b ef 58 9c 58 d0 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 aa 98 29 4c da 59 ba 86 69 0f aa 97 5c a7 b1 94 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:16:b6:60:9e:e8
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 57 ee f4 89 00 00 00 01
  key_nonce - hexdump(len=32): c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:16:b6:60:9e:e8 (ver=1)
WPA: PTK derivation - A1=00:0c:41:a6:56:dc A2=00:16:b6:60:9e:e8
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 57 ee f4 89 00 00 00 01 ae 4e bc 51 58 47 7d 7d 05 70 1e 7f ff 58 60 3e 08 f0 0a d2 a5 20 ef 41 5e 4b ef 58 9c 58 d0 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 aa 98 29 4c da 59 ba 86 69 0f aa 97 5c a7 b1 94 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: startWhen --> 0
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RX EAPOL from 00:16:b6:60:9e:e8
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 57 ee f4 89 00 00 00 01
  key_nonce - hexdump(len=32): c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:16:b6:60:9e:e8 (ver=1)
WPA: PTK derivation - A1=00:0c:41:a6:56:dc A2=00:16:b6:60:9e:e8
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 57 ee f4 89 00 00 00 01 ae 4e bc 51 58 47 7d 7d 05 70 1e 7f ff 58 60 3e 08 f0 0a d2 a5 20 ef 41 5e 4b ef 58 9c 58 d0 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 aa 98 29 4c da 59 ba 86 69 0f aa 97 5c a7 b1 94 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:16:b6:60:9e:e8
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 57 ee f4 89 00 00 00 01
  key_nonce - hexdump(len=32): c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 57 ee f4 89 00 00 00 01 c5 c4 21 d7 b6 69 3c cd 39 09 9d a8 12 44 d1 c0 2c f3 bc 49 93 c2 59 dd 2c db 26 57 f7 4c 32 29 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:16:b6:60:9e:e8 (ver=1)
WPA: PTK derivation - A1=00:0c:41:a6:56:dc A2=00:16:b6:60:9e:e8
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 57 ee f4 89 00 00 00 01 ae 4e bc 51 58 47 7d 7d 05 70 1e 7f ff 58 60 3e 08 f0 0a d2 a5 20 ef 41 5e 4b ef 58 9c 58 d0 2c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 aa 98 29 4c da 59 ba 86 69 0f aa 97 5c a7 b1 94 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Setting scan request: 0 sec 100000 usec
Added BSSID 00:16:b6:60:9e:e8 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds

```

```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="davesnetwork"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
	#psk="mypresharedkey"
	psk=6bec7c28fd56128f96b54acb0241d5eb850aea35a0751b5b1538b51587bdaf14
}
```

---

### Post by Nathan.Flow on 2009-08-10
I'm having a problem with what once was a working wpa_supplicant.conf file.

the out put of 
```
sudo sudo wpa_supplicant -D wext -i eth1 -c /ect/wpa_supplicant/wpa_supplicant.conf -dd
```

gives me
```

Initializing interface 'eth1' conf '/ect/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/ect/wpa_supplicant/wpa_supplicant.conf' -> '/ect/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/ect/wpa_supplicant/wpa_supplicant.conf'
Failed to read or parse configuration '/ect/wpa_supplicant/wpa_supplicant.conf'.
Failed to add interface eth1
Cancelling scan request
Cancelling authentication timeout
```

I belive that my problem lies some where in the ctrl interface 'N/A' bridge 'N/A'

Did I break something? and where?


here's my snip of my wpa_supplicant.conf file
```

#PEAP with MSCHAPv2
#for use with RADIUS servers that use old peaplabel
#(e.g., Funk Odyssey and SBR, Meetinghouse Aegis, Interlink RAD-Series)


ctrl_interface=/var/run/wpa_supplicant
#eapol_version=1
#ap_scan=1
#fast_reauth=1

network={
    ssid="UCM-WiFi-Secured"
    key_mgmt=IEEE8021X
    eap=PEAP
    identity="*******"
    password="*******"
    ca_cert="path to.cer"
    phase2="auth=MSCHAPV2"
}

```

Thanks in advance.

---

### Post by sideburnie on 2009-10-27
All I'm getting is 

CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS

using backtrack 4 with an RTL8187 series card.... 

did a networking restart... card is in managed mode.... don't know what to do....  :frown:

---

### Post by sideburnie on 2009-10-27
hooooolyyyy crap that took a long time.....  that whole -dd thing is really helpful at least.....  airport extreme's are so useless....

---

### Post by kevdog on 2009-10-27
Your syntax is wrong:

sudo sudo wpa_supplicant -D wext -i eth1 -c /ect/wpa_supplicant/wpa_supplicant.conf -dd

Its /etc/wpa_supplicant......

Note the spelling problem.

---

### Post by axe87 on 2009-11-15
Since upgrading to Ubuntu 8.10 I have had successive problems with WiFi. Having upgraded to 9.10 I can run wpa_supplicant and dhclient manually and get connectivity. Trying to do this automatically (as per the original post) prints the wpa_supplicant help message.

Also, when I get a connection, dns doesn't seem to work, or at least not via firefox.

Sure I must be missing something obvious.

I have an Atheros AR5001X+ D-Link card.

---

### Post by kevdog on 2009-11-15
I love doing it manually as well, but is there some reason you have to do this manually?  Network Manager or WICD isn't sufficient?

---

### Post by Cammy on 2009-11-16
Ok, I need to pick someone's brain.

I have an old Dell Inspiron 5100 that I just picked up a Broadcom internal wireless card for (BCM4309).  I installed the B43legacy driver for it, and managed to get it connected using NetworkManager.  Only one problem.  It connects at 80-90% signal strength, but the speed is slow to none (i.e. it only actually resolves websites on rare occasion).

So I disabled NetworkManager, and tried the steps in this tutorial.  Same thing.  It *sometimes* connects, and when it does, the speed is dead slow.

Any ideas as to what might be causing this?

---

### Post by axe87 on 2009-11-16
> I love doing it manually as well, but is there some reason you have to do this manually? Network Manager or WICD isn't sufficient?

Hmm, Network Manager fails to connect. It spends ages trying and then eventually 'fails' showing the form to enter the passcode. I had tried wicd but as 9.10 reinstalled Network Manager hadn't tried again. Thought I'd get it working manually first.

---

### Post by Kiru0293 on 2010-01-01
When I open interfaces to place those two lines in, it has nothing with in it. I'm a noob so I don't know if that's a problem or not.

---

### Post by 2hot6ft2 on 2010-03-02
It's been roughly 4.5 years since this how to was created and for those that wonder if it still works the answer is YES.
I disabled network manager under System > Preferences > Startup Applications
and am now connected without it using 9.10.

Actually I'm using Ubuntu Ultimate Edition 2.5, which is based on 9.10, so if you don't have Startup Applications you can install it with
```
sudo apt-get install gnome-session-properties
```
For those using AES encryption instead of TKIP just change them around in the instructions when doing it.

EDIT: I also removed these 2 lines, otherwise I would get an error.
>         pairwise=CCMP AES
        group=CCMP AES


Thanks to the OP for the how to, to Chili555 for pointing me to it, and to others that have added to it over the years.

---

### Post by cmommsen on 2010-03-07
This is by far one of the most helpful howto's in this entire forum.  I keep coming back every few months when I have to re-install my system cause I play around with it too much.. :D

Works every time!

---

### Post by pnguine on 2010-04-08
I only read the first three pages of posts but it still helped me a lot. I just tried FreeBSD and had to configure wireless 'manually' with wpa_supplicant because of the Atheros based PCMCIA card. It was basically the same thing. Here's what my .conf file looks like if it will help anyone:

```
ctrl_interface=/var/run/wpa_supplicant
network={
  ssid="my_access_point_name"
  proto=WPA
  key_mgmt=NONE
  wep_key0=<10 digits in here - no quotes>
  wep_tx_keyidx=0
}
```
So there is a _lot_ of possibilities in that file.

Thanks for the help.

Oh yeh - this was in Xubuntu FWIW

---

### Post by _cvt_ on 2010-08-23
Hi,

I'm trying to connect to a AP by command line but I can't yet. Using the network manager it's possible but I need the command lines to use in my code programming.

Here it's what I tryed:
```
sudo iwconfig wlan0 mode managed channel 6 key restricted s:'12345' essid 'cassiano-PC_AP'

```

and the tail: sudo tail -f /var/log/syslog
```

05:55 cassiano-linux kernel: [13476.935795] wlan0: direct probe to AP 00:15:af:84:29:d3 (try 1)
Aug 13 14:05:55 cassiano-linux kernel: [13476.935943] wlan0: deauthenticating from 00:15:af:84:29:d3 by local choice (reason=3)
Aug 13 14:05:55 cassiano-linux kernel: [13476.936002] wlan0: direct probe to AP 00:15:af:84:29:d3 (try 1)
Aug 13 14:05:55 cassiano-linux kernel: [13476.939620] wlan0: direct probe responded
Aug 13 14:05:55 cassiano-linux kernel: [13476.939628] wlan0: authenticate with AP 00:15:af:84:29:d3 (try 1)
Aug 13 14:05:55 cassiano-linux kernel: [13476.942595] wlan0: authenticated
Aug 13 14:05:55 cassiano-linux kernel: [13476.942631] wlan0: associate with AP 00:15:af:84:29:d3 (try 1)
Aug 13 14:05:55 cassiano-linux wpa_supplicant[828]: No network configuration found for the current AP
Aug 13 14:05:55 cassiano-linux kernel: [13476.944736] wlan0: RX AssocResp from 00:15:af:84:29:d3 (capab=0x431 status=0 aid=20)
Aug 13 14:05:55 cassiano-linux kernel: [13476.944742] wlan0: associated
Aug 13 14:05:55 cassiano-linux kernel: [13476.965044] wlan0: deauthenticating from 00:15:af:84:29:d3 by local choice (reason=3)
Aug 13 14:05:55 cassiano-linux wpa_supplicant[828]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

I think that the error is:
```

Aug 13 14:05:55 cassiano-linux wpa_supplicant[828]: No network configuration found for the current AP

```

And when I connect with the network manager appears this on the tail:
```

NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto cassiano-PC_AP' has security, and secrets exist.  No new secrets needed.
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'ssid' value 'cassiano-PC_AP'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'

```

and this:
```

Aug 13 14:31:32 cassiano-linux wpa_supplicant[828]: Associated with 00:15:af:84:29:d3

```

My /etc/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="cassiano-PC_AP"
        scan_ssid=1
        key_mgmt=NONE
        auth_alg=OPEN
        wep_key0="12345"
        wep_tx_keyidx=1
}

```

And when I run this:

sudo wpa_supplicant -dd -iwlan0 -c/etc/wpa_supplicant.conf

```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 10 - start of a new network block
ssid - hexdump_ascii(len=14):
     63 61 73 73 69 61 6e 6f 2d 50 43 5f 41 50         cassiano-PC_AP 
scan_ssid=1 (0x1)
key_mgmt: 0x4
auth_alg: 0x1
wep_key0 - hexdump(len=5): [REMOVED]
wep_tx_keyidx=1 (0x1)
Priority group 0
   id=0 ssid='cassiano-PC_AP'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:19:d2:22:99:4f
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): a5 33 8d 4b 44 f7 5d bd ac b3 f9 23 07 2b 46 f4
WPS: Build Beacon and Probe Response IEs
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Response Type (2)
WPS:  * UUID-E
WPS:  * Manufacturer
WPS:  * Model Name
WPS:  * Model Number
WPS:  * Serial Number
WPS:  * Primary Device Type
WPS:  * Device Name
WPS:  * Config Methods (0)
WPS:  * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=14):
     63 61 73 73 69 61 6e 6f 2d 50 43 5f 41 50         cassiano-PC_AP 
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 1123 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Trying to associate with 00:15:af:84:29:d3 (SSID='cassiano-PC_AP' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
Overriding auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=0 seq_len=0 key_len=5
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1123 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Already associated with the selected AP.
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:15:af:84:29:d3
Association info event
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:15:af:84:29:d3 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1121 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Trying to associate with 00:15:af:84:29:d3 (SSID='cassiano-PC_AP' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
Overriding auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=0 seq_len=0 key_len=5
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1121 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Already associated with the selected AP.
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:15:af:84:29:d3
Association info event
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:15:af:84:29:d3
Associated with 00:15:af:84:29:d3
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
Removed BSSID 00:15:af:84:29:d3 from blacklist
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:15:af:84:29:d3 completed (reauth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:15:af:84:29:d3 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1121 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Trying to associate with 00:15:af:84:29:d3 (SSID='cassiano-PC_AP' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
Overriding auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=0 seq_len=0 key_len=5
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1121 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Already associated with the selected AP.
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:15:af:84:29:d3
Association info event
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:15:af:84:29:d3
Associated with 00:15:af:84:29:d3
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
Removed BSSID 00:15:af:84:29:d3 from blacklist
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:15:af:84:29:d3 completed (reauth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:15:af:84:29:d3 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1121 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Trying to associate with 00:15:af:84:29:d3 (SSID='cassiano-PC_AP' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
Overriding auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=0 seq_len=0 key_len=5
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1121 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Already associated with the selected AP.
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:15:af:84:29:d3
Association info event
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
^CAssociated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (reauth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
CTRL-EVENT-TERMINATING - signal 2 received
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
BSSID 00:15:af:84:29:d3 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 1121 bytes of scan results (3 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:15:af:84:29:d3 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0f:3d:af:85:76 ssid='LabPlan' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: c4:7d:4f:38:ea:f0 ssid='redeUFSCSemFio2X' wpa_ie_len=24 rsn_ie_len=20 caps=0x11
   skip - SSID mismatch
1: 00:15:af:84:29:d3 ssid='cassiano-PC_AP' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:15:af:84:29:d3 ssid='cassiano-PC_AP'
Trying to associate with 00:15:af:84:29:d3 (SSID='cassiano-PC_AP' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
Overriding auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=0 seq_len=0 key_len=5
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Removing interface wlan0
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

```

---

### Post by mcasperson on 2010-08-26
The easiest way to configure wpa_supplicant is to connect to a wireless network using NetworkManager and then copy the config settings out of the daemon logs. This post [here]("http://www.brighthub.com/hubfolio/matthew-casperson/articles/84351.aspx") shows you how.

---

### Post by PatchesTheCaveman on 2011-01-04
Hi t_anjan.  Happy New Year!

For *iwconfig* to return useful output, you must run it as superuser:
```
sudo iwconfig
```

Unfortunately, I have no experience with *ndiswrapper* so I can't help you with that.

However, there is a native Linux driver for your wireless adapter I'd be glad to help you get working if you're interested.

---

### Post by kedarkekan on 2011-01-05
@_cvt_

I am facing the same issue.

Surprisingly I am able to connect using network manager 

Successful connection using Network Manager (ubuntu 10.10 native)


Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) starting connection 'Auto safari'
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> (wlan0): bringing up device.
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0/wireless): access point 'Auto safari' has security, but secrets are required.
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0/wireless): connection 'Auto safari' has security, and secrets exist.  No new secrets needed.
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Config: added 'ssid' value 'safari'
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Config: added 'scan_ssid' value '1'
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Config: added 'psk' value '<omitted>'
Jan  5 15:14:21 Latitude NetworkManager[1005]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  5 15:14:21 Latitude NetworkManager[1005]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> Config: set interface ap_scan to 1
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> (wlan0): supplicant connection state:  inactive -> disconnected
Jan  5 15:14:21 Latitude NetworkManager[1005]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan  5 15:14:23 Latitude wpa_supplicant[1130]: Trying to associate with 00:15:c7:fe:e0:60 (SSID='safari' freq=2437 MHz)
Jan  5 15:14:23 Latitude NetworkManager[1005]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan  5 15:14:23 Latitude wpa_supplicant[1130]: Associated with 00:15:c7:fe:e0:60
Jan  5 15:14:23 Latitude NetworkManager[1005]: <info> (wlan0): supplicant connection state:  associating -> associated
Jan  5 15:14:23 Latitude NetworkManager[1005]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan  5 15:14:23 Latitude NetworkManager[1005]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jan  5 15:14:23 Latitude wpa_supplicant[1130]: WPA: Key negotiation completed with 00:15:c7:fe:e0:60 [PTK=TKIP GTK=TKIP]
Jan  5 15:14:23 Latitude wpa_supplicant[1130]: CTRL-EVENT-CONNECTED - Connection to 00:15:c7:fe:e0:60 completed (reauth) [id=0 id_str=]
Jan  5 15:14:23 Latitude NetworkManager[1005]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jan  5 15:14:23 Latitude NetworkManager[1005]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'safari'.


[B]

When I try doing so using terminal command line, getting to below issue :[/B]
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:15:c7:fe:e0:60
Association info event
resp_ies - hexdump(len=42): 01 08 82 84 8b 0c 12 96 18 24 32 04 30 48 60 6c dd 18 00 50 f2 02 01 01 81 00 03 a4 00 00 27 a4 00 00 42 43 bc 00 62 32 66 00
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED



ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="safari"
           scan_ssid=1
           key_mgmt=WPA-PSK
           pairwise=TKIP
           group=TKIP
    psk="key is mine"


All, Any help would appreciated !

---

### Post by gewone on 2012-02-06
I have an ancient(!) laptop that is running Ubuntu Desktop. However, I mainly (99.5%) use it as a server with console connections. Truth is, neither GNOME nor KDE runs very smoothly on P3/1.2GHz with 512MiB of SDRAM. In fact, the only reason I got the *'gdm'* running at all is because I've never had time to learn the routines for "manually" connecting to a router with WPA2 security (after all, the *'nm-applet'* is really smooth). But today I just had it. Lately, X has been eating up my RAM (and swap), and it's just not efficient. I looked in */etc/* but I had no *'wpa_supplicant.conf'* file there, but(!) a directory called 'wpa_supplicant/' that contained three files (*action_wpa.sh*, *functions.sh*, *ifupdown.sh*). I looked at those but they were very confusing and I really don't seem needy to care for those.

**As it turned out, the only thing I needed to do to successfully connect was the following:**

[I]```
sudo -i
wpa_passphrase NAMEOFMYSSID myactualwpapassphrase > /etc/wpa_supplicant.conf
wpa_supplicant -B -ieth1 -c/etc/wpa_supplicant.conf
dhclient eth1
```[/I]**Done!**

I am now online with my machine. Of course, I will probably get issues when I eventually decide to reboot it. Oh, wait. In fact, as I'm running Ubuntu Desktop it will launch GDM and automatically connect with the nm-applet then anyways, so it's cool. However...
> gewone@LOSANGELES:~$ uptime
 22:47:53 up 163 days, 14:17,  6 users,  load average: 0.00, 0.00, 0.03

As you may realize, I have no plans on rebooting my laptop anytime soon. But when I do, I guess those few lines in *'/etc/network/interfaces'* will do the trick; sort of like an *'AUTOEXEC.BAT'* executing (more or less) the commands I ran just now. Awesome.

Again, big thanks for this thread!

---

### Post by spiderDuck on 2013-09-01
Hi. I'm new with these stuff so I hope I'm not being very stupid here. My problem is that in step 6, where you have to add the two lines, my 
"sudo gedit /etc/network/interfaces" doesn't look like the example "iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
wireless-essid my_essid
gateway 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant" 

but it looks like this: 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#NetworkManager#auto eth0
#NetworkManager#iface eth0 inet dhcp


Does anybody know what am I to do? Also, when my laptop starts I get this message "the disk drive for /dev/mapper/crypyswap1 is not ready yet or not present. 
Any help is very appreciated. Thank you

---

### Post by MintyFreshLinux on 2014-04-23
Can't connect to my wireless network
 
I followed these tutorials
Configure the rtl8190 with ndiswrapper:
[http://ubuntuforums.org/showthread.php?t=1433401](http://ubuntuforums.org/showthread.php?t=1433401)
Configure wpa_supplicant:
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)
 
 
 
Here is my /etc/network/interfaces file:
 
```
auto lo
iface lo inet dhcp (I changed this value from loopback to dhcp)
pre-up wpa_supplicant -Bw -Dwext -wlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```
 
And here's my wpa_supplicant.conf file:
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2
 
network={
        ssid="2WIRE201"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=2efdade6c94ad65fda3e453879cf0a81a8cd09ec3fe1886154c0ba0c35478d13
}
 
```

My router is configured to accept wpa-tkip and wpa2-aes so why am I getting this message when I type this:
 
```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
 
 
 
Successfully initialized wpa_supplicant
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: Trying to associate with 60:c3:97:b4:73:f9 (SSID='2WIRE201' freq=2452 MHz)
wlan0: Associated with 60:c3:97:b4:73:f9
wlan0: CTRL-EVENT-DISCONNECTED bssid=60:c3:97:b4:73:f9 reason=0
wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="2WIRE201" auth_failures=1 duration=10
```

---

### Post by MintyFreshLinux on 2014-04-23
Sorry didn't mean to post twice I was tring to edit my original post, don't know how that happened

---

