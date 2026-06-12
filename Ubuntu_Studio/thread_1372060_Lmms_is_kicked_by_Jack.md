---
title: "Lmms is kicked by Jack"
date: 2010-01-04
forum: Ubuntu Studio
---

### Post by Oasu4g on 2010-01-04
Hi,

Every time I open a file, or try to use LMMS with Jack, xruns occur and I keep getting a somewhat ambiguous error that says "LMMS was kicked by JACK for some reason. Therefore the JACK backend of LMMS has been restarted. You will have to make manual connections again."

I'm running Linux Mint Gloria 7 Standard. This occurs on both the generic and rt kernels I have installed.

Any help would obviously be greatly appreciated.

Thanks,

Tim

---

### Post by AutoStatic on 2010-01-04
Hello Tim, increase the timeout in QjackCtl to 5000ms, that should take care of most of your issues with LMMS. The JACK implementation of LMMS is not optimal unfortunately but bugreports have been posted so hopefully they'll get picked up by the devs.

---

### Post by tazztone on 2010-01-17
increasing timeout didn't work for me. any other solving method?:(

edit: i'll use PULSE instead (is this a good idea?)

---

### Post by Oasu4g on 2010-01-18
Increasing the timeout doesn't help me either.

As long as you get sound with Pulse it's fine. In fact I would recommend anything that works other than Jack, because it looks like LMMS has no support for Jack at the moment. There's really no advantage to using LMMS with Jack as it is now anyway.

---

### Post by AutoStatic on 2010-01-18
@A. Tim, LMMS does have JACK support, it is not optimal though and the devs are working on it. I don't have any real big problems with it myself as long as I don't switch from one huge project to another, then LMMS will nag. But if you keep your latency settings not too low and increase the timeout setting a bit LMMS should work quite nicely.
And you're right, there really is no advantage to using LMMS with Jack as it is now anyway ([http://forum.linuxmusicians.com/viewtopic.php?f=24&t=2368](http://forum.linuxmusicians.com/viewtopic.php?f=24&t=2368)). But in my case I happen to use JACK on an exclusive basis so decent JACK support in LMMS would be very nice.

@tazztone, you can use PulseAudio, no problem, but you're warned by LMMS itself already: bad latency!

---

