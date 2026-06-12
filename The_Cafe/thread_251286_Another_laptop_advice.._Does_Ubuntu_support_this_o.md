---
title: "Another laptop advice.. Does Ubuntu support this one?"
date: 2006-09-05
forum: The Cafe
---

### Post by aktiwers on 2006-09-05
Hi,

I almost settled on this laptop. Sadly I dont know the most important thing.. what hardware does ubuntu support. 

Would Ubuntu Support this animal?

    15.4" WXGA+ Crystal Clear 1280x800 Monitor (2425Wx)    
    2.00 GHz Intel® Core™2 Duo T7200 4MB    
    2048MB PC5300 RAM    
    nVidia Geforce Go 7600 256MB graphics
    100GB 7200rpm Hardisc
    DVD-RW Slot-in 
    Intel® PRO/Wireless 3945ABG 54Mbit
    100/1000 Megabit network, 56K modem        
    High Performance 9 Cell (2x25W) 
    3 x USB 2.0 ports, 1 x Firewire, 1 x VGA out
    1.3M Pixel webcam
    Fingerprint reader (WTF?)


Thanks a lot for any advice. Would be nice before I though 2k after this little baby.

---

### Post by prizrak on 2006-09-05
What is the brand? 
Video, wireless, dvd-rw, usb, firewire, network will be supported out of the box. Webcam is unlikely to work at all, fingerprint reader won't work almost certainly. Knowing the brand would let us make a judgement on ACPI support.

---

### Post by aktiwers on 2006-09-05
> **prizrak said:**
> What is the brand? 
Video, wireless, dvd-rw, usb, firewire, network will be supported out of the box. Webcam is unlikely to work at all, fingerprint reader won't work almost certainly. Knowing the brand would let us make a judgement on ACPI support.

Thanks for the support.
Its from a Danish company.

[http://zepto.dk/Default.aspx?page=NotebookSummaryPage&notebookid=VeIFYindlUdm](http://zepto.dk/Default.aspx?page=NotebookSummaryPage&notebookid=VeIFYindlUdm)

Where I custumized it to those specs. But the site is on danish :(

---

### Post by prizrak on 2006-09-05
I thought that Zepto sold Linux preloaded systems. Looks like ASUS (alot of companies buy whitebox laptops from companies like ASUS and brand them as their own, System76 does that) and those work well with Linux. Do they have a storefront? If they do, they might let you try a LiveCD on a display machine. The only thing for you to watch out is ACPI, otherwise what I said earlier holds.

---

### Post by Spif on 2006-09-05
I got everything working on my Zepto Znote 4200, although battery life is not as long as it should have been (probably a Linux/Ubuntu related issue)

I personally wouldn't buy that laptop though, as you won't get more than a few hours of battery life with it. A friend of mine has a model with almost identical specs, and it doesn't even run 2 hours.

But if you need performance, then it is pretty good ;)

---

### Post by aktiwers on 2006-09-05
Ok thanks for the comments. I will look some more and see if I find anything better.

---

### Post by prizrak on 2006-09-05
Battery life issue is known and is a Linux one. nVidia driver for Linux doesn't support GPU throttling (the one for Windows does) so the gfx runs at full speed all the time destroying battery life.

Try looking at Acer machines, I got one and it works perfectly out of the box. Thinkpads are good with Linux as well, Toshiba has good support. I guess that's as much advice as I can give someone from the other side of the pond.

---

### Post by aktiwers on 2006-09-05
what about intel onboard video cards.. are they supported?
Or just onboards in general?

---

### Post by aktiwers on 2006-09-05
Anyone know how good Ubuntu runs on a macbook? :P

---

### Post by prizrak on 2006-09-05
> **aktiwers said:**
> what about intel onboard video cards.. are they supported?
Or just onboards in general?

Intel releases the specs for their hardware in the open so they work very well. They even have their own open sourced drivers for the community to work off. So the best Linux laptop would be 
Intel CPU
Intel Chipset
Intel GPU
Intel Motherboard
Intel NIC
Intel WNIC
Intel Sound

---

