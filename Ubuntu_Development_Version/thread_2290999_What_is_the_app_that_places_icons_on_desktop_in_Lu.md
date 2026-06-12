---
title: "What is the app that places icons on desktop in Lubuntu?"
date: 2015-08-17
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-08-17
What is the app that places icons on desktop in Lubuntu? Is it a Xfce app?

---

### Post by vasa1 on 2015-08-17
PCManFM.

---

### Post by Chanath on 2015-08-17
> **vasa1 said:**
> PCManFM.
Thanks. Will it do so in Openbox too?
Can you tell me how to make a text file executable in PCManFM?

---

### Post by vasa1 on 2015-08-17
> **Chanath said:**
> Thanks. Will it do so in Openbox too?
Can you tell me how to make a text file executable in PCManFM?

AFAIK, if you're referring to the Openbox session, there's no desktop to speak of in the sense of icons of files or folders or apps or shortcuts being visible by default.

But, if you're running an Openbox session there maybe a way to show some icons, etc. The image I'm attaching is from here: [http://openbox.org/wiki/Help:Contents](http://openbox.org/wiki/Help:Contents) under the section titled "Panels, widgets, desktops, pagers, etc.. " Please note that I haven't tried either.

Re. making "a text file executable in PCManFM?" do you mean a script? I have mine in *~/bin*. While it can be done from the terminal, I find it easier to use PCManFM. (I have version 1.2). I right-click on the file, choose *Properties*, *Permissions*. The default "Access Control > Execute" is *Nobody*, but you can change that to *Owner*. I hope I understood correctly!

---

### Post by Chanath on 2015-08-17
> **vasa1 said:**
> Re. making "a text file executable in PCManFM?" do you mean a script? I have mine in *~/bin*. While it can be done from the terminal, I find it easier to use PCManFM. (I have version 1.2). I right-click on the file, choose *Properties*, *Permissions*. The default "Access Control > Execute" is *Nobody*, but you can change that to *Owner*. I hope I understood correctly!

Thank you!

In Thunar, you click "make this file executable" in the Permissions box to make a script executable, is changing Access Control>Execute to Owner make the script executable? I haven't used PCmanFM for years. For last few years Thunar was my favourite.

About desktop icons; I actually don't want them, only asked out of curiosity. I find Openbox much easier and nicer to use. :)

---

### Post by vasa1 on 2015-08-17
> **Chanath said:**
> ..., is changing Access Control>Execute to Owner make the script executable? 
Yes, exactly.
> **Chanath said:**
>  ... I find Openbox much easier and nicer to use. :)
I'm using it as well.

---

