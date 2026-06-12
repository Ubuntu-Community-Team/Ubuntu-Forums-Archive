---
title: "Changing Hardware ID info with Ubuntu"
date: 2010-08-31
forum: Security
---

### Post by Nishi_Niigata on 2010-08-31
Each computer has certain hardware that has its own ID...My understanding is that this info can be used to identify you. 

Is there a way to either permanently change the ID values of that hardware in the bios or hardware, or at least a way to alter what you transmit to websites when that info is recorded?

What information is being transmitted as I post right now?


Lately I have become very concerned about data mining. I do not want corporations to be saving my web browsing behavior so they can market me products, and I do not want that same info being given to the government either. I have an expectation of privacy on the internet.

---

### Post by Bachstelze on 2010-08-31
Probably not, such information is generally hardcoded in the hardware's microcode.

---

### Post by BkkBonanza on 2010-08-31
I think if you were to monitor data sent out with Wireshark you'd be pretty hard pressed to find any data that identifies your machine. Of course, the MAC address is in each packet but that is usually stripped by your router, and it can easily be spoofed anyway so doesn't mean much. There is various OS fingerprinting techniques but I'm not aware of machine id values being inserted into packets. I haven't looked for this myself though and sometimes it's surprising what is going on without you being aware.

---

