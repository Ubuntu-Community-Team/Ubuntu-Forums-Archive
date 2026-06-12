---
title: "No sound device installed after repair install"
date: 2008-10-09
forum: Windows
---

### Post by Raccoon1400 on 2008-10-09
I just did a repair (upgrade) install to fix a problem in the registry. That problem is now fixed, but now my sound card is not seen by the computer.
I have a dell running Vista. The card is Sigma tel. It does not show up in device manager now, the only thing under the sound card section is a high definition audio codec.

How can I get the computer to see my sound card so I can install it?

---

### Post by smoker on 2008-10-10
hi, not sure why this would have happened with a repair install, the hardware and drivers shouldn't be affected, can you check the audio is still enabled in the bios? - also, did you visit windows update and download the latest updates after the repair, including sp1, if necessary?

you could also check what vista support is available here, dell may have something to improve hardware support and recognition in vista.
[http://support.dell.com/](http://support.dell.com/)

best of luck

---

### Post by Raccoon1400 on 2008-10-10
I have downloaded some updates, but I dont't think I have sp1 yet. Audio is definitely a problem with vista, it works fine in linux.

---

### Post by Raccoon1400 on 2008-10-11
I tried installing the driver from the dell site, after finding it with my service tag.
It did nothing at all.

---

### Post by smoker on 2008-10-11
seems to be a common problem with vista and sigma tel audio.

i don't know if it will help, but have a look at this link, post #4 (poster colschmoll)
[http://forums.techguy.org/windows-vista/595062-no-audio-device-installed-problem.html](http://forums.techguy.org/windows-vista/595062-no-audio-device-installed-problem.html)__[]("http://forums.techguy.org/members/328172-colschmoll.html")
> I had the same problem after upgrading from Vista Premuim to Vista Ultimate.
 
This resoved it:
 
1. Uninstall Sigma Tel Audio Program.
2. Doenload latest driver from [dell]("http://forums.techguy.org/#"): [http://support.euro.dell.com/support...WW1&hidlang=en]("http://support.euro.dell.com/support/downloads/driverslist.aspx?os=WLH&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=XPS_M1710&hidos=WW1&hidlang=en")
3. Install new driver.

best of luck

---

### Post by Raccoon1400 on 2008-10-11
> **smoker said:**
> seems to be a common problem with vista and sigma tel audio.

i don't know if it will help, but have a look at this link, post #4 (poster colschmoll)
[http://forums.techguy.org/windows-vista/595062-no-audio-device-installed-problem.html](http://forums.techguy.org/windows-vista/595062-no-audio-device-installed-problem.html)__[]("http://forums.techguy.org/members/328172-colschmoll.html")


best of luck

Thanks. That worked.
Smoker, thanks for all your help recently.

---

