---
title: "Trojan virus wiped off printer programs?"
date: 2010-05-16
forum: Security
---

### Post by Camilia on 2010-05-16
This mourning I used my printer without any problems using ubuntu os. As the day went surfing got slower. I lost ability to print. Went into windows os, which I haven't used for a few day, and scanned with superantispyware. A Trojan virus was found. Went back to ubuntu os and found that all printer programs had been removed.

Anybody have this happen? This totally confuses me for I thought no virus could affect Ubuntu.

---

### Post by OpSecShellshock on 2010-05-16
Where was the trojan found? Thing is, malware requiring installation can't or won't affect Ubuntu the OS. However, something that is OS independent and rendered within the browser (like a javascript) can run, at least while the browsing session is active. In Firefox you can go to Tools-->clear private data and take care of most of that stuff if it lingers. It's a good idea to use the NoScript extension to prevent those scripts from running if you aren't doing so already. This may have been caused by a malicious banner ad or something.

As for the print drivers, removing those is an administrative action. I'm not sure if that's what happened, or if so, how.

---

### Post by lavinog on 2010-05-17
Do you have windows setup to access your ubuntu filesystems?
(this is not common unless you went through the trouble of doing it)

Normally windows cannot read a ext2/3 partition without another program, and currently I am not aware of a way to get windows to read a ext4 partition yet.
Without being able to read/write to your ubuntu partition, ubuntu should be safe from the virus.

---

### Post by Camilia on 2010-06-07
Superantispyware found trojan.mgr in files. I simply installed ubuntu in windows.

---

### Post by an0dos on 2010-06-07
I haven't messed around with Wubi installs before. The windows malware shouldn't affect your Ubuntu install. It could be that it is a simple coincidence. Have you tried disconnecting and reconnecting your printer?

---

### Post by Camilia on 2010-06-07
> **an0dos said:**
> I haven't messed around with Wubi installs before. The windows malware shouldn't affect your Ubuntu install. It could be that it is a simple coincidence. Have you tried disconnecting and reconnecting your printer?

I did try that! Looked in the synaptic manager and saw had no printer programs installed.

---

### Post by an0dos on 2010-06-07
Does the software center show that "cups" is installed?
Have you tried clicking on "System-->Administration-->Printing" and adding your printer?

---

### Post by Linuxforall on 2010-06-07
Not possible that the Trojan could infect Ubuntu partition, the only explanation is that unless the Trojan executed itself when you were in Windows and wiped out the ROM of the printers, again not really possible there.

---

### Post by Camilia on 2010-06-07
> **an0dos said:**
> Does the software center show that "cups" is installed?
Have you tried clicking on "System-->Administration-->Printing" and adding your printer?

Yeh, I went in Synapse manager and download the hiplip programs. Just trying understand why this could have happened. Seems more logical that superantispyware caused the problem.

---

### Post by an0dos on 2010-06-07
> **Camilia said:**
> Seems more logical that superantispyware caused the problem.

Sometimes it can be hard to distinguish malware from the software designed to remove it. :)

---

### Post by Timmer1240 on 2010-06-07
> **an0dos said:**
> Sometimes it can be hard to distinguish malware from the software designed to remove it. :)

This is true!

---

### Post by lavinog on 2010-06-07
> **Camilia said:**
> Yeh, I went in **Synapse manager** and download the hiplip programs.

Anyone want to beta test that program? ;)

---

