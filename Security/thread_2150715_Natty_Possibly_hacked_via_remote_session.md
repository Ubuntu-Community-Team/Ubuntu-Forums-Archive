---
title: "Natty: Possibly hacked via remote session"
date: 2013-06-02
forum: Security
---

### Post by carverj on 2013-06-02
Hi All,
I was using Ubuntu and pressed a button on a website and at that moment it appeared that I had lost control of my session. It seems as though the desktop sharing preferences may have been used as the 'Allow other users to control your desktop' setting is selected although greyed. Is there a log that can prove that someone took control at a specific time? I am unaware of any VNC type utilities installed or running right now.
Thanks for your time I appreciate it.
carverj

---

### Post by QIII on 2013-06-02
Hello!

Is "Allow others to view your desktop" selected?

---

### Post by CharlesA on 2013-06-02
There is no log for vino (the remote desktop application that comes with Ubuntu), but it should have showed an icon if someone was connected.

---

### Post by carverj on 2013-06-02
No I didn't see the vino icon and 'Allow others to view your desktop' was unchecked when I had a look after restarting computer. It just seems odd that web page tabs were selected and then a webpage as selected with Ctrl-A is if they were copying from my screen.

---

### Post by mr-woof on 2013-06-02
what happens if you go back to the same webpage?

---

### Post by Cheesemill on 2013-06-02
This is why you should never run an outdated OS.

It may not have anything to do with your issue but support for 11.04 ended 8 months ago.  Any security issues that may have been discovered in your applications since then will never get fixed, there may be a new exploit around that lets anyone access your system with ease which your system will never get patched against.

---

### Post by carverj on 2013-06-02
mr-woof : Yes I tried to open the pages again to see if it was a software issue but no issues 
Cheesemill: Oh, that might be my problem. Is there any way I can show an unlawful access happened?

---

### Post by CharlesA on 2013-06-02
It could have been some javascript on that specific site. You said you clicked on a button.

If everything shown in the remote desktop thing is greyed out, it isn't enabled, so it would probably be best to monitor the system and to at the very least upgrade to a version of Ubuntu that is currently supported.

---

### Post by carverj on 2013-06-02
Yes, OK. I would like to test again to see if it was browser or remote control/security issue. Would netstat -a catch someone in the act?

---

### Post by carverj on 2013-06-02
OK so I tried hitting a similar button on this website and no Javascript problems and also no interaction with my desktop. However, towards the end of the function the site was performing I received the following strange info with a bunch of connections establishing. Also, my ISP connection doesn't appear suddenly. Is this usual behaviour?:-

```
tcp        0      0 me:40589     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0      0 me:44659     a60-254-148-11.de:https ESTABLISHED
tcp        0      0 me:59696     channel-ecmp-13-p:https FIN_WAIT2  
tcp        0      0 me:55789     a23-53-149-222.de:https ESTABLISHED
tcp        0      0 me:51980     a125-56.181-186.d:https ESTABLISHED
tcp        0      0 me:49679     64.4.26.37:https        ESTABLISHED
tcp        0      0 me:46488     a-61-9-193-134.de:https ESTABLISHED
tcp        0      0 me:40620     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0      0 me:55855     a23-53-148-185.de:https ESTABLISHED
tcp        1      0 me:41073     barbadine.canonica:http CLOSE_WAIT 
tcp        0      0 me:40592     OCSP.TKO2.VERISIGN:http ESTABLISHED
tcp        0      0 me:40617     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0      0 me:59529     a-61-9-129-238.de:https ESTABLISHED
tcp        1      0 me:44496     mulberry.canonical:http CLOSE_WAIT 
tcp        0      0 me:59527     a-61-9-129-238.de:https ESTABLISHED
tcp        0      0 me:55858     a23-53-148-185.de:https ESTABLISHED
tcp        0      0 me:40616     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0      0 me:46486     a-61-9-193-134.de:https ESTABLISHED
tcp        0      0 me:40612     OCSP.TKO2.VERISIGN:http ESTABLISHED
tcp        0      0 me:40594     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0      0 me:51140     168.61.17.76:https      ESTABLISHED
tcp        0      0 me:46487     a-61-9-193-134.de:https ESTABLISHED
tcp        0      0 me:55862     a23-53-148-185.de:https ESTABLISHED
tcp        0      0 me:43802     64.4.21.42:https        ESTABLISHED
tcp        0      0 me:59376     a118-215.112-124.:https ESTABLISHED
tcp        0      1 me:49317     128.121.22.160:http     LAST_ACK   
tcp        0      0 me:40587     OCSP.TKO2.VERISIGN:http ESTABLISHED
tcp        0      0 me:46485     a-61-9-193-134.de:https ESTABLISHED
tcp        0      0 me:46489     a-61-9-193-134.de:https ESTABLISHED
tcp        0      0 me:53567     65.55.195.238:https     ESTABLISHED
tcp        0      0 me:50760     65.54.191.41:https      ESTABLISHED
tcp        0      0 me:40586     OCSP.TKO2.VERISIGN:http ESTABLISHED
tcp        1      0 me:41074     barbadine.canonica:http CLOSE_WAIT 
tcp        0      0 me:54810     origin.sn131w.snt1:http ESTABLISHED
tcp        0      0 me:55859     a23-53-148-185.de:https ESTABLISHED
tcp        0      0 me:51979     a125-56.181-186.d:https ESTABLISHED
tcp        0      0 me:40619     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0      0 me:40614     OCSP.TKO2.VERISIGN:http ESTABLISHED
tcp        0      0 me:40588     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0     38 me:51012     flextags.co3.bing:https LAST_ACK   
tcp        0      0 me:55861     a23-53-148-185.de:https ESTABLISHED
tcp        0      0 me:40593     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0      0 me:40618     OCSP.TKO2.VERISIGN:http TIME_WAIT  
tcp        0      0 me:58067     edge-star-ecmp-02:https ESTABLISHED
tcp        0      0 me:42638     65.55.195.236:https     ESTABLISHED
tcp        0      0 me:55792     a23-53-149-222.de:https ESTABLISHED
tcp        0      0 me:37137     a-61-9-193-174.de:https ESTABLISHED
tcp        0      0 me:55791     a23-53-149-222.de:https ESTABLISHED
tcp        0      0 me:44658     a60-254-148-11.de:https ESTABLISHED
tcp        0      0 me:55778     a23-53-149-222.de:https ESTABLISHED
tcp        0      0 me:55860     a23-53-148-185.de:https ESTABLISHED
tcp        0      0 me:46997     baymsg1010712.gat:https ESTABLISHED
tcp        0      0 me:55790     a23-53-149-222.de:https ESTABLISHED
tcp        1      0 me:59715     channel-ecmp-13-p:https CLOSE_WAIT 
tcp        1      0 me:59528     a-61-9-129-238.de:https CLOSE_WAIT 
tcp        0      0 me:40591     OCSP.TKO2.VERISIGN:http ESTABLISHED
tcp        1      0 me:59531     a-61-9-129-238.de:https CLOSE_WAIT 
tcp        0      0 me:39300     64.4.45.62:https        ESTABLISHED
tcp6       0      0 ip6-localhost:ipp       [::]:*                  LISTEN     
udp        0      0 *:34198                 *:*                                
udp        0      0 localhost:domain        *:*                                
udp        0      0 *:mdns                  *:*                                
udp6       0      0 [::]:33140              [::]:*                             
udp6       0      0 [::]:mdns               [::]:*
```

---

### Post by Soul-Sing on 2013-06-03
microsoft, bing search engine, canonical, verisign, NTT america. doesn't look like a hack.

---

