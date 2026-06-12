---
title: "No sound on darter 2"
date: 2008-01-29
forum: System76 Support
---

### Post by poetbeware on 2008-01-29
OK, hard drive crashed in my Darter late last year, system76 sent me a new hard drive (thanks!) and I installed, re-installed Ubuntu, re-installed the system76 driver. I thought everything was groovy until just now when I finally got around to ripping CDs again.

The volume icon has a little circle-slash over it, and clicking it says:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

OK. In another thread other people were having this problem back in April, the solution was to:

  sudo apt-get remove --purge system76-driver
  sudo rm -r /opt/system76
  sudo apt-get install system76-driver
  system76-driver
  reboot

So I did all that, but it still doesn't work. During the run of system76-driver, it output this line:

  options snd-hda-intel model=targa-dig

But when I 

  lsmod | grep snd

there's no listing for snd-hda-intel. When I

  sudo modprobe snd-hda-intel

It says:

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

And dmesg reports:

[   97.764000] snd_hda_intel: disagrees about version of symbol snd_dma_free_pages
[   97.764000] snd_hda_intel: Unknown symbol snd_dma_free_pages
[   97.764000] snd_hda_intel: disagrees about version of symbol snd_dma_alloc_pages
[   97.764000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages

Um...help?

---

### Post by thomasaaron on 2008-01-29
The reason your sound doesn't work is probably becuase when you re-installed, you usded update manager to bring your installation up to date. There was a bug in update manager that hosed ALSA.

The fix for it is in the System76 driver, though. So, verify that you have version 2.0.3 of the driver (Open it and click the 'About' button.) If you do, run the driver's "Install Drivers" function and then reboot your computer. Do you still have the red mark on the speaker icon?

If not, double-click the icon. In the resulting window, go to Edit > Preferences and check all available checkboxes. You should then be able to get your sound going.

If the red mark is still there, email me at support(at)system76(dot)com, and I'll send you a .deb file that will fix it.

If you don't have version 2.0.3 of the driver, run the "Restore" function on the driver you have. This will update your sources.list and the new driver should become available via the update icon. (This may hose any custom xorg settings you've made, though. So you may want to back up your xorg.conf file.)

Best,
Tom

---

