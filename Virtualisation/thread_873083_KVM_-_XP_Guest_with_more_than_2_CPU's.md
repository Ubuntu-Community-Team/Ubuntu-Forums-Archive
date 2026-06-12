---
title: "KVM - XP Guest with more than 2 CPU's?"
date: 2008-07-28
forum: Virtualisation
---

### Post by ubuntastic on 2008-07-28
Hi All,

My first Ubuntu forums post, so be gentle...  :)
 
I'm a recent convert to Ubuntu from the Microsoft world, and loving every minute of it...  Seriously, the 5 systems I have in my household have all been switched!

There is only one multi-threaded Windows application that I still need to use daily however, for which I was hoping KVM would serve my needs.

I've setup KVM (-62 from the repo), on 64-bit Hardy and created a VM for 32-bit Windows XP with SP3 installed.  ACPI is enabled and works great for up to 2 CPUs.  However, I can't seem to get the XP VM to see more than the 2 CPUs, even though it is a quad (Intel Q9450).

I've tried using the KVM-70 in the Intrepid repo on Hardy to see if it might help, but no luck.

Any ideas on what I might be missing to get the other two cores working in the XP VM?  I've searched the forums, googled and scoured the KVM wiki site but I can't seem to find the answer.

Thanks for any help in advance!

---

### Post by blazercist on 2008-07-28
Is it Home or Pro version of windows?  Im pretty sure Home will not work with more than 2 CPUs.

edit: O wait, I don't think its possible to do what you want at all.  Im pretty sure that the Quad core CPU are just two dual cores on the same die, that means that you can assign one "dual core" to the VM and the other one to your host OS.


Or perhaps im completely wrong.  Also If im not mistaken VM's emulate processors, so can't you just make the VM processor whatever you want and assign however many cores to the KVM application in the host OS?

---

### Post by ubuntastic on 2008-07-28
Wow, thanks for the quick reply...

It is XP Professional.

You raise a good point though.  Your post triggered a thought, I'm to try booting a live-CD in KVM to see if it sees more than one CPU, so I can isolate the problem to my XP VM.

---

### Post by ubuntastic on 2008-07-28
Tried the following...

```
kvm -m 1024 -smp 4 -usb -boot d -cdrom ~/Desktop/Downloads/ubuntu-8.04.1-desktop-amd64.iso -name xp ~/scrap/WinXP.img 
```

and the live CD saw all four cores.  So it looks like KVM is running fine and it has to do with XP Pro.  The only change to the line above was the addition of "-boot d -cdrom ~/Desktop/Downloads/ubuntu-8.04.1-desktop-amd64.iso" to test out my theory.

I missed your edits on that first post.  I believe that because KVM uses the hardware virtualization on the processor that it should see all 4 cores.  Checked the KVM wiki and it says it'll go up to 16 cores, so I'm still stumped.  :(

Thanks for trying to help though!

---

### Post by David Cartwright on 2008-07-28
You may find the following article on **Running Windows SMP Guests** helpful. I have used it for a Windows 2003 Server guest to support a quad core CPU.

The link is here:

[http://www.linux-kvm.com/content/running-windows-smp-guests]("http://www.linux-kvm.com/content/running-windows-smp-guests")

---

### Post by ubuntastic on 2008-07-29
David,
 
Thank you for the link.  I've never come across that site before and it is a great resource.

I went through the article and made sure my XP image was using the same HAL.  Unfortunately it already had the ACPI Multiprocessor HAL installed, and I still seemed to be capped at 2 processors.

I have a 64-bit Vista license I'm not using (I gave up on it a year ago!), which I might try installing.  I'm starting to suspect that it has everything to do with the XP installation.  I even tried re-applying SP3 as quad-core use requires SP2 or greater.

Once again, thanks to everyone for their help.

---

### Post by ubuntastic on 2008-07-31
No luck.  Vista only sees 2 processors as well.

I'm starting to wonder if it might have something to do with my motherboard, as I upgraded the CPU to a Quad and simply flashed the bios to accommodate it, but it is still an old board (Asus P5B, about 1 1/2 yrs old).

Its really frustrating because I do see two processors, but not four.  I'd feel better if I only saw one processor because I'd at least have hope that the other three might be found wgen I figure it out...  :)

Any ideas?

---

