---
title: "[SOLVED] Pangolin Performance and Virtualization"
date: 2008-11-06
forum: System76 Support
---

### Post by tow on 2008-11-06
I am considering purchase of a Pangolin Performance -- have the config up in another window and ready to click "Add to cart" :) -- but it is essential that whatever I buy has hardware virtualization fully supported in the CPU and BIOS.  Is that the case with the Pangolin Performance?

TIA.

---

### Post by thomasaaron on 2008-11-06
I'm going to have to ask R&D to do some testing on that. I'm 99% sure the answer is yes, but it's not something that we generally deal with unless the question is specifically asked.

System76-ers? Are any of you using hardware virtualization on the PanP4(i/n)?

---

### Post by Vadi on 2008-11-06
Virtualbox will work anyway, since it uses software virtualization by default. For VMware or the hardware virtualization option in virtualbox, you do need to have the virtualization technology enabled in the CPU.

For Pangolin... I couldn't find any info on T5800, but P8400, P8600, and T9400 claimed to support hardware virtualization. P9500 and T9600 do not claim so.

See [http://processorfinder.intel.com/List.aspx?ParentRadio=2643%2C3040%2C2967%2C2278%2C2883%2C2304%2C2848%2C826%2C942%2C58%2C3008%2C&ProcFam=2643&SearchKey=](http://processorfinder.intel.com/List.aspx?ParentRadio=2643%2C3040%2C2967%2C2278%2C2883%2C2304%2C2848%2C826%2C942%2C58%2C3008%2C&ProcFam=2643&SearchKey=)

---

### Post by tow on 2008-11-06
Thanks for the CPU info. I must have been looking in the wrong spot (the Intel processor info list). :-/

Sometimes the CPU will support VT but the BIOS has it turned off (and in some cases no way to turn it on).  That's why I was asking about both CPU and BIOS in the currently available Pangolin model.

---

### Post by tow on 2008-11-06
> **thomasaaron said:**
> I'm going to have to ask R&D to do some testing on that. I'm 99% sure the answer is yes, but it's not something that we generally deal with unless the question is specifically asked.

System76-ers? Are any of you using hardware virtualization on the PanP4(i/n)?

I've done some further checking and the info provided by "Vadi" appears to be correct (thanks!). By opting for the P8400 CPU I should have VT support **if** its supported in the BIOS.  Maybe an easy way to get an answer to that would be to just boot one up and poke through the BIOS screens ???? If there is a place to turn it on/off then that would be fairly definitive (have seen that in another brand that will remain nameless here).  On the other hand, if there is no mention of VT in the BIOS that could mean that its always on or, more likely, not supported. You might also ask R&D about the Serval.  The Pangolin is for my wife and I need that now, but I want the Serval and Christmas is just around the corner 8-)

---

### Post by Vadi on 2008-11-07
The serval with that CPU has it enabled by default if the CPU supports it.

I know because I first got a serval that did not support it, upgraded my CPU to one that did, and the option was automatically on.

(my bios seems to be password protected anyway... and I don't remember setting a password for it. Or if I did, I forgot it!)

---

### Post by thomasaaron on 2008-11-07
Vadi,

Thanks for helping with this thread.

You can reset your bios password by clearing your cmos. Contact me via email and I'll give you instructions.

---

### Post by tow on 2008-11-10
I'm still waiting on a definitive yes/no regarding VT support in the Pangolin and still have the config I want (with P8400 or P8600 CPU) waiting to go into the cart...

Private emails have so far generated 0 responses from System 76... kind of disappointing but of course they could be too busy to respond or could be waiting for a response from the ODM.  Dunno.

Does anyone with a Pangolin Performance with one of the above CPU's know if hardware assisted virtualization works?  Both of the above CPU's support it but that doesn't necessarily mean that the BOIS does.  Some of the other CPU choices for the Pangolin definitely do not support VT so that's why I'm choosing from either the P8400 or P8600.

TIA

---

### Post by Vadi on 2008-11-10
They're probably checking it out. They also don't work on weekends, not that big ;)

---

### Post by thomasaaron on 2008-11-10
I've not seen any emails come through from you (or, more accurately, any emails regarding virtualization).

...not in the junk folder either.

Please send to support(at)system76(dot)com.

---

### Post by tow on 2008-11-10
> **thomasaaron said:**
> I've not seen any emails come through from you (or, more accurately, any emails regarding virtualization).

...not in the junk folder either.

Please send to support(at)system76(dot)com.

Used "private message" facility of the forum.  Just did it again.  Perhaps I didn't do something correctly last time ????

---

### Post by thomasaaron on 2008-11-10
Just heard back from R&D. They say it is enabled in the BIOS. So, you should be fine with the P8400 and P8600.

---

### Post by tow on 2008-11-10
> **thomasaaron said:**
> Just heard back from R&D. They say it is enabled in the BIOS. So, you should be fine with the P8400 and P8600.

Thank you, Thank you, Thank you.  Its ordered!

---

### Post by tow on 2008-11-21
System arrived right on time, impressively boxed. :)

There isn't any spot in the BIOS that speaks to VT but it just works (assuming you've selected a CPU that has VT support).  Verified that with Virtualbox.  This is a sweet machine.  The only problem I've encountered so far is that the wife doesn't like the white keyboard :( and daughter (has older HP laptop) is jealous and wants to "upgrade".  I suspect System 76 will be getting more of my business.

Thanks to "thomasaaron" and "vadi" for their input!

---

### Post by Vadi on 2008-11-21
Glad you're liking it.

I'd tell the wife that a white keyboard is easier to keep in a clean condition than a black one ;)

---

### Post by thomasaaron on 2008-11-21
I'd try to come up with a way that it saves money, and tell her you can put that saved money in your Hawaii vacation fund. It works every time. Trust me. ;)


BTW: > Used "private message" facility of the forum. Just did it again. Perhaps I didn't do something correctly last time ????

Yeah, I don't use that feature. You can just email me at support(at)system76(dot)com or fill out this form (which I am starting to prefer, as it gives me everything I need in one swoop)... It still comes directly to my email.

[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

---

