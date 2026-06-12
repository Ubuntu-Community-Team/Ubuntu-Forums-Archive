---
title: "No Internet with 7.04 (CE) upgrade"
date: 2007-04-23
forum: Ubuntu Christian Edition
---

### Post by Huggy on 2007-04-23
I decided to click upgrade to 7.04 in my update manager. I am currently running ubuntu CE 6.10. When it finished upgrading. It solved many of my current problems...mounting sata drives, getting my graphics and sound cards to work, etc... It just had one problem. No internet...thus no way to surf the web to learn how to fix it. So I have re-installed ubuntu 6.10 and am looking for reasons as to why it didn't work. I am running regular cable internet. Is this a common bug in 7.04 because I couldn't find the bug chart.

---

### Post by mysticrider92 on 2007-04-23
Dansguardian could have been messed up in the upgrade. If you decide to try it again, open the Dansguardian GUI and click the button for disable Dansguardian and maybe unlock firefox proxy settings. That *should* fix the problem. Feisty seems to have very good support for network cards, especially wired ones. Once you get internet back, try checking for a 7.04 version of Danguardian or just wait until CE 7.04 is released (which should be soon).

---

### Post by chris308 on 2007-04-23
I don't have this problem after my upgrade, but I no longer have a working Dans Guardian proxy.  It seems the upgrade broke Dans Guardian and I see tinyproxy isn't running as well.  So I can get my internet working, but no  filtering is taking place.  It's not a big deal for me since this is just a test box running in Vmware.  I guess I'll just wait for Jeremy to finish the new version and reinstall.

BTW, I have tried to uninstall Dans Guardian, but it fails due to breaking other packages so I can't try a reinstallation to fix things.

Chris

---

### Post by Huggy on 2007-04-24
I had no internet even with Dansgaurdian off. No upgrade package worked, no synaptic, no add/remove. Nothing with internet works. It kinda stumps me.

---

### Post by mysticrider92 on 2007-04-24
Try opening System>Administration>Networking and check the settings for whatever network adapter you use (wireless, wired, modem). Your ISP might require settings that got changed with the upgrade. If you use DHCP, that probably won't help, but its worth a try. Also if you do use DHCP, try typing 'ifconfig' in a terminal. Put the IP address, gateway, and DNS server in the Networking window as static and that might solve it.

---

### Post by cjm5229 on 2007-04-24
I tried that a couple of weeks ago while Feisty was still in Beta. It does wipe out Dansguardian, but the problem with the internet is probably the proxy settings in Firefox. I noticed that Firefox would not allow me to change the settings either. I installed Opera and it worked, so I installed a standalone version of Firefox, and it worked also.  I did finally just reinstall everything because the Dansguardian issue was also giving me problems with synaptic. I suggest waiting for CE 3.0.

---

