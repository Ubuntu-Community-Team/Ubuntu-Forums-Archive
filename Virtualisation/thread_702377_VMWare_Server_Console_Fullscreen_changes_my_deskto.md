---
title: "VMWare Server Console Fullscreen changes my desktop size"
date: 2008-02-20
forum: Virtualisation
---

### Post by benbelly on 2008-02-20
I have windows xp running in a virtual machine using VMWare Server Console on top of Gutsy (so I can remote into work).  Everything works fine except that when I go to full screen in the console, then leave full screen, my gnome desktop is the wrong size - bigger than my screen resolution.  So I have to scroll to the bottom to get to the taskbar, then scroll to the top to get to the menu bar, etc.

  My Gnome resolution is at 1680x1050.  My VMWare XP resolution is 1280x1024 (1680x1050 is not available in the desktop settings).

  Does anyone know how to prevent this desktop resize?

Thanks,
-Ben

---

### Post by fjgaude on 2008-02-20
Seems like if you set the host desktop and then in vmware use the auto screen sizing everything should be okay. That's what I do.

In vmware console, go to **Edit/Preferences/Display** and click both auto functions. Then simply drag the windows in vm guest to what size you wish. Windows will auto handle any size you let it go to.

Try it, you'll like it.

---

### Post by benbelly on 2008-02-20
Thanks for your reply.  That didn't seem to fix it, but everything works ok in a window.  However, I can't get the full 1024 vertical pixels on the screen w/o scroll bars unless I go full screen (CTRL+ALT+ENTER)

With the changes you suggested, did you mean that the XP guest would change its desktop size when I changed the vmware console window size?  Because that doesn't happen - I get scroll bars on the sides.

I should probably mention that I'm running compiz - maybe that's where my problem is.

---

### Post by fjgaude on 2008-02-20
Yes, I meant simply click on a window corner and drag to the size you wish.

I don't use compiz...

---

### Post by zalym on 2008-06-08
hi,

thanks for the suggestion.  that worked for me.  i seem to have another problem.  when i goto fullscreen in the virtual machine, and then come back.  the gnome ui acts weird.  none of the ctrl, shift or alt keys work.  when i open a terminal, when i type a letter it closes.  likewise for gedit.  likewise my caps key wont work as well.  i hv to reboot to get it all working again.  i am unable to reboot the x server alone using ctrl plus alt plus backspace, because my ctrl keys dont work.  

i am using hardy heron and xp on vmware server.  

please help

---

