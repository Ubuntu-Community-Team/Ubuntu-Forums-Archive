---
title: "Black screen when loading unity 3d"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by terry_gardener on 2012-04-21
i have upgraded one of my pcs to 12.04 and when i try and load unity 3d all i get is a black screen with the cursor that is it. 

it is a geforce 6150se GPU using the new nvidia 295.40 driver. 

unity 2d works fine. 

is this part of the nvidia driver issue or is the GPU to crap to handle unity 3d.

---

### Post by soro2005 on 2012-04-21
I think it's safe to assume it's part of the driver issue. Particularly so if in the past, you've run compiz, unity, gnome-shell or some newer version of kde on the machine.

---

### Post by terry_gardener on 2012-04-21
gnome-shell worked under 11.10 but had tearing affect in some apps 
unity struggled to open apps fullscreen in 11.10

---

### Post by soro2005 on 2012-04-21
In any case, you could try whether the nouveau driver is any good for you. Just uninstall the package named nvidia-current. Since compositing is currently not working for you anyway, I can't see what you could lose.

---

### Post by NoNameWill on 2012-04-22
You need to download Nvidia 295.33 then purge nvidia-current

```
sudo apt-get purge nvidia-current
```

```
cd path/to/nvidia_driver
```

```
sudo service lightdm stop
```

```
sudo sh NVIDIA-Linux-x86_64-295.33.run 
```

Do this from tty and not terminal. 

Best to just reboot from tty than try to restart lightdm. At least it was for me unity is glitchy and hung up on restarting for me.

---

### Post by NoNameWill on 2012-04-22
Also install compiz ccsm Unity will need some tweaking to autohide. Still doesn't run smooth after tweaking but aleast it will hide.

---

### Post by suoshao on 2012-04-23
In any case, you could try whether the nouveau driver is any good for you[IMG]http://www.keyforex.info/iPad.gif[/IMG]

---

### Post by NoNameWill on 2012-04-23
How far along has the nouveau driver come in the last year? My geforce 7000m which is the same as the 6150 would not work with nouveau.

---

### Post by terry_gardener on 2012-04-23
the pc is used by my parents and they are currently happy using unity 2d so i will wait for the problem to be fixed. thanks for the replies.

---

### Post by NoNameWill on 2012-04-23
That may be best. With each kernel update the driver may have to be reinstalled. I had to do that in 10.04 for the first year.

---

