---
title: "Is it possible to install Chinese games in wine?"
date: 2010-07-29
forum: Wine
---

### Post by buzhidao on 2010-07-29
Hello,
I want to install some windows games with chinese characters in ubuntu, the only solution I can find so far is to do it through wine, but after the game is installed, all characters turns into ? . :(

I have no problem to read any Chinese or other Asian documents in ubuntu, so I suppose it has something to do with the font lib in wine? Does anyone know how to solve this problem, or is it even possible to install a chinese version windows game in ubuntu?:confused:

Thanks

Cherie

---

### Post by asdfoo on 2010-07-30
> **buzhidao said:**
> Hello,
I want to install some windows games with chinese characters in ubuntu, the only solution I can find so far is to do it through wine, but after the game is installed, all characters turns into ? . :(

I have no problem to read any Chinese or other Asian documents in ubuntu, so I suppose it has something to do with the font lib in wine? Does anyone know how to solve this problem, or is it even possible to install a chinese version windows game in ubuntu?:confused:

Thanks

Cherie

yes, chinese symbols may not exist... you can try installing corefonts?

winetricks corefonts

---

### Post by buzhidao on 2010-08-03
Thanks for the reply, how can I install corefonts ?is it 
sh winetricks corefonts

but I get 

sh: Can't open winetricks


did I miss anything?

---

### Post by elmaz on 2010-08-03
Hi,

You can press Alt + F2, type *winetricks* then enter, tick 'allfonts' and try again, hope this can help you.

---

