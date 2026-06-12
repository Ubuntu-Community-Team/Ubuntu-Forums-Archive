---
title: "Alternate CD -&gt; Dell C610 installer bug?"
date: 2011-12-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2011-12-03
Hello All

I'm testing 12.04 on a spare partition on a Dell C610 laptop (P3, 512Mb ram, b43 wifi firmware needed).

[LIST]
[*]Installed ok from Alternate CD(cd drive only) without network connection
[*]Reboot stopped at the 'Ubuntu' splash
[*]Rebooted into recovery: text messages stopped at the b43 firmware warning - in 11.10 this is just skipped and proceeds to desktop with 'firmware' warning in Network indicator menu
[*]Rebooted into network root recovery and manually started network with cable connection, updated and installed the firmware-b43-installer package
[*]Rebooted and now in graphical desktop with wifi working
[/LIST]

Just so anyone else with b43 wifi knows. Is this difference in behaviour from 11.10 installer just one of those things with an alpha CD or is it worth reporting?

PS: I'm testing 12.04 on this hardware that is below Ubuntu suggested spec in the spirit of the discussion here: [http://ubuntuforums.org/showpost.php?p=11507772&postcount=8](http://ubuntuforums.org/showpost.php?p=11507772&postcount=8)

---

