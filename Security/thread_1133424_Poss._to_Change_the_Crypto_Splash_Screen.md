---
title: "Poss. to Change the Crypto Splash Screen?"
date: 2009-04-22
forum: Security
---

### Post by PaganImmolator on 2009-04-22
I just finished creating a fully encrypted system using the 9.04 Jaunty Alternate Install Disk. 

It looks like all that and a bag o' chips but the first splash screen that asks for your encryption pw rubs me the wrong way. Is there anyway to change that? I wish I could find one that was just a green terminal screen with

**>pass:** 

type prompt. That would be kinda retro and cool. I guess I would settle for an all black screen.

---

### Post by PaganImmolator on 2009-04-23
hmm, 26 views and no replies. I am guessing this isn't possible. 

Any other place I could ask this question before I give up completely?

---

### Post by mosburn on 2009-04-23
You could always change your boot splash screen to that. It shouldn't be that hard as it would be only a black background and a config for green text.

---

### Post by PaganImmolator on 2009-04-23
> **mosburn said:**
> You could always change your boot splash screen to that. It shouldn't be that hard as it would be only a black background and a config for green text.

Where are the files kept for that?

is it somewhere in /boot ?

---

### Post by kanka on 2009-05-04
As I see it, you'd need to take 2 steps:

1. Change the splash. I don't know much about it, but if you just want to get rid of it, you could try to remove the option at the end of the kernel line of your grub entry

2. Change the cryptsetup prompt. Instructions can be found here:
[http://ubuntuforums.org/showthread.php?t=1070031&highlight=encrypted+prompt]("http://ubuntuforums.org/showthread.php?t=1070031&highlight=encrypted+prompt")

Hope this helps

---

### Post by PaganImmolator on 2009-05-05
> **kanka said:**
> As I see it, you'd need to take 2 steps:

1. Change the splash. I don't know much about it, but if you just want to get rid of it, you could try to remove the option at the end of the kernel line of your grub entry

2. Change the cryptsetup prompt. Instructions can be found here:
[http://ubuntuforums.org/showthread.php?t=1070031&highlight=encrypted+prompt]("http://ubuntuforums.org/showthread.php?t=1070031&highlight=encrypted+prompt")

Hope this helps

Actually, this helps a lot. Thanks for the info.

---

