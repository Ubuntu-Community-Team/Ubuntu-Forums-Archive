---
title: "wineASIO, PulseAudio and JACK"
date: 2013-09-24
forum: Ubuntu Studio
---

### Post by paulo_sousa2 on 2013-09-24
Hello.

Once I found out I can now run FL Studio 11 flawlessly on Ubuntu, I jumped from Windows.

I managed to set up FL, WineASIO loads up and sometimes shows up immediately on JACK Audio Connection Kit, sometimes I need to stop it, start it, mess in FL, and FL shows up again.

FL is signaling low latency audio, just like it happens with ASIO4ALL. However, I can't hear it.

I have PulseAudio, wine 1.4, and am using jackd1, I believe. I'm running UbuntuStudio 13.04 with KXStudios repos added. I installed wineasio through those. Cadence used to work, now it can't, says jackdbus is not available. Qjackctl seems to be fine, though.

My two questions are:
1 - FL vanishes from Qjackctl as soon as it loses focus. Can I fix that?
2 - [SOLVED]How can I hear JACK?

Turns out I had the wrong soundboard selected, didn't see the arrow. My actual soundcard is now selected and FL chirped! The first problem still stands. I've noticed that while on the splash screen, FL shows up and vanishes right before the GUI loads. Could it be the same focus thing? FL has an auto close device option but it's off.

Thank you,
Paulo

---

### Post by byteknightrepairs on 2014-01-14
Having the same problems buddy! Any progress since this happened?

---

### Post by su:bhatta on 2014-01-15
> **byteknightrepairs said:**
> Having the same problems buddy! Any progress since this happened?

You have to elaborate a little more about your problem. 

Paulo had two concerns in the thread. 
If it is regarding Jack, then all you have to do is select the right hardware from the dropdown list that comes in Jack's settingspage, Interface option.

Please give us detailed information regarding the problem you are facing.

---

