---
title: "Occasional loss of wifi connection"
date: 2017-06-03
forum: Ubuntu/Debian BASED
---

### Post by pemartins on 2017-06-03
Hi,

My wifi connection to my home network ZON-7FB0_2 is sometimes lost on my new OS install. After the installation I had trouble connecting so I entered these commands suggested here at the forum for my previous OS:
 [https://ubuntuforums.org/showthread.php?t=2341569&p=13563160#post13563160](https://ubuntuforums.org/showthread.php?t=2341569&p=13563160#post13563160)

```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
sudo iw reg set PT
```
```
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
```

The other network I connect to is ZON-E850, which usually has a weaker connection than the previously mentioned one. My laptop is an Asus X55U-SX038H.

I don't know if something can be done to strength the connection and stability, here the output from the wireless info script:
[https://pastebin.com/raw/Y8MkyPMd](https://pastebin.com/raw/Y8MkyPMd)


Thank you very much in advance.

---

### Post by again? on 2017-06-03
Have you looked at your router channel.
I use an adroid app [**Wifi Analyzer**]("https://play.google.com/store/apps/details?id=com.farproc.wifi.analyzer&hl=en") 
to determine the best channel to use in relation to neighbours.

---

### Post by jeremy31 on 2017-06-03
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by chili555 on 2017-06-03
Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

You might also experiment with N speeds turned off. In many cases with your particular driver rt2800pci, turning off N is very helpful.

Your driver, Jeremy and I hate hate hate TKIP.

---

### Post by pemartins on 2017-06-03
Thank you all very much for your help.

I'll adjust the router settings as told. Nevertheless, is there something I should do on my pc?

About this:
> **chili555 said:**
> Your driver, Jeremy and I hate hate hate TKIP.
Is there any other driver I could use? If there is please tell me so I can try it, anything I can do to improve is very welcome.

Thank you all very much once again fro your help!

---

### Post by chili555 on 2017-06-03
I was simply referring to this:> Cell 01 - Address: <MAC 'ZON-E850' [AC1]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"ZON-E850"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d350a99b72
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        [COLOR="#FF0000"]Group Cipher : TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                       [COLOR="#FF0000"] Group Cipher : TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKWe strongly recommend that you reset the router from WPA/WPA2 mixed mode and TKIP to the preferable WPA2-AES. TKIP is insecure and mixed mode requires a bit of hopping around for your driver and hardware to find the router. We suggest that you use the best security at all times.

I fully realize that router manufacturers set their hardware to use the lowest common denominator but we users ought to examine their choices and over-rule them if they are insecure or difficult.

---

### Post by pemartins on 2017-06-03
I'll do so. If I have any difficulties or questions I'll ask for more assistance but I believe I know how to set all the suggested changes.

A huge thank you once again!

---

