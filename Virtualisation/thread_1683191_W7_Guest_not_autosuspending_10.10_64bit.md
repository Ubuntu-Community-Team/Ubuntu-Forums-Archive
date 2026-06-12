---
title: "W7 Guest not autosuspending 10.10 64bit"
date: 2011-02-07
forum: Virtualisation
---

### Post by stewartv on 2011-02-07
Hi,

I upgraded to Vbox 4.0 and now my W7 guest doesn't autosuspend when the host Ubuntu 10.10 goes to sleep. This used to work flawlessly in V3 of Vbox. I can of course select ACPI Shutdown in the guest and that works but I want this to happen automatically like it used to in V3. I've looked at the power options in both host and guest to see if there is any mention of sending or receiving ACPI notifications and can't see anything.

I've found a post that discusses writing a script to do this [http://www.wiki.blue-it.org/VirtualBox#Auto_suspend_virtual_machines_on_standby_.2F_hibernation](http://www.wiki.blue-it.org/VirtualBox#Auto_suspend_virtual_machines_on_standby_.2F_hibernation) 
but as it used to just work automatically I'd rather configure that to happen than implement a coded solution.

I have Vbox 4.0.2 PUEL, Ubuntu 10.10 64bit host, Windows 7 Ultimate 32 bit guest. I have installed guest additions and the USB extensions.

Thank you for reading this.

S

---

### Post by stewartv on 2011-02-10
My post had no replies so I used the script method in the link in my original post. I used method 2 for pausing per user. It works. I also created a launcher for VirtualBox that runs the 90virtualbox script after starting Vbox.

VirtualBox %U
cd /etc/pm/sleep.d
./90virtualbox

---

