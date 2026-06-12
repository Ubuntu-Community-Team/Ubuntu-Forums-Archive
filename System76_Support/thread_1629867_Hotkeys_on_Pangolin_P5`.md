---
title: "Hotkeys on Pangolin P5`"
date: 2010-11-24
forum: System76 Support
---

### Post by jtappin on 2010-11-24
For a number of reasons I'd like to switch my Pangolin P5 to Pardus, however right now there are some issues with hotkeys at least with the live image of the upcoming 2011 edition.

Specifically the following do not work:
Fn F1 -- toggle touchpad 
Fn F11 -- toggle wireless
Fn F4 -- sleep (though I'm not too bothered about that one)
All the others look OK, in fact the video output switching is (IMHO) better as it automatically scales to the external monitor [a difference between the Nvidia and Nouveau drivers?].

Does anybody know what needs to be done to make those keys work?
I've looked through the System76 driver code and can't find any clues there (that of course doesn't mean there aren't any, just I couldnt find them).

---

### Post by isantop on 2010-11-24
The Touchpad hotkey should work in any OS (Even something like DOS) as I don't believe it's tied to software; rather to hardware. Does it still work in Ubuntu?

For the wireless, it may be that the wireless card is not supported by Pardus. Similar issues with suspend.

---

### Post by isantop on 2010-11-24
The Touchpad hotkey should work in any OS (Even something like DOS) as I don't believe it's tied to software; rather to hardware. Does it still work in Ubuntu?

For the wireless, it may be that the wireless card is not supported by Pardus. Similar issues with suspend.

---

### Post by isantop on 2010-11-24
The Touchpad hotkey should work in any OS (Even something like DOS) as I don't believe it's tied to software; rather to hardware. Does it still work in Ubuntu?

For the wireless, it may be that the wireless card is not supported by Pardus. Similar issues with suspend.

---

### Post by isantop on 2010-11-24
The Touchpad hotkey should work in any OS (Even something like DOS) as I don't believe it's tied to software; rather to hardware. Does it still work in Ubuntu?

For the wireless, it may be that the wireless card is not supported by Pardus. Similar issues with suspend.

---

### Post by jtappin on 2010-11-24
> **isantop said:**
> The Touchpad hotkey should work in any OS (Even something like DOS) as I don't believe it's tied to software; rather to hardware. Does it still work in Ubuntu?

Yes it does.

> **isantop said:**
> 
For the wireless, it may be that the wireless card is not supported by Pardus. Similar issues with suspend.

The iwlagn module is present and loaded, and the kernel is a more recent one than on Maverick 2.6.36 rather than 2.6.35. The network manager reports a wireless device as present but unavailable.

I did manage to find some comments related to broadcom cards that suggested that the various CONFIG_RFKILL kernel options may not be enabled -- I'll try to chase that down on my installed Pardus machines and if that is the case report it as a wishlist item in their bug system.

---

### Post by jtappin on 2010-11-24
> **jtappin said:**
> 
I did manage to find some comments related to broadcom cards that suggested that the various CONFIG_RFKILL kernel options may not be enabled -- I'll try to chase that down on my installed Pardus machines and if that is the case report it as a wishlist item in their bug system.

I've managed to chase that down: on Pardus rfkill is compiled as a module and it is loaded on those machines with wireless (including the PanP5 booted from the live media).

---

