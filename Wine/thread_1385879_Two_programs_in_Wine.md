---
title: "Two programs in Wine"
date: 2010-01-20
forum: Wine
---

### Post by Dweomer on 2010-01-20
Why can't I find how to run two programs in Wine? Seems like it would be a pretty common question.

---

### Post by arubislander on 2010-01-20
> **Dweomer said:**
> Why can't I find how to run two programs in Wine? Seems like it would be a pretty common question.

You mean how do you run two programs at the same time? Or how do you run two specific programs?

---

### Post by beastrace91 on 2010-01-20
Install program a, install program b. Load one or the other from your applications menu...

~Jeff

---

### Post by Dweomer on 2010-01-20
> **beastrace91 said:**
> Install program a, install program b. Load one or the other from your applications menu...

~Jeff

Are you being serious? I thought it obvious I meant running two programs simultaneously. Why would I ask how to run two programs separately if I didn't specify them by name? Wouldn't I just ask how to run a program in wine, or name the specific two programs I was having issues with? If it was truly unclear, I apologize, but yes I need to know how to run two windows program simultaneously. I can't alt+tab back to Ubuntu to run the other after I've started one.

---

### Post by arubislander on 2010-01-20
> **Dweomer said:**
> Are you being serious? I thought it obvious I meant running two programs simultaneously. Why would I ask how to run two programs separately if I didn't specify them by name? Wouldn't I just ask how to run a program in wine, or name the specific two programs I was having issues with? If it was truly unclear, I apologize, but yes I need to know how to run two windows program simultaneously. I can't alt+tab back to Ubuntu to run the other after I've started one.

I am sorry if I offended you... that was not my intention... I just wanted to be clear on the question before I went off suggesting an answer to a problem you didn't have...

Now for your question... as beastrace91 said.. just start one program, and then select the other one...

I am assuming none of the programs are games, and that they startup in their respective windows... You then should be able to click outside the window and start another program. If the window is maximized, you could of course minimize it or unmaximaze it... but somehow, I don't think that is what your problem is... Maybe you could post a screenshot?

---

### Post by beastrace91 on 2010-01-20
> **Dweomer said:**
>  I can't alt+tab back to Ubuntu to run the other after I've started one.

You should be more clear about that next time.

Wined applications that are full screen do not always play nicely with alt+tab - the solution is to run said application in a "virtual desktop". Access this option via your **winecfg**

Regards,
~Jeff

---

### Post by Dweomer on 2010-01-20
> **beastrace91 said:**
> You should be more clear about that next time.

Ha. u trol mi.

Anyway, you helped me out. It was the enabling virtual desktop that I needed to do. It turns out Wine just can't run the other program because it interacts with the first one. Oh well. I'll have to try a virtual box if I ever find my Windows CD.

Thanks.

> Arubislander

No, you didn't offend me. One was a game, and the other was a music player integrated into the game, since using a linux music player in the background was muting my sound, but the second program doesn't work because it interacts with the first. I'll just try VirtualBox. Thanks.

---

