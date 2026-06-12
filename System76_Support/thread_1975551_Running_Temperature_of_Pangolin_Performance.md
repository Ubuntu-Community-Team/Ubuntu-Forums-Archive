---
title: "Running Temperature of Pangolin Performance?"
date: 2012-05-07
forum: System76 Support
---

### Post by neomantic on 2012-05-07
Hi,

I was wondering what the usual running temperature of a Pangoline Performance is.  Mine new one is currently running at 65 Celsius. If I run a script as I'm developing - something trivial - it jumps to 75 Celsius quite quickly, and the fan begins to roar like I'm landing a plane.

This seems a bit warm for me...does anyone have the same experiences?

---

### Post by isantop on 2012-05-07
> **neomantic said:**
> Hi,

I was wondering what the usual running temperature of a Pangoline Performance is.  Mine new one is currently running at 65 Celsius. If I run a script as I'm developing - something trivial - it jumps to 75 Celsius quite quickly, and the fan begins to roar like I'm landing a plane.

This seems a bit warm for me...does anyone have the same experiences?

That seems okay to me. Just make sure that for a given load, you don't see the temps go up over time, and that if you reduce the load, it goes down.

---

### Post by brdmn on 2012-05-10
> **neomantic said:**
> I was wondering what the usual running temperature of a Pangoline Performance is.  Mine new one is currently running at 65 Celsius. If I run a script as I'm developing - something trivial - it jumps to 75 Celsius quite quickly, and the fan begins to roar like I'm landing a plane.

This is interesting, because I've never been sure what constitutes a "normal" operating temperature.  My new lemu4 generally seems to run at in the mid to high 50's C, which is pretty similar to other computers I've owned.  The exhaust feels hot, but the rest of the laptop feels fine.  I'd be curious to hear what temperatures others are seeing under various conditions.

---

### Post by mc1brew on 2012-05-11
I just got a Pangolin the other day.  I'm not doing anything terribly intense right now.  I currently have open Eclipse, Terminal, Chrome (8 tabs, no streaming), System Settings, and System Monitor.  My system is 53C/134.6F.

---

### Post by brdmn on 2012-05-15
Now that I've had my lemu4 for a week or so, I'm noticing the trackpad is hot to the touch and not so comfortable to use.  Sensors shows core temps of 55 C, which seems acceptable according to what I see posted here.

Is there anything I can do to lower the temp?  Is there a bios setting for running the fan at a higher rpm?  Doesn't seem to be running at all at the moment.

---

### Post by isantop on 2012-05-16
> **brdmn said:**
> Now that I've had my lemu4 for a week or so, I'm noticing the trackpad is hot to the touch and not so comfortable to use.  Sensors shows core temps of 55 C, which seems acceptable according to what I see posted here.

Is there anything I can do to lower the temp?  Is there a bios setting for running the fan at a higher rpm?  Doesn't seem to be running at all at the moment.

It should be running (the firmware shouldn't let it completely stop). That said, if you push the system hard, can you get it to spin up? There could still be some sort of problem. We haven't seen any issues with heat on the Lemurs yet.

---

### Post by brdmn on 2012-05-16
> **isantop said:**
> It should be running (the firmware shouldn't let it completely stop). That said, if you push the system hard, can you get it to spin up? There could still be some sort of problem. We haven't seen any issues with heat on the Lemurs yet.

Fan's definitely working... it spins high when I get the CPU load up.  I actually posted a support request for this, and found out about Fn+1.  Except that it doesn't work for me.  Is there anything different about Lemu4 that prevents Fn+1 from throttling the fan?

I should reiterate that the heat issue is not catastrophic, and lm-sensors is reporting temps in the 50's.  I'm just looking to see if I can get the fan to a little higher rpm so the trackpad is more comfortable to use.

---

### Post by isantop on 2012-05-16
> **brdmn said:**
> Fan's definitely working... it spins high when I get the CPU load up.  I actually posted a support request for this, and found out about Fn+1.  Except that it doesn't work for me.  Is there anything different about Lemu4 that prevents Fn+1 from throttling the fan?

I should reiterate that the heat issue is not catastrophic, and lm-sensors is reporting temps in the 50's.  I'm just looking to see if I can get the fan to a little higher rpm so the trackpad is more comfortable to use.

Yeah, the secret key is only programmed into the SerP7 Serval and GazP6 Gazelle so far. The mainstream systems don't have that.

---

### Post by brdmn on 2012-05-17
> **isantop said:**
> Yeah, the secret key is only programmed into the SerP7 Serval and GazP6 Gazelle so far. The mainstream systems don't have that.

Does "so far" mean there is some hope the lemu4 will get this feature in the future via a BIOS update?  It would be really useful to be able to ramp up the rpm a bit--not necessarily to max, but something higher than the default.

---

### Post by isantop on 2012-05-17
> **brdmn said:**
> Does "so far" mean there is some hope the lemu4 will get this feature in the future via a BIOS update?  It would be really useful to be able to ramp up the rpm a bit--not necessarily to max, but something higher than the default.

No, it's "So far, those are the only models that have it". We may see it in future models, but this will not be coming to the Lemur.

---

