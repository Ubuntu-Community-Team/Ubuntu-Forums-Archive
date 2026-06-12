---
title: "connecting to USB keyboard"
date: 2010-01-04
forum: Ubuntu Studio
---

### Post by PsYcHoTiC_MaDmAn on 2010-01-04
put very simply, got ubuntu studio installed (on a 2.2GHz 64bit, 2GB RAM) and got a Kawai MP5.

the kawai has a USB out as well as midi, however I dont have the cables or adapters for using midi.

I have managed to connect the Kawai to Sibelius on laptop a while back (though it lacked anything with timing or expression, was just the note.) using the USB. 

however much as I've been looking I cant find anything about connecting a USB keyboard to any of the ubuntu studio software.

when in jack control and then connections in the alsa section it shows 2 entries as standard (with no other programs running) that being 14:Midi Through > 0:Midi Through Port-0 and 20:USB-MIDI > 0:USB-MIDI MIDI 1

and those options are on both the input and output ports

---

### Post by AutoStatic on 2010-01-04
Hello, maybe this will help: [http://ubuntuforums.org/showpost.php?p=8540958&postcount=18](http://ubuntuforums.org/showpost.php?p=8540958&postcount=18)

Instead of the Keystation you should be able to select USB-MIDI.

---

### Post by raboofje on 2010-01-04
> **PsYcHoTiC_MaDmAn said:**
> 20:USB-MIDI > 0:USB-MIDI MIDI 1

I'd say these should correspond to the midi ports on your card.

You should, however, be able to plug in the keystation and it should show up in the 'alsa' tab. Depending on the exact version of your keystation, you might need to install the midisport-firmware package.

---

