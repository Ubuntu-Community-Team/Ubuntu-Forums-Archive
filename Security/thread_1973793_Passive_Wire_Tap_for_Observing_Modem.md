---
title: "Passive Wire Tap for Observing Modem"
date: 2012-05-05
forum: Security
---

### Post by SparTacux on 2012-05-05
If a modem router has been compromised - is there a way to observe the traffic out of the modem onto the internet.  Wireshark can observe traffic inside the LAN but I'm looking for some sort of wire tap to observe internet traffic out. 

Can a computer be attached to the ISDN phone-line and  listen to traffic without it being part of your network and stay undetected - ie act passively.  Just curious.

---

### Post by HermanAB on 2012-05-05
You can probably do it with tee, which is a T-junction for devices.

---

### Post by SparTacux on 2012-05-05
I should have mentioned this was an ADSL line that I wanted to listen in on. The technology is a wee bit different than  ISDN. I presume it can be wire tapped with the right equipment?

---

### Post by Cheesemill on 2012-05-06
You can get devices such as [this]("http://www.tracespan.com/2_2LI%20Monitoring.html"), but they're not available to the general public for the simple reason that they can be placed anywhere on the copper wire between the target and the telephone exchange, including outside the premises you wish to monitor. There would be nothing to stop you going around attaching it to any phone line you wanted.

---

### Post by SparTacux on 2012-05-06
> **Cheesemill said:**
> You can get devices such as [this]("http://www.tracespan.com/2_2LI%20Monitoring.html"), but they're not available to the general public for the simple reason that they can be placed anywhere on the copper wire between the target and the telephone exchange, including outside the premises you wish to monitor. There would be nothing to stop you going around attaching it to any phone line you wanted.

Yeah that looks like the gadget for the job - Nice one. 
It doesn't say how much it costs though. I bet it ain't cheap.

Legit uses could be analysis of  your own network traffic especially after a suspect dodgy modem firmware update. You just can't trust everything you download these days. I was hoping  for a cheaper PC solution. The Good News is that it can be done.  

Thanks Again.

---

### Post by CharlesA on 2012-05-06
> **SparTacux said:**
> 
Legit uses could be analysis of  your own network traffic especially after a suspect dodgy modem firmware update. You just can't trust everything you download these days. I was hoping  for a cheaper PC solution. The Good News is that it can be done.  

Thanks Again.

Define "dodgy." If you downloaded an update from the manufacture's website, you'd be fine.

---

### Post by OpSecShellshock on 2012-05-06
Is the modem yours or your ISP's? If it's theirs then they might be able to support suspicious traffic from their side. That doesn't help you do your own proactive analysis, but may help in the case of a possible incident on your home network.

---

### Post by SparTacux on 2012-05-06
> **CharlesA said:**
> Define &quot;dodgy.&quot; If you downloaded an update from the manufacture's website, you'd be fine.

 It's an hypothetical scenario.  HTTP connections and no checksum provided by modem manufacturer is a recipe for disaster imo.  Also take the example of the defence industry buying branded routers made in China - are you going to trust how they work or can you check them out and make sure their are no backdoors and make certain that they are ok. There's no way to tell unless you can analise that equipment.  Hacking modems is possible and their security and functioning may need investigating.

---

