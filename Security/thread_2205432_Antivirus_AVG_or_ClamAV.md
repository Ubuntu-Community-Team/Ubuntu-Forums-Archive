---
title: "Antivirus: AVG or ClamAV ?"
date: 2014-02-13
forum: Security
---

### Post by chrbar on 2014-02-13
Hello,

I would like to install an antivirus on my Linux server (running as NAS).

I found several free antivirus solutions, some are out of date, thus I kept [AVG]("http://www.avg.com/ww-en/faq.num-5329") (now free for personal and commercial use) and [ClamAV]("http://www.clamav.net/lang/en/") (which is OpenSource).

Do you uses (or have tried) one of these solutions?
Do you know which is the best?
Do you have some advices?

I would like a solution that moves infected files to quarantine folder, instead of delete them.

Thanks for your help!
Chris

---

### Post by raja.genupula on 2014-02-13
What is the main protection you are expecting from anti virus?

---

### Post by lisati on 2014-02-13
As with Windows, whatever you choose for AV protection is only as good as its database. Another consideration is the need for real time protection: the flavours of AVG and ClamAV I've used with Unutu ran on-demand rather than in realtime.

If you're considering running an email server, configuring Postfix to use ClamAV to scan emails is fairly straightforward; there are plenty of tutorials available.

---

### Post by raja.genupula on 2014-02-14
> **lisati said:**
> As with Windows, whatever you choose for AV protection is only as good as its database. Another consideration is the need for real time protection: the flavours of AVG and ClamAV I've used with Unutu ran on-demand rather than in realtime.

If you're considering running an email server, configuring Postfix to use ClamAV to scan emails is fairly straightforward; there are plenty of tutorials available.

+1 .

---

