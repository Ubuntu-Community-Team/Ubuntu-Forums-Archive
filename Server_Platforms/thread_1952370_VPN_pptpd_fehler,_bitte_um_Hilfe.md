---
title: "VPN pptpd fehler, bitte um Hilfe"
date: 2012-04-04
forum: Server Platforms
---

### Post by JSunny on 2012-04-04
Liebe Ubuntu Community,

ich muss gestehen, dass ich ein blutiger Anfänger mit Ubuntu bin. Ich habe mich in den letzten Wochen in meinen Ubuntu vServer eingearbeitet und kann jetzt erst die basics mit cd, cp, nano, mv, ifconfig usw.
Für alle die jetzt noch nicht aufgehört haben weiter zu lesen möchte ich mich schon einmal bedanken.
Ich habe probiert VPN auf meinem Server zu installieren. Es gibt ja dazu diverse Tuturials via google die auch sehr gut erklärend sind. Also habe ich via 

sudo apt-get install pptpdpptpd installiert und die konfigurationen gemacht wie z.B. hier beschrieben wurden: [http://www.networkinghowtos.com/howto/configure-a-pptp-vpn-server-on-ubuntu-linux/](http://www.networkinghowtos.com/howto/configure-a-pptp-vpn-server-on-ubuntu-linux/)

Es gab keinerlei komplikationen außer dass bei meinem Server scheinbar keine schnittstelle eth0 gibt sondern scheinbar nur venet0, hier der ifconfig auszug:


root@h2014422:~# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:682265 (682.2 KB)  TX bytes:682265 (682.2 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:547715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:652893 errors:0 dropped:8 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:224323666 (224.3 MB)  TX bytes:642187033 (642.1 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:85.214.218.184  P-t-P:85.214.218.184  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

Wenn ich nun probiere von einem Klienten (PC WIN7 oder Android) zu connecten kommt immer ein Error 807, das scheinbar die authentisierung fehlgeschlagen ist. jedoch sind die chap-secrets korrekt konfiguriert.
Könntet ihr mir helfen meinen Fehler zu finden damit der VPN tunnel funktioniert.
Für mehr infos einfach die jeweilige Datei mit pfad erbitten und ich kann  sie posten. Danke im Vorraus!!

---

### Post by spynappels on 2012-04-04
You might get more answers if you outlined the problem in English, if that is possible. If not I'll try and translate the salient points for you in another post. 

Is there a specific reason you chose pptp rather than a different VPN solution like OpenVPN/SSL based VPN?

It appears that there may be some issues in that venet0 has the same IP address as lo, which could be causing problems for you.

---

### Post by Karlchen on 2012-04-04
Hallo, JSunny,

wie dir vielleicht aufgefallen ist, ist dies das internationale Ubuntu Benutzerforum und darum englischsprachig. Das deutschsprachige Benutzerforum findest du hier: [**ubuntuusers**]("http://ubuntuusers.de/"). Die meisten Leute hier werden dich einfach nicht verstehen und darum auch nicht helfen können.

Grüße
Karl
--
Hello, JSunny,

as you may have noticed, this is the international Ubuntu user forum and therefore English is spoken. The German speaking user forum can be found here: [**ubuntuusers**]("http://ubuntuusers.de/"). Most people in this forum will simply not understand your post and be unable to write any helpful reply as a consequence.

Kind regards,
Karl

---

### Post by spynappels on 2012-04-04
See your English thread [http://ubuntuforums.org/showthread.php?t=1952379](http://ubuntuforums.org/showthread.php?t=1952379), maybe ask for this one to be closed?

---

### Post by JSunny on 2012-04-04
hey guys,

yea sorry i got that ^^ i translated it already, sorry again :)

---

