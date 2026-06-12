---
title: "Lemur Ultra: angle brackets on German keyboard layout"
date: 2012-12-14
forum: System76 Support
---

### Post by Wolfhart on 2012-12-14
Hello,

I've just received my new Lemur Ultra. This is my first time with a System76 computer and with Linux. My first impression is very good, but I am facing one significant problem: I am used to the German keyboard layout on a MacBook which has the angle brackets <> on the top left key (the key left of the "1" key).  On Ubuntu, by contrast, the German keyboard layout has the angle brackets on the bottom left key (the key left of the "z" key). The problem is that this key does not exist on the Lemur Ultra keyboard, its place is taken up by the large Shift key. And so it seems that I cannot enter angle brackets on the German keyboard layout. But it is important for me to have the angle brackets as I am working a lot with xml data. Ubuntu has a "German (Macintosh)" keyboard layout, but it too has the angle brackets on the key that does not exist on the keyboard.

Does any of you know a solution to this? For example, is it possible to reassign single keys on a keyboard layout?

Thanks in advance for your help,
Wolfhart

---

### Post by isantop on 2012-12-14
> **Wolfhart said:**
> Hello,

I've just received my new Lemur Ultra. This is my first time with a System76 computer and with Linux. My first impression is very good, but I am facing one significant problem: I am used to the German keyboard layout on a MacBook which has the angle brackets <> on the top left key (the key left of the "1" key).  On Ubuntu, by contrast, the German keyboard layout has the angle brackets on the bottom left key (the key left of the "z" key). The problem is that this key does not exist on the Lemur Ultra keyboard, its place is taken up by the large Shift key. And so it seems that I cannot enter angle brackets on the German keyboard layout. But it is important for me to have the angle brackets as I am working a lot with xml data. Ubuntu has a "German (Macintosh)" keyboard layout, but it too has the angle brackets on the key that does not exist on the keyboard.

Does any of you know a solution to this? For example, is it possible to reassign single keys on a keyboard layout?

Thanks in advance for your help,
Wolfhart

Did you order a US or UK keyboard?

---

### Post by Wolfhart on 2012-12-14
I ordered a US keyboard.

---

### Post by Wolfhart on 2012-12-14
I found a solution, namely to customize the German keyboard layout, as described in [https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions](https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions)

It took me a while to figure out how to apply these instructions to my case, but I finally made it work.
[]("https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions")

---

### Post by timbo3 on 2013-08-17
Wolfhart.

I'm having the same problem but with a Swedish layout. How did you fix this? I didn't understand the instructions from that link you posted. I am very new to Ubuntu.

---

### Post by timbo3 on 2013-09-15
[SOLVED]
Adding the missing character to a new place in the /usr/share/X11/xkb/symbols/se file helped this issue. se is for swedish in my case. You must be in sudo to correct this. For some reason I couldn't save the changes while using gedit but in emacs it worked. I also had to restart the computer for the changes to take hold.

---

