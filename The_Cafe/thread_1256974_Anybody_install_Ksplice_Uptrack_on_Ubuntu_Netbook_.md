---
title: "Anybody install Ksplice Uptrack on Ubuntu Netbook Remix 9.04 (Jaunty) ??"
date: 2009-09-03
forum: The Cafe
---

### Post by SuperBaby on 2009-09-03
I have just installed Ksplice Uptrack in my Kohjinsha SH6 netbook running Ubuntu Netbook Remix 9.04 (Jaunty).   
  Everything works well except one thing which is really annoying:
   
  Every time when I boot up my netbook, a series of text appears showing the boot sequence of Ksplice processes. This text shows up after the Ubuntu splash screen. Although it is not affecting the performance, the text is annoying to me.
   
  I have searched through the internet and could not find a way to turn it off.
   
  I wonder if other UNR 9.04 users also have this problem?

---

### Post by stwschool on 2009-09-03
What's probably happening here is that it's taking longer than it should to boot that extra ksplice stuff. Basically the graphical progress bar drops to the text if things are taking too long so you can see if there's a particular process being a pain in the bum, so that you can do something about it. As to how to stop that happening, you'd need to look into making ksplice boot faster, and I'm not an expert on that so I can't help too much there sorry :(

---

### Post by SuperBaby on 2009-09-05
This is the response from Ksplice:

 > Thanks for the bug report.  The annoying behavior you describe is not intentional, and I think I know why this is happening.  I don't have an easy workaround for you, but I have a plan for how to fix this and hope it will make it into one of our upcoming feature releases.
   
        -Tim Abbott
  

---

### Post by SuperBaby on 2009-10-05
I just found a solution by accident. Add "profile" to /boot/grub/menu.lst and the bootup text is gone.> kernel /vmlinuz-2.6.15-25-686 root=/dev/hda2 ro quiet splash [COLOR=SeaGreen]profile[/COLOR]

---

