---
title: "Password/Encryption Keys Questions"
date: 2010-10-22
forum: Security
---

### Post by The_Accursed_One on 2010-10-22
Okay, I know this has probably been asked too many times here but I need to secure my emails. Personal matters of course. But yeah. I use the program "Password and Encryption Keys" to generate a key to sign my emails with but I do not know what to do. To be blunt, I'm stupid when it comes to this. Is there any sort of tutorial or guide to help me work this program? IF not, can anyone help me through the steps in creating a key? and giving it (my public key) to the significant other? Finding where both keys are? Implementing it into Thunderbird? If it helps any here's some extra information:

Ubuntu distro: Ubuntu 10.04
Email client: Thunderbird

Thanks for the help. Really not trying to sound like a complete dumbass but you have to start somewhere right?

---

### Post by rjbl on 2010-10-25
> **The_Accursed_One said:**
> Okay, I know this has probably been asked too many times here but I need to secure my emails. Personal matters of course. But yeah. I use the program "Password and Encryption Keys" to generate a key to sign my emails with but I do not know what to do. To be blunt, I'm stupid when it comes to this. Is there any sort of tutorial or guide to help me work this program? IF not, can anyone help me through the steps in creating a key? and giving it (my public key) to the significant other? Finding where both keys are? Implementing it into Thunderbird? If it helps any here's some extra information:

Ubuntu distro: Ubuntu 10.04
Email client: Thunderbird

Thanks for the help. Really not trying to sound like a complete dumbass but you have to start somewhere right?

Pull down Enigmail from the software centre - it is Thunderbird's GPG extension. It installs transparently and will add Encrypt / Sign options to your emailsystem.

Open Password and Encryption Keys from your Apps > Accessories drop down. Hit 'New' and select New PGP Key, then follow the Wizard.

The encryption resources in Ubuntu are impressive. Enigmail/Thunderbird works really well. eCryptFS is a good quality crypto product and TrueCrypt appears to be a good encrypted virtual disk creator / manager.

  Hope this helps - do come back here for any clarification needing. No, you ain't a dumbass.
rjbl

---

### Post by anomie on 2010-10-25
[QUOTE=The_Accursed_One]Really not trying to sound like a complete dumb*** but you have to start somewhere right?[/QUOTE]

The dumb*** is the guy who won't even ask the question and/or refuses to learn.

---

### Post by The_Accursed_One on 2010-10-25
Okay, this really answered all of my questions. Thank you guys. If there was kudos to give, you'd have mine. I only haqve one more question, where do I set the OpenPGP passphrase? Again thanks for the help and esteem boost :D

---

### Post by rookcifer on 2010-10-25
> **The_Accursed_One said:**
> Okay, this really answered all of my questions. Thank you guys. If there was kudos to give, you'd have mine. I only haqve one more question, where do I set the OpenPGP passphrase? Again thanks for the help and esteem boost :D

When you create a key it should ask you for it.  [Here]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") is the official Ubuntu Wiki for using GPG.

---

### Post by rjbl on 2010-10-26
> **The_Accursed_One said:**
> Okay, this really answered all of my questions. Thank you guys. If there was kudos to give, you'd have mine. I only haqve one more question, where do I set the OpenPGP passphrase? Again thanks for the help and esteem boost :D

The wizard will prompt you for it.

Tip: Use a long passphrase which cannot be guessed by anyone, particularly anyone close to you. Try mixed languages and insert a few numbers and punctuation marks into the phrase. Make it memorable and never, EVER, write it down anywhere.

Hope this helps

rjbl

---

### Post by The_Accursed_One on 2010-10-27
Okay, thanks for the help guys. Solved all my problems. Just one last question: How does the public key thing work when I get a message? Do I just need to get them to generate a key and give me their public key? This is starting to come to sense to me as I type this I just want to be sure.

EDIT: And, where do I find my public key in PGP?

Edit2: Where/How do I save someone's public key?

---

### Post by The_Accursed_One on 2010-10-29
:p

---

