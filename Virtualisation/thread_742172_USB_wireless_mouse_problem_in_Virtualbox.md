---
title: "USB wireless mouse problem in Virtualbox"
date: 2008-04-01
forum: Virtualisation
---

### Post by startling on 2008-04-01
I installed Virtualbox on Ubuntu Feisty and am very impressed, but I have one snag.

At first my USB wireless mouse wasn't recognised at all in my XP VM. So in Virtualbox's settings, under USB, I found a section named USB device filters and added the device. The mouse now worked in Xp but, when I switch back to my Ubuntu host, the keyboard is released but not the mouse which seems to have hung (the pointer stays static on the screen). I tried changing the Remote setting from No to Any (I'm not sure what that setting means) but it did not make any difference - the mouse still froze.

In Ubuntu, from a terminal, if I do a 
sudo modprobe -r usbmouse
followed by a
sudo modprobe usbmouse

then the mouse comes back to life, but this is obviously a clunky way to do it!

I'd be grateful for suggestions as to a permanent fix.

---

### Post by hyperair on 2008-04-01
Do you really need it to be recognized by the XP VM? Surely if it works as a pointer in X then it'll work in Virtualbox as well without further configuration? Just click the window and it'll grab, host key to release?

---

### Post by startling on 2008-04-01
> **hyperair said:**
> Do you really need it to be recognized by the XP VM? 
Yes, I do! Have you ever tried using Windows Xp without a mouse?  ;-)

> Surely if it works as a pointer in X then it'll work in Virtualbox as well without further configuration?
No, I'm afraid not. As I wrote in my original post, I had to add it manually.

 > Just click the window and it'll grab, host key to release?
Host key releases the keyboard, but not the mouse. (Or perhaps the mouse has gone from Ubuntu as soon as the Xp VM starts?) Either way, there's no mouse when I return to Ubuntu.

---

### Post by ianb72 on 2008-04-03
I am having the same problem but I am running Gusty.

Every time I click the mouse on Windoze I can not release it back to Gusty with the Ctrl key.

Like you said you can't use Windoze without a mouse really, especially when I am only running Windoze XP so I can run Photoshop and Dreamweaver CS3 

Could it be a problem with wireless USB mice?
I have a USB to PS/2 converter I am going to try to see if that makes any difference.

Ian

---

### Post by startling on 2008-04-03
> **ianb72 said:**
> I am having the same problem but I am running Gusty.

Every time I click the mouse on Windoze I can not release it back to Gusty with the Ctrl key.

Do you have the Guest Additions installed? If not I recommend doing so as this may solve the problem and they also add some nice functionality.

Prior to installing The Guest Additions (which worked for me only after I had uninstalled the Logitech mouse drivers from the guest machine, BTW) I had a short term clunky workaround:

Find the relevant file by typing in a terminal:
```
modprobe -l | grep mouse
```
a number of .ko files should appear. The one I needed, since my mouse is USB, is called, helpfully, **usbmouse.ko**

Then, after shutting down the VM, I typed in a terminal:
```
sudo modprobe -r usbmouse
```
followed by:
```
sudo modprobe usbmouse
```
which should re-start the mouse. Clunky, I know, but it worked for me until I found the solution.

---

### Post by ianb72 on 2008-04-03
Guest additions??

What are they and where do and how do I install them??

---

### Post by startling on 2008-04-03
With your VM running, in the menu bar at the top you should see Machine | Devices | Help.

You need to select Devices > Install Guest Additions...

Without a mouse it's tricky though, as I discovered! If you haven't got a mouse active you can press the Host key (default right control) plus your Home key, followed by a D which should activate the menu you need.

---

### Post by hyperair on 2008-04-03
That's because when you register a USB device under the VM, it automatically unregisters it under Ubuntu, and lets the VM use its own drivers with the raw USB interface. If you use it as a normal X pointer it _should_ work. If it doesn't then it's a bug. But I don't understand why. I thought Virtualbox didn't mess around with the drivers of mice.

---

