---
title: "Reinstalling Xfce (no window frames and saved session problems)"
date: 2012-03-06
forum: Ubuntu Studio
---

### Post by sirriffsalot on 2012-03-06
Hello!

   All the configuring in Ubuntu Studio was going fine until I felt like adding a desktop environment.. I installed the gnome package, and complications arose when I tried to save a session in Xfce and returned from GNOME later. Now, none of my windows have any frames I can move around, no close button, and even if I reboot and start Xfce again the same damn saved session keeps popping up, one of the windows of which simply will not go away (PulseAudio).

   I've already removed Compiz, and all the GNOME-related packages in Synaptic that I could find.. So I have probably removed some things that Xfce needs to. Is it possible to fix, or, more appropriately, remove this saved session, or to make things a little more tricky; reinstall the entire Xfce setup? Thank you!:) I would appreciate quick response, and I will be most beholden to you if you do. Either way, thanks for reading!:)

   --> Leo

---

### Post by sirriffsalot on 2012-03-06
I managed to fix this problem by going to Synaptic (via terminal if you're struggling with this problem yourself and can't even click on panel buttons) and removing completely the "xfce4-session" package. I now added it again and with compiz removed and all the frames are back and the saved session bug disappeared. Hope this helped someone:)

   --> Leo

---

### Post by maxter on 2012-05-11
windows frame can be restored deleting the ~/.cache directory.
this must be done logging out from the active xfce session and then going to a console with ctrl+alt+f1.
login with your username and password and then:

rm -R ./cache

restart lightdm:

sudo invoke-rc.d lightdm restart

done :)

---

### Post by hubbardglutch on 2012-05-14
thank you very much maxter, your suggestion worked perfectly for me :) 

i would however like to ask you for a bit of clarification.  i am a total newb to console language and it was unclear precisely which parts of your directions i was supposed to type, and which i wasn't.  i literally tried typing each character of each line, and i don't believe any of the character-for-character attempts were the correct ones.  for me, it seemed "rm -R .cache" was the correct line, then i typed "restart lightdm" without the ":"  and finally i typed "sudo invoke -rc.d lightdm".  actually, i don't think that line ever did anything, especially now that i realize that i included a space where you said not to.  

anyways, just trying to get clear the specific code to use since it did totally fix my problem.  thank you again!

---

### Post by jejeman on 2012-05-14
This is a mistake: rm -R ./cache
Your is correct: rm -R .cache
The most mistake less version is
```
rm -R ~/.cache
```

This is not a command, but a comment: restart lightdm:
This is command
```
sudo invoke-rc.d lightdm restart
```Using the code tags in forum posts reduces mistakes.

---

### Post by pjhoyer on 2012-07-14
thanks, worked perfect for me :D

---

