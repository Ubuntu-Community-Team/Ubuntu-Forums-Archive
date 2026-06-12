---
title: "WinXP in Virtualbox won't connect to my wireless modem"
date: 2010-06-27
forum: Virtualisation
---

### Post by asharpham on 2010-06-27
When I open WinXP in Virtualbox, there is no connection to my wireless modem. There used to be a connection but I think I must have changed a setting and now the computer no longer sees the modem from WinXP. There is no problem from Ubuntu. I can move back to Ubuntu and have full internet access and no connection problem.

Can someone advise what settings need to be in place for me to access the modem (and Internet) while using Windows in virtualbox? I'm using Ubuntu 9.10.

---

### Post by Sonsum on 2010-06-27
I believe a virtual machine sees the internet as just given by the host machine. So if the host machine has internet, so should the virtual machine. 

Does the internet work in Ubuntu while the XP virtual machine is running?

---

### Post by asharpham on 2010-06-28
Yes it does. It all used to work normally but it's been a while now since a connection to the modem could be established via Windows in Virtualbox. While connected to the Internet in Ubuntu, I can open WinXP in Virtualbox and not be able to access the modem via its ip address.

---

### Post by stlsaint on 2010-06-29
Have you checked your settings in xp. I doubt that ubuntu is purposefully blocking internet from the vm unless you specify it to. If you plug up a ethernet cable to your wirelss router and open up the winxp vm do you have internet. Just some ways you could troubleshoot:
1. Check windows connection settings!
       a. Make sure driver is installed/updated
2. Use ethernet cable to test connection in vm.

---

