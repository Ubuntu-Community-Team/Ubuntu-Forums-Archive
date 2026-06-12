---
title: "Server 18.10 - bluetooth issue / timeout"
date: 2018-09-19
forum: Server Platforms
---

### Post by LaCruz on 2018-09-19
Bluetooth is working so far, but on dmesg I got this:

```

[65858.610191] Bluetooth: hci0: command 0x041b tx timeout
[66159.443172] Bluetooth: hci0: command 0x041b tx timeout
[66458.963817] Bluetooth: hci0: command 0x041b tx timeout
[66758.484238] Bluetooth: hci0: command 0x041b tx timeout
[67059.316487] Bluetooth: hci0: command 0x041b tx timeout
[67358.836653] Bluetooth: hci0: command 0x041b tx timeout
[67658.388886] Bluetooth: hci0: command 0x041b tx timeout
[67959.221055] Bluetooth: hci0: command 0x041b tx timeout
[68258.741157] Bluetooth: hci0: command 0x041b tx timeout
[68558.261282] Bluetooth: hci0: command 0x041b tx timeout
[68859.093391] Bluetooth: hci0: command 0x041b tx timeout
[69158.613515] Bluetooth: hci0: command 0x041b tx timeout
[69459.414790] Bluetooth: hci0: command 0x041b tx timeout
[69758.935741] Bluetooth: hci0: command 0x041b tx timeout
[70059.736308] Bluetooth: hci0: command 0x041b tx timeout
[70178.776605] Bluetooth: hci0: command 0x041b tx timeout
[70359.256863] Bluetooth: hci0: command 0x041b tx timeout
[70660.057244] Bluetooth: hci0: command 0x041b tx timeout
[70958.329664] Bluetooth: hci0: command 0x041b tx timeout
[71259.133730] Bluetooth: hci0: command 0x041b tx timeout
[71558.640018] Bluetooth: hci0: command 0x041b tx timeout
[71859.452168] Bluetooth: hci0: command 0x041b tx timeout
[72160.260639] Bluetooth: hci0: command 0x041b tx timeout
[72458.507197] Bluetooth: hci0: command 0x041b tx timeout
[72759.312798] Bluetooth: hci0: command 0x041b tx timeout
[73058.869653] Bluetooth: hci0: command 0x041b tx timeout
[73358.360243] Bluetooth: hci0: command 0x041b tx timeout
[73659.191983] Bluetooth: hci0: command 0x041b tx timeout
[73958.713389] Bluetooth: hci0: command 0x041b tx timeout
[74259.515881] Bluetooth: hci0: command 0x041b tx timeout
[74559.038510] Bluetooth: hci0: command 0x041b tx timeout
[74858.561607] Bluetooth: hci0: command 0x041b tx timeout
[75159.364889] Bluetooth: hci0: command 0x041b tx timeout
[75458.913837] Bluetooth: hci0: command 0x041b tx timeout
[75758.460358] Bluetooth: hci0: command 0x041b tx timeout
[76059.258144] Bluetooth: hci0: command 0x041b tx timeout
[76358.777774] Bluetooth: hci0: command 0x041b tx timeout
[76658.298296] Bluetooth: hci0: command 0x041b tx timeout
[76959.131423] Bluetooth: hci0: command 0x041b tx timeout
[77259.932877] Bluetooth: hci0: command 0x041b tx timeout
[77558.174484] Bluetooth: hci0: command 0x041b tx timeout
[77858.976272] Bluetooth: hci0: command 0x041b tx timeout
[78158.497932] Bluetooth: hci0: command 0x041b tx timeout
[78459.331769] Bluetooth: hci0: command 0x041b tx timeout
[78758.853553] Bluetooth: hci0: command 0x041b tx timeout
[79058.375367] Bluetooth: hci0: command 0x041b tx timeout
[79359.209208] Bluetooth: hci0: command 0x041b tx timeout
[79658.760890] Bluetooth: hci0: command 0x041b tx timeout
[79959.561071] Bluetooth: hci0: command 0x041b tx timeout
[80259.081820] Bluetooth: hci0: command 0x041b tx timeout
[80558.634840] Bluetooth: hci0: command 0x041b tx timeout
[80860.748093] Bluetooth: hci0: command 0x041b tx timeout
[81158.989381] Bluetooth: hci0: command 0x041b tx timeout
[81458.542899] Bluetooth: hci0: command 0x041b tx timeout
[81759.352821] Bluetooth: hci0: command 0x041b tx timeout
[82058.879286] Bluetooth: hci0: command 0x041b tx timeout
[82358.404143] Bluetooth: hci0: command 0x041b tx timeout
[82659.175957] Bluetooth: hci0: command 0x041b tx timeout
[82958.699256] Bluetooth: hci0: command 0x041b tx timeout
[83259.534738] Bluetooth: hci0: command 0x041b tx timeout
[83559.055042] Bluetooth: hci0: command 0x041b tx timeout
[83858.602021] Bluetooth: hci0: command 0x041b tx timeout
[84159.399827] Bluetooth: hci0: command 0x041b tx timeout
[84458.919230] Bluetooth: hci0: command 0x041b tx timeout
[84758.471552] Bluetooth: hci0: command 0x041b tx timeout
[85059.272347] Bluetooth: hci0: command 0x041b tx timeout
[85358.793388] Bluetooth: hci0: command 0x041b tx timeout
[85658.309368] Bluetooth: hci0: command 0x041b tx timeout
[85959.100413] Bluetooth: hci0: command 0x041b tx timeout
[86258.647303] Bluetooth: hci0: command 0x041b tx timeout
[86559.444259] Bluetooth: hci0: command 0x041b tx timeout
[86858.962457] Bluetooth: hci0: command 0x041b tx timeout

```

Kernel:
Linux ubuntu-server 4.18.0-7-generic #8-Ubuntu SMP Tue Aug 28 18:24:42 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Device:
Bus 002 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

Bluez:
5.50-0ubuntu1

---

