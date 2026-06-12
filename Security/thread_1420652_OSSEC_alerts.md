---
title: "OSSEC alerts"
date: 2010-03-03
forum: Security
---

### Post by Advait on 2010-03-03
Hi All,

I installed and activated OSSEC on my Ubuntu 9.10 and I looked thru the OSSEC alert logs. Because I've only been using Ubuntu for about a week, the logs pretty much made zero sense to me. I'm guessing that the vast majority of alerts can be classified as "Standard Alert. Just Ignore". Is this accurate?

Is there some kind of tool that can alert me when I get a *real* alert versus all the "background noise" alerts?

Keep in mind I have just about zero knowledge of the Ubuntu command line.

Thanks,

Tom

---

### Post by bodhi.zazen on 2010-03-03
You need to know what is "normal" and what is not.

You will also need to read up on what the alerts mean and then decide what, if anything, to do about them.

Yes the way it is designed generates a lot of false positives. If you are not willing to sort all this out, you can sit back and allow ossec to do it's work (it will ban IP automatically for you), but that is sub optimal.

I would note that you keep claiming you are new to all this and that you feel overwhelmed. Only you can decide if you wish to learn security, the learning curve is steep and it will take time.

Alternately you can sit back and relax for a while and return to these security issues once you are more comfortable with how your system works.

[Ubuntu Forums - View Single Post - General Security ?]("http://ubuntuforums.org/showpost.php?p=8620985&postcount=236")

---

