---
title: "install gnome on ubuntu server 10.04"
date: 2010-05-17
forum: Server Platforms
---

### Post by fro1269 on 2010-05-17
I have a ubuntu server install 10.04 LTS, and I want to install the gnome desktop; however, I do not want it to start automatically for performance reasons. I only want to run it at my choosing with startx. if i use sudo apt-get install ubuntu-desktop, will it start auto? if so, how can I take it out of startup?

---

### Post by cdenley on 2010-05-17
> **fro1269 said:**
> if i use sudo apt-get install ubuntu-desktop, will it start auto?

yes
> **fro1269 said:**
> 
if so, how can I take it out of startup?
```

sed -e 's/^start on \(.*\)/start on false and \1/' /etc/init/gdm.conf|sudo tee /etc/init/gdm.conf

```

---

### Post by Groodles on 2010-05-18
> **cdenley said:**
> 
```

sed -e 's/^start on \(.*\)/start on false and \1/' /etc/init/gdm.conf|sudo tee /etc/init/gdm.conf

```

Is it the same if GDM is started by Upstart and not by a script in /etc/init.d/ ?

---

### Post by cdenley on 2010-05-18
> **Groodles said:**
> Is it the same if GDM is started by Upstart and not by a script in /etc/init.d/ ?

Well, if you're using lucid, the script /etc/init.d/gdm is only there for backwards compatibility. That is actually a symlink to /lib/init/upstart-job which just starts the upstart configuration with the same name. Regardless of whether you use the "service" command or the symlink in /etc/init.d, it will be started by upstart. The command I gave modifies the upstart configuration file /etc/init/gdm.conf.

---

### Post by TheFuturian on 2010-05-18
Hi There,

There's some info in one of my threads which I think may be of use ;)

[http://ubuntuforums.org/showthread.php?t=1479980](http://ubuntuforums.org/showthread.php?t=1479980)

---

### Post by cdenley on 2010-05-18
> **TheFuturian said:**
> Hi There,

There's some info in one of my threads which I think may be of use ;)

[http://ubuntuforums.org/showthread.php?t=1479980](http://ubuntuforums.org/showthread.php?t=1479980)

You mean this?
```

sudo mv /etc/init/gdm.conf /etc/init/gdm.disabled

```

I like my command better. It doesn't prevent you from starting gdm manually.
```

sudo service gdm start

```

---

### Post by fro1269 on 2010-05-28
thanks I really appreciate it.

---

### Post by impresionist on 2010-08-04
Hi all,

In my case, under Lucid Server, I did already the mistake, I mean, i installed with: sudo apt-get install ubuntu-desktop

And now I get auto run of the X server, so, when I need to shut it down, every time I have to lunch, and shut it down back...

I don't know if it possible now deactivate the auto start of the x server, to keep it only under my command startx?

Regards,

---

### Post by cdenley on 2010-08-04
> **impresionist said:**
> I don't know if it possible now deactivate the auto start of the x server, to keep it only under my command startx?


Did you read the thread?

---

### Post by StolerTech on 2010-08-04
I hope you didn't install the package yet. You should use gnome-core, it has the least junk. If you install gnome-core, it doesn't use as much from what I can tell. My server running without gnome is 2% cpu load, with gnome-core it is 10%, with ubuntu-desktop it is about 15-25% idle.

---

### Post by fro1269 on 2010-08-14
> **StolerTech said:**
> I hope you didn't install the package yet.

Unfortunatly I did install the package since it has been a few months since I asked my inital question ; however, I will look into switching to gnome-core to save some cpu. thanks!

I also found this thread which has some additional info on how to manage grub2

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1526732](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1526732)

---

### Post by diminuendo on 2010-12-01
```

sed -e 's/^start on \(.*\)/start on false and \1/' /etc/init/gdm.conf|sudo tee /etc/init/gdm.conf

```Will this code work with xubuntu too?

---

### Post by warfie on 2013-03-30
> **cdenley said:**
> yes

```

sed -e 's/^start on \(.*\)/start on false and \1/' /etc/init/gdm.conf|sudo tee /etc/init/gdm.conf

```

What exactly does one do with this code? Just enter it in a terminal? Add it to some script somewhere? Edit the GRUB script at boot?

Sorry, that I'm so stupid that I need to ask...

---

