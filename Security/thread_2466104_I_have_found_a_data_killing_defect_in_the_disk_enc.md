---
title: "I have found a data killing defect in the disk encryption - linked to Kernel process."
date: 2021-08-19
forum: Security
---

### Post by llifandd on 2021-08-19
[COLOR=#333333][FONT=Ubuntu]I have a few encrypted external back up drives.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I encrypted them with relatively simple passwords / phrases, using a type of disk encryption, that connects the passphrase to the Linux Kernel on the machine used to encrypt them.... . 

I actually thought it was a stand alone disk encryption that could be opened simply with what was on the disk, from any (Linux) PC.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
Now a few computer systems later, I want to open them up and use them, AND the pass words / phrases do not work.

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The problem as I see it is that the connection from the Linux OS, was that the other part of the function / pass phrase, was stored in the Linux Kernel - which allowed the encrypted drive to be opened up.

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Now that the OS's and OLD computer/s are long gone, the encrypted drives are still working / available but the pass phrases do not work, because the matching kernel / linux OS is not there to synch with the encypted drive.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]This appears to be an unmentioned trap with using disk encryption.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Is there a way to open up an encrypted drive with it's passphrase, without the matching kernel?

And the disk encryption system need to be modified to make for stand alone encrypted drives that are able to operate on any OS, 

AND it needs to be pointed out that SOME Linux disk encryption methods, tie that drive exclusively to that machine and that OS with the matching data in the Kernel - and that they will not work anywhere else.

This being said, is there a way to open up an encrypted drive with it's passphrase, without the matching kernel?[/FONT][/COLOR]

---

### Post by CharlesA on 2021-08-21
It might help if you mentioned which encryption utility you used to encrypt the drives.

Do you mean you stored the encryption keys on the TPM of that specific machine?

---

