---
title: "gpg stopped decrypting"
date: 2010-08-23
forum: Security
---

### Post by kiridude on 2010-08-23
Hi. I use gpg with thunderbird and had no problems over the last couple of years. All of a sudden, now, I cannot decrypt mails. These are from a windows machine using thunderbird.

The errors I get are:

```
gpg command line and output:
/usr/bin/gpg
gpg: invalid radix64 character 3A skipped
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 28 skipped
gpg: invalid radix64 character 29 skipped
gpg: invalid radix64 character 3A skipped
gpg: invalid radix64 character 2D skipped
gpg: CRC error; F00893 - 0A9B73
gpg: [don't know]: invalid packet (ctb=55)
```

Does anyone know what is wrong?

---

### Post by DaithiF on 2010-08-23
sounds like this issue:
[http://lists.gnupg.org/pipermail/gnupg-users/2008-September/034532.html](http://lists.gnupg.org/pipermail/gnupg-users/2008-September/034532.html)

---

### Post by kiridude on 2010-08-24
Thank you, but I still can't decrypt by removing that line. It happens that the person sending the mail to me has changed to Outlook. Do you know anything about reading encrypted mails from there?

---

