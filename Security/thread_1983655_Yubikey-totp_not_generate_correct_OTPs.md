---
title: "Yubikey-totp not generate correct OTPs"
date: 2012-05-20
forum: Security
---

### Post by JarG0n on 2012-05-20
Yubikey-totp is not generating correct OTPs (one time passwords) on Ubuntu, but it generates correct OTPs in Windows.  Can anyone help?

```
usage: yubikey-totp [-h] [-v] [--debug] [--time TIME] [--step STEP]
                    [--digits DIGITS] [--slot SLOT]

Generate OATH TOTP codes using a YubiKey

optional arguments:
  -h, --help       show this help message and exit
  -v, --verbose    Enable verbose operation (default: False)
  --debug          Enable debug operation (default: False)
  --time TIME      Time to use as number of seconds since epoch (default:
                   1337558049)
  --step STEP      Time step in use (in seconds) (default: 30)
  --digits DIGITS  Length of OTP in decimal digits (default: 6)
  --slot SLOT      YubiKey slot configured for Challenge-Response (default: 2)

```

---

