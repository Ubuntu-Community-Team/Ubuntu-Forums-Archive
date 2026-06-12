---
title: "Rakarrack not working 24 hours after installation"
date: 2013-05-28
forum: Ubuntu Studio
---

### Post by rva1945 on 2013-05-28
Hi:

I installed (on Linux Ubuntu 12.04) Rakarrack yesterday, it worked like a charm, even with the electric guitar directly plugged into the mic input.

Now when I want to run it, I get:

Cannot make a jack client, is jackd running?

QjackClt is already installed, but seems as if i now have to start it prior to running Rakarrack. Not bad, but I always get this when starting Qjackctl (even before installing Rakarrack):

D_BUS:SetParameterValue('driver:outchannels','1')
Parameter value type mismatch: was ex&#7765;ecting 'i' got 'u' (org.jackaudio.error.InvalidArgs).

I click on Cancel, and QjackClt starts anyway. Then I run Rakarrack but the sounds are distorted, I mean, like saturated, no way playing with the input level in sound configuration, it is saturated or nothing. I tried turning the effects off for a clean sound, to no avail.

I had installed Guitarix in the past, it never worked.

Any help?

Thanks

---

### Post by jejeman on 2013-05-29
Disable Dbus in Qjackctl setup.

Yes, you need always to first start JACK, and then rakarrack.

---

### Post by rva1945 on 2013-05-29
But I couldn't access the setup window in Qjackclt, it crashed. I had to kill it from Terminal. But now, after deinstalling jack and rakarrak, I installed all again (previously deleting a .con file whose name now I can't remember, I'm at the office now) and now everything is working.

Thanks

---

### Post by rva1945 on 2013-05-29
> **jejeman said:**
> Disable Dbus in Qjackctl setup.

Yes, you need always to first start JACK, and then rakarrack.

I have this problem: Rakarrack seems to send audio to one channel (sometimes right, sometimes left), not both. I built a mono to stereo adapter to plug the guitar into the input jack, and when I run Video Lan (VLC) and open the audio capture device (hw:0,0) the guitar comes through both channels.

Is it an issue with Rakarrack?

---

### Post by rva1945 on 2013-05-29
Nowe How to disable Dbus? I couldn't find that option in Setup.

---

### Post by zequence on 2013-05-30
Under the tab "misc", "Enable Dbus interface".

When enabled, qjackctl will start jackdbus. When disabled, qjackctl will start jackd.

---

