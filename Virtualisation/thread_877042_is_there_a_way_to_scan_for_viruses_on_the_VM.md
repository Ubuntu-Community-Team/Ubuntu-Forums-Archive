---
title: "is there a way to scan for viruses on the VM?"
date: 2008-08-01
forum: Virtualisation
---

### Post by eival on 2008-08-01
i dont want to have to install one inside the VM an have it using ram

is there any AV for Ubuntu that will scan for windows xp intrusions on the VM?

---

### Post by aysiu on 2008-08-01
If you boot a Ubuntu live CD inside the VM, you might be able to use that to scan for viruses.

---

### Post by Keithel on 2008-08-01
I don't think there's any reason you couldn't do something like this:

* Set up ClamAV on your Ubuntu host.
* Get networking all set up on your VM, so that it can see your VM host and vice versa.
* Share out all of your drives in your Windows VM (typically just C:\)
, with perms set so that your VM host can read all files 
* Set up samba to mount your guest VM share(s) you just set up
* Configure ClamAV to virus check those newly mounted directories.

I haven't tested any of the above, so this may not work, but it should.

---

