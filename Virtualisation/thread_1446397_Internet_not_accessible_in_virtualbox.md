---
title: "Internet not accessible in virtualbox"
date: 2010-04-04
forum: Virtualisation
---

### Post by asharpham on 2010-04-04
I don't know why, but I can't "connect" to the internet when running XP in virtualbox. Neither IE nor Firefox will browse any pages - they both come up with error pages like the internet is not connected. If I go back to the other panel where Ubuntu is running, the internet is readily available. There are situations where I need to access something on the net via XP instead of Ubuntu, such as updating a piece of Windows-based software from the program itself.

---

### Post by HermanAB on 2010-04-04
Does your DHCP server work?

Try Start, Run, cmd.exe
c:\> ipconfig /all

To see what is wrong, then try ipconfig /renew

---

### Post by asharpham on 2010-04-04
Thanks HermanAB.  After running ipconfig /all and then ipconfig /renew, I got the attached result. How do I enable Local area Connection and Bluetooth in Windows. The lights on my Dell machine are both on. However, Bluetooth is not working in Ubuntu either.

I'm not sure if you'll be able to read the attachment but if not, I'll duplicate the result and copy the result as text. Basically, however, as I mentioned above, the result is that the Local Area Connection and Bluetooth are both shown as disconnected.

---

### Post by dorris on 2010-04-06
I'm unsure about bluetooth, I haven't tried it through virtualbox.
But regarding the interfaces, shutdown your vm.
right click on the container, and check the network settings.

If you want to use dhcp and be a part of your local network, you will need to change the adaptor type to a 'bridged adaptor'

Also ensure you have the right nic selected, ie ensure the virtual adaptor is linked to eth0 / wlan0 (whichever you actually use).

---

### Post by asharpham on 2010-04-07
Igot into the VB settings and made the canges you suggested. But I've run into another problem that occurred when I turned the computer on this morning. I found I couldn't connect to the wireless connection. I have all the correct details including the key but it refuses to connect. So I can't sort out the virtualbox until I fix this. I'm currently using my wife's computer to get on the net. I'm ready to reinstall Ubuntu which should overcome these problems.
 
Alan.

---

### Post by asharpham on 2010-04-07
I just realised I can't reinstall Ubuntu without destroying Windows. Any suggestions?

---

