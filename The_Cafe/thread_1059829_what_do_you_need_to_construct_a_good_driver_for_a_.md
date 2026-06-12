---
title: "what do you need to construct a good driver for a piece of hardware?"
date: 2009-02-04
forum: The Cafe
---

### Post by simtaalo on 2009-02-04
i've recently setup my tascam us-428 sound-desk. i've got it working but don't think i can get the full functionality due to the drivers.

i emailed tascam about this and not surprisingly (and understandably) they said

[quote=tascam]I will forward your mail to our R&D department but generally we tend not to give out code even on past products.  These products were also joint ventures between TASCAM and Frontier.[/quote]

so my question is do we need the actual code from them, or is there something else they can give us which isn't their code but can help us build better drivers for the hardware?

---

### Post by jespdj on 2009-02-04
You do not really need source code, but you do need the exact specifications of the interface between the device and the computer - technical documentation that describes exactly how the device talks to the computer.

And ofcourse you'd have to be a programmer and know how to write Linux device drivers.

---

### Post by simtaalo on 2009-02-04
i replied to their email telling them we don't need the code and the tech-spec would be enough. the issue has been forwarded to their R&D dept.

even if they do reply with a no, they have at least acted in a measured mature way unlike certain manufacturers when asked about linux support.

---

### Post by gnomeuser on 2009-02-04
You might have luck letting [the Linux Driver Project](http://www.linuxdriverproject.org/twiki/bin/view) do the talking. They will sign NDAs and develop the driver for free, all they need is specifications and a sample of the hardware to test with. 

Regardless, their website should get you started.

---

### Post by simtaalo on 2009-02-04
thanks for the link, really helpful :)

i've had a fairly encouraging follow-up email from tascam, they have some concerns but the information at linux driver project should be enough to address those.

lets hope it carries on being a positive dialogue with them.

---

