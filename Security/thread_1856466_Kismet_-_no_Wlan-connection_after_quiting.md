---
title: "Kismet - no Wlan-connection after quiting"
date: 2011-10-08
forum: Security
---

### Post by Karottenbaum on 2011-10-08
hallo,
after some installing problems i managed.d to run kismet and it seemed to run smooth..

but after i quited Kismet (control C) i wasnt able to establish connection to my wlan again, i had to reboot since i dont know any commands (im new to linux)... after reboot it worked again.


what i really want to know is there any tool (maybe small) which can display the dBi of the networks? i think Kismet doesn't.

thanks

---

### Post by Dangertux on 2011-10-08
The reason your wireless connection would not re-establish after use of kismet is likely because you put your card in monitor mode to capture packet traffic you have to place it back in managed mode if you want it to connect to an access point again.

```

iwconfig wlan0 mode managed

```

* note: wlan0 = your interface ath0 wlan0 wlan1 whatever.

Are you sure you should be messing with what you're trying to do?

---

### Post by Karottenbaum on 2011-10-08
do you know any tool (maybe small/ in shell) which can display the dBi of the networks? i think Kismet doesn't.

---

### Post by Dangertux on 2011-10-08
You should consult the documentation : [http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

Because it does support this functionality.

---

