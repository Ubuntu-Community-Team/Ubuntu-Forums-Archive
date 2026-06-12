---
title: "JVM crashes"
date: 2010-01-27
forum: Virtualisation
---

### Post by lokesh.pandya on 2010-01-27
[COLOR=navy][FONT=Trebuchet MS][SIZE=3]Hi all,[/SIZE][/FONT][/COLOR]
 
[COLOR=navy][FONT=Trebuchet MS][SIZE=3]I have created virtual machine using VMwareWorkstation using Ubuntu 9.04 as guest OS. I have installed Weblogic 10.3 on the guest OS i.e. Ubuntu and deployed webapplications on it.[/SIZE][/FONT][/COLOR]
[COLOR=navy][FONT=Trebuchet MS][SIZE=3]When i am firing http request weblogic is crashing i.e. JVM is crashing with a attached log file.[/SIZE][/FONT][/COLOR]
[FONT=Trebuchet MS][SIZE=3][COLOR=#000000]Can someone tell me why this is happening so that this problem can be fixed.[/COLOR][/SIZE][/FONT]
 
[SIZE=3][FONT=Trebuchet MS][COLOR=#000000]Thanks[/COLOR][/FONT][/SIZE]

---

### Post by lokesh.pandya on 2010-01-29
adding [COLOR=#1f497d][FONT=Calibri]“[/FONT][/COLOR][FONT=Times New Roman]-Djava.*awt*.*headless*=true”  solved my problem.[/FONT]

---

