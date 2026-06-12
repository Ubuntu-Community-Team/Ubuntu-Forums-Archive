---
title: "Installing FireFox plugin - how to?"
date: 2009-02-23
forum: Wine
---

### Post by paker on 2009-02-23
No problem with FireFox running in wine.
My question is  how to install aa internet browser plugin in the Windows-based FireFox. I ran 

wine msiexec /i Scorch525NetscapeInstaller.msi

Scorch is a sheet music plugin.

I checked wine > browse C drive > program files > Sibelius Software > Scorch > NetscapePlugin and I see 2 dll's in there. The plugin seems to be installed but FireFox still cannot open the sheet music. Is there anything else I need to do? Is Netscape a different program from FireFox? I thought they were the same. Thanks.


Thanks.

FireFox 3.0.6
ubuntu 8.10 32 bit
wine 1.1.15

---

### Post by Quirriff on 2009-02-24
Why are you running Firefox within wine in the first place?

Those types of plugins have its own directions so follow the directions on the site.

However I remember Scorch doesn't work that well anyway.

---

### Post by trlkly on 2009-02-24
> **Quirriff said:**
> Why are you running Firefox within wine in the first place?

Those types of plugins have its own directions so follow the directions on the site.

However I remember Scorch doesn't work that well anyway.

Probably because they want to use Scorch. Wine hasn't figured out a way to get Windows-only plugins to run in Linux Firefox, unless you know something I don't.

----

Anyways, it sounds like the DLLs are installing in the wrong location. Firefox plugins generally have to be installed in the Firefox folder.

A quick look at the Wine AppDB seems to prove me correct. Try going here and doing what the tester did:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13749](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13749)

---

