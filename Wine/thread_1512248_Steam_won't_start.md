---
title: "Steam won't start"
date: 2010-06-17
forum: Wine
---

### Post by ucal on 2010-06-17
Using 1.2rc3, the only special setting would be that it's set to emulate vista.  From a previous install of wine, I have a bunch of codecs installed.  Basically everything you get from allcodecs and allfonts.  That's it besides Steam.  

When running from terminal, I receive this output:

```
CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  1345
  Current serial number in output stream:  1365

```

I'm using an ATI Radeon HD 3650 iirc, with the proprietary drivers installed.  Thanks for reading all of this, and thanks for considering to help me get my TF2 fix :D

---

### Post by cogadh on 2010-06-17
Did you try changing it to Windows XP instead of Vista?

---

### Post by ucal on 2010-06-17
> **cogadh said:**
> Did you try changing it to Windows XP instead of Vista?

I actually changed it to vista from xp, so that's a no go. Thank you though.

---

### Post by asdfoo on 2010-06-17
Did it work with an earlier version of Wine?

---

### Post by ucal on 2010-06-18
> **asdfoo said:**
> Did it work with an earlier version of Wine?

I tried two earlier versions, the one normally in the ubuntu repos, and the one you get after adding wine as a source (which ironically was supposed to take me to the latest version.  It didn't).  I think those versions were 1.12 and 1.14 respectively. It didn't work in either.  Well, in the first, I was able to log in to steam after installing it, but it shortly crashed and then went into the same behavior I'm experiencing now.

---

### Post by cogadh on 2010-06-18
Those version numbers can't be right, Wine hasn't reached 1.2 yet, so 1.12 and 1.14 are still years away from existing. The default that available with Ubuntu is version 1.0.1 and what you get when when you add the WineHQ repository would be different depending on when you added it, since that version is updated roughly every two weeks. For most of the past month, that would have been one of the 1.2 release candidates, if you added it earlier than that, it probably would have been one of the 1.1.4X releases. If this problem only started after you updated, it could indicate a regression of some kind, but I kind of doubt it. Given the number of people who use Steam in Wine, if there was regression of this magnitude, the forums would be filled with posts about it.

That being said, the fact that Steam was running and then crashed might explain everything. Steam used to have a problem in Wine where if you didn't get a "graceful" exit out of the app, it would corrupt and refuse to work again. I thought that it was no longer a problem, but since the old fix for the problem won't hurt anything, you might as well try it. Go to Steam's install directory and delete the file "ClientRegistry.blob", then try running Steam again. If it works, you will have to log in again and any games you have installed will need to be re-verified by the client, but you shouldn't have to re-download anything.

---

### Post by ucal on 2010-06-18
> **cogadh said:**
> Those version numbers can't be right, Wine hasn't reached 1.2 yet, so 1.12 and 1.14 are still years away from existing. The default that available with Ubuntu is version 1.0.1 and what you get when when you add the WineHQ repository would be different depending on when you added it, since that version is updated roughly every two weeks. For most of the past month, that would have been one of the 1.2 release candidates, if you added it earlier than that, it probably would have been one of the 1.1.4X releases. If this problem only started after you updated, it could indicate a regression of some kind, but I kind of doubt it. Given the number of people who use Steam in Wine, if there was regression of this magnitude, the forums would be filled with posts about it.

That being said, the fact that Steam was running and then crashed might explain everything. Steam used to have a problem in Wine where if you didn't get a "graceful" exit out of the app, it would corrupt and refuse to work again. I thought that it was no longer a problem, but since the old fix for the problem won't hurt anything, you might as well try it. Go to Steam's install directory and delete the file "ClientRegistry.blob", then try running Steam again. If it works, you will have to log in again and any games you have installed will need to be re-verified by the client, but you shouldn't have to re-download anything.

I believe I started with the ubuntu repository, then updated to the version got from updating your repository following these directions.  Then I compiled from source the release candidate of 1.2rc3.  

Your advice worked.  Thank you very much.  The client is a little buggy, but I'm downloading TF2 now, so all is well!  Hopefully that'll run without a hitch :D.  Thanks a lot!

---

