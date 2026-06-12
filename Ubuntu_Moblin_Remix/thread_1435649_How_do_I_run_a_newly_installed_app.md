---
title: "How do I run a newly installed app?"
date: 2010-03-21
forum: Ubuntu Moblin Remix
---

### Post by BusaDave9 on 2010-03-21
I have Ubuntu Moblin.
 I downloaded and installed an application with the following command:
 aptitude -y install network-manager-vpnc vpnc
 Now I can't figure out how to run it. It doesn't show up in my applications even if I search for it.  
 When I search for it in the file system I find the many files that I installed. But nothing happens when I double-click on them. Maybe I haven't yet found the correct file to double-click.

---

### Post by owenll on 2010-03-27
Have you tried running **vpnc** or **sudo vpnc** in a terminal?

---

### Post by BusaDave9 on 2010-03-27
Progress! Thanks. I can run it as a command line app. 
To run it in a GUI I found I needed Gnome's Network Manager. I installed it and set up a VPN connection. Now I am trying to figure out how to initiate a vpn session. I was expecting a "connect" button. They say:

"To connect to the VPN, simply select the VPN name you entered via the NetworkManager Gnome applet under VPN Connections, and it will connect automatically."

I don't get that. I select the vpn connection I want. It is merely highligted at this point. Now it is supposed to connect automatically? ? ?     Well it doesn't ask for my password. 
I guess I will just keep messing with it.
Thanks again.

---

### Post by BusaDave9 on 2010-04-05
So I installed Gnome's Network Manager. The VPN connection isn't working in the Network Manager. As a matter of fact no connection is working according to the Network Manager. when I open Network Manager it says my ethernet connections have never been used. Of course I use my Ethernet connections whenever I get on the Internet such as now. Ubuntu Moblin has it's own networks applet. There it correctly says my ethernet is connected. Is there someplace I should specify that I want to use Gnome's Network Manager instead of Ubuntu Moblin's Networks applet?

---

