---
title: "Wine auto Upgrade - Now program won't start"
date: 2009-03-28
forum: Wine
---

### Post by Metaljaz on 2009-03-28
Well wine did an automatic upgrade today to version 1.1.18. I can no longer
run portal gt, which is a mud client. The program worked fine before the upgrade and i am not sure what happened. I deleted portal and reinstalled it and still got the same problem. (Exception EDBEngineError in module Portal.exe. Invalid file name.)

---

### Post by hikaricore on 2009-03-28
Run it from a terminal and see what kinda error output you get.

---

### Post by Metaljaz on 2009-03-28
command not found

Now, is there a way to roll back wine to ver 1.1.17 without a reinstall?

---

### Post by hikaricore on 2009-03-28
run this from a terminal

> wine --version

If that still gives you an error download this:

[http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.17~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.17~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)

I'm assuming you're on a 32 bit system otherwise find the correct package here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Likely something went wrong during your updates.

---

### Post by Metaljaz on 2009-03-28
wine-1.1.18

I really thank you for helping me with this problem. I really need my portal back.

So if I delete wine I can reinstall 1.1.17 just don't do any updates to it, right?

---

### Post by hikaricore on 2009-03-28
You can actually just install the 1.1.17 package without uninstalling wine.  Just be sure to skip it when updating later.  ^_^

---

### Post by Metaljaz on 2009-03-28
When i tried to do the above install i got an error message that states:
Error: A later version is already installed

Any other suggestions?

---

### Post by Metaljaz on 2009-03-28
Okay I deleted version 1.1.18 and installed 1.1.17. Wine is back up and running. I installed it from the WineHQ .deb package file archive link that you posted and not from Synaptic Package Manager. It was showing 1.1.18. 

Thanks for the help.

---

