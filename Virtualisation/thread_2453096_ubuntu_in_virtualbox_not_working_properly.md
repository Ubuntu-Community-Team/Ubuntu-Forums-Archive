---
title: "ubuntu in virtualbox not working properly"
date: 2020-11-03
forum: Virtualisation
---

### Post by vishnusai6923 on 2020-11-03
I am using the latest ubuntu in virtual box.But the applications screen kind of blinks and that too happens only to the last row of apps.My laptop has i5 and 1TB SSHD. Can somebody tell me if this is normal or if it's happening only with my computer?

---

### Post by slickymaster on 2020-11-03
Thread moved to **Virtualisation** for a better fit

---

### Post by franknfurter2 on 2020-11-14
Dear vishnusai6923,

if you want people to answer, it is a good idea to give more details about your problem. An, of course, I really do not understand what you want to tell us. How can a screen blink only at the last row of apps? I really have no idea, what you mean.

Try to describe it more clearly and tell us what your host is, which system an which version is it running and which version is your ubuntu within your vm?

Regards

Frank

---

### Post by ajgreeny on 2020-11-14
franknfurter2 is not the only one who does not understand what you mean; I can't figure it out either!

We need a lot more information rather than just saying "the latest ubuntu in virtual box".

What version of Ubuntu does that mean, 20.04 or 20.10?
What host OS are you using?
What version of VBox do you have and how did you install it?  I recommend using the instructions at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the **Debian-based Linux distributions** section, which will add the repos to your system and keep VBox fully updated.
Do you have the guest additions installed in the guest OS? They are needed for a better guest experience 

Also please give us full details of your hardware with the output of command ```
inxi -Fzx
```

---

### Post by SeijiSensei on 2020-11-14
Did you install the Expansion Pack? If so, you'll get better video drivers than the default.

---

