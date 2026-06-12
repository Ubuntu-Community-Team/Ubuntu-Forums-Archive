---
title: "Unable to Drop/Drag with Virtualbox"
date: 2020-05-18
forum: Virtualisation
---

### Post by KenUBF on 2020-05-18
I've got an issue I've been unable to solve. I've got the updated Extension Pack, I've enabled the host to guest settings but I keep getting the following error and I haven't been able to find any solution online. You can see the attached screenshot for more information. Thank you!

For more context I've installed Ubuntu 16.04 in a VM because I've noticed that version after that the emulators I always used stopped working correctly.

---

### Post by wildmanne39 on 2020-05-18
Have you also installed guest additions? if so I would google the error, I would do it myself but since you posted a picture and not the actual text I can not simply copy and paste the error.

Thread moved to virtualisation.

---

### Post by KenUBF on 2020-05-18
Yes I've installed Guest Additions. Here is the error:

```
Drag and drop error from host (VERR_NO_TRANSLATION)
```

None of the very few forums posts' solutions worked for me.

---

### Post by wildmanne39 on 2020-05-18
What is the host you are running and what version of guest additions do you have installed?

---

### Post by wildmanne39 on 2020-05-18
I just dragged a file from ubuntu 18.04 to window's 7 guest and it worked, I think you need to go to vb settings>>general>>advance and make sure clipboard is set to bidirectional.

---

### Post by KenUBF on 2020-05-18
I'm running Ubuntu 18.04 as Host. Guest Additions are 6.1.8. I'm also running the latest version of Virtualbox.

---

### Post by ajgreeny on 2020-05-18
> **KenUBF said:**
> I'm running Ubuntu 18.04 as Host. Guest Additions are 6.1.8. I'm also running the latest version of Virtualbox.

The latest version of Virtualbox from where?

If you are using Ubuntu's own repos you will have an eariler version of VBox, 6.1.6 at present.  If you are using the Oracle repos you should have 6.1.8 and be OK, but tell us exactly what you are using.

---

### Post by wildmanne39 on 2020-05-18
Did you try what I suggested in post 5? please let us know if there is any change.

---

### Post by KenUBF on 2020-05-24
I got Virtualbox and the guest additins from the Vbox website. Yes I had Bidirectional settings set but still didn't work.

---

