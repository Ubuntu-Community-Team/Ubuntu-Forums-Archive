---
title: "Consensus on HDMI"
date: 2012-08-15
forum: System76 Support
---

### Post by zenlunatic on 2012-08-15
How is the HDMI output on the current laptops?  I was particulary thinking of using the Gazelle Professional connected to a 32" 1080i television to watch youtube documentaries.

---

### Post by 3Miro on 2012-08-15
I have Pangolin, but the previous model with Sandy Bridge. HDMI works great, I have the laptop almost constantly connected to external monitors and TV. Both sound and video work great.

I can't imagine the current Ivy Bridge laptops being worse.

---

### Post by mapman88 on 2012-08-15
I have a gazp6 running 12.04. I tried to HDMI to my tv - no joy. Is there a tutorial?

---

### Post by zenlunatic on 2012-08-15
It could be your television settings.  My TV has multiple input formats.  You have to switch to the correct input through the menu in order for your tv to listen on that port.

---

### Post by Carborundum on 2012-08-16
I regularly connect my gazp7 to my receiver, which in turn is connected to my speakers and my TV. I've never had any problem with it.

---

### Post by isantop on 2012-08-16
> **mapman88 said:**
> I have a gazp6 running 12.04. I tried to HDMI to my tv - no joy. Is there a tutorial?

Your Gazelle uses Nvidia graphics. You'd need to configure it from the "Nvidia X Server Settings" Application.

---

### Post by zenlunatic on 2012-08-16
Makes perfect sense isantop.

---

### Post by mgolden on 2012-08-17
I have (and love) a GazP6, and I regularly use it for HDMI.  The one annoying thing is that the TV does an "overscan" which you have to correct for.  There is a setting in the NVidia X Server settings (somewhat difficult to find) to deal with it.

---

### Post by Ctrl+Alt+Del on 2012-08-17
> **mgolden said:**
> I have (and love) a GazP6, and I regularly use it for HDMI.  The one annoying thing is that the TV does an "overscan" which you have to correct for.  There is a setting in the NVidia X Server settings (somewhat difficult to find) to deal with it.
or just deactivate the overscan feature on your tv :)

---

### Post by zenlunatic on 2012-08-19
I don't really expect an answer because it's more a virtualbox question.  If I get the 3720 with VT-d, will vms be able to talk directly to the hdmi-out?  I'm only asking because I'm assuming direct communication (VT-d) would allow for accpetable flash playback.

If not I assume the host Ubuntu can just enlarge virtualbox session and play through hdmi via Ubuntu host.

However I'm also pretty sure that virtualbox OSE doesn't support peripheral support.

I don't really expect system76 to answer this because apparantly hdmi works shipped, but I just thought I'd throw it out there.

Why would I want to do this?  Flash needs secure isolation.

---

### Post by isantop on 2012-08-20
> **zenlunatic said:**
> I don't really expect an answer because it's more a virtualbox question.  If I get the 3720 with VT-d, will vms be able to talk directly to the hdmi-out?  I'm only asking because I'm assuming direct communication (VT-d) would allow for accpetable flash playback.

If not I assume the host Ubuntu can just enlarge virtualbox session and play through hdmi via Ubuntu host.

However I'm also pretty sure that virtualbox OSE doesn't support peripheral support.

I don't really expect system76 to answer this because apparantly hdmi works shipped, but I just thought I'd throw it out there.

Why would I want to do this?  Flash needs secure isolation.

Nope. VMs don't have access to the physical output ports.

---

