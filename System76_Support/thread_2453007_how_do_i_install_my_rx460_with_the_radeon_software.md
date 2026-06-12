---
title: "how do i install my rx460 with the radeon software settings"
date: 2020-11-01
forum: System76 Support
---

### Post by avit2019 on 2020-11-01
how do i install my rx460 with the radeon software settings so i can change all settings of my card..this is the only thing that is stopping me using linux full time

---

### Post by QIII on 2020-11-01
Would you please post the results of 

```
lsmod | grep radeon
```

and

```
lsmod | grep amdgpu
```

---

### Post by avit2019 on 2020-11-01
sweet..im guessing thats from cmd

---

### Post by avit2019 on 2020-11-01
in the attachment is all that happened when i used the cmd lines..nothing installed ..no program showed up..like the radeon app in order to change settings of my gpu

---

### Post by QIII on 2020-11-01
What showed up was exactly what you asked for:  which driver module is loaded.

lsmod = list loaded modules

| grep = find the following string

You checked for radeon and amdgpu and you were told that the amdgpu module is loaded.

Because the installation automatically detects which driver module supports your hardware, amdgpu was selected.  

That is the driver -- which is open source -- that is appropriate for your hardware.  There is nothing further to do.  AMD has made that driver available for the Linux developers to include in the kernel with no need to install a driver.

Are you looking for a GUI application to change your settings?  amdgpu does not offer a GUI.  Settings are made in text config files.

While there are GUIs that private people have developed, I can't vouch that any of them works properly and I don't know if you would be satisfied or find yourself with an inoperative system.

The best documentation I have found is [Arch's wiki]("https://wiki.archlinux.org/index.php/AMDGPU").  You may need to adjust things a bit for a deb-based distro like Ubuntu.  Also, much of what is there will need to be preceded by sudo or pkexec.  Arch users often use the root account, so that is not needed.  I use AMD graphics and I consult the Arch Wiki for setting the configs.

Proceed with extreme caution.  Ask questions if you have any doubts.

---

