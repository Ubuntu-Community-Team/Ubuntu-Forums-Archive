---
title: "daru3 shuts down once unplugged"
date: 2010-08-21
forum: System76 Support
---

### Post by Temposs on 2010-08-21
I think perhaps the most recent kernel update from Ubuntu has caused an issue in the my Darter Ultra rev3 where when the machine is plugged in, but then you unplug it, it shuts down.

What I'm seeing is that once you unplug the power cord, Ubuntu does its processing for transferring to battery mode, which takes a few seconds, and then it shuts down. A weird symptom is that the brightness indicator comes up automatically and shows the brightness being put all the way down, as though the battery were low, which triggers the brightness to go all the way down.

Any confirmation of this bug or help is appreciated.

---

### Post by isantop on 2010-08-23
Is it a full, proper shutdown or is it simply dying?

---

### Post by Temposs on 2010-08-23
It just "dies" as you put it. It takes about 5 seconds after unplugging to do its processing to transfer to battery mode, and then it just turns itself off. 

Suspend still works when plugged in, and unplugging once suspended does not make the machine turn off, which makes sense.

---

### Post by isantop on 2010-08-23
What happens if you suspend, then unplug, then try and resume?

---

### Post by Temposs on 2010-08-23
> **isantop said:**
> What happens if you suspend, then unplug, then try and resume?

In that case, it resumes, and then once it's fully resumed and I see the window to unlock the screen, it turns off.

Another interesting symptom that happens along with the turning off is that when I start up the machine again after this incident, networking is disabled. I don't know how that is linked, but it is consistently happening after an unplugging incident.

---

### Post by isantop on 2010-08-24
I've seen that crop up randomly. I'd go ahead and contact us at support...at...system6...dot...com.

This will allow us to provide a better one-on-one experience, an I'll bet this is hardware related.

---

### Post by Temposs on 2010-08-24
Thanks.

Just for public documentation's sake, I have to make a correction. The computer *does* turn itself off if the computer is unplugged while in suspend mode. But, it takes about 10 seconds and the indicator lights go all wonky compared to the normal pattern.

---

