---
title: "Dual booting XP, can't get internet to work"
date: 2010-06-20
forum: System76 Support
---

### Post by chez17 on 2010-06-20
Hey guys, I'm trying to dual boot XP and I can't get the internet to work inside windows. The network 'wizard' says it can't even find my hardware which I think means I have to install the drivers. Where do I go about finding these drivers?

I have a pangolin model panp4n. Thanks so much for your help.

---

### Post by JDorfler on 2010-06-20
Unfortunately WinXP and Ubuntu may be using different firmware drivers for your hardware.  One thing you may try is to instead of just rebooting to enter into the different OSes is to completely shut down, Then turn the PC back on to get into the desired OS.

---

### Post by chez17 on 2010-06-20
Maybe I wasn't clear enough, my bad. Everything works fine in Ubuntu, but when I boot into XP I can not use the internet. It can not detect any of the hardware. When I go into device manager the Ethernet Controller and the Network Controller are listed in the 'Other Devices' section. That's why I'm pretty sure I just need to get the proper drivers. I have no idea where to get those, where do I look?

---

### Post by JDorfler on 2010-06-20
Ah, I'm assuming the manufacturer of your PC is System 76.  If so, what PC did you buy from them.  If it's a laptop you may want to try [www.sagernotebook.com](www.sagernotebook.com) and see if you can find your model there and download the proper drivers via Ubuntu.  Then save the files to your XP partition for install.

On a side note, I prefer Sager over 76 due to they will actually ship their products to APO addresses.  76 does not and refuses to answer any emails or posts about the situation.

---

### Post by wilee-nilee on 2010-06-20
> **chez17 said:**
> Maybe I wasn't clear enough, my bad. Everything works fine in Ubuntu, but when I boot into XP I can not use the internet. It can not detect any of the hardware. When I go into device manager the Ethernet Controller and the Network Controller are listed in the 'Other Devices' section. That's why I'm pretty sure I just need to get the proper drivers. I have no idea where to get those, where do I look?

If this is a true dual boot, not a virtual the drivers should be available with a windows update. Probably even available with a virtual, you need to go to the MS update.

---

### Post by chez17 on 2010-06-20
@JDorfler, I must say I find it in bad taste that you are crawling a support forum with the sole purpose of advertising for another company. You clearly didn't read my first or second post as the questions you asked in yours were already answered. I am more than pleased with my 76 am not searching for another computer right now.

@Wilee, yes, this is a true dual boot. Not vertualization. I have borrowed a USB wireless thing from a friend have been able to update my computer up to SP 3 and I still can't use the acutal hardware.

Windows Update has not solved the problem, anyone know where I can get the drivers for my mahcine? (Pangolin, panp4n)

---

### Post by wilee-nilee on 2010-06-20
Run this in the terminal to identify the network card.
```
lspci
```

---

### Post by bill516 on 2010-06-20
Altogether odd.  I have a PanP4 and material packed with it suggested a machine originally built to run Vista.  In any event LSPCI as suggested by wilee-nilee should return an Intel 5100 wireless and a Realtec RTL 8111 ethernet card.  These are mainstream devices XP should see with no problem.  Apparently it does see them but lacks drivers.

I would go out to the Intel and Realtec sites and see if XP drivers for the devices are listed there.  If they are there they can be downloaded and installed.

No drivers there?  Hard to believe but I suppose it is possible. A revoltin' development if that is true!

---

### Post by wilee-nilee on 2010-06-20
> **bill516 said:**
> Altogether odd.  I have a PanP4 and material packed with it suggested a machine originally built to run Vista.  In any event LSPCI as suggested by wilee-nilee should return an Intel 5100 wireless and a Realtec RTL 8111 ethernet card.  These are mainstream devices XP should see with no problem.  Apparently it does see them but lacks drivers.

I would go out to the Intel and Realtec sites and see if XP drivers for the devices are listed there.  If they are there they can be downloaded and installed.

No drivers there?  Hard to believe but I suppose it is possible. A revoltin' development if that is true!

I suspect that if the OP used the ms update,
[http://www.update.microsoft.com/microsoftupdate/v6/default.aspx?ln=en-us](http://www.update.microsoft.com/microsoftupdate/v6/default.aspx?ln=en-us)
and clicked on custom updates and looked in the sidebar the drivers are offered.

---

### Post by chez17 on 2010-06-20
That command worked perfectly, thank you. I could see what I needed and got the proper drivers for my wireless card and everything works great.

---

### Post by wilee-nilee on 2010-06-20
> **chez17 said:**
> That command worked perfectly, thank you. I could see what I needed and got the proper drivers for my wireless card and everything works great.

Are you saying that the drivers were in the ms update.
If so some don't know about using the custom and looking for drivers.

---

### Post by isantop on 2010-06-22
We do provide Windows drivers for most of our systems through our Knowledge Base article for your system. We only provide drivers for windows versions listed there. You can go to [http://knowledge76.com/index.php/Category:Systems](http://knowledge76.com/index.php/Category:Systems) to select which system you have.

---

