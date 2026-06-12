---
title: "How do I adjust screen contrast on a Gazelle Professional?"
date: 2012-02-16
forum: System76 Support
---

### Post by JohnSmithNot1882 on 2012-02-16
How do I adjust screen contrast on a Gazelle Professional with 95% NTSC Color?

Thank you,
John Smith Not 1882:popcorn:

---

### Post by jschall1 on 2012-02-16
> **JohnSmithNot1882 said:**
> How do I adjust screen contrast on a Gazelle Professional with 95% NTSC Color?

Thank you,
John Smith Not 1882:popcorn:

nvidia-settings has adjustments for contrast. I don't think there is a hardware control.

---

### Post by isantop on 2012-02-17
That's correct. Any contrast adjustments would need to be made if software.

You can control the brightness by holding Fn and pressing F8 or F9.

---

### Post by abqsteve on 2012-07-15
I've found that I can get a much better contrast by lowering the screen gamma setting.  I use the following command:

xgamma -gamma 0.65

After changing the gamma setting, the screen is beautiful and doesn't seem so washed out.  I created a small shell script which runs the xgamma command and I've added it to the startup programs.

---

