---
title: "VMPlayer missing scrollbars when not maximized"
date: 2010-08-23
forum: Virtualisation
---

### Post by r_avital on 2010-08-23
Hi all, here's the situation:

Host: Ubuntu Lucid 10.04 64-bit, am-dual processor, resolution=1680x1050.
VMPlayer 3.1.1 build-282343 for Linux.

Guest: Windows XP Pro 64-bit, processor allocated = 1, resolution = host (automatically set)
VM-TOOLS *installed*, latest version


Displays full screen beautifully when maximized, works like a charm. If I "restore" the VMPlayer so it's at less than full-screen (so I can see some apps on the host),* no scrollbars appear. None*. All shortcuts on the guest desktop are re-arranged to fit, and the Windows taskbar is shrunk and visible at the bottom of the player window.  In this situation, I *want* the scrollbars, and don't want the player to rearrange the shortcuts on the XP guest. I found nothing on the VM-TOOLS to address scrollbars.

What am I missing?

[I've checked the VM forums, so far no reply, maybe someone here has seen the problem?]

TIA

---

### Post by fjgaude on 2010-08-23
Can't you just drag the guest window to make it the size you wish? I also don't understand the "resolution=host". If you have the right items checked the resolution should be automatic as you size the guest window.

One thing you might try, in the .vmx file, make sure the virtualHW.version = "6", and not "5". You find that file in your VMware main file, open with a text editor.

---

### Post by r_avital on 2010-08-23
Thanks for the reply.  Actually, I checked, and mine is set to virtualHW.version =  "7" since it's the latest version of the player.

What I meant by the shorthand "resolution=host" was, that in the settings for the VM, I have the guest resolution set to equal the host resolution, rather than a specific number, and it is in fact rendering correctly.  

I guess I didn't explain the question correctly:  When the guest (WinXP) is maximized, I arrange my shortcuts on the desktop, let's say, a vertical arrangement, two columns.  Then I "UN-maximize" so the guest is just a window in the desktop of the host.  At THIS point, the shortcuts re-arrange to fit in the smaller window, instead of staying put, and I don't get a set of scrollbars.  

What I would like it to do, is show scrollbars, and keep the shortcuts in the same original arrangement.  This is how the Windows VMPlayer works.

---

### Post by fjgaude on 2010-08-25
Well, I tried what you describe on my system... it worked like I think it should. In the Windows VM, the icons on the left side followed the resizing of the window.

The only differnce in our systems is I'm running 32-bit WinXP. Do you wish the WinXP icons to end up on the Ubuntu desktop? I'm not sure that is possible.

Now if you were running a Windows host with a WinXP guest, well, that's something I've never tried or ever will.

---

