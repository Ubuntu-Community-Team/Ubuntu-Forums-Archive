---
title: "Issue with apparmor default profile"
date: 2013-08-10
forum: Security
---

### Post by Traxster on 2013-08-10
Hello to all,

Just trying to configure apparmor in its default profile, 

and below is what i get when I start it.

```
root@hades:~# /etc/init.d/apparmor start
 * Starting AppArmor profiles                                                                                                                          
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox


```
 
for some reason, it appears, that it is skipping the firefox and rsyslogd profiles. 
firefox is what I want protected the most.

```
root@hades:~# /etc/init.d/apparmor status
apparmor module is loaded.
22 profiles are loaded.
22 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/lib/telepathy/telepathy-*//pxgsettings
   /usr/lib/telepathy/telepathy-*//sanitized_helper
   /usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper
   /usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser
   /usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper
   /usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
3 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (3198) 
   /usr/lib/telepathy/mission-control-5 (2271) 
   /usr/sbin/cupsd (1306) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.


```

any help would be greatly appreciated

Traxster

---

### Post by Hungry Man on 2013-08-10
Have you tried running 

aa-enforce /etc/apparmor.d/*firefox*

---

### Post by Traxster on 2013-08-10
> **Hungry Man said:**
> Have you tried running 

aa-enforce /etc/apparmor.d/*firefox*

Ok, it looks like that did it here are the results now


```
root@hades:~# aa-enforce /etc/apparmor.d/*firefox* 
Setting /etc/apparmor.d/usr.bin.firefox to enforce mode.
root@hades:~# /etc/init.d/apparmor status
apparmor module is loaded.
26 profiles are loaded.
26 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox/firefox{,*[^s][^h]}
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/lib/telepathy/telepathy-*//pxgsettings
   /usr/lib/telepathy/telepathy-*//sanitized_helper
   /usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper
   /usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser
   /usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper
   /usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
3 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (1904) 
   /usr/lib/telepathy/mission-control-5 (2404) 
   /usr/sbin/cupsd (1128) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.



```

Thank you much

Traxster

---

### Post by Traxster on 2013-08-11
Ok, 

after reading introduction to apparmor by bodhi.zazen, i decided to try and set up my own profile . Generated a profile for OpenVPN which I use as strictly a client to connect to a remote VPN.

I used the command:  aa-genprof openvpn

this generated a profile, however, I was not able to connect to my remote vpn, so since I really was not sure of what to change, I used command aa-logprof openvpn, to read complain log, 5 times finding a different errors until it finally worked. 

the resulting profile is below:

# Last Modified: Sun Aug 11 20:27:06 2013
#include <tunables/global>

/usr/sbin/openvpn {
  #include <abstractions/apache2-common>
  #include <abstractions/base>

[COLOR=#ff0000]  capability net_admin,



  /dev/net/tun rw,
  /etc/openvpn/xxx.ca.crt r,
  /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper rix,
  /usr/sbin/openvpn mr,[/COLOR]

}

I believe the last 5 lines marked in red are the ones that were added one at a time untill openvpn worked again. Can someone explain what they mean and verify that this profile ok? Does anything need to be added? As stated above, I am only using openvpn as a client to connect to a remote vpn. 

Now that I have gotten through the above mentioned guide, where do I go from here to gain more knowledge. 

Any help would be greatly appreciated.


traxster

---

### Post by Traxster on 2013-08-14
> **Traxster said:**
> Ok, 


  where do I go from here to gain more knowledge?




traxster

Here is [URL="http://wiki.apparmor.net/index.php/QuickProfileLanguage"]A quick guide to apparmor profile language.





[/URL]

---

