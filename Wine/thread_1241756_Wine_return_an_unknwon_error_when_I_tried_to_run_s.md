---
title: "Wine return an unknwon error when I tried to run starcraft."
date: 2009-08-16
forum: Wine
---

### Post by legolas_w on 2009-08-16
Hi
I used to play starcraft on my computer from time to time and it was working fine until recent days which I tried to use it and it returned the following error when I tried to run it in command console. I am using wine-1.1.27 and ubuntu 9.04


the command I used:

```

env WINEPREFIX="/home/legolas/.wine" wine "C:\Program Files\arcraft Brood war\Starcraft Loader.exe"

```

The error:

```

fixme:advapi:SetSecurityInfo stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  161 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  548
  Current serial number in output stream:  548

```

Wine Process is not killed or stopped. I should press CTRL+C to kill the process.

Thanks.

---

### Post by PmDematagoda on 2009-08-16
Moved to the Wine section.

---

### Post by sandyd on 2009-08-16
have you installed directx?

---

### Post by NightMKoder on 2009-08-16
> **carlee said:**
> have you installed directx?

dont do that. ever (unless it says on the appdb page).

Get wine 1.1.26. there is a xrender-related regression giving you that error.

---

### Post by legolas_w on 2009-08-17
Thank you, reverting back to 1.1.26 worked fine for me.
Thanks.

---

