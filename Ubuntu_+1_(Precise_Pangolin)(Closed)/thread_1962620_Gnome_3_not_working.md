---
title: "Gnome 3 not working"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prinknash on 2012-04-21
I've just moved from 11.10 to 12.04 beta 2 (64) with a fresh install. Previously I always used Gnome 3 as my desktop environment and I tried to do the same again. But 12.04 won't start in "Gnome" and gives me Gnome Classic instead. If I then do "gnome-shell --replace" from terminal, I do get the familiar Gnome 3 environment, but as soon as I close the terminal window Gnome freezes and I have to exit.

The error messages I get after "gnome-shell --replace" are:
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)

I've tried googling the error messages but haven't been able to establish whether this is a general problem with beta 2 or if something has gone a bit awry in my installation of it. I've cleared out the .local/share/gnome-shell/extensions folder and tried removing and reinstalling the gnome shell but that didn't solve anything. If anyone can tell me something I can do to fix it, I'd be immensely grateful.

Many thanks.

p

---

### Post by dino99 on 2012-04-21
there is actually lot of issues with some geforce cards & nvidia 295.40 (6, 7 & 8800), is your card one of them ?

The workaround is to install gnome-classic as GS & unity are affected : they are either broken or very slow

The errors you got might be of previous GS process still not killed when you have set the command

---

### Post by prinknash on 2012-04-21
Thanks dino99. I'm actually using a (quite old) Nvidia GeForce 8300GS with driver 295.40. So it sounds like that could be the problem. 

Presumably we're waiting for Nvidia to release a driver that plays nicely with Gnome 3 and I can't just go back to the driver I was using with Ubuntu 11.10? Gnome 3 worked fine until I upgraded to the 12.04 beta this morning.

p

---

### Post by prinknash on 2012-04-21
Well, I discovered that uninstalling the 'additional driver' and rebooting with the nouveau driver lets me use Gnome 3 again. So that seems (so far!) to be an answer, if not an ideal one.

p

---

### Post by xebian on 2012-04-21
Using a much older GeForce 7300SE/7200GS witn 295.40 here with no problem.

---

### Post by xebian on 2012-04-21
To be 'precise', Ubuntu 12.04 is running on Gnome 3 whether you use  Unity, or gnome-shell, or cinnamon, or etc.

---

### Post by prinknash on 2012-04-21
You're right, of course. But you know what I mean ......

The only tiresome thing now is that when I tried to run nvidia-settings to see what driver I was using, I got an error message saying that I didn't seem to be using the nvidia x driver and that I needed to edit the x configuration file by running nvidia-xconfig as root and restarting the x server. But I don't have an nvidia-xconfig file. Oh, I don't expect it matters.

p

---

### Post by pbrane on 2012-04-21
> **dino99 said:**
> there is actually lot of issues with some geforce cards & nvidia 295.40 (6, 7 & 8800), is your card one of them ?

The workaround is to install gnome-classic as GS & unity are affected : they are either broken or very slow

The errors you got might be of previous GS process still not killed when you have set the command

Although I'm not running Precise I don't have any issues with my  nVidia 8600 running the 295.40 drivers. I don't use unity or GS or compositing either. 

I found this link about the issues: [http://www.pclinuxos.com/forum/index.php?topic=104561.0]("http://www.pclinuxos.com/forum/index.php?topic=104561.0")

---

### Post by soro2005 on 2012-04-21
> **prinknash said:**
> You're right, of course. But you know what I mean ......

The only tiresome thing now is that when I tried to run nvidia-settings to see what driver I was using, I got an error message saying that I didn't seem to be using the nvidia x driver and that I needed to edit the x configuration file by running nvidia-xconfig as root and restarting the x server. But I don't have an nvidia-xconfig file. Oh, I don't expect it matters.

p

If you're running on the nouveau driver, then you're not using the nvidia driver. Those two are mutually exclusive alternatives. If you're forcing the nvidia driver through an x config file, then that will fail, because for the nouveau driver to work, you will have uninstalled the nvidia driver. In other words, as long as you're using the nouveau driver, just forget about nvidia-settings. It's nothing to do with it. It's only good for the nvidia proprietary driver.

From your first post at the head of the thread: If you close the terminal from which you've run a command, then the process you've initiated from that terminal (in this case gnome-shell --replace) will terminate. The process is linked to the terminal. To prevent this from happening, you can run the command as follows:
```
gnome-shell --replace &
```
Note the ampersand at the end. You can then close the terminal by typing
```
exit
```
into it.

Or alternatively, you can hit Alt+F2 and type gnome-shell --replace into the run dialog that should open.

The nvidia driver is screwed up big time for many of us. Unfortunately that is how it is. I think they're working on it, and perhaps some good soul will soon provide packages with a driver version before the big screw up. In the meantime, my Gnome Shell works fairly well once I get it to run. I have frequent temporary hang-ups, though, and the occasional no-show after suspends.

---

### Post by prinknash on 2012-04-21
That's very interesting and helpful, soro. Thanks. It's good to learn new stuff, like the use of the ampersand.

I'd figured out that nvidia-settings and nvidia-configx are part of a package with the nvidia driver and that as I wasn't using the 'closed source' driver I didn't have them. I then started wondering whether there was any mileage in trying to use one of the older nvidia drivers which still seem to be available in Synaptic. But nouveau seems to be working all right for me so I'm happy to stick with that.

p

---

### Post by xebian on 2012-04-21
> **prinknash said:**
> That's very interesting and helpful, soro. Thanks. It's good to learn new stuff, like the use of the ampersand.

I'd figured out that nvidia-settings and nvidia-configx are part of a package with the nvidia driver and that as I wasn't using the 'closed source' driver I didn't have them. I then started wondering whether there was any mileage in trying to use one of the older nvidia drivers which still seem to be available in Synaptic. But nouveau seems to be working all right for me so I'm happy to stick with that.

p

nouveau is quite nice btw and if you are happy with it then it's fine.

But sometimes a simple re-install of nvidia-current would do the trick.  IIRC there was a libc6 update so a re-compile is probably needed.  Usually, you get the gnome classic as a fallback when gnome-shell can't load because of 3d-accelaration is not available.  Sometimes this happens when nouveau gets loaded first.

I use the NVidia installer from nvidia and everytime I get the fallback a recompile is just I needed to do.

---

