---
title: "Windows in a VirtualBox and shortcuts"
date: 2012-04-04
forum: Virtualisation
---

### Post by Araberen on 2012-04-04
Hi,

                         I have installed Windows 7 in a Virtual Box which is running on top of Ubuntu 12.04 beta 64 bits. Guest additions are installed, everything is working fine with my Windows.
There are just two little things I'd like to improve:

[LIST]
[*]When I'm in Windows (ie. the Virtual Box window has the focus) and I press the Windows key (between Ctrl & Alt), it opens the Dash Home menu of Ubuntu and the Windows Start Menu. Since the focus is in Windows, I'd like this shortcut to not open the Dash Home but just the Start Menu.
[*]When I'm using the short Ctrl + Alt + arrow to go to another desktop and that I'm in Windows, nothing happens! I'd like this shortcut to have its normal behavior in Ubuntu (changing the desktop) and not doing anything in Windows.
[/LIST]
If I can solve those two problems, it'll be very nice to use Windows in the Virtual Box. :)


Any ideas?

---

### Post by zeljkojagust on 2012-04-04
When in Virtual Box go to File -> Preferences -> Input. There check "Auto capture keyboard", think that should solve your problems.

---

### Post by Araberen on 2012-04-04
Half solved!
By **un**checking the Auto Capture Keyboard option, I can indeed change of desktop with the shortcut.
But I still have the "Windows key" shortcut problem.

And actually, it is not that practical to uncheck that option cos now, yes I can change quickly of desktop, but I cannot continue to type directly in Windows without first making a click to get the focus back on Windows (this is not painful, but this is improvable).
And the only way to get that behavior is by rechecking the option...

Maybe there is a solution on top of the Virtual Box, like building a script that intercept every shortcuts and do something like:
if (shortcut is Windows key && Window of Windows has focus) then
  follow signal to VB
  do not follow signal to unity
else if (shortcut is Ctrl + Alt + arrow) then
  do not follow signal to virtual box
  # auto follow signal for all other apps
end if

Ideas?

---

### Post by Rebelli0us on 2012-04-06
Supposedly you can customize keyboard shortcuts in Ubuntu, including the Win key.

[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/")

but I haven't been able to make it work. For example I wanted the Win key to open the main menu in Linux as it does in Windows.

---

### Post by Araberen on 2012-04-06
On Unity, the win key opens by default the Dash Home...

---

