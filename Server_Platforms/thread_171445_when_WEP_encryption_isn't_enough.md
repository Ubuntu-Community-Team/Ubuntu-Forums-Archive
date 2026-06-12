---
title: "when WEP encryption isn't enough?"
date: 2006-05-06
forum: Server Platforms
---

### Post by jingo811 on 2006-05-06
Hi I have a 802.11b connection to my router with WEP encryption.  Now I've studied up on this matter a little bit still never having implemented the techniques involved in checking for vulnerabilities.

But from reading guides on Wireless router security it seems WEP is like having no security at all compared to WPA encryption for 802.11g or something like that.
I wondered is there some thing one can do in order to bump up the security level a notch.  In addition to the WEP encryption for brief FTP, IRC, Telnet sessions?
Like using some program that makes encrypted FTP and IRC sessions, any recommendations?

---

### Post by cgjones on 2006-05-06
If your hardware supports it, you could use WPA. From what I've read, it can get kind of tricky getting in working in Linux, although I think that mainly depends on the hardware. As for encrypted protocols, use SSH and SFTP instead of Telnet and FTP. Towards the end of my Windows days, I was using wireless without any encryption, only because the only thing I was doing over the wireless was SSH'ing into my linux box.

---

### Post by jingo811 on 2006-05-06
You have to forgive me if I ask something that you might already have answered earlier.  I'm not that high-tech when it comes to IT, I only know how to troubleshoot my homenetwork for play only.

Unfortunately I'm one of those that have an old 802.11b that won't have flash capability to upgrade to WPA.  I'm forever stuck with WEP.  But that don't seem to be a problem given your SSH and SFTP answer.
Not that I'm familiar with those things, guess I have to read up on that issue in the near future.

But my laymens worry lies to be more exact in the VOIP, Skype, Ventrilo area when dealing with 802.11b routers.
If someone is familiar with using Ventrilo or Skype (which might not be available for Linux at this moment, but still...) will the SSH implementation be the thing that can level up the security?
So that my neighbors can't eavesdrop and record my VOIP conversations when using my Wireless router?

---

### Post by Jason_25 on 2006-05-06
If you just did skype or other encryted voip and ssh, no one should be able to sniff your data or listen in to your conversation.  But anything you do over the web will be sniffable.  This isn't a realistic security measure because of that, and because someone could connect to your router and hog your bandwidth.  You could put a second linux PC directly connected to the router and forward a port for web usage over SSH so it goes through the directly connected pc.  If you went that far, you might as well install a compatible wireless card in the second pc, and make it your router with WPA authentication.  Anyway, skype is available for linux.  It has some problems though.

---

### Post by jingo811 on 2006-05-07
ic sort of.
So is there a point-&-click program that one can use to encrypt VOIP traffic.  Or does Skype and Ventrilo have those encryption functions built-in already?
Or did your explaination mean that sniffing and recording live VOIP conversations is a very unlikely occurence compared to someone sniffing for passwords on the same WEP router.

I'm hoping that I won't have to touch that SSH business for my brief VOIP telephone usages.  It feels like SSH is more like a science than a simple point-&-click program.

---

### Post by Jason_25 on 2006-05-07
Not sure about other VOIP but all actual skype conversations are supposedly encrypted.  A little while ago, I made one of my pcs into a wireless 802.11b access point with hidden essid with no wireless security at all.  I just connected to it with my pocket pc running skype and blocked all ports that skype didn't need.  Maybe not the most secure but secure enough for me considering alot of  my neighbor's networks are totally unsecured.

---

### Post by jingo811 on 2006-05-07
So what you are saying with Skype's encryption alone.  For a cracker it will require them to have Skype source code in order to decrypt my private conversations on the 802.11b wireless net.

Having logged all or a big portion of my conversation traffic alone wouldn't be enough for the cracker to see what I've said earlier right, without the Skype source code?
Thus using a Free OpenSource VOIP program is not a wise choice when using old 802.11b WEP hardwares?

---

### Post by Jason_25 on 2006-05-07
That would make for an interesting argument.  But to answer your first question, they would need to break skype's encryption to listen to your conversations.

---

