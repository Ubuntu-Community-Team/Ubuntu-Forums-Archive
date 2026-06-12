---
title: "How can I get this Alltel/Verizon Wireless HUAWEI to work in Ubuntu/Kubuntu 9.10?"
date: 2009-08-28
forum: The Cafe
---

### Post by gymophett on 2009-08-28
It worked fine in Linux Mint 7! I plugged it in and it got connected by clicking connect to Mobile Broadand or something like that...
It's an Alltel Wireless HUAWEI EC168 Usb Sitck. I plug it in, and it says "Network Management.. Device Attached".
So I see a cell phone device at the bottom and it says "Not Connected"
I click it and it sayd "New Cellular Connection"
I click that, and something comes up asking me for mobile number, username, and password. I didn't know there was supposed to be a mobile number. It used to JUST WORK.
Where can I find all of this information, or is there something else I can do?

---

### Post by t0p on 2009-08-28
When the network manager runs the New Cellular Connection wizard, aren't you asked to select your service provider from a drop-down menu?  That's how it works for me.  When you select your provider, the user name, password and number fields should be automagically filled in for you.

If this doesn't happen, you should be able to find out the user name and password by asking your service provider.  The number will be *99#.

**Edit:** I just noticed that you're testing karmic.  The fact that you're using a Beta may explain why the network manager isn't working as it does in older versions.  Anyway, my advice still stands.  Especially about calling your cellular provider's customer service and asking them for the user name and password required.  A quick google should also discover this info for you.

---

### Post by GeorgeVita on 2009-08-28
Hi **gymophett**,
although this forum is to 'relax and drink your coffee' (joke),

> I click it and it sayd "New Cellular Connection"
I click that, and something comes up asking me for mobile number, username, and password.

You need to setup Country, Provider and type of account (if more than one type as prepaid or postpaid) leave all other parameters to defaults. If asking for 'keyring' password leave it blank and proceed (use unsafe space).

If you cannot do it, post me Ubuntu version, country/provider to give you exact steps.

Regards,
George

EDIT: same time ... Hi tOp!

---

