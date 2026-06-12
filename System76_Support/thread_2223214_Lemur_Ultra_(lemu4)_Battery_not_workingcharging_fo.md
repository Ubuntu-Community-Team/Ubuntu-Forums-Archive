---
title: "Lemur Ultra (lemu4) Battery not working/charging following 14.04 update?"
date: 2014-05-10
forum: System76 Support
---

### Post by adamtomaino on 2014-05-10
Since i updated to Lemur Ultra (lemu4) I've been having an issue with running my lemur off the powerstrip.  Once unplugged (while in operation) the laptop turns off. When off power supply I cannot get the laptop to power on. battery info is as follows:
:~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
native-path: BAT0
vendor: NOTEBOOK
model: BAT
serial: 0001
power supply: yes
updated: Sat 10 May 2014 12:40:18 AM EDT (28 seconds ago)
has history: yes
has statistics: yes
battery
present: yes
rechargeable: yes
state: charging
energy: 24.1536 Wh
energy-empty: 0 Wh
energy-full: 33.0114 Wh
energy-full-design: 48.84 Wh
energy-rate: 0 W
voltage: 12.623 V
percentage: 73%
capacity: 67.5909%
technology: lithium-ion

---

### Post by adamtomaino on 2014-05-24
Follow-up, System 76 directed me toward purchasing a replacement battery ($95 :( ). I was sure the battery wasnt the issue but I purchases anyway....... 1 week later, new battery is in and problem solved :guitar:. Guess there tech support has seen this problem again. The lemur is a great lappy, so i am thrilled the issue is fixed.

---

