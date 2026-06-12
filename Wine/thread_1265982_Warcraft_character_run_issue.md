---
title: "Warcraft character run issue"
date: 2009-09-14
forum: Wine
---

### Post by HieroPosche on 2009-09-14
So I've got WoW installed and running, I'm finally on the verge of being able to kick M$ out of my life for good, but I'm having 1 small issue with the gameplay.  

For some reason when my character is running in a strait line, the legs will stop moving and the character will kind of hover forward.  This happens when strafing also, but will stop if I turn or perform any action.  It certainly doesn't make the game unplayable, but I'd love for it to stop all the same.

I am running the game through Wine 1.1.29 from an NTFS partition with WoW installed to utilize the directx so I have hardware support for the cursor.  But the issue is the same if I'm running from the linux partition with OpenGL.

I'm currently running 9.04 with the Nvidia 180 restricted driver on a 9600GT card.  4 Gigs of RAM and an AMD 3200+ 2ghz processor.

I've seen the issue listed on a few posts, but haven't seen any suggestions on a fix.  Any help would be greatly appreciated.

---

### Post by hikaricore on 2009-09-14
This is a key repeat issue.
Go into your Preferences/Keyboard settings (in Ubuntu) and turn off keyrepeat.

That's the only way I know around it.  Since I personally need the keyrepeat for other things I simpley use autorun or mouse movement most of the time.

---

### Post by HieroPosche on 2009-09-14
Perfect. You sir (or ma'am) are awesome.

I can finally tell Mr. Gates where he can put it :)

Cheers.

---

### Post by ajackson on 2009-09-14
> **hikaricore said:**
> This is a key repeat issue.
Go into your Preferences/Keyboard settings (in Ubuntu) and turn off keyrepeat.

That's the only way I know around it.  Since I personally need the keyrepeat for other things I simpley use autorun or mouse movement most of the time.

An alternative is to tap another movement key (ie left/right) after your forward movement key is pressed. I guess it makes Ubuntu think that the first key is being held so it doesn't get the sticky key treatment.

---

### Post by jasonditz on 2009-09-14
Very cool info, I was having the same problem but I'd basically decided to ignore it.

---

### Post by rafar on 2009-09-14
Ahhhh THANK YOU!!!
Its been annoying me so much!
And it only happens if I press forward on my keyboard. If i use the mouse the character runs fine.

---

### Post by donkyhotay on 2009-09-14
I've had this before with other games, almost any game I play in wine that requires holding down a key (like a FPS) I just always turn off keyrepeat before playing. Kind of annyoing but you have to work with what you have.

---

