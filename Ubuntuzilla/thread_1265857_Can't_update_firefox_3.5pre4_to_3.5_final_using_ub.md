---
title: "Can't update firefox 3.5pre4 to 3.5 final using ubuntuzilla"
date: 2009-09-13
forum: Ubuntuzilla
---

### Post by dj-toonz on 2009-09-13
hi all, hope somebody can keep me, I'm using Shiretoko 3.5 pre4 browser via the Ubuntu mozilla PPA repo and now having problems trying to install firefox 3.5 final via ubuntuzilla it keeps coming up with this error

Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 343, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 743, in install
    self.aptgetMeasures()
  File "/usr/local/bin/ubuntuzilla.py", line 518, in aptgetMeasures
    self.util.execSystemCommand(executionstring="sudo apt-get install " + self.aptPackage, errormessage="Package installation failed. Cannot proceed.")
  File "/usr/local/bin/ubuntuzilla.py", line 143, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

anybody else seen the error & how can I download the default 3.5 firefox as google toolbar or a lot of program's don't work with Shiretoko cheers

---

### Post by nanotube on 2009-09-13
could you paste the complete output of your ubuntuzilla install session?

---

### Post by dj-toonz on 2009-09-14
Managed it :), right now I'm running firefox 3.5.3, when I rebooted, I had a red circle in the taskbar with a white line though it and click on that and it said something about installing a lib file can't remember which now & tried the .py file again and bob's your uncle & fanny's your aunt running the latest version of firefox :-)

what will happen when firefox 3.5 final goes into the Unbuntu mozilla PPA repo will I need to remove firefox 3.5.3 final from the system now?

p.s now It doesn't show the red firefox icon on the taskbar or the applications/network menu it's still showing the blue Shiretoko one. I thought ubuntuzilla would remove the icon'ns? how can I replace it with the red one like It was when I was using firefox 2.0.14 ? cheers

---

### Post by nanotube on 2009-09-14
> **dj-toonz said:**
> Managed it :), right now I'm running firefox 3.5.3, when I rebooted, I had a red circle in the taskbar with a white line though it and click on that and it said something about installing a lib file can't remember which now & tried the .py file again and bob's your uncle & fanny's your aunt running the latest version of firefox :-)

hehe nice :)

> 
what will happen when firefox 3.5 final goes into the Unbuntu mozilla PPA repo will I need to remove firefox 3.5.3 final from the system now?

nothing will happen... you can continue using the mozilla build if you want, or you can uninstall it if you want... all up to you.

> 
p.s now It doesn't show the red firefox icon on the taskbar or the applications/network menu it's still showing the blue Shiretoko one. I thought ubuntuzilla would remove the icon'ns? how can I replace it with the red one like It was when I was using firefox 2.0.14 ? cheers

check the link properties (for the menu - go through the menu preferences, for the panel icon, just rightclick and go properties), and see where it points for the icon. point it to /opt/firefox/icons (where the mozilla build stores its icons).

normally ubuntuzilla doesn't touch the icons, it just changes the the system shortcut to point to the new firefox. so since shiretoko changed your icons... they're gonna stay until you change them back (or uninstall shiretoko?)

hope that helps :)

---

### Post by dj-toonz on 2009-09-27
Thx managed to replace the icons back to default, I'd used the Mozillia Ubuntu PPA from ubuntu-tweak that's how come it came up with the blue icon instead of the default one :-(

---

