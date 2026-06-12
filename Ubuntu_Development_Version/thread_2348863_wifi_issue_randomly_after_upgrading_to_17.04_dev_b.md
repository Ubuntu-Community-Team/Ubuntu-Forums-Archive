---
title: "wifi issue randomly after upgrading to 17.04 dev branch :("
date: 2017-01-08
forum: Ubuntu Development Version
---

### Post by alain.roger on 2017-01-08
Hello,

by mistake i upgraded my kubuntu 16.10 to 17.04 dev branch.
Everything works great except that sometimes (it could be 0 to several times per day) i lost my wifi connection.
i must click on "disconnect" and "connect" in front of my wifi SSID to get it back.
except that everything works great.

i was wondering what could be the problem but i was not able to find a solution.
result of:  [FONT=monospace][COLOR=#000000]lspci -knn | grep Net -A2
[/COLOR]
```
03:00.0 [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work controller [0280]: Qualcomm Atheros AR9285 Wireless [/COLOR][COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter (PCI-Express) [168c:002b] (rev 01)[/COLOR]
        Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
        Kernel driver in use: ath9k
```

if i restart the networkmanager everything works great too... so it's like for an unknown reason, my wifi adapter was down and i need to bring it back to up...

any idea what could be the issue or what should i test/do to find the issue and solve it ?
thx.
[/FONT]

---

### Post by dino99 on 2017-01-08
so what is the > cat /etc/apt/sources.list output now ? Is there mixed (16.10 + 17.04) entries ?
Try cleaning the system (i does not use/know kubuntu, but with gnome im using deborphan & bleachbit; find the kde relative package) to purge the old settings left behind the upgrade.
Also > sudo apt-get -f install & > sudo dpkg --configure -a might help 
Maybe some warning/error(s) are also logged (see journalctl)

---

### Post by alain.roger on 2017-01-08
[FONT=monospace][COLOR=#000000]output of : cat /etc/apt/sources.list[/COLOR]

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu zesty main restricted
deb-src http://archive.ubuntu.com/ubuntu zesty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu zesty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu zesty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu zesty universe
deb-src http://archive.ubuntu.com/ubuntu zesty universe
deb http://archive.ubuntu.com/ubuntu zesty-updates universe
deb-src http://archive.ubuntu.com/ubuntu zesty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu zesty multiverse
deb-src http://archive.ubuntu.com/ubuntu zesty multiverse
deb http://archive.ubuntu.com/ubuntu zesty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu zesty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes                                                                                                                              
## newer versions of some applications which may provide useful features.                                                                                                                               
## Also, please note that software in backports WILL NOT receive any review                                                                                                                             
## or updates from the Ubuntu security team.                                                                                                                                                            
deb http://archive.ubuntu.com/ubuntu zesty-backports main restricted universe multiverse                                                                                                                
deb-src http://archive.ubuntu.com/ubuntu zesty-backports main restricted universe multiverse                                                                                                            
                                                                                                                                                                                                        
deb http://security.ubuntu.com/ubuntu/ zesty-security main restricted                                                                                                                                   
deb-src http://archive.ubuntu.com/ubuntu zesty-security main restricted                                                                                                                                 
deb http://security.ubuntu.com/ubuntu/ zesty-security universe                                                                                                                                          
deb-src http://archive.ubuntu.com/ubuntu zesty-security universe                                                                                                                                        
deb http://security.ubuntu.com/ubuntu/ zesty-security multiverse                                                                                                                                        
deb-src http://archive.ubuntu.com/ubuntu zesty-security multiverse                                                                                                                                      
                                                                                                                                                                                                        
## Uncomment the following two lines to add software from Canonical's                                                                                                                                   
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu/ zesty partner
```

As you can se ONLY ZESTY sources

[/FONT][FONT=monospace][COLOR=#000000]2. sudo apt-get -f install
i already did it and nothing to remove or to install

3. [/COLOR][/FONT][FONT=monospace][COLOR=#000000]sudo dpkg --configure -a[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]the same result...nothing 


[/COLOR][/FONT][FONT=monospace]
[/FONT]

---

### Post by jeremy31 on 2017-01-08
I wonder if wifi power management is at fault
```
iwconfig; cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

---

### Post by alain.roger on 2017-01-08
[COLOR=#000000]cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf [/COLOR]result:
[FONT=monospace][COLOR=#000000][connection][/COLOR]
wifi.powersave = 3

for testing purposes i set it to 2 (so no wifi powersave) but nothing changed... just at 23h56 it stopped to work :(


[/FONT]

---

### Post by jeremy31 on 2017-01-08
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
That should change the power management to disabled by default rather than enabled.  Power management has been causing wifi issues for some time and now it gets enabled by default in Network Manager settings
Reboot or restart network manager

---

### Post by alain.roger on 2017-01-09
If you read what i previously wrote, i already did it by writing it directly and manually in the file... but nothing helped as less than 40 minutes later i had the same issue.

---

