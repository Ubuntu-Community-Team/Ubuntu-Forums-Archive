---
title: "Internet virus pro"
date: 2009-02-11
forum: Security
---

### Post by lanark95 on 2009-02-11
Somehow I have downloaded the malware internet antivirus pro and it insists on staying on my screen..It will not let me  close the window..help..am using ubuntu 8.04 LTS

---

### Post by mikewhatever on 2009-02-11
What window/application are you trying to close?

---

### Post by digitalbenji on 2009-02-11
try hitting alt+F2 then typing xkill then clicking the window you want to close.

---

### Post by lanark95 on 2009-02-11
I went to [http://scan4gate.com](http://scan4gate.com) and a malware downloaded automatically to my computer...this is the box opened on my screen form that site:
"Serious security and privacy threats found on your computer. It may damage your files or steal your personal and financial information.

Click "OK" to start downloading CRITICAL security software update."
I don't want to download anything, but canceling does not close the box..I rebooted but the page [http://scan4gate](http://scan4gate) just re-appears..I can't find the window to kill in xkill

---

### Post by cariboo on 2009-02-11
Go to Firefox-->Edit-->Preferences-->Main-->Home Page and click the Restore To Default button.

Btw the link doesn't work anymore.

Jim

---

### Post by mikewhatever on 2009-02-11
We don't know what internet browser you use. The default one is firefox, and if that's the case, open a Terminal window, type 'killall firefox' without quotes and hit Enter. That command should close all firefox windows, and in case you use another browser, you obviously have to reveal which one.

---

### Post by lanark95 on 2009-02-11
> **mikewhatever said:**
> We don't know what internet browser you use. The default one is firefox, and if that's the case, open a Terminal window, type 'killall firefox' without quotes and hit Enter. That command should close all firefox windows, and in case you use another browser, you obviously have to reveal which one.

I use firefox..but when I restart the computer the page comes up again..restoring defaults doesn't  help

---

### Post by lanark95 on 2009-02-11
> **mikewhatever said:**
> We don't know what internet browser you use. The default one is firefox, and if that's the case, open a Terminal window, type 'killall firefox' without quotes and hit Enter. That command should close all firefox windows, and in case you use another browser, you obviously have to reveal which one.

Thanks, mikewhatever..this time it has worked...indebted..

---

