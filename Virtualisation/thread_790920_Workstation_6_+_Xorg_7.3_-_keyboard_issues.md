---
title: "Workstation 6 + Xorg 7.3 - keyboard issues"
date: 2008-05-11
forum: Virtualisation
---

### Post by Nequeo on 2008-05-11
Hello all,

I was wondering if anyone in these parts has encountered the issue described here: [http://communities.vmware.com/thread/104635]("http://communities.vmware.com/thread/104635")

Briefly: The issue is that after using keyboard to enter, leave, or switch VMs in full-screen mode, using VMware Workstation 6 or 6.5 beta running under Xorg 7.3, mucks up the keyboard.

The symptoms I am experiencing is that Alt, Shift, Caps and Numlock all stop working, and typing or hitting Ctrl tend to kill the focused window.

A work-around is to use only GUI buttons for entering/leaving fullscreen. Also, if the keyboard mucks up, you can go to KeyBoard preferences, change your keyboard layout, and then hit 'reset to defaults' to get most things working again (alt+tab still doesn't work - but at least you can type without killing anything). 

We could live with this until VMware releases a fix - because we don't really do anything with our hosts, but I was wondering if there was a file I could mark as read only, or a permission I could deny, or some similar exercise, that could be used as a temporary fix. 

Anyone have any ideas?

Cheers,

---

### Post by pangloss on 2008-05-11
I've encountered the same issue (VMWare Workstation 6.3 running on Ubuntu 8.04 amd64). Workarounds I've seen include:
[URL="http://bitubique.com/tutorials/recovering-from-stuck-modifier-keys"]
http://bitubique.com/tutorials/recovering-from-stuck-modifier-keys[/URL]
or just running "setxkbmap".

Pretty annoying bug and with the VMWare forums shut for the weekend, I haven't heard anything new.

---

### Post by Nequeo on 2008-05-11
> **pangloss said:**
> I've encountered the same issue (VMWare Workstation 6.3 running on Ubuntu 8.04 amd64). Workarounds I've seen include:
[URL="http://bitubique.com/tutorials/recovering-from-stuck-modifier-keys"]
http://bitubique.com/tutorials/recovering-from-stuck-modifier-keys[/URL]
or just running "setxkbmap".

Pretty annoying bug and with the VMWare forums shut for the weekend, I haven't heard anything new.

Thanks for the reply. The xmodmap script works fine, and for now I'm happy enough to put a launcher on the panel that runs that script. We really don't use our hosts for anything beyond running Workstation, so we're piloting a switch from WindowsXP as the host OS to a lighter Linux setup.

So far so good.

Cheers,

---

### Post by waynema on 2008-05-18
I experienced the same problem, "setxbdmap" works fine for me. 
Great thanks:)

---

### Post by agibby5 on 2008-07-28
> **Nequeo said:**
> Thanks for the reply. The xmodmap script works fine, and for now I'm happy enough to put a launcher on the panel that runs that script. We really don't use our hosts for anything beyond running Workstation, so we're piloting a switch from WindowsXP as the host OS to a lighter Linux setup.

So far so good.

Cheers,

I did the same thing, setup the launcher, and now everything is working fine.  This bug sucks!

---

### Post by Midahed on 2008-08-02
I have the same problem with VMware Workstation 6.0.4 build 93057 and Ubuntu 8.04.  In my case pressing _any_ key closes the window which has the focus.

I used to run VMware Server with no problems and decided to give Workstation a try.  I'm still running the trial version, so I may have to give VirtualBox a shot before deciding whether it's worth paying for Workstation.

---

### Post by NickD-NLUG on 2009-07-02
> **pangloss said:**
> I've encountered the same issue (VMWare Workstation 6.3 running on Ubuntu 8.04 amd64). Workarounds I've seen include:
[URL="http://bitubique.com/tutorials/recovering-from-stuck-modifier-keys"]
http://bitubique.com/tutorials/recovering-from-stuck-modifier-keys[/URL]
or just running "setxkbmap".

Pretty annoying bug and with the VMWare forums shut for the weekend, I haven't heard anything new.

Excuse me adding to such an old thread... but thanks for posting this - "setxkbmap" just got my special key functionality back after running vmplayer on 9.04 amd64.

---

