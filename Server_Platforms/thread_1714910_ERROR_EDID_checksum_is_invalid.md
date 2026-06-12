---
title: "*ERROR* EDID checksum is invalid"
date: 2011-03-26
forum: Server Platforms
---

### Post by somone77 on 2011-03-26
Hello,

I've been using a copy of Ubuntu Server 10.10 for a few months now, running a simple web server. Recently, I've noticed some scripts in my /etc/init.d stopped running on startup. I checked the kernel logs and found this error:

```
[   63.210372] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 131
[   63.210539] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[   63.210643] <3>00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff  ................
[   63.210650] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   63.210656] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   63.210661] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   63.210666] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   63.210671] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   63.210676] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[   63.210681] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff 00 ff  ................
```

I found the error can be repeted when I run 'dmesg'.

I have no idea what could be causing this problem, I have not made any recent changes to the server since this started happening. Any help would be greatly appreciated, thanks.

---

### Post by disabledaccount on 2011-03-26
Do you have active gfx card in Your server? Optionally: what is the gfx and display model?

You can try:
>Xorg -configure

Add this to device section in xorg.conf: (you will have to create one if it doesn't exist)
Option &#8220;IgnoreEDID&#8221; &#8220;true&#8221;

edit: This error have nothing to do with init.d scripts -> what scripts are stopped? ..or maybe more imortant: what effects have you observed before you've checked the logs?

---

### Post by Vegan on 2011-03-26
I am lucky, my box has a built-in video solution that is liked.

Backup your machine and install fresh. If it continues to be at issue, consider a new system board

---

### Post by somone77 on 2011-03-26
> **tomazzi said:**
> Do you have active gfx card in Your server? Optionally: what is the gfx and display model?

You can try:
>Xorg -configure

Add this to device section in xorg.conf: (you will have to create one if it doesn't exist)
Option “IgnoreEDID” “true”

edit: This error have nothing to do with init.d scripts -> what scripts are stopped? ..or maybe more imortant: what effects have you observed before you've checked the logs?

My server didn't seem to have xserver-xorg-core installed. I therefore installed it (via apt-get, obviously), and tried what you recommended. My result was still the same, the error is printed on startup. 

I guess unless there are any more ideas, a fresh install will have to suffice. 
Thanks for your help.

---

### Post by disabledaccount on 2011-03-27
ehh, You shouldn't install Xorg - I assumed that You have it installed but that was wrong.
However this error is gfx-related - wrong EDID from display (or just no display) ...so I wouldn't change Mother Board because of such low-priority problem :) If you would tell something about Your GFX then solution could be simple.

But, as I mentioned before - this is not the reason for stopping ini.d scripts - what scripts are affected?

---

