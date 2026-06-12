---
title: "Truecrypt noob question"
date: 2012-02-14
forum: Security
---

### Post by Nesaskewatch on 2012-02-14
I realise this is likely a stupid question, but please be mercyful...  This is all new to me.  I am about to create a hidden volume within an existing encrypted volume made earlier with Truecrypt, but don't know if the contents of the "outer" volume will be wiped when I create the hidden volume.  Is it necesarry to create both first, *then* move files into the volume(s)?

I hope I am making sense here.  Thanks!

---

### Post by elizabethmc on 2012-02-14
> **Nesaskewatch said:**
> I realise this is likely a stupid question, but please be mercyful...  This is all new to me.  I am about to create a hidden volume within an existing encrypted volume made earlier with Truecrypt, but don't know if the contents of the "outer" volume will be wiped when I create the hidden volume.  Is it necesarry to create both first, *then* move files into the volume(s)?

I hope I am making sense here.  Thanks!

Don't want to sound negative, but despite my best efforts I have failed to make Truecrypt work! :(

---

### Post by Nesaskewatch on 2012-02-14
> **elizabethmc said:**
> Don't want to sound negative, but despite my best efforts I have failed to make Truecrypt work! :(Chin up! :)  You'll get there.  I am a noob too, but maybe I can help?  What went wrong?  If you open the online manual there is a tutorial that walked me through the process quite well.  I am simply hung up on a detail, but the tutorial is very good.  Have you tried that?

---

### Post by azmyth on 2012-02-14
I would guess you could create a large container then mount it and then create another encrypted container inside the large container but I haven't tried it. I don't think it would wipe out your large one by making a smaller one inside. You could probably test it failry quick and easily before you risk losing files.

---

### Post by Nesaskewatch on 2012-02-14
> **azmyth said:**
> I would guess you could create a large container then mount it and then create another encrypted container inside the large container but I haven't tried it. I don't think it would wipe out your large one by making a smaller one inside. You could probably test it failry quick and easily before you risk losing files.I believe Truecrypt hidden volumes _must_ be inside another Truecrypt volume.  At least that is what I understand anyway.  I guess I will try and fool around with it but it makes me nervous monkeying with things like this.  I don't understand Linux enough to have the courage yet, but I'll give it a go.

Thanks.

---

### Post by ztux on 2012-02-15
Hidden volumes are supposed to be deniable and are created inside of existing volumes. For example, let's consider a 100MB outer volume with a 30MB hidden volume. The hidden volume is at the end of the outer volume. If you open the outer volume, it will appear to have 100MB of space. However, if you add more than 70MB (outer - hidden) you will destroy the hidden volume. You can open the outer volume in such a way that the hidden volume is protected from this. This should be what you do if you write files to it.

All of this is in the very well written and very well organised TrueCrypt manual. The only part that I couldn't find was opening the hidden volume. To do this, you simply enter the hidden volume's password or keyfile.

---

### Post by elizabethmc on 2012-02-15
> **Nesaskewatch said:**
> Chin up! :)  You'll get there.  I am a noob too, but maybe I can help?  What went wrong?  If you open the online manual there is a tutorial that walked me through the process quite well.  I am simply hung up on a detail, but the tutorial is very good.  Have you tried that?

Okay, thanks for the word of encouragemnt. Maybe I have not tried hard enough! I think I would give it another shot. :)

---

