---
title: "Detect Keylogger?"
date: 2010-05-08
forum: Security
---

### Post by PDA1 on 2010-05-08
How can I find out if there's a keylogger program running my machine?

---

### Post by calinut1 on 2010-05-08
> **PDA1 said:**
> How can I find out if there's a keylogger program running my machine?

well, you could install klam-av (antivirus) and do a scan of your system.

```
sudo apt-get install klamav
```

or if you don't trust the results just reinstall Ubuntu :P (maybe not the best solution)


what makes you think you got a keylogger?

---

### Post by OpSecShellshock on 2010-05-08
> **PDA1 said:**
> How can I find out if there's a keylogger program running my machine?

Best way to determine this is to know whether you installed one or not. If you didn't, then there isn't one.

---

### Post by rookcifer on 2010-05-08
Depends on what type of keylogger you're asking about -- hardware or software.  If you're wondering about hardware keyloggers, then no one here is likely to be able to help.  Physical access = game over.

If you're wondering about software keyloggers, chances are 99.99% that you do not have one even if you think you do.  For one, keyloggers need root access to install and access locations in the file system needed for reading I/O from the keyboard.  So this means basically you would have had to install one either accidentally or on purpose.

---

### Post by fululian on 2010-08-06
Same question - and for me the reason would be weak Wifi-security and security/online people yelling and screaming about keyloggers. So, there still would be a nice obstacle in form of root's pw. Other suggestions?

---

### Post by wacky_sung on 2010-08-06
> **fululian said:**
> Same question - and for me the reason would be weak Wifi-security and security/online people yelling and screaming about keyloggers. So, there still would be a nice obstacle in form of root's pw. Other suggestions?

Wifi is always prone to MTM(Man in The Middle) attack and i have no doubt it can easily be spoof or getting keylogged.

---

### Post by cariboo on 2010-08-06
Even with a man in the middle attack, the bad guy would still need the root password to install a keylogger anywhere else but the users home directory.

---

### Post by wacky_sung on 2010-08-06
> **cariboo907 said:**
> Even with a man in the middle attack, the bad guy would still need the root password to install a keylogger anywhere else but the users home directory.
Actually the bad guy can insert an exploit into the browser/application and depending on what type of exploit the bad guys is using through MTM attack.

---

### Post by OpSecShellshock on 2010-08-06
Strengthen your wi-fi security and don't install any keyloggers or anything you don't recognize from outside of the Ubuntu repositories. If an intruder has sufficient local privileges to install one, then they have sufficient privilege to hide it from any locally-run means of detection anyway.

---

### Post by linux18 on 2010-08-06
this is linux, if your not running a server no one will want to hack you even if they could. what you need to worry about are hackers hijacking your router.

---

### Post by wacky_sung on 2010-08-07
> **OpSecShellshock said:**
> Strengthen your wi-fi security and don't install any keyloggers or anything you don't recognize from outside of the Ubuntu repositories. If an intruder has sufficient local privileges to install one, then they have sufficient privilege to hide it from any locally-run means of detection anyway.

There is no way to strengthen the wifi connection once an exploit has been found.Check [this]("http://www.networkworld.com/newsletters/wireless/2010/072610wireless1.html") out.

```
WPA2 vulnerability found
'Hole 196' means malicious insiders could spoof WI-Fi packets, compromise WLAN
```

If the exploit code leak and i have no doubt wifi connection will be hijacked with those bad guys around.

In additonal ,

[http://www.pcworld.com/article/201822/wpa2_vulnerability_found.html](http://www.pcworld.com/article/201822/wpa2_vulnerability_found.html)

---

### Post by OpSecShellshock on 2010-08-07
> **wacky_sung said:**
> There is no way to strengthen the wifi connection once an exploit has been found.Check [this]("http://www.networkworld.com/newsletters/wireless/2010/072610wireless1.html") out.

```
WPA2 vulnerability found
'Hole 196' means malicious insiders could spoof WI-Fi packets, compromise WLAN
```If the exploit code leak and i have no doubt wifi connection will be hijacked with those bad guys around.

In additonal ,

[http://www.pcworld.com/article/201822/wpa2_vulnerability_found.html](http://www.pcworld.com/article/201822/wpa2_vulnerability_found.html)

This is a MiTM attack. It doesn't require any exploit code at all (though apparently it requires the attacker to be running a custom driver), because it's just a malicious use of a built-in feature. However, it does require legitimate access in the first place since the attacker would need to have an acceptable key for the access point in order to even begin.

---

### Post by bodhi.zazen on 2010-08-08
> **PDA1 said:**
> How can I find out if there's a keylogger program running my machine?

> **fululian said:**
> Same question - and for me the reason would be weak Wifi-security and security/online people yelling and screaming about keyloggers. So, there still would be a nice obstacle in form of root's pw. Other suggestions?

This thread is a bit off topic.

(Software) Keyloggers are uncommon in Linux and you would need to either install one yourself or your system is already compromised, in which case there are an overwhelmingly large number of potential problems/exploits key loggers would be the least of your worries. In that event, you would either be more proficient (at security) then your intruder or re-install.

You can list all running processes with ps aux or top, look for a key logger.

Wireless security is an entirely different topic. If you are on an untrusted network, best tunnel your traffic over ssh or VPN.

If you are trying to secure your WAP, use WPA and turn the router off when not in use.

---

