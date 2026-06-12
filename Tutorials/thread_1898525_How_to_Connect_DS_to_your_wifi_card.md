---
title: "How to: Connect DS to your wifi card"
date: 2011-12-21
forum: Tutorials
---

### Post by darkdragn on 2011-12-21
This is going to be step by step procedures for configuring a machine with a wired connection and a wifi card so that a Nintendo DS can connect up and access updates, Nintendo store, or game specific servers.
I know some people may look at that as though it's useless, however I'm in the Navy, and currently stationed in Japan. Every wifi connection available requires some form of proxy authentication (Ex click proceed/accept terms and agreements) Without a web browser my 3DS was a little crippled, and it was getting embarrassing to spend time in McDonalds using the Nintendo connection available there, however cyber cafe's offer wired connections for personal laptops, and thus the poking and prodding for this method was born. To anyone who reads this, and can help teach me the proper methods of creating Virtual Access Points on an Atheros wifi card using ath9k as the driver, please post your method. I've attempted using iw, however I can never get it to broadcast. It constantly gives the error 'cannot set channel.'

Now that I have the introduction out of the way, here we go:

**Preparation:**
We're going to have to install a couple of tools first:
(hostapd - Seems to be the only way I can force my card into Master mode; dhcp3-server - To assign IP's to any connecting device)
```
apt-get install hostapd dhcp3-server
```
(I have to tell you, that after a half an hour of banging my head against the wall, I was kind of depressed to discover that these were the only tools that deviated from the baseline... >_<)

**Configuration:**
[INDENT]hostapd: For some reason hostapd doesn't come from the repo's with any configuration file, and the man is of little use. But never fear! Here is a copy of hostapd.conf straight from their git, with just about every configuration you can think of.
[http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=hostapd/hostapd.conf](http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=hostapd/hostapd.conf)

If you're going to use this for a 3DS and 3DS games only, I recommend using the highest level of security available. Having said so, this configuration file will have hostapd use WPA2 Personal. NOTE!!! This will not work for DS/DSI/DSIXL or any of their associated games, even if they are being played on a 3DS. This is the exact reason that the 3DS has a Nintendo DS Connections section.
hostapd_wpa.conf - 
```
#wireless interface to use as AP
interface=wlan0
#bridge device (needed for madwifi & nl80211 drivers)
#bridge=br0
#driver interface type (hostapd/wired/madwifi/prism54/test/none/nl80211/bsd)
# Use nl80211 for wifi drivers that implement MAC80211 interface
#You should set this to your relevant driver interface type
driver=nl80211
#Enables logging to standard output (useful for debugging)
logger_stdout=-1
logger_stdout_level=2
#Set SSID to use
ssid=testIt
# Operation mode (a = IEEE 802.11a, b = IEEE 802.11b, g = IEEE 802.11g)
# note your card may not support every mode.
hw_mode=g
#Channel to use (1-13)
channel=6
# IEEE 802.11 specifies two authentication algorithms. hostapd can be
# configured to allow both of these or only one. Open system authentication
# should be used with IEEE 802.1X.
# Bit fields of allowed authentication algorithms:
# bit 0 = Open System Authentication
# bit 1 = Shared Key Authentication (requires WEP)
auth_algs=3
#maximum number of stations (clients connecting to AP) allowed
# Maximum number of stations allowed in station table. New stations will be
# rejected after the station table is full. IEEE 802.11 has a limit of 2007
# different association IDs, so this number should not be larger than that.
max_num_sta=5
#Enable WPA2
# This field is a bit field that can be used to enable WPA (IEEE 802.11i/D3.0)
# and/or WPA2 (full IEEE 802.11i/RSN):
# bit0 = WPA
# bit1 = IEEE 802.11i/RSN (WPA2) (dot11RSNAEnabled)
wpa=1
#Set passphrase for WPA
wpa_passphrase=testItNow
wpa_key_mgmt=WPA-PSK
```

I have no idea why, but with the version of hostapd from the repo's all blank lines in the .conf error out, so I took them out. And now, the part you're all waiting for. The one that will work with all the original DS games.

hostapd_wep.conf -
```
#wireless interface to use as AP
interface=wlan0
#bridge device (needed for madwifi & nl80211 drivers)
#bridge=br0
#driver interface type (hostapd/wired/madwifi/prism54/test/none/nl80211/bsd)
# Use nl80211 for wifi drivers that implement MAC80211 interface
#You should set this to your relevant driver interface type
driver=nl80211
#Enables logging to standard output (useful for debugging)
logger_stdout=-1
logger_stdout_level=2
#Set SSID to use
ssid=testItWep
# Operation mode (a = IEEE 802.11a, b = IEEE 802.11b, g = IEEE 802.11g)
# note your card may not support every mode.
hw_mode=g
#Channel to use (1-13)
channel=6
# IEEE 802.11 specifies two authentication algorithms. hostapd can be
# configured to allow both of these or only one. Open system authentication
# should be used with IEEE 802.1X.
# Bit fields of allowed authentication algorithms:
# bit 0 = Open System Authentication
# bit 1 = Shared Key Authentication (requires WEP)
auth_algs=2
wep_default_key=0
wep_key0=123456789a
#maximum number of stations (clients connecting to AP) allowed
# Maximum number of stations allowed in station table. New stations will be
# rejected after the station table is full. IEEE 802.11 has a limit of 2007
# different association IDs, so this number should not be larger than that.
max_num_sta=5

```

I actually keep both configs saved on my computer and choose which one is necessary when I go to use it. (Mainly because Pokemon Diamond/Heart Gold/Black are all orig DS games.


IPTABLES - DISCLAIMER: This will break the google talk voice/video plugin until you flush your config, or reboot your machine. If anyone can tell me why, and figure out how to resolve this issue, please tell me. 
First you need to know the names of your interfaces, so run the following:```
ifconfig -a
```
For me, eth0 is my wired interface and wlan0 is my wifi interface. If your wireless interface is named something else, please correct that in the hostapd configuration file.
Once we know all of that, here are some configurations for iptables to ensure your computer can forward incoming connections, and generally function as a natted interface. (Turns your computer into a gateway, in the simplest fashion without any real filtering.)
```
iptables -A FORWARD -o eth0 -i wlan0 -s 192.168.66.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE
```
At this point you have two options. You can save the current iptables settings to a file and load them every time you want to do this, or run these three commands. This is a very simple configuration so for some running these commands sounds feasible. For those of you that want to save it to a file and import every time just do: ```
iptables-save > $fileName
``` $fileName being whatever you want to name the file. Then to import it do: ```
cat $fileName |iptables-restore
```
Yes, I am going to use 192.168.66.1-255 as my ip range... mainly because I never see it used. 

dhcpd.conf - Because it is the last one I configured, but not least! All you need is a working subnet... however, you are more than likely going to have to put the DNS server in manually each time before you start up the daemon. 
```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...                                                                                                                                          
option domain-name-servers 192.168.1.254;                                                                                                                                   
                                                                                                                                                                            
default-lease-time 600;                                                                                                                                                     
max-lease-time 7200;

# Use this to send dhcp log messages to a different log file (you also                                                                                                      
# have to hack syslog.conf to complete the redirection).                                                                                                                    
log-facility local7;                                                                                                                                                        
 
# This is a very basic subnet declaration.

subnet 192.168.66.0 netmask 255.255.255.0 {
  range 192.168.66.2 192.168.66.24;
  option routers 192.168.66.1;
}

```
Also, this is going to sound crazy, but for some reason the defaults that came from the repo's kept giving the error that it couldn't create the pid file. This was frustrating so I stopped trying to start it with the /etc/init.d script and created my own folder in /var/run called dhcp3-server and gave dhcpd ownership over it with the following commands:```
sudo mkdir /var/run/dhcp3-server
sudo chown dhcpd:dhcpd /var/run/dhcp3-server
sudo chmod 755 /var/run/dhcp3-server
```
[/INDENT]

**Procedure: (The fun part...)**

NOTE: [I]This should all either be ran as super user, or have sudo in front of each command. Using sudo can get tedious and annoying, so... To become root in any terminal just type:```
su
```
If you don't know what the password is, either you shouldn't know or you just never set one. You can set one by typing: ```
sudo passwd root
``` Then try just su again.[/I]

First thing is first, we have to kill the nail in our foot:```
service network-manager stop
```
And check to make sure that eth0 still has an IP: ```
ifconfig 
```
As long as it does, lets bring up wlan0 and give it an IP:```
ifconfig wlan0 up
ifconfig wlan0 192.168.66.1 netmask 255.255.255.0
```

Pre-staging looks good now, so lets give iptables it's config. You can either use the commands above or use iptables-restore. Both should have the desired effect. Also, ensure your kernel is allowing port forwarding: ```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Kick up hostapd: ```
hostapd hostapd_wep.conf
```
Choose which ever config file suits your needs. As long as it doesn't give any errors, chances are your wifi card supports Master mode. I don't have a complete list of which cards do and which don't, so if you are trying this out, please post your results. I know most Atheros cards seem to...

Kick up the dhcp server. Don't forget to take a look at /etc/resolv.conf and copy the current DNS server into your dhcpd.conf. (Again, exchange wlan0 for your wifi card's name) ```
 dhcpd -pf /var/run/dhcp-server/dhcpd.pid wlan0
```

And there we are. At this point, kick open your DS, connect up and check it out. Anyone that tries this out, please report how it worked for you. I have tested it on a Vaio, and an Acer Aspire One and it worked perfectly on both for me.

---

