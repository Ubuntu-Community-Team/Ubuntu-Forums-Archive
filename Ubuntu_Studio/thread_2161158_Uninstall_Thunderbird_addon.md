---
title: "Uninstall Thunderbird addon?"
date: 2013-07-09
forum: Ubuntu Studio
---

### Post by shaunthesheep on 2013-07-09
I want to uninstall a Mozilla Thunderbird v17.07  addon called Enigmail and then do a clean reinstall. But there is only a disable option. I even tried uninstalling Thunderbird and reinstalling it but the addon is still there.

Any suggestions gratefully received.

---

### Post by ajgreeny on 2013-07-09
I'm not sure how safe this is, but you can find most, but not all the extensions for TB in the hidden folder **~/.thunderbird/x*x*x*x*.default/extensions** (the **x*xc*x*x*** will be a random alphanumeric) as separate folders for each.  These folders are just numbered, which is not helpful, but if you open the **install.rdf** file in each of the folders with a text editor, you will quickly find out which extension it is.

Remove that file and the extension will be gone, BUT, as I said, I have no idea how safe this is, so just move the folder to another location, or even just to wastebin, just in case you do need to get it back to allow TB to run again.

---

### Post by shaunthesheep on 2013-07-12
Many thanks for the advice. In the end I resolved my problem without having to uninstall Enigmail.

---

