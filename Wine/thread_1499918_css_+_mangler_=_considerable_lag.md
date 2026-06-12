---
title: "css + mangler = considerable lag?"
date: 2010-06-02
forum: Wine
---

### Post by Metrop021 on 2010-06-02
I think i found a topic somewhere that addressed this issue but i've had trouble finding it again. Basically what the title says, running css with mangler in a vent server lags my css (cursor only lag it seems) considerably more than when i run without it, this is kind of annoying since my temporary solution is to use my laptop to run ventrilo while i let my desktop play css.

anyone run in to a similar problem?

---

### Post by asdfoo on 2010-06-02
what is mangler? is there a download available for me or someone else to try it?  which version of vent 2 or 3?
have you tried using the latest version of Wine 1.2-rc2

which video card and drivers are you using?

---

### Post by Metrop021 on 2010-06-02
mangler is a linux equivalent of the ventrilo client, since the linux vent client has been 'in development' for years. [http://www.mangler.org/](http://www.mangler.org/)
if there's a better native linux ventrilo replacement/alternative then let me know, mangler works quite well though apart from this problem. It's connecting to a ventrilo 3.x server but i'm not sure that matters, and yes this is with wine 1.2 rc1.

I'm using an nvidia 7300 LE (piece of complete ****), with the nvidia 195 driver (latest version i'm pretty sure). even though the card is terrible, mangler shouldn't be lagging anything that the card is playing...

---

### Post by asdfoo on 2010-06-03
> **Metrop021 said:**
> mangler is a linux equivalent of the ventrilo client, since the linux vent client has been 'in development' for years. [http://www.mangler.org/](http://www.mangler.org/)
if there's a better native linux ventrilo replacement/alternative then let me know, mangler works quite well though apart from this problem. It's connecting to a ventrilo 3.x server but i'm not sure that matters, and yes this is with wine 1.2 rc1.

I'm using an nvidia 7300 LE (piece of complete ****), with the nvidia 195 driver (latest version i'm pretty sure). even though the card is terrible, mangler shouldn't be lagging anything that the card is playing...

I think you can try using -dxlevel 80 to get a slightly higher fps at the cost of lower detail.

  I don't know, mangler could be using a lot of CPU?  if you open a terminal and type top, it will show you what's running.

---

### Post by ekilfoil on 2010-06-05
This is probably because we open and close the input device every time we check the mouse state.  It's probably not a bug with WINE or CSS, just a conflict caused by my bad code. :P

---

### Post by Ha&#1093;ar on 2010-06-05
We've committed a fix to trunk which may work for you if you can compile from source.

The final version of Mangler 1.2 will contain this fix if it does work for you and be released at some point.

---

### Post by Metrop021 on 2010-06-08
Ah sweet thanks, yeah i've noticed it's only when i'm transmitting really, maybe it lags slightly when i receive but mainly it's when i transmit. Cheers i'll be checking the mangler site often for a new version.

I'll try compiling from source.

---

### Post by Metrop021 on 2010-06-08
tried to compile mangler from source. I couldnt find the trunk source code anywhere.

```

/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1767: undefined reference to `XListInputDevices'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1778: undefined reference to `XOpenDevice'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1782: undefined reference to `XQueryDeviceState'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1805: undefined reference to `XFreeDeviceState'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1806: undefined reference to `XFreeDeviceList'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1807: undefined reference to `XCloseDevice'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1805: undefined reference to `XFreeDeviceState'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1806: undefined reference to `XFreeDeviceList'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/mangler.cpp:1807: undefined reference to `XCloseDevice'
manglersettings.o: In function `ManglerSettings::getInputDeviceList()':
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/manglersettings.cpp:745: undefined reference to `XListInputDevices'
/home/nicolas/Téléchargements/mangler-1.2.0beta1/src/manglersettings.cpp:751: undefined reference to `XFreeDeviceList'
collect2: ld returned 1 exit status
make[2]: *** [mangler] Erreur 1
make[2]: quittant le répertoire « /home/nicolas/Téléchargements/mangler-1.2.0beta1/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/nicolas/Téléchargements/mangler-1.2.0beta1 »
make: *** [all] Erreur 2

```

my usual luck with source compiling

---

### Post by haidivolume on 2010-06-08
[COLOR=black]running css with mangler in a vent server lags my css (cursor only lag it seems) considerably more than when i run without it[/COLOR]

---

### Post by Metrop021 on 2010-06-08
yep, its frustrating isn't it? my comp can barely run css as is, i have to use some pathetically small resolution to get 30+ fps.

---

