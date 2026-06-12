---
title: "printer sharing not working"
date: 2008-05-18
forum: Server Platforms
---

### Post by nix4me on 2008-05-18
Hi,

I have my Deskjet D2400 series printer shared to the network.  Another Linux machine can see it fine and print to it fine.

But, my windows machines cannot add the printer.  I use: [Http://192.168.1.102:631/printers/Deskjet_D2400_series](Http://192.168.1.102:631/printers/Deskjet_D2400_series) as the url and it connects.  Then I choose the driver on the windows machine and it just hangs and never finishes.

Any idea whats going on?  I've never had this problem before.  I've had this same printer shared before on many different Linux distros.

Any ideas?

---

### Post by persev on 2008-05-19
> **nix4me said:**
> Hi,

I have my Deskjet D2400 series printer shared to the network.  Another Linux machine can see it fine and print to it fine.

But, my windows machines cannot add the printer.  I use: [Http://192.168.1.102:631/printers/Deskjet_D2400_series](Http://192.168.1.102:631/printers/Deskjet_D2400_series) as the url and it connects.  Then I choose the driver on the windows machine and it just hangs and never finishes.

Any idea whats going on?  I've never had this problem before.  I've had this same printer shared before on many different Linux distros.

Any ideas? a HP photosmart and I am having the same problem, my wifes XP laptop cannot see the cups printer. 50000 thread searches later still no help. For what it is worth I followed this guide:  [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

Edit: Had to open port 631 0n my router, working now.

---

