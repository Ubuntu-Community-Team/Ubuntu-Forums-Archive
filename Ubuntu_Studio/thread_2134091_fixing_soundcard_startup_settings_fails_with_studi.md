---
title: "fixing soundcard startup settings fails with studio 12.04"
date: 2013-04-10
forum: Ubuntu Studio
---

### Post by Keiner298 on 2013-04-10
I tried to fix my USB soundcard selection with th solution mention here [http://ubuntuforums.org/showthread.php?t=764949](http://ubuntuforums.org/showthread.php?t=764949) 
[FONT=arial]My devices name is CODEC. When I start jack with [/FONT]jackd -d alsa -d hw:CODEC. it works. But if i use qjackl and enter "hw:CODEC" in the device tag it is changed automaticaly into "hw:codec". When I start jack it will not finde the device "hw:codec" and fails. Worse if i use ladiconf. in the driver section it allows only "hw:0" wich was the physikal device connection at this time. The problem with the "changing names into lower case" does not happen with AVLinux and not with Ubuntu studio 10.04. (those have other disadvantages). Anybody any idea?

---

### Post by zequence on 2013-04-10
Delete the config file for qjackctl, to get rid of the stored options, or edit it manually (deleting will create a new default next time you start Qjackctl).

It's located in ~/.config/rncbc.org/QjackCtl.conf

---

### Post by Keiner298 on 2013-04-12
Thanks zequence im going to try your recomendations. In any case it is good to know where all those configs are stored. But I solved my problem:

I wrote that **hw:CODEC** and the entry was changed to **hw:config**. Than I used my Zoom H2 and the device name **H2** was not changed and stayed **hw:H2**. 
I used than **hw:CODEC1** simply to try if this would be unchanged. It was not changed, but of course did not work. Finaly I entered **hw:'CODEC'** (only single quot. marks, not double)
This entry won't be changed and jack works. You cannot use this trick in ladiconf, but ladiconf, when invoked new, uses the last used jack configs. So if one does not touch the alsa name in the device driver one can change all the other features you like. Than save the studio and it will work next time.

thx

---

### Post by Keiner298 on 2013-04-12
@zequence.

Hi zequence,
You've been right, my solution is a workaround, **Your solution is the right clean way.** I deleted the old options in the [History] section, and "surprise" the hw:CODEC worked fine. Then i remebered that I made false entry hw:codec by mistake first. After that hw:CODEC was not possible anymore. This [History section has room for improovment:-)

But the trick with ladiconf stays the same, as before.
thx again

---

