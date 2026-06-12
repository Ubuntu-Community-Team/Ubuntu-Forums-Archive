---
title: "Windows client not syncing from online storage (anymore)"
date: 2011-09-29
forum: Ubuntu One (CLOSED)
---

### Post by polyfragmented on 2011-09-29
Hello,

my U1 Windows client (2.0.0, had the betas as well, Windows is Windows 7) doesn't sync files/folders from the online storage (anymore). At some point it stopped updating.

I can upload from my Ubuntu installation fine, but when I sit at my Windows box, the client there says that all stuff is synced while it is clearly not.

I noticed that in the devices section it showed multiple entries for the Windows box with slightly differing names. I deleted everything but the current entrey, to no avail. I checked the settings as well, syncing of new cloud folders is activated.

I did a search here, but didn't find related posts. If I used the wrong search terms or overlooked something, I apologise.

Does anybody else have similar problems?

---

### Post by Felipejane on 2011-09-29
I have had a similar problem, under Windows XP; on another machine running Windows 7 I haven't yet seen the problem you describe. I'm going to try re-installing the Windows UbuntuOne client (if XP will take it) to see if that helps, as I see there's an announcement about it dated today.

But right now I can't even get to my Ubuntu One files by going to the website. That troubles me a good bit more.

---

### Post by polyfragmented on 2011-09-30
> **Felipejane said:**
> But right now I can't even get to my Ubuntu One files by going to the website. That troubles me a good bit more.
Indeed, that's not good at all

I have a bug open for what I experience: [https://bugs.launchpad.net/ubuntuone-client/+bug/862628](https://bugs.launchpad.net/ubuntuone-client/+bug/862628). I failed to mention that I have a NTFS symlink from the standard U1 folder to another folder on a different partition. The instructions on how to do that were on the Windows client page, but have been removed now. Told the engineers about it, maybe they removed the functionality in the official client.

Will keep you guys posted here.

---

### Post by Captain Spectacular on 2011-10-27
Did you guys figure this out?  I've been having the same trouble.  In my case the directories to be synced are in ~, so is Windows' differing directory syntax affecting things here, maybe?  The "Ubuntu One" directory seems to sync just fine.

---

### Post by polyfragmented on 2011-10-28
I haven't heard back from the supporters, but it seems that my sync corrected itself (maybe on the server- side, I don't know). It looks like the formerly-affected folders sync correctly. I say "it looks like", because they're still syncing. None of my syncs worked for days, they're picking up now, cross-OS though.

---

