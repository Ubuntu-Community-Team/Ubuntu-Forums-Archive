---
title: "Virtualization method for using an spirometer via Windows"
date: 2008-05-31
forum: Virtualisation
---

### Post by Gustavo Narea on 2008-05-31
Hello, everyone.

My father has been stuck to Windows because he's a doctor and needs to use an spirometer (a medical device) controlled by a Windows application.

It's impossible to get it working with Wine and it's such a uncommon situation that I don't get enough help, so I think my last try should be virtualization.

But I have never tried virtualization, I'm a Linux-only user since a long time ago, and thus I have a big doubt: **What is the best virtualization software for this?** Keep in mind that Windows needs access to the medical device.

I've heard some virtualization software need an special processor, so we're willing to get a new one.

Thanks in advance!

---

### Post by bradmkjr on 2008-05-31
Conrgats on being willing to try out virtualization.

Before I give any advice, I must know more about the medical device. HOW does it connect to the computer? Is it serial, parallel, usb, firewire, pci, isa, pci-x, scsi?

Some of these methods can be passed into a virtual machine others cannot. Generally if it plugs into the OUTSIDE of the computer it can be passed onto the virtual machine, if it plugs into an internal slot then you are out of luck.

After a quick search on Google I came across this:
[http://www.cardiologyshop.com/brmipcsp.html](http://www.cardiologyshop.com/brmipcsp.html)
This device is USB, and should be able to work with virtualization.

Let me know more, and then I can answer your question. If you are impatient, I'm recommending VMware Workstation as I feel it is the most stable and reliable product currently.

Good Luck
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

### Post by Gustavo Narea on 2008-05-31
Hello, bradmkjr, and thanks for your answer.

It connects to the computer via RS232 but my father uses a RS232-USB converter, so I guess it can be taken as USB too, right?

The connection between [the non-free application](http://www.spirometry.com/ENG/Products/WinspiroPRO.asp) and the device is what worries me the most. I'd prefer the most reliable virtualization software for these connections, even if it's not the latest and greatest.

Also, it's likely that my father will buy a new medical device soon, so would it be hard to make it work via USB? Would I need to configure something everytime I want to make a new device work? That's also important to me, because my father lives in Venezuela and I'll control his computer via SSH.

What's your suggestion for this situation?

Thanks again!

---

