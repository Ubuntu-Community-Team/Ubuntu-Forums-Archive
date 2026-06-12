---
title: "[SOLVED] ClamTK found viruses - van pdf be virus"
date: 2008-05-03
forum: Security
---

### Post by Kognit on 2008-05-03
I launched my ClamTk and found three viruses. On my surprise, when i looked into quarantine, i saw three pdf files. Can pdf be a virus?

My examples in quarantine:
xxx.pdf.VIRUS

Each file in the end content .VIRUS, as shown by example. Are these really viruses?

When do i use false positive
Thanks for answers

---

### Post by Monicker on 2008-05-03
> **Kognit said:**
> I launched my ClamTk and found three viruses. On my surprise, when i looked into quarantine, i saw three pdf files. Can pdf be a virus?

My examples in quarantine:
xxx.pdf.VIRUS

Each file in the end content .VIRUS, as shown by example. Are these really viruses?

When do i use false positive
Thanks for answers


A file can be named anything and still be a virus, even if its not in actual pdf format.  I do recall that some viruses are able to spread via pdf though.  The adobe pdf format is capable of carrying embedded scripting for one thing, which could be used as an avenue of execution for a virus.

---

### Post by ThorstenS on 2008-05-16
At the moment several malware authors are using PDF exploits to attack vulnerable computers.

I've seen three different ones the last week.

The PDFs contain a javascript which triggers a vulnerability in acrobat. Malware is either included in the PDF as executable to be dropped or is downloaded.

The PDFs are a danger to windows users. But similar attacks would be possible on linux. Trust your AV software and check suspicious files on [http://www.virustotal.com](http://www.virustotal.com) .
Expect only a few vendors to detect it, the criminals are optimizing their malware on a daily basis to avoid detection.

---

