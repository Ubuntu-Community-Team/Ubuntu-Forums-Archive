---
title: "help using rfid-tools &amp; mfcuk"
date: 2015-01-27
forum: Security
---

### Post by thomas_margotta on 2015-01-27
i installed rfid-tools and am trying to figure out how to use mfcuk. i believe i installed libnfc. because i went into the ubuntu store and installed anything that had to do with libnfc. how do i use mfcuk now? im under the assumption that i can use mfcuk to find the first key, then afterward use mfoc to find the rest. how do i do this? there are absolutely no guides anywhere at all about this. its really annoying.

---

### Post by thomas_margotta on 2015-01-28
kinda got it working. it detected my reader, i tried it on a blank card and got
tom@tom-3570R-370R-470R-450R-510R-4450RV:~$ mfcuk -C -R 0


mfcuk - 0.3.2
Mifare Classic DarkSide Key Recovery Tool - 0.3
by Andrei Costin, [email]zveriu@gmail.com[/email], [http://andreicostin.com](http://andreicostin.com)




INFO: Connected to NFC reader: ACS ACR122U PICC Interface 00 00 / ACR122U213 - PN532 v1.6 (0x07)




VERIFY: 
	Key A sectors: 0 1 2 3 4 5 6 7 8 9 a b c d e f
	Key B sectors: 0 1 2 3 4 5 6 7 8 9 a b c d e f


RECOVER:  0^C
tom@tom-3570R-370R-470R-450R-510R-4450RV:~$ 
soo i guess it knows my card reader is there n stuff.

i tried it with something that has keys i dont know and get this
tom@tom-3570R-370R-470R-450R-510R-4450RV:~$ mfcuk -C -R 0


mfcuk - 0.3.2
Mifare Classic DarkSide Key Recovery Tool - 0.3
by Andrei Costin, snip, [http://andreicostin.com](http://andreicostin.com)




INFO: Connected to NFC reader: ACS ACR122U PICC Interface 00 00 / ACR122U213 - PN532 v1.6 (0x07)




VERIFY: 
	Key A sectors: 0Bus error (core dumped)
tom@tom-3570R-370R-470R-450R-510R-4450RV:~$ 








i dont even know what this code means. it just looked like people were typeing that and getting results... can someone give me something to work with!!!

---

### Post by thomas_margotta on 2015-01-28
now i think when i put a blank card on it it just hangs, because when i try to x out of the terminal window it tells me something is still running. i left it up while i took a shower, which is like, 30 minutes. so for thirty minutes the same screen hung there... can someone please just point me in the right direction here? give me something to start with? anyone at all?

---

### Post by cariboo on 2015-01-28
We don't support this type of activity here. Thread closed.

You may want to try [here]("https://forums.kali.org/") to get your problem solved.

---

