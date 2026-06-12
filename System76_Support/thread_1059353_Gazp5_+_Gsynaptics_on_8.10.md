---
title: "Gazp5 + Gsynaptics on 8.10"
date: 2009-02-03
forum: System76 Support
---

### Post by LinuxPS2 on 2009-02-03
It seems that I cannot get gsynaptics to work on my gazelle, I continuously get the SHMConfig error despite both adding the section to my xorg.conf (though its a tad outdated with 8.10) and following [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig") when I run 'xinput list' a touchpad interface does not appear. any thoughts?

oh and here is the result of the 'xinput list'
```
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Macintosh mouse button emulation"	id=2	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"ImPS/2 Logitech Wheel Mouse"	id=3	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```
the HAL solution worked on my old acer that I put 8.10 on but is a no-go on my gazelle

---

### Post by thomasaaron on 2009-02-03
The GazP5 has a ElandTech mousepad. ElandTech touchpads do not work with Gsynaptics, which is made to configure Synaptic touchpads.

---

### Post by LinuxPS2 on 2009-02-03
is there anyway to garner the same functionality from it?... eg. circular scrolling etc?...

---

### Post by thomasaaron on 2009-02-03
Not that I'm aware of. At one point, some developers were trying to put together a better driver for ElanTech touchpads. But I don't think it ever amounted to anything.

---

