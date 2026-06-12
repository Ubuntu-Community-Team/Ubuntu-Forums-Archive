---
title: "Be careful when handling infected email's Source Message"
date: 2019-09-06
forum: Security
---

### Post by ubix on 2019-09-06
A spammer can use > <STYLE> --... GARBAGE, garbage, GARBAGE ...-- </STYLE> section in the **eMail source-message files**, to confuse the laser printers with PDF creation commands, and potentially create embedded code by PDF-creator software like "ghostscript", with which they can potentially gain control of your PC hardware and peripherals including MICROPHONES, CAMERAS, and even COLLECT your DATA, package them and wait for a malicious code in a web Browsers to pick it up and deliver it to a culprit anywhere on the Internet. Indeed they can totally destroy your data and render your computer totally useless.

You need to be careful even when printing **email-message source** file from any Linux GUI based text editors, in particular Gedit and/or Pluma (and I believe also any other IDE text editors) that utilize laser printers and PDF creator programs. I suggest if you need to print **email-message source files**, to use _simple Unix pipe print facilities and filters_ on the command line rather than print functions built into editors to avoid triggering, into email embedded, attackers code.

_Please let me know if anybody has already reported this security risk_. Usually the first and the mildest form of symptoms for such an infection show up when your laser printer drivers start behaving erratically unexpectedly, or stop working all together. Though Thunderbird mail agent most often seems to be smart enough to ignore such malicious code however it can also be affected, which shows up as misconfiguration, for instance you loose menus or menu options you've set up, or even access and proper functioning of your Enigma features including your keys. Restoring your configuration to what it should be should fix any problems. At least it so far this always worked for me. 

So be safe, and make sure you have a record of your Thunderbird configuration somewhere!

Cheers, ubix

---

### Post by sevendogs1337 on 2019-09-07
Please provide an example of this ridiculous situation.

---

