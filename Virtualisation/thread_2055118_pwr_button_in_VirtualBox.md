---
title: "pwr button in VirtualBox"
date: 2012-09-08
forum: Virtualisation
---

### Post by newb85 on 2012-09-08
Say, for example, I'm running Linux Mint in VirtualBox installed from the repos on Ubuntu 12.04.

Everything works great with one exception.  When I hit the pwr key to bring up the Mate equivalent of the Dash (not sure what it's called), The Dash also comes up on the host computer, over the top of the VM.  I would have thought VirtualBox would prevent that keystroke from getting through to the host machine, but apparently not.  Can I change this?

---

### Post by newb85 on 2012-09-11
Is there really no one else using VirtualBox with Unity on their host machine who can confirm or deny that they are also experiencing this?

---

### Post by cybergalvez on 2012-09-11
happens to me all the time, have no clue how to fix it

---

### Post by newb85 on 2012-09-12
I just realized that I've been saying "pwr button" when I mean "Super Key".  ](*,)  Perhaps that's why I've had so few hits on this thread...

I can still edit my initial post, but is it possible to change the thread title?

---

### Post by CharlesA on 2012-09-13
Same thing happens on Windows machines if you have guest additions installed and have it set so the keyboard isn't "locked" to the VM.

---

### Post by newb85 on 2012-09-13
I'm not sure what you mean by "locked to the VM".  I have VirtualBox set to auto capture the keyboard.  The description VirtualBox gives of that option is:

> When checked, the keyboard is automatically captured every time the VM window is activated.  When the keyboard is captured, all keystrokes (including system ones, like Alt-Tab) are directed to the VM.

The behavior I'm observing is inconsistent with this description.  Methinks I should be filing a bug report...

---

### Post by CharlesA on 2012-09-13
Do you have the guest additions installed?

If you don't have them installed, the VM "grabs" the keyboard and mouse and alt+tab + super key and whatnot work fine, but if you have them installed, it is integrated into the host system.

There should be a button to send the super key to the VM tho.

---

### Post by newb85 on 2012-09-13
> **CharlesA said:**
> Do you have the guest additions installed?

If you don't have them installed, the VM "grabs" the keyboard and mouse and alt+tab + super key and whatnot work fine, but if you have them installed, it is integrated into the host system.

Hmm...I didn't specifically install them, but I pulled up "Additional Drivers" in Mint, and sure enough, they're installed and activated.

So, why would guest additions integrate Super into the host system?  I guess I don't fully understand the point of guest additions.  I know that it fixes resolution issues, but that has nothing to do with Super...

> **CharlesA said:**
> There should be a button to send the super key to the VM tho.

Where is this button exactly?  It's certainly not in the same place as the Auto Capture option.

---

### Post by CharlesA on 2012-09-14
I must be thinking of something else. Try disabling mouse integration and see what happens.

---

### Post by newb85 on 2012-09-14
No change...

---

