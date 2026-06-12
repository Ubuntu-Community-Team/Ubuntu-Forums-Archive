---
title: "Can't use numlock keypad when using &quot;xset led on&quot;."
date: 2015-11-21
forum: Ubuntu Studio
---

### Post by sethanath2 on 2015-11-21
Hi,

I cannot use numlock keypad when using "xset led on".
My keyboard is "Cooler Master Devastrator CMStorm", and in order to turn the light on I use such command.

By leaving the light off, my keyboard would work normally.

Thanks.

---

### Post by sethanath2 on 2015-11-21
I forgot to mention that my OS is Ubuntu Studio 14.04 Trusty Tahr.

---

### Post by sethanath2 on 2015-11-26
> **sethanath2 said:**
> Hi,

I cannot use numlock keypad when using "xset led on".
My keyboard is "Cooler Master Devastrator CMStorm", and in order to turn the light on I use such command.

By leaving the light off, my keyboard would work normally.

Thanks.

Hi,

I wonder if there are different methods than "xset led on" to turn on the keyboard LED light.

Thank you.

---

### Post by matt_symes on 2015-11-26
Hi

From here:

[https://answers.launchpad.net/ubuntu/+source/linux/+question/241299](https://answers.launchpad.net/ubuntu/+source/linux/+question/241299)

Does the backlight come on and can you use the numlock keyboard if you use this variation of xset instead ?

```
xset led 3
```

Kind regards

---

### Post by sethanath2 on 2015-11-29
> **matt_symes said:**
> Hi

From here:

[https://answers.launchpad.net/ubuntu/+source/linux/+question/241299](https://answers.launchpad.net/ubuntu/+source/linux/+question/241299)

Does the backlight come on and can you use the numlock keyboard if you use this variation of xset instead ?

```
xset led 3
```

Kind regards

It works now with "xset led 3" command.

Thanks.

---

### Post by matt_symes on 2015-11-29
Hi

No problem. I'll mark this thread as [solved] for you.

Kind regards

---

