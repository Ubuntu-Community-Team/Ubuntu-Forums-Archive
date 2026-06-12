---
title: "Serval Professional -- Mountall: Disconnected from Plymouth"
date: 2011-12-20
forum: System76 Support
---

### Post by MckayKnight on 2011-12-20
[FONT="Trebuchet MS"]Hey all I just got my brand new Serval Professional last night opened it up and worked flawlessly until...

I updated the system and it installed the necessary nVidia restricted driver for me to use Compiz/Unity 3D to it's fullest.

Though I ran into two minor problems such as these:
1. When it installed the restricted nVidia driver when I rebooted the system it gave me the error message. Mountall: Disconnected from Plymouth. 

2. Now my boot splash is all funky looking and it doesn't work properly like the shudown boot splash does.[/FONT]

In order for me to use the restricted driver I have to completely ctrl-alt-f1 to grab a terminal and log into root. It's the only way I can use it no login screens available.

I'm happily surprised with Ubuntu being stable here and there, but if I can't get those two minor issues fixed I just wasted $2,000 on a laptop box.

Other than that I can freely use Ubuntu with the open source nvidia driver but it lacks Compiz and Unity 3D I also seen how many times the user error has been posted on here yet I haven't found a solution available... :(

---

### Post by isantop on 2011-12-21
Try logging into the text console and running this command:

```
sudo chown lightdm:lightdm -R /var/lib/lightdm
```

Then, reboot. Does that make the issue go away?

---

### Post by MckayKnight on 2011-12-21
[FONT="Trebuchet MS"]Nope, still hasn't fixed it. Remember I'm using the open source nvidia driver whereas I can see my login screen and login.

I'm just surprised at how installing a restricted binary driver pretty much just destoryed my brand new machine.

I need to figure out how to install the driver without having the two minor problems I'm listed above.[/FONT]

[FONT="Trebuchet MS"]Am I better off just reinstalling Ubuntu from scratch and trying to install the nVidia driver yet again to see what happens.[/FONT]

---

### Post by MckayKnight on 2011-12-21
[FONT="Trebuchet MS"]I tried your suggestion with the nVidia driver and yes it fixed the issue.

Just what I was looking for but is there anyway to adjust the boot splash it's far to wide and doesn't look right.[/FONT]

---

### Post by isantop on 2011-12-21
The proprietary Nvidia drivers do not support the required KMS extensions for the boot splash to load properly, so it will appear too large. This is an unfortunate shortcoming of the nivida driver, and will need to be fixed there.

---

