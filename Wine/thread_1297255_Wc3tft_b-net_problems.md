---
title: "Wc3/tft b-net problems"
date: 2009-10-21
forum: Wine
---

### Post by banquo on 2009-10-21
HI every1!

i know a lot of u guys out there are great at linux som i am confident that some1 
could help me out with this one;

i used play Warcraft III : the frozen throne quite alot, but since the last patch i cannot connect to battle.net does.

does anyone know how to fix this problem? ive surfed around a bit, and it seems that it's not anything wrong with my computer/connection (well i guess i figured that much out myself^^ ) but something with the latest patch, and its compability with linux. 

thanks, oskar

---

### Post by beastrace91 on 2009-10-21
Did they just recently release a new patch version? Let me fire up my WC3 install and see what it does :)

In the mean time Wine version, gfx card, and driver version? Also did your WC3 work fine prior to this last update?

~Jeff

---

### Post by beastrace91 on 2009-10-21
It appears I need to reinstall WC3 >.< Will do some tomorrow and see if I can help some.

~Jeff

---

### Post by banquo on 2009-10-22
I'm not sure if it is the latest patch anymore, it's at least 6 months old, i
tried some scripts and stuff, but i didnt get it to work, so i gave up.
Yes it worked great prior to that patch.

---

### Post by beastrace91 on 2009-10-22
> **beastrace91 said:**
> In the mean time Wine version, gfx card, and driver version?

Also does WC3 work in general other than not connecting to battle.net?

~Jeff

---

### Post by banquo on 2009-10-22
oh, im sorry ;

Wine 1.1.30 (thinks thats right, although 1.1.30 sounds old :S i update it about 2 weeks ago)

My graphics driver ; NVIDIA accelerated graphics driver (version 180)
my 3D-card is Geforce 8400M GT GPU

---

### Post by beastrace91 on 2009-10-22
In terminal run ```
wine --version
``` to get your exact version number.

And other than not connecting to battle.net it runs fine? (LAN/Single player)

~Jeff

---

### Post by banquo on 2009-10-24
Wine version; wine-1.1.30

yes, no problems w wc3 besides bnet, LAN and regular gaming works fine. the only problem is that i can&#7831; connect to bnet, or rather i cant login. after ive entered my password and is about to log in, wc3 / wine crashes with the following message:

```

This application has encountered a critical error :
FATAL ERROR!
program : ... ... \war3.exe
exception : 0xC0000005 (ACCES_VIOLATION) at 0073:6F7E5AC1

The instruction at  '0x6F7E5AC1' referenced memory at '0x00000078'
the memory could not be 'written'

press OK to termnate the application


```

---

### Post by beastrace91 on 2009-10-24
Try downgrading your Wine version to .28 or .29 and give it a go. (these are two of the most current + stable versions of Wine for most games)

~Jeff

---

