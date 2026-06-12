---
title: "Installing Broadcom b43 Drivers on Ubuntu Server"
date: 2012-04-10
forum: Server Platforms
---

### Post by the pwner224 on 2012-04-10
Hello,

I have a HP Mini 210-1041nr netbook onto which I recently loaded Ubuntu Server (11.10). Before this, I used normal Ubuntu, and I knew I needed proprietary drivers. I tried installing them with the instructions on [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)
I have no internet access on the computer. My internet comes from a Clear 4G hotspot. When I connect it to the laptop with a USB cable, it does not connect to the internet. ifconfig -a will show usb0, but it will not work, even if I turn on usb0. There is no Ethernet on the modem. With normal Ubuntu, the computer automatically set up a wired connection with it when I connected the USB.
I have followed the instruction on the website under "Installing b43 Drivers", in the second section ("b43 - No Internet Access"). I have completed steps 1-3. I cannot complete step 4 because there is no GUI. I Googled about this and found out that I could do this with the program jockey-text. However, I found out that jockey-text is installed under jockey-common. On my other computer, I did
apt-get download jockey-common
and I transferred the file onto the netbook. When I did
sudo dpkg -i <name of downloaded file>*
it said there were unresolved dependencies (python-xkit and policykit-1). These applicatons have more dependencies, and they have more dependencies. Since on the netbook I cannot apt-get jockey-common, which will also install all of the dependencies, because I do not have internet on the netbook.
Is there any way I can install jockey-text or get the Clear modem working over USB?

Thanks for any help. :)

---

### Post by the pwner224 on 2012-04-10
Also, my WiFi card is the BCM4312.

---

### Post by snowpine on 2012-04-10
A non-GUI alternative to Step 4 of your tutorial is:

```
sudo modprobe b43
```

---

### Post by the pwner224 on 2012-04-11
Thanks for the reply. I will try this when possible.

---

### Post by the pwner224 on 2012-04-11
It worked!

How would I connect to the WiFi?

I set up the /etc/network/interfaces and made the line for the ip address
address 192.168.1.15
Before installing Ubuntu server, I changed my router's setting to give my WiFi card's MAC address an ip of 192.168.1.15, which is what I put in /etc/network/interfaces. Now, on my router's settings page, it shows that my laptop is connected, but its ip is 0.0.0.0.
A screenshot of the settings page is attached. How can I fix this?

Thanks for the help.

---

### Post by the pwner224 on 2012-04-11
I just commented out the address, netmask, and gateway lines in /etc/network/interfaces. I ran sudo dhclient, and restarted wlan0. Now, my router says my laptop has an ip of 192.168.1.15, which is what I want. However, if I run ifconfig, it says my ip address is 192.168.1.19, which is what I set when I installed Ubuntu server. In /etc... the only lines about wlan0 that are not commented out are

auto wlan0
iface wlan0 inet static
network 192.168.1.1
broadcast 192.168.1.255
wpa-essid Clear_1244_A
wpa-psk <my password>

I tried changing the static in the iface line to both DHCP and then dhcp. After each change, I restarted wlan0 and ran dhclient, but ifconfig still showed the address as 192.168.1.19. The router always showed that the laptop had an ip of 192.168.1.15 (picture is attached), but when I pinged 192.168.1.1, it failed all times.

What should I do?

EDIT: Just to remove any doubts, the static IP of 192.168.1.14 is the laptop I am typing on right now. The server is .15.

---

### Post by the pwner224 on 2012-04-11
I changed the router to give my server a static ip of 192.168.1.19. 

The /etc file is set to

auto wlan0
iface wlan0 inet dhcp
network 192.168.1.1
broadcast 192.168.1.255
wpa-essid Clear_1244_A
wpa-psk (my password)

I restarted /etc/init.d/networking, ran sudo dhclient, and ifconfig shows that everything is correct. The inet address is 192.168.1.19. However, I still can not ping my router or the internet. My router shows that it is connected at 192.168.1.19.

What am I doing wrong?

---

### Post by the pwner224 on 2012-04-11
The output of iwconfig is:

[FONT="Courier New"]wlan0   IEEE 802.11bg  ESSID:"Clear_1244_A"
        Mode:Managed  Frequency:2.417 GHz  Access Point: 00:30:0D:6B:D2:C3
        Bit Rate=1 Mb/s   Tx-Power=20 dBm
        Retry  long limit:7   RTS thr:off   Fragment thr:off
        Power Management:off
        Link Quality=68/70  Signal level=-42 dBm
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:9  Missed beacon:0[/FONT]

Is there anything wrong?

---

