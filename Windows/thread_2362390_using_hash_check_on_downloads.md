---
title: "using hash check on downloads"
date: 2017-05-28
forum: Windows
---

### Post by ddjtrkr on 2017-05-28
Using Win10, how do I check hash count to verify download integrity? I will be downloading from the distribution center and then burning to a USB stick.

Can hash count be used with u torrent downloads?

Thank you.
Don Jones

---

### Post by CharlesA on 2017-05-28
> **ddjtrkr said:**
> Using Win10, how do I check hash count to verify download integrity? I will be downloading from the distribution center and then burning to a USB stick.

Can hash count be used with u torrent downloads?

Thank you.
Don Jones

Assuming you are talking about downloading Ubuntu and verifying the ISO.. the SHA256 hashes can be found here:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

As far as generating the checksum on Windows 10, you can use Powershell to do it:
[https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/get-filehash](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/get-filehash)

---

### Post by SeijiSensei on 2017-05-28
Torrent clients calculate checksums on each block received to ensure the accuracy of transfers so I wouldn't be too concerned about file integrity.  If a block's checksum doesn't match, the client asks the tracker to resend the block.

---

