---
title: "Lynx/Meerkat/ffado - a plea for clarity..."
date: 2010-11-06
forum: Ubuntu Studio
---

### Post by mango42 on 2010-11-06
Could someone clarify a very basic question for me?

Like many here I am trying to get a Focusrite Saffire 40* to work in UbuntuStudio. I thought that installing an LTS (Long Term Support) version, ie. Lucid Lynx, would allow me to settle down to 3-4 years consistent support *but* it seems that when it comes to firewire, it is still necessary to follow the 'bleeding edge', (ie: Maverick Meerkat et seq.) of development due largely to the changeover in stack (JuJu?) and 'firewire' rather than ohci1394/raw1394 drivers.

Is this the case or will Lucid Lynx Studio eventually be updated to encompass and reflect the recent developments necessary to get this firewire interface to work properly?

Increasingly :confused:

Thank you for your forbearance.

--------------------------------------------------
* Some background: Thanks mainly to AutoStatic & Trulan's efforts with updating the relevant wiki's, I have reached the stage where Jack recognises *and displays* the Saffire 40's I/O yet there is obviously some clocking issue or the like, as unless I run the non-functional(?) 'ffado mixer' first then close it (which even then seems to prevent jackd from loading the firewire driver), channels 5 thru 8 *on the hardware* show a -6 to -3dB constant signal, despite there being no sound, no input and no noise. This concerns me to the extent as to whether this is causing any damage to the hardware or not...

---

### Post by AutoStatic on 2010-11-06
mango42, I've updated my FFADO packages so the mixer partly works. The part that isn't functional yet is the routing, but I think if I package a more recent svn checkout that should work too.
Not sure where your signal issue comes from but I think it has something to do with the routing, apparently something is looping in the mixer matrix. Do you still have a Windows machine with a FireWire connection? Or a [BartPE]("http://www.nu2.nu/pebuilder/") Windows boot CD? Then you could try adjusting the mixer matrix with the Saffire MixerControl software. I use the [oldest stable version (1.5)]("http://beta.focusrite.com/releases/saffire_mix_control/") because the latest version wants to update the firmware and I'm a bit relectant to do that as I'm not sure if FFADO will still recognize the device afterwards. The 1.5 version does nag about firmware too but at least the mixer works.

And no need to go bleeding edge. Stick with 10.04, use my packages or try the ones from Tango Studio ([http://tangostudio.tuxfamily.org/en/packages](http://tangostudio.tuxfamily.org/en/packages)). No need to use the new FireWire stack either.

Best,

Jeremy

---

### Post by mango42 on 2010-11-06
Thanks once again for your very prompt response, **AutoStatic** and your explanation of where the *ffado mixer* is at. The way I understand it, shouldn't QJackCTL or QTractor, Ardour etc handle basic mixer functionality in their connect and mixer dialogs, without getting ffado mixer involved? I'll visit your PPA again ASAP :KS

Unfortunately(? no loss, IMO), Windows blinks on and off at ~1 sec intervals on the machine that allows firewire to work (due to a hardware problem; most likely one video RAM chip in the SLI setup is damaged) when using the nVidia drivers, whereas on Linux, nv or nouveau drivers work fine (perhaps they use system RAM or just one video card?)

I'm very glad to hear I can stay with 10.04 as that reduces the imponderables a bit ;-)

---

### Post by AutoStatic on 2010-11-06
> **mango42 said:**
> The way I understand it, shouldn't QJackCTL or QTractor, Ardour etc handle basic mixer functionality in their connect and mixer dialogs, without getting ffado mixer involved?That's right. You only need ffado-mixer to adjust the internal routing of the Saffire Pro 40, in other words, the monitoring settings. Once you've set that up to your liking you can have Ardour or Qtractor do the monitoring. With the Windows Saffire MixControl application I've set the Routing Preset to 'DAW Tracking' and set the monitor volume of all analog inputs to 0 iirc. 

[http://focusrite.com/support/download/saffire_pro_40_user_guide/614](http://focusrite.com/support/download/saffire_pro_40_user_guide/614) (Page 10 and further)

> **mango42 said:**
> Unfortunately(? no loss, IMO), Windows blinks on and off at ~1 sec intervals on the machine that allows firewire to work (due to a hardware problem; most likely one video RAM chip in the SLI setup is damaged) when using the nVidia drivers, whereas on Linux, nv or nouveau drivers work fine (perhaps they use system RAM or just one video card?)Can't help you with that other than suggesting you could try the onboard graphics controller (assuming your mobo has one).

> **mango42 said:**
> I'm very glad to hear I can stay with 10.04 as that reduces the imponderables a bit ;-)Yes, you can stay with 10.04. There won't be any FFADO updates in the official repo's (unless those packages have a security flaw) but that's where the multimedia PPA's like mine are for.

---

### Post by mango42 on 2010-11-06
[QUOTE="AutoStatic"]That's right. You only need ffado-mixer to adjust the internal routing of the Saffire Pro 40, in other words, the monitoring settings.[/QUOTE]

To be absolutely clear on this, are you saying that ffado-mixer or it's windows equivalent are necessary (essential?) to set hardware routings; ie: values written to non-volatile memory in the Saffire?

Hmm, perhaps I should backtrack and re-RTFM ;-)

---

