---
title: "The anti-virus engine is reporting an outdated engine"
date: 2010-10-15
forum: Security
---

### Post by Richiegs on 2010-10-15
I use ClamTK Virus Scanner.Every time I check for updates, I get the following message: "The anti-virus engine is reporting an outdated engine." Does anyone know how I can get the latest version of the anti-virus engine for ClamTK Virus Scanner? Thank you in advance

---

### Post by boxcorner on 2010-10-17
> **Richiegs said:**
> I use ClamTK Virus Scanner.Every time I check for updates, I get the following message: "The anti-virus engine is reporting an outdated engine." Does anyone know how I can get the latest version of the anti-virus engine for ClamTK Virus Scanner? Thank you in advance

When I installed ClamTK from the Ubuntu Software Centre recently it reported that both the Antivirus engine and GUI version were  out-of-date.  

I updated the GUI to version 4.29 via sourceforge.net

This FAQ [http://clamtk.sourceforge.net/faq.html#outdated_engine]("http://clamtk.sourceforge.net/faq.html#outdated_engine") suggests politely reminding the maintainer of the distribution, to get the engine updated ... :confused:

_Updated Sunday 17 October 2010 @ 11:59:49_
I completely removed all ClamTK packages using the Synaptic Package Manager,
then using the SPM, searched for 'clam', re-installed all 8 marked with Ubuntu logo, plus clamtk (unmarked)
Result: the AV engine was up-to-date but the GUI was out-of-date!
Re-installed clamtk_4.29-1_all.deb previously downloaded from sourceforge.net
now the GUI is now up-to-date, but am unsure whether I need install any of the other unmarked ones,
for example to screen e-mails.

---

