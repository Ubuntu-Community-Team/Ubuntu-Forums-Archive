---
title: "Ubuntu Server crashing"
date: 2007-10-04
forum: Server Platforms
---

### Post by jcdutton on 2007-10-04
I have ubuntu server installed.
Running ubuntu kernel "2.6.15-28-server".

When is crashes, it still responds to pings, but all other comms is dead.
I.e. sshd does not respond, apache does not respond etc.
Also, the local console does not respond.

Can anybody point me to the best way to diag this. I have just plugged a PC into the serial port to hopefully catch a trace next time is hangs, but it has been up for 19 hours now. Yesterday is crashed 3 times.

Kind Regards

James

---

### Post by conjur3r on 2007-10-04
Try the usual log files under /var/log, especially /var/log/messages.  Next time it freezes, check the screen for any error messages.  It wouldn't hurt to try testing the memory chips using memtest.

---

### Post by jcdutton on 2007-10-04
No messages appear in the logs after the reboot, but that might just be ext3 journal rolling back.
When in hangs, the screen is blank, probably due to the console screen blanker.
I am waiting for it to fail again, as I have a com port connected now.

---

### Post by tgalati4 on 2007-10-04
Could be a powersupply problem.  Take some extra power leads and snake them outside the case.  Put a voltmeter and check your 5VDC and 12VDC--Red and Yellow wires to black.  Any dips during operation could indicate a failing power supply.

It's interesting how we first point to the software when a machine freezes.

What is the make and model of the PC?  How old?

---

### Post by jcdutton on 2007-10-04
The server is a Dell Power Edge 1800 with PERC4e/DC RAID controller.

---

### Post by tgalati4 on 2007-10-04
Have you done a google search on the Power Edge 1800 to see if there are problems on the Window's side?  I know that Dell had a rash of bad capacitors in their power supplies of their business machines.

What was your longest uptime on this machine?

---

### Post by netlogic on 2007-10-04
"When is crashes, it still responds to pings, but all other comms is dead.
I.e. sshd does not respond, apache does not respond etc.
Also, the local console does not respond."

i think he is right. it sounds like not enough juice. i am pretty sure it is a hardware issue. if it isn't the power supply, it is your ram. i doubt it is the board.
also, try rolling back to i386 kernel... just in case...actually, i will do that first.

---

