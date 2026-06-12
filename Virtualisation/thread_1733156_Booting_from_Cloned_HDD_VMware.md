---
title: "Booting from Cloned HDD VMware?"
date: 2011-04-18
forum: Virtualisation
---

### Post by jkjensen on 2011-04-18
I was wondering if it was possible or someone's thoughts on this before I go ahead and try it. Basically the goal I want to achieve is being able to boot my windows partition in VMware so I could virtually expand my linux partition to the full HDD without having to worry about (pretty much) ruining my current Win 7 Ultimate license... I'm not a total beginner to Linux nor Windows although I'm far from being an expert as well. Thanks Ahead of time!

EDIT: My final assumption is I cannot get it to work without cloning to a separate partition on a different HDD. Since I don't have another drive to try this with I'm going to let the idea settle for now until I think of it again when I have more resources which I can test it with. And I'm sure this will cross my mind again.

---

### Post by varunendra on 2011-04-19
What I understand from the title of your post is that you want to 'image' your Win7 physical installation to VMware's virtual hard disk such that it can be run in VMware (using its 'virtual hard disk', not the physical partition itself). I further assume that the final scene you want to be is:
Your physical harddisk => fully dedicated to Ubuntu
Win7 => In a virtual hard disk in VMware

VMware help guide has instructions on how to do it using VMware Conversion Wizard. However, Win 7 is not in the 'Supported Source Machines' list (but Vista 32/64 bit is). So I think you should try that yourself before making any changes to your physical layout.

If you sense a risk there then I think it'd be best to image your current installation to some external media (DVD or a usb drive) so that you can safely return to current setup if required. In this case you'd have to image your (boot partition + installation partition) including MBR and boot sectors, which can be done using clonezilla or some other disk-imaging tool.

Another idea which I've yet to test myself is to simply image the current installation and restore it inside the virtual machine, then reboot it to see if the installation could adapt itself to the changed (virtual) hardware. But I haven't tested it yet and it may fail for several reasons.

---

### Post by jkjensen on 2011-04-19
Yes! That's exactly the goal I am looking to achieve. I have a 2TB external I use for all sorts of things so I think I'll boot up Clonezilla tonight and copy my Win7 partition to that and then see what I got to work with. The only reason I could see it failing is the Virtual Hardware won't be the same as my Reality Hardware lol.

---

