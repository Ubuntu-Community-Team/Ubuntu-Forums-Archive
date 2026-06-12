---
title: "GRUB error: Safe to reboot?"
date: 2020-04-09
forum: Ubuntu Development Version
---

### Post by amano on 2020-04-09
After installing the latest updates (PROPOSED not enabled) I get this:

```
dpkg: Abhängigkeitsprobleme verhindern Triggerverarbeitung für shim-signed:
 shim-signed hängt ab von grub-efi-amd64-signed | grub-efi-arm64-signed; aber:
  Paket grub-efi-amd64-signed ist noch nicht konfiguriert.
  Paket grub-efi-arm64-signed ist nicht installiert.

dpkg: Fehler beim Bearbeiten des Paketes shim-signed (--configure):
 Abhängigkeitsprobleme - Trigger bleiben unverarbeitet
Trigger für dbus (1.12.16-2ubuntu2) werden verarbeitet ...
Trigger für libc-bin (2.31-0ubuntu7) werden verarbeitet ...
Fehler traten auf beim Bearbeiten von:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is it safe to reboot or power down or should I wait for the next GRUB/Shim updates. It is scary sounding...

---

### Post by bbogert24 on 2020-04-09
The problem is due to a syntax error in /var/lib/dpkg/info/grub-efi-amd64-signed.postinst:

/var/lib/dpkg/info/grub-efi-amd64-signed.postinst: 23: Syntax error: word unexpe
cted (expecting ")")

The problem code is as follows:

```
case $1 in
    configure)
    target=x86_64-efi ;;
    # Check /boot/grub to see if we previously installed to an ESP. We don't
    # want to trigger the install code just by installing the package,
    # normally the installer installs grub itself first.
    if test -e /boot/grub/$target/core.efi; then
        /usr/share/grub/grub-check-signatures
        /usr/lib/grub/grub-multi-install --target=$target
    fi

    ;;
esac
```

Fix is to remove the extra set of semicolons after the target=x86_64-efi
statement.

Corrected code is as follows:
```
case $1 in
    configure)
    target=x86_64-efi
    # Check /boot/grub to see if we previously installed to an ESP. We don't
    # want to trigger the install code just by installing the package,
    # normally the installer installs grub itself first.
    if test -e /boot/grub/$target/core.efi; then
        /usr/share/grub/grub-check-signatures
        /usr/lib/grub/grub-multi-install --target=$target
    fi

    ;;
esac
```

This could have easily been prevented if one was to run shellcheck on their
code prior to testing/submission. Running lint type analyzers should be a
standard part of the software development process and will prevent these
types of occurances in the future if done(hint.. hint.. hint).

This error was found using the geany IDE and shellcheck.

Hopefully someone has already bug reported it.

P.S. I have tested this and it works your experience may vary.

Thanks,
Brett "WolfMan" Bogert

---

### Post by bbogert24 on 2020-04-09
I have bug reported the problem against grub2 version 2.04-1ubuntu24. 

You may want to add yourself to the bug report as the more folks we have 
reporting it the sooner it will get screened and fixed.

Thanks,
Brett "WolfMan" Bogert

---

