---
title: "Windows 7 Incorrectly Flagged As Not Genuine After Update"
date: 2019-01-22
forum: Windows
---

### Post by DeadlyOats on 2019-01-22
About a week and a half ago, I read an article that after updating Windows 7 using the Update Manager, that many installations of Windows 7, from several large business Windows networks, were incorrectly being flagged as not Genuine Windows.  The IT departments of these large businesses had to do all kinds of Windows acrobatics to fix the issue on their systems, but it's stuff that I don't understand.  So, I know I wouldn't be able to fix it.

As a result, I have not updated my Windows 7 installation, fearing that it would cause chaos on my machine.  However, I have not seen any follow up articles showing that Microsoft fixed the issue with their Update.

Does anyone know if this problem has been addressed?  Or has anyone had any issues with Windows Updates for Windows 7?

Thanks, in advance for your thoughts.

---

### Post by Frogs Hair on 2019-01-22
I have installed the January windows updates on both my computers without any problems.

---

### Post by howefield on 2019-01-22
This link might help.

[https://support.microsoft.com/en-au/help/4487266/activation-failures-and-not-genuine-notifications-on-vl-win-7-kms-clie](https://support.microsoft.com/en-au/help/4487266/activation-failures-and-not-genuine-notifications-on-vl-win-7-kms-clie)

---

### Post by DeadlyOats on 2019-01-22
It keeps mentioning "volume licensing."  So, I guess if I got mine as an individual license, I should be O.K.?  Well.  I sure hope so.  I printed the page you linked, howefield.  Thanks for that.

Thank you, Frogs Hair, for your input.  It is reassuring that you had no issues with your update.

---

### Post by DeadlyOats on 2019-01-22
O.K.  I have successfully updated Windows 7 without issue.  I held off because of that scare that my licensed copy of Win7 Pro would become trash if I did, but after looking more closely at howefield's link, I see that it this problem happened specifically to Enterprise licensed products that use Key Management Service (KMS) or Multiple Activation Key (MAK) and NOT Update Manager to update Windows.

> KB 971033 ("Description of the update for Windows Activation Technologies”) contains the following text:

"Note For an Enterprise customer who uses Key Management Service (KMS) or Multiple Activation Key (MAK) volume activation, we generally recommend to NOT install this update in their reference image or already deployed computers. This update is targeted at consumer installs of Windows using RETAIL activation."

We strongly recommend that you uninstall KB 971033 from all volume-licensed Windows 7-based devices. This includes devices that are not currently affected by the issue that is mentioned in the "Symptoms" section.

In other words, it seems that these businesses added an update that was meant for consumer licenses in their Enterprise, and that is what messed up their Win7 installs.

The article I read was not at all clear about that.  When I read it, it made it seem that this was a problem for anyone with Win 7.

Thanks again for your help!

---

### Post by jamesbrown2 on 2019-01-25
It is unclear if you do not know the terminology:  KMS activation vs SLIC activation.> So, I guess if I got mine as an individual license, I should be O.K.?Yes.

---

