---
title: "[SOLVED] Batch File Wont Stay Open"
date: 2008-10-16
forum: Windows
---

### Post by Rytron on 2008-10-16
Hi,
I have a batch file.

Here is the code:
@echo off
arp -d *
nbtstat -R
ipconfig /flushdns
nbtstat -RR
ipconfig /registerdns

I click it but it just flashs and then closes. How can I make it stay open until I click a key to close it?

Thanks.

---

### Post by mobilediesel on 2008-10-16
> **Rytron said:**
> Hi,
I have a batch file.

Here is the code:
@echo off
arp -d *
nbtstat -R
ipconfig /flushdns
nbtstat -RR
ipconfig /registerdns

I click it but it just flashs and then closes. How can I make it stay open until I click a key to close it?

Thanks.

Add "pause" as the last line, then it will say "Press any key to continue . . ." and wait for you to finish reading. So make it look like this:
```

@echo off
arp -d *
nbtstat -R
ipconfig /flushdns
nbtstat -RR
ipconfig /registerdns
pause
```
That should do it.

---

### Post by Rytron on 2008-10-17
> **mobilediesel said:**
> Add "pause" as the last line, then it will say "Press any key to continue . . ." and wait for you to finish reading. So make it look like this:
```

@echo off
arp -d *
nbtstat -R
ipconfig /flushdns
nbtstat -RR
ipconfig /registerdns
pause
```
That should do it.

Excellent, that worked.

I also have this .bat file:
```
ipconfig /release
ipconfig /renew
pause
```

It just flashes. It wont stay open. Is there a fault with the above bode?

---

### Post by mobilediesel on 2008-10-17
> **Rytron said:**
> Excellent, that worked.

I also have this .bat file:
```
ipconfig /release
ipconfig /renew
pause
```

It just flashes. It wont stay open. Is there a fault with the above bode?
It's actually been about 6 months since I stopped using Windows entirely to use Ubuntu. If you have a shortcut to the batch file on the desktop, you can right-click and click "properties" and I believe there's an option to keep the window open after the batch file runs.

---

### Post by Vishal Agarwal on 2008-10-17
You can put the sleep option also for automatic execution of next statement 
like 

> sleep n seconds

---

