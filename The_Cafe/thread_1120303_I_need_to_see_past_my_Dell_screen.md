---
title: "I need to see past my Dell screen"
date: 2009-04-08
forum: The Cafe
---

### Post by swoll1980 on 2009-04-08
When I turn my computer on there's a Dell screen. If I hit pause/break it will freeze the boot, and stop the progress bar. Is there a way to see what the computer is doing here. A way to see verbose output?

---

### Post by matrixblue on 2009-04-08
Check the BIOS for an option to disable quick boot

---

### Post by damis648 on 2009-04-08
> **swoll1980 said:**
> When I turn my computer on there's a Dell screen. If I hit pause/break it will freeze the boot, and stop the progress bar. Is there a way to see what the computer is doing here. A way to see verbose output?

That's called POST. :popcorn:

Often in the BIOS settings there is an option to what you want to see during post, a splash or verbose/extra info. See if there is an option like that. :popcorn:

---

### Post by swoll1980 on 2009-04-08
Thanks guys. I turned the fast boot off. It boots slower, but still wont show me anything. There's no options for a splash in the setup menu. I've googled the crap out of this, but found nothing. Got any other ideas? A key combo maybe?

---

### Post by matrixblue on 2009-04-08
What exactly are you looking for?

---

### Post by swoll1980 on 2009-04-08
> **matrixblue said:**
> What exactly are you looking for?

It's a home work assignment I'm supposed to watch the boot process, and write down my observations. The POST, and other such things.

---

### Post by Skripka on 2009-04-08
> **swoll1980 said:**
> Thanks guys. I turned the fast boot off. It boots slower, but still wont show me anything. There's no options for a splash in the setup menu. I've googled the crap out of this, but found nothing. Got any other ideas? A key combo maybe?

Who wrote the BIOS?

Every BIOS I've ever come across has an option to hide the boot logo/splash--they might call it different, but every BIOS I've seen at all recently can do that...

---

### Post by tjwoosta on 2009-04-08
i dont know if this is what you want, but you can watch the boot process of ubuntu if you edit your grub file to show a verbose output instead of the bootsplash

```

sudo gedit /boot/grub/menu.lst


```

down toward the bottom of the file you will see your ubuntu entries

(they will look similar to this, except for ubuntu)

```


title  Arch Linux
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/9a7a347f-83cc-455d-a4d8-3dadce1e52d0 ro vga=791 splash=silent
initrd /boot/kernel26.img


```


see where it says splash=silent

change it to say splash=verbose or nosplash

so it will look like this

```


title  Arch Linux
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/9a7a347f-83cc-455d-a4d8-3dadce1e52d0 ro vga=791 splash=verbose
initrd /boot/kernel26.img

```

---

### Post by matrixblue on 2009-04-08
Oh I get it now. Back in the day the BIOS would show all sorts of info about connected hardware and memory testing et.

Nowadays computers try to be as non technical as possible and hide that info from the users.

I'd try searching a dell forum and if that doesn't work try searching youtube for a video of an older system booting.

---

### Post by FuturePilot on 2009-04-08
Sometimes there's a certain key to press and it will actually switch it to verbose mode. I know one of my computers is like that.

---

### Post by swoll1980 on 2009-04-08
> **Skripka said:**
> Who wrote the BIOS?

Every BIOS I've ever come across has an option to hide the boot logo/splash--they might call it different, but every BIOS I've seen at all recently can do that...

It doesn't say what kind of BIOS it is anywhere. It's version A05 of whatever BIOS is. I want to say it's a Phoenix, just because every other Dell I ever used had a Phoenix.

---

### Post by cariboo on 2009-04-08
I'm closing this thread, as I'm sure part of the homework assignment, is figuring out how to disable the splash screen.

Jim

---

