---
title: "daru2 + Gutsy: WPA connection frequently drops"
date: 2008-01-15
forum: System76 Support
---

### Post by Mr. Farlops on 2008-01-15
So I've running with Gutsy for about 2 months now and, aside from [a work around for the screen dimming issue]("http://ubuntuforums.org/showthread.php?t=587276"), things have  been going quite well.

But I've recently discovered, after I set my wireless network to WPA, that nm-applet would frequently drop my connection. Sometimes it would reset and find it again but often it would just drop it and never get it back even after specifying my SSID and password multiple times. Restarting my system seems to restore it but then often it just drops it again.

My network does broadcast its SSID and it's just a basic personal mode WPA network with a PSK. I did a little research on my actiontec gateway but couldn't really find anything wrong with it.

I tried changing its broadcast channel and moving my gateway around to clear any interference issues (I have no wireless phones, electric fans or even mobile phones in my apartment but, I do have a lot of neighbors with wireless networks.) but, this didn't really help.

Is it just that WPA is still problematic for ipw3945 in Gutsy? Should I just fall back to WEP?

Any advice would be helpful!

---

### Post by patrickfromspain on 2008-01-15
you could try wicd:

[http://downloads.sourceforge.net/wicd/wicd_1.4.1-all.deb?modtime=1199416037&big_mirror=0](http://downloads.sourceforge.net/wicd/wicd_1.4.1-all.deb?modtime=1199416037&big_mirror=0)

---

### Post by Mr. Farlops on 2008-01-16
Patrick,

Well, I tried that and it didn't really help and it didn't mesh as well with my other gnome network gadgets as I would have liked.

Thanks for the suggestion but I've just fallen back to nm-applet and using WEP to protect my wireless network. It's not as secure but it is more stable with my System76 hardware and Gutsy.

---

### Post by thomasaaron on 2008-01-17
I did a little more googling on this, and there seems to be a mix out there of people who have NO problems with WPA and people who complain that it drops their connection.

Can you give more detail about the wireless settings both on your router and on Network Manager? I've found that Network Manager is supremely finicky with settings.

If they are not identical, you can end up with a weak or unstable signal.

---

### Post by Mr. Farlops on 2008-01-19
Thomas,

My wireless settings in the gateway are as follows:

My gateway is an Actiontec gt704-wg. I purchased this to reduce wiring and clutter, consolidating 3 boxes into one. And it was compatible with my ISP and DSL provider.

I live in an apartment in a dense urban neighborhood with a lot of techy neighbors. My wireless card sees at least 10 SSIDs when I check it. 3 of which I suspect, based on signal strength, are in apartments close to mine. Most of these networks are protected by variations of WEP.

My SSID is set to broadcast. The gateway is transceiving on channel 11. (I've yet to systematically try different channels to see if interference reduces. More on this in a moment.) My group key interval is 60. (I don't really know what that's for, some sort of key renewal timeout or something?) I'm using the basic PSK string option since I don't really know how to set up and probably don't need server-level WPA. I do nothing with MAC authentication, all these fields are left entirely blank. The gateway is set to communicate on both 802.11b and 802.11g.

Now, I've set my card to use roaming mode in nm-applet and generally this works just fine. If I use nm-applet to hook to my network manually, I set security to WPA personal, specify my key and then leave the type as automatic, figuring things are smart enough to decide between TKIP or AES. Sometimes this works but it is tedious to have to keep manually specifying things every 20 or so minutes just to stay connected. 

When I start a session, nm-applet starts with a strong signal from my gateway but then this sporadically diminishes or jumps up and down and then just drops altogether.

But sometimes Network Manager does hang. I notice this sometimes when I need to shut down or restart my machine. In the case X seems to exit normally but I catch this warning message from the system:

NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.

The system seems to have killed all other processes and unmounted everything but when I see this message things just hang in the shut down process. I'm sometimes forced to use the three-fingered salute, or worse the power button, to shut the system down. 

nm-applet has never had any trouble recognizing the DARU2 wireless card and usually does just fine with wireless connections in other locations (Although most of these locations were open networks or using some form of WEP and they were locations where the density of other networks was lower.). I agree with you, that I don't think it's really a problem with ipw3945 driving daru2's card right. I think it must something as prosaic and maddening as interference. 

I've moved my gateway around a bit but I haven't systematically checked each channel to see which communicates with the least interference from my neighbors.

By the way, I want make clear that this in no way diminishes my high opinion of System76's hardware and great technical support. I was just looking for tips. As I said for some weird reason, when I set my network back to WEP things just seem to work better. Why, I don't know.

---

### Post by warrior24 on 2008-01-19
Could you not just turn mac filtering on?

---

### Post by knattlhuber on 2008-01-19
Mr. Farlops,
I had similar experiences with my D-Link WUA 1340. After blacklisting the open source driver for my chipset (rt73usb) and installing the Windows driver through ndiswrapper, WPA2 worked flawlessly. Never had any connection drops again.
Not sure which card/driver you are using, but ndiswrapper might fix your problem.

This tutorial helped me a lot configuring my wireless security options:
[http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless+security](http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless+security)

---

### Post by Mr. Farlops on 2008-01-19
Warrior,

Thanks for the advice but I don't think that's relevent. 

I don't turn MAC filtering on because I don't want to remember or shut out the MAC addresses of my friends who bring their laptops over to me house.

I never really saw the utility of MAC filtering as a security measure since MAC addresses are easily spoofed. I leave it off on any small network I set up.

---

### Post by Mr. Farlops on 2008-01-19
Knatt,

Well perhaps that might work but I'd rather avoid changing my card drivers if I can. I'd rather stick with the System76 recommend settings and configurations. They work well enough in most situations.

I did a little experimentation with WICD a few days ago and it paritally worked but I decided to stick with Network Manager since it meshes better with rest of the gadgets in Ubuntu's GUI.

But I'll keep your suggestion in mind over the weekend. I might play around with it--after backing up just in case the experimentation borks my system badly.

---

### Post by thomasaaron on 2008-02-11
Try the fix in this bug report.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/140422](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/140422)

---

