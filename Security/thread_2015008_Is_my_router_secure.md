---
title: "Is my router secure?"
date: 2012-07-02
forum: Security
---

### Post by jonnyboysmithy on 2012-07-02
My ISP was blocking ports. I asked them to unblock the ports so now we have set all of the port blocking handling to the router we have here at home.
So my question is, is my system secure? Anything I should be aware of? 
And if my computer isn't behind any sort of firewall, just straight connected to the Internet (demilitarized zone?) is it secure? does it impose any security risks? :confused:
I'm running ubuntu 12.04 and the others in the house are using windows 7
Btw I have uPnP enabled.
Sorry for being such a noob.. :lolflag:

---

### Post by ratcheer on 2012-07-02
The best situation would be to have a firewall on your router. Even if you do, it still requires knowledge to set it up, properly.

If you do not have a firewall on your router, then you should have one on every LAN host.

This is my opinion and I am sure you will get differing opinions from others.

Tim

---

### Post by Cheesehead on 2012-07-02
> **jonnyboysmithy said:**
> we have set all of the port blocking handling to the router we have here at home.
So my question is, is my system secure?

Depends on the router, and how you have it set up.
Is it store bought?
Have you customized it?
Have you changed the settings?
Is it home built?

---

### Post by sammiev on 2012-07-02
You can test your router [HERE]("https://www.grc.com/x/ne.dll?bh0bkyd2"). :)

---

### Post by Killer Jacker on 2012-07-03
> **jonnyboysmithy said:**
>  So my question is, is my system secure? Anything I should be aware of? 


Generally, the default settings of common routers are safely. There is no waste of time in give some check to the security setting.

I think that in main way, you must worry about **your** router in particular (brand/model) and search for possible bugs and security holes. Of course, always having the latest firmware.

---

### Post by lisati on 2012-07-03
One piece of wisdom I recently read (citation needed) is to turn off uPNP on publicly-facing routers if you don't need it.

---

### Post by spynappels on 2012-07-03
> **lisati said:**
> One piece of wisdom I recently read (citation needed) is to turn off uPNP on publicly-facing routers if you don't need it.

+1 to this, UPNP has been instrumental in opening the built in VNC server to the internet on at least 2 systems I've seen that have been owned. While I recommend not running the VNC server if it is not absolutely required, UPNP can definitely add holes to your security.

---

### Post by Grenage on 2012-07-03
Yup, uPnP is not great for security; It's 'OK' if you vouch for everything that's going on internally.

Unfortunately, many things are designed with uPnP in mind, and it _can_ make things much more convenient - there's always a trade-off.  I leave it on, because our home router handles connection from many, many things, and life is too short.

---

### Post by jonnyboysmithy on 2012-07-03
Ok, so I may want to turn off the upnp feature. I hear that this may cause problems with network printers? We have one. Anything else that it may disturb?
I updated the firmware on the router. I'll disable it for now. If I get any problems I might enable it again.
Thank you all very much for your help :D

---

### Post by Grenage on 2012-07-03
> **jonnyboysmithy said:**
> Ok, so I may want to turn off the upnp feature. I hear that this may cause problems with network printers? We have one. Anything else that it may disturb?

It will disturb anything which uses uPnP to automatically forward ports, which for many people, is nothing much at all.  It won't cause any problems unless you're accessing your printer externally, which I imagine you are not.  Torrent client and VNC servers will generally use uPnP; IM clients *may* use them.

Bottom line: if something needs uPnP, you can manually create a rule to forward the ports.

---

### Post by jonnyboysmithy on 2012-07-03
> **Grenage said:**
> It will disturb anything which uses uPnP to automatically forward ports, which for many people, is nothing much at all.  It won't cause any problems unless you're accessing your printer externally, which I imagine you are not.  Torrent client and VNC servers will generally use uPnP; IM clients *may* use them.

**Bottom line: if something needs uPnP, you can manually create a rule to forward the **ports.
In that case I shouldn't have any problems. Thanks!:KS

---

### Post by spynappels on 2012-07-03
> **Grenage said:**
> Bottom line: if something needs uPnP, you can manually create a rule to forward the ports.

+1 to this, from memory, I had to do this for Skype at one site, but I can't remember the details, but do check things like that as Grenage said.

---

### Post by Killer Jacker on 2012-07-03
> **spynappels said:**
> +1 to this, from memory, I had to do this for Skype at one site, but I can't remember the details, but do check things like that as Grenage said.

yeah... +1 too...
every port fowarding MUST be doing in the router setup, not using uPnP

---

### Post by jonnyboysmithy on 2012-07-05
I didn't need to setup any ports manually (uPnP is off) and skype worked no problem. Yay!! :D

---

### Post by Ashtechsmith on 2012-07-07
WPA PSK and WPA Personal is the same. They just call the same thing with different names.

[INDENT]Why is the process so convoluted ? It's a very simple request, you'd think it would be an obvious Option like

Make Network Secure-Enabled ? yes/no;

Choose Password[/INDENT]

Once  you have chosen WPA with preshared key it is that simple. You just  enter the passphrase. Historically you just have WEP as well. That's why  there is WEP as well. And for larger enterprise setups you use RADIUS  server authentication. That's why you find "WPA Enterprise" or "WPA  RADIUS" (which are the same thing again). If you used WEP it would be  more complicated.

Obviously your computer gets kicked out the  moment you set the WPA passphrase because your computer does not know  the passphrase and with passphrase in place only computers which know  the passphrase are supposed to connect. You have to reconnect to your  protected network. Remove the network from the list of preferred  networks. Then search for available networks again, pick your network  and the computer should automatically ask for the passphrase and then  you are in.

---

### Post by samiux on 2012-07-08
> **jonnyboysmithy said:**
> My ISP was blocking ports. I asked them to unblock the ports so now we have set all of the port blocking handling to the router we have here at home.
So my question is, is my system secure? Anything I should be aware of? 
And if my computer isn't behind any sort of firewall, just straight connected to the Internet (demilitarized zone?) is it secure? does it impose any security risks? :confused:
I'm running ubuntu 12.04 and the others in the house are using windows 7
Btw I have uPnP enabled.
Sorry for being such a noob.. :lolflag:

I would like to tell you that there are some tools out there for pwning a router.  This [video]("http://www.youtube.com/watch?v=SL4UoDFXH2I") is talking about a tool namely "rotuerpwn".

Samiux

---

### Post by needhelppeeps on 2012-07-09
Turnoff upnp, restrict router management from the outside world and wifi and lock it down to a single physical port if possible, place the firewall in a locked room or rack, turn off any ports that you don't need open, enable IPS/AV features, don't try to run public services from your internal network.

---

