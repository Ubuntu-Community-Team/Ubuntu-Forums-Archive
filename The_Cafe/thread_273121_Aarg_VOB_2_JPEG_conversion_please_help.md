---
title: "Aarg? VOB 2 JPEG conversion please help?"
date: 2006-10-07
forum: The Cafe
---

### Post by schurtek on 2006-10-07
This is driving me nuts... long time ago I use to use a Win32 program called DVD Backup... which is now impossible to find cos the coder has been arrested or something... now I use it for legit work... I have a client who has had a Dancing Tutorial DVD made... and he now wants to write a book and use shots from the DVD... so he wants me to convert the entire DVD to JPEG... 

Now the first thing would be to rip out MPEG files chapter by chapter for simple viewing pleasure... then break the MPEG files down into JPEG files... but do you think I can find any tools to do this, both for Linux and for Windows... I am going nuts...

Please help me... or at least tell me where I left my revolver so I can blow my brains out? *kidding*

---

### Post by Albi on 2006-10-07
Sorry if this seems really stupid or simple, but why can't you just screenshot the DVD while you're playing it?

---

### Post by schurtek on 2006-10-08
was considered... ut the client is not really clued up on how to use a PC so he want's each and every frame as jpegs... video is 89minutes. that is 130 000 jpegs... I am not going to sit doing that... when there must be software that does it...

---

### Post by GeneralZod on 2006-10-08
mencoder claims it can do this; check out the man page for details! :) I'm guessing it can do the entire movie in one go, but you might have to make a few other calls if there are multiple titles on the tracks. Should be pretty easy, though.

[quote=mencoder man page]```

jpeg
              Output each frame into a JPEG file  in  the  current  directory.
              Each  file  takes  the frame number padded with leading zeros as
              name.
                 [no]progressive
                      Specify standard or progressive  JPEG  (default:  nopro&#8208;
```
[/quote]

---

