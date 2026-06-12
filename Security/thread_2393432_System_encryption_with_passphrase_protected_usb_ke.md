---
title: "System encryption with passphrase protected usb key, how to configure ubuntu boot"
date: 2018-06-03
forum: Security
---

### Post by cgcuriouscg on 2018-06-03
I'm trying the solution posted here [http://blog.refu.co/?p=1398](http://blog.refu.co/?p=1398) to enable full disk luks encryption which requires the presence of a usb key to boot the system. The guide is writte for Arch which uses mkinitcpio and that's the part where I get stuck on ubuntu. Is ubuntu using it? If so, which package should I install to use it or is ubuntu using a different way of booting that can be used to access and decrypt the usb key during boot? 

> [COLOR=#1A1A1A][FONT=Merriweather]he bootloader loads the kernel and the initramfs scripts from the boot partition. The new iteration of initramfs is called [/FONT][/COLOR][mkinitcpio]("https://wiki.archlinux.org/index.php/Mkinitcpio")[COLOR=#1A1A1A][FONT=Merriweather] and is essentially a very small early userspace environment which loads various kernel modules and sets up all necessary things before handing control over to init.[/FONT][/COLOR][COLOR=#1A1A1A][FONT=Merriweather]We can use the already existing encrypt and lvm2hooks of mkinitcpio. To enable them edit /etc/mkinitcpio.conf and add them in the HOOKS line. They should be added before the filesystemshook. so in essence it should look like this:[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Merriweather][COLOR=#268BD2]HOOKS[/COLOR]=[COLOR=#2AA198]"... encrypt lvm2 ... filesystems ..."[/COLOR]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Merriweather]Run the following in order to create the updated initcpio scripts.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Inconsolata]mkinitcpio -p linux[/FONT][/COLOR]


Thank you very much for any help, information or pointers in the right direction.

---

### Post by TheFu on 2018-06-04
Linux distros aren't usually all that different really. Try it. See if it works.   That's the only way to be sure.  

I use a yukikey and passphrase to secure my LUKS disks and there is a 80+ random character backup access code with my lawyer.  LUKS/dm-crypt has 8 slots for these things.

---

### Post by cgcuriouscg on 2018-06-05
> **TheFu said:**
> Linux distros aren't usually all that different really. Try it. See if it works.   That's the only way to be sure.  

I use a yukikey and passphrase to secure my LUKS disks and there is a 80+ random character backup access code with my lawyer.  LUKS/dm-crypt has 8 slots for these things.


Thank you for your response. Will you share how you configured your setup to use yubikey and password on LUKS ? That would be very helpful! Thanks again.

---

### Post by TheFu on 2018-06-05
> **cgcuriouscg said:**
> Thank you for your response. Will you share how you configured your setup to use yubikey and password on LUKS ? That would be very helpful! Thanks again.

Nothing special.  A passphrase (something I know) merged with a long, static, stored characters in the yubikey (something I have). It is far from perfect. By using an "AnyKey" instead which requires a pin to unlock access, it would be much better.
Yubikeys are just HIDs as far as the computer knows.

I've seen that some people setup the OTP options for this, but that seemed like more hassle than I was willing to deal with.

---

### Post by cgcuriouscg on 2018-06-06
> **TheFu said:**
> Nothing special.  A passphrase (something I know) merged with a long, static, stored characters in the yubikey (something I have). It is far from perfect. By using an "AnyKey" instead which requires a pin to unlock access, it would be much better.
Yubikeys are just HIDs as far as the computer knows.

I've seen that some people setup the OTP options for this, but that seemed like more hassle than I was willing to deal with.

Thanks! I wonder if using a HID is less secure than an encrypted keyfile on a usb drive for different threat scenarios, loosing the device, having a keylogger etc, (someone having physical access and somehow logging on the hardware usb) but the HID route is probably a very reasonable route to go, though the password file is free since I have usb sticks and no yubikey yet :-)

The anykey seems to recommend what you are doing, enter a pin and the rest of the pw string comes from the anykey, not unlocking the anykey with a pin, as via google translate:
[COLOR=#FFFFFF][FONT=Lato]For a higher security you can also type a pin code yourself and then have AnyKey add the rest of your password. [/FONT][/COLOR][COLOR=#FFFFFF][FONT=Lato]In this way, safety is ensured in the event of loss or theft.[/FONT][/COLOR]

---

### Post by TheFu on 2018-06-06
If you want to avoid the "evil maid" attack, then you need to keep the boot code with you always.

I don't see how a flash drive with a keyfile is any more secure than a yubikey in the practical world.  Sure, in theory a 4K key is billions of times better than a passphrase + 30+ character code from the yubikey (minus 12 characters which are public as the yubikey identifier), but with mostly random entries and local access required, does that difference matter?  Inside LUKS, the encryption isn't any different since the unlock allows access to the real data encryption key and isn't used for the data encryption at all.

Plus, I carry a few different yubikeys and have never shared the length of my passphrase. I suppose someone with a video camera could slow down the typing and figure that out ... even I'm not that paranoid.  My passphrase is not a pin code.

Please don't use funny fonts/colors.

---

