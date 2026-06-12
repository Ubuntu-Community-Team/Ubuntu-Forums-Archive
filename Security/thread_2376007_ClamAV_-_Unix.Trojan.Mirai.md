---
title: "ClamAV - Unix.Trojan.Mirai"
date: 2017-10-29
forum: Security
---

### Post by t-info-o on 2017-10-29
I recently ran Clam AV it produced this result.

Any advice as to what I should do next.

Thanks


/usr/lib/chromium-browser/chromium-browser:	Unix.Trojan.Mirai-5932143-0 FOUND


LibClamAV Warning:cli_scangpt: detected a non-protective MBR


LibClamAV Warning:cli_scangpt: detected a non-protective MBR


----------- SCANSUMMARY -----------
Known viruses:6326416
Engine version:0.99.2

---

### Post by SeijiSensei on 2017-10-29
Read: [https://www.hackread.com/linux-mirai-trojan-a-ddos-nightmare/](https://www.hackread.com/linux-mirai-trojan-a-ddos-nightmare/)

Then I'd uninstall chromium-browser and its files in your home directory.
```

sudo apt-get remove --purge chromium-browser
cd ~
rm -rf .cache/chromium
rm -rf .config/chromium

```

Now you can decide whether to reinstall chromium or not.

---

### Post by t-info-o on 2017-10-30
Thanks for your advice 

I have reinstalled chromium-browser and this appears to have fixed part of the problem.

Can anyone explain what this means

 [COLOR=#000000]               > LibClamAV Warning:cli_scangpt: detected a non-protective MBR

Thanks[/COLOR]

---

### Post by lisati on 2017-10-30
@t-info-o: I have read elsewhere that the report you received *could* be what's known as a false positive. The advice given was similar to that given by SeijiSensei, and is a sensible precaution against the possibility that it wasn't a false positive. Once you have removed chromium and it's cache, the decision to re-install is entirely up to you.

---

