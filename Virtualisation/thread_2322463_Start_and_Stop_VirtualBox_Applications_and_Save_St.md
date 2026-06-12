---
title: "Start and Stop VirtualBox Applications and Save State"
date: 2016-04-28
forum: Virtualisation
---

### Post by dannymichel on 2016-04-28
Right now I have a .sh file to start Photoshop seamlessly and a .sh file to shut down the VM and save the state.

What I would love to do ultimately if possible at all is have one script(launcher if possible, so it can be found when searching apps) that will start Photoshop and when it's detected that I've exited out of Photoshop in the VM, it does a shutdown and save state for the VM

Is this possible? If so, would someone be so kind as to help me do that? 
Would I be creating a photoshop.desktop file in /usr/share/applications with whatever in it(what would be the whatever?)?
Would I be modifying the current photoshop.sh and moving it into /usr/bin THEN creating a photoshop.desktop in /usr/share/applications that somehow points to that?
Or maybe somehow creating some file in /usr/bin?

Any help would be greatly appreciated. Thanks in advance

Photoshop:
```
#!/bin/sh
VBoxManage startvm "Windows"
VBoxManage --nologo guestcontrol "Windows" run --exe "C:\\Program Files\Adobe\Adobe Photoshop CC 2015\\Photoshop.exe" --username danny --password xxxx --wait-stdout
```

Shutdown:
```
#!/bin/sh
VBoxManage controlvm "Windows" savestate
```

Would this be how to do it?
```
#!/bin/sh
VBoxManage startvm "Windows"
VBoxManage --nologo guestcontrol "Windows" run --exe "C:\\Program Files\Adobe\Adobe Photoshop CC 2015\\Photoshop.exe" --username danny --password xxx --wait-stdout && echo OK
VBoxManage controlvm "Windows" savestate
```

---

### Post by dannymichel on 2016-04-28
The only problem i see with the above is the VM shutting down and/or trying to restart if i forget i had photoshop open and i made another .sh for Illustrator the same way. Closing either app would shut the VM down and they'd both have commands to start the VM as well

---

### Post by dannymichel on 2016-05-02
Bump?

---

### Post by slickymaster on 2016-05-02
*Thread moved to **Virtualisation**.*

---

### Post by dannymichel on 2016-05-02
> **slickymaster said:**
> *Thread moved to **Virtualisation**.*

This is not solved, which is why i bumped it.
[edit]
Sorry, I read your signature as a response.

---

### Post by MAFoElffen on 2016-05-04
It was a question concerning Virtualization so he knew you might get help here... and with that--

That would start your VM session, start your app, then once it stated, close and save state... wittout you having a chance to do anything. (You could confirm that by running it once.)

I think what you want is for your script to "wait" for something before it shuts down right? Some interaction by you, or for something to actually indicate that you want it to shut down?

---

