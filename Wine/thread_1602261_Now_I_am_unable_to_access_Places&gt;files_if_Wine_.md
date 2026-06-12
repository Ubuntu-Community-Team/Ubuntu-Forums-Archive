---
title: "Now I am unable to access Places&gt;files if Wine installed"
date: 2010-10-21
forum: Wine
---

### Post by Handssolow on 2010-10-21
If I install Wine now and I try look at Home Folder, Documents, Music or Downloads etc. through Places> a small grey box appears with ERROR and a red cross. It looks like Wine windozs is running. Completely removing Wine restores things but if I re-install Wine the problem returns. 

With Wine Firefox and the Sibelius Scorch plug-in, hopefully sheet music can be played. It appears to work except there is no sound. Looking to play midi sounds I probably by mistake installed Timidity using the wine installer. whoops. Is this the cause or something else?

I can find two entries for timidity, one directory in /etc containing one file freepats.cfg and in /usr/share/app-install/desktop there is the file timidity-interfaces-extra.desktop.

I seem to have created a link to Wine when I open Places> and I can only prevent this being actioned by not having Wine installed.

What do I need to do?

---

### Post by Handssolow on 2010-10-21
Though I'd removed Wine, I'd corrupted my~/.local/share/applications/mimeapps.list file with two references to wine and also the mimeinfo.cache file where every line referred to wine.

I deleted the mimeinfo.cache file.
In mimeapps.list I removed the lines referring to wine and added inode/directory=nautilus.desktop;

I can view files using Places>Home Folder> so it's back to normal. Is my edit sensible?

I re-installed Wine, Firefox, the Scorch plug-in and under Ubuntu the midi program Timidity. I can play sheet music and see the score. It's not perfect but it will do for now.

---

