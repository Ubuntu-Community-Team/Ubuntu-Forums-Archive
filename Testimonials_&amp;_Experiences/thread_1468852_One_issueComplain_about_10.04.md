---
title: "One issue/Complain about 10.04"
date: 2010-05-01
forum: Testimonials &amp; Experiences
---

### Post by retro89 on 2010-05-01
I finally decided to get 10.04 and download .iso and burn it. I had problems with .iso so I created a usb live cd and it worked well on my desktop.I was able to get everything working correctly (graphics, sound, etc...).Then I decided on load 10.04 on my compaq laptop  cq-50 because Vista was a pain and getting a virus . I was so tried of using windows (stupid kodak 5300 printer). I installed 10.04 fine and started hoping my wireless would work since 8.10 had issues and 9.10 worked for a while. Well, I could not use my wifi card (Atheros AR928X).If Uubntu developers would package the Atheros drivers with this distro I would have not any issues what so ever. I wish my wifi would work.Maybe Uubntu developers need to fix this issue.

---

### Post by coffeecat on 2010-05-01
> **retro89 said:**
> Well, I could not use my wifi card (Atheros AR928X).If Uubntu developers would package the Atheros drivers with this distro I would have not any issues what so ever. I wish my wifi would work.Maybe Uubntu developers need to fix this issue.

I have an Acer laptop with the Atheros AR928X wireless chipset, and this works just fine in Lucid. As it did in Karmic after I had installed the backported wireless modules. So clearly the AR928X should work for you.

I suggest you start a thread in a support forum so that someone can help you find out why you are having wireless problems.

Good luck.

---

### Post by matchett808 on 2010-05-01
I am not familiar with the laptop model or the card but have you tried "Hardware drivers" under system --> administration

is there nothing on the forums about that chipset? have you look into madwifi?

Just a boot note, have you ever install windows from a non-oem disk? they mostly drivers for multiple bits of H/W! on (other than a desktop that i had that needed quite a bit of digging for the graphics issue) most H/W I have installed it has worked OOTB on ubuntu (I will admit my current laptop needed the i802 thingmy added to grub but worked 100% otherwise!) Not to turn it into a debate or anything, but hope you get it sorted! :)


EDIT: or......what that ^ guy said! lol - Disregard my advice as the wireless can be fixed using backports....

---

### Post by coffeecat on 2010-05-01
> **matchett808 said:**
> I am not familiar with the laptop model or the card but have you tried "Hardware drivers" under system --> administration

Not necessary.

> **matchett808 said:**
> have you look into madwifi?

Not necessary. The AR928X chipset works with the ath9k driver that comes in a default install of 10.04. I should imagine the OP is experiencing some some other issue that is causing a problem with his wireless.

---

### Post by matchett808 on 2010-05-01
as I said in my edit (although not clearly enough) your soloution is much better as you have ran into this chipset before....I shall re-edit my post to fix it....

---

### Post by retro89 on 2010-05-01
> **coffeecat said:**
> I have an Acer laptop with the Atheros AR928X wireless chipset, and this works just fine in Lucid. As it did in Karmic after I had installed the backported wireless modules. So clearly the AR928X should work for you.

I suggest you start a thread in a support forum so that someone can help you find out why you are having wireless problems.

Good luck.

Going to try installing backported wireless modules to see if it works.

---

### Post by coffeecat on 2010-05-01
> **retro89 said:**
> Going to try installing backported wireless modules to see if it works.

Well - good luck with that, but I'm not optimistic. The only reason I mentioned the backported modules is that they were necessary (at least for me) in Karmic. The ath9k driver that came with Karmic I found to be unreliable. But the backported driver in Karmic is the same as the one that comes in Lucid (I believe).

Anyway - good luck. But just to remind you. This is the Testimonials forum. It's not appropriate to give support advice here, so I'm going to shut up now. :wink: If you want any further help you do really need to start a new thread in another subforum.

---

### Post by Tamlynmac on 2010-05-01
> coffeecat
Anyway - good luck. But just to remind you. This is the Testimonials forum. It's not appropriate to give support advice here, so I'm going to shut up now. :wink: If you want any further help you do really need to start a new thread in another subforum. 	

Well written. This section, is defined as not being for support, debate or discussion.
:-k

As stated [here]("http://ubuntuforums.org/showthread.php?t=1394144&page=18") & [here]("http://ubuntuforums.org/showthread.php?t=1343965").

---

