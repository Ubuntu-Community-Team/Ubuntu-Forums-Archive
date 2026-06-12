---
title: "How fast does your laptop wake up from suspend mode?"
date: 2010-08-23
forum: The Cafe
---

### Post by spupy on 2010-08-23
When I put my laptop to sleep (suspend) mode it takes something like 8 seconds to go to sleep, and around 8 to wake up again. Perhaps these facts are justified by the fact that the laptop is a netbook (1,6GHz Atom, Nvidia Ion, 5400RPM HDD, 1GB RAM).

How fast does your laptop sleep/resume? Please also post the relevant hardware components of your configuration (though I'm not sure which components are really relevant).

Also, does anyone know why Macbooks sleep/wake up so *fast*?It's around a second, 2 at most, not sure how fast exactly, but it feels almost instant. How do they do it? Is it a special feature of the hardware/OS or just the machine is good enough (I haven't seen many laptops do the sleep thing, so maybe that's the reason)?

---

### Post by Rahbee Kannuhn on 2010-08-23
Not sure, I press the wake button, HDD lights up, I look out the window a moment, or at my cell phone, look back at the laptop, enter my password, and I'm back.

---

### Post by ~Aquatic on 2010-08-23
When using 'pmi action suspend' it takes 2 seconds to suspend and 1 second to start again for me. But If I'll use 'Suspend' from the shut down menu, it takes 3 seconds to suspend and 5 seconds to get to the password dialog.

---

### Post by matthewbpt on 2010-08-23
My netbook takes about 5 seconds to sleep, and about 3 or 4 seconds to wake up from sleep. I have am EeePC 901, similar specs to yours, but mine has intel graphics and an SSD. I've read that SSD makes computers boot faster, I don't know if this would have an effect on suspend. I think it may have more to do with the nvidia graphics. Are you using the proprietary or open source driver. The proprietary driver could cause it to resume slower, but it also gives you much better graphics performance and power management (I think) than the open source driver so I'd say the pros and cons point in favour of the proprietary driver until the open source driver has matured more.

---

### Post by Sporkman on 2010-08-23
4 times out of 5, my laptop wakes up after about 5 seconds or so.

Its that annoying 5th time, where the system hangs and I'm forced to do a hard restart...

Interestingly, after the restart in such cases, networking always shows as disabled...

---

### Post by libssd on 2010-08-23
> **matthewbpt said:**
> My netbook takes about 5 seconds to sleep, and about 3 or 4 seconds to wake up from sleep. I have am EeePC 901, similar specs to yours, but mine has intel graphics and an SSD. I've read that SSD makes computers boot faster, I don't know if this would have an effect on suspend. I think it may have more to do with the nvidia graphics. Are you using the proprietary or open source driver. The proprietary driver could cause it to resume slower, but it also gives you much better graphics performance and power management (I think) than the open source driver so I'd say the pros and cons point in favour of the proprietary driver until the open source driver has matured more.
Waking from suspend requires disk access, so an SSD is noticeably faster. Acer AA1 D150, N270 @ 1.6gHz, replaced the Toshiba 160gb HDD that came with it with a 32gb Vertex SSD. 

**Ubuntu 10.04**
Boot: 20 seconds
Shutdown: 4 seconds
Suspend by closing (so I don't time it)
Resume by re-opening: 2 seconds

If you are just running Linux, a 32gb drive is more than big enough, can be had for under $100 and, in my opinion, offers the biggest bang for the buck performance improvement for a netbook. A SSD also consumes less power/generates less heat (therefore the cooling fan runs less) and is probably the most shock-resistant thing in the computer. When faster hardware comes along (as it always does), just transfer the drive.

---

### Post by spupy on 2010-08-23
> **libssd said:**
> Waking from suspend _requires disk access_, so an SSD is noticeably faster.

I thought it doesn't? Isn't hibernation the action that requires disk access? Suspend just cuts power from everything except RAM (as I understand it according to wikipedia)?

---

