---
title: "Nautilus Right-Click to verify PGP signture?"
date: 2012-01-16
forum: Security
---

### Post by PDA1 on 2012-01-16
How do I configure Nautilus or Seahorse (or other?) so that when I right click on a pgp signature associated with an encrypted file it will provide an option to Verify PgP Signature?

I'm running Ubuntu 11.04

---

### Post by emiller12345 on 2012-01-18
You could try this out,

create a file called gpg-verify.sh, with this in it
```
#!/bin/bash
#This script verifies the gpg sig
if [ ! -e "$1" ]; then 
    gdialog --title "GPG Verify" --msgbox "GPG file does not exist!" 20 80
    exit 1
fi

if [ ! -r "$1" ]; then 
    gdialog --title "GPG Verify" --msgbox "GPG file is not readable!" 20 80
    exit 1
fi

MAGIC="$(file "$1" | awk -F: '{print $NF}')"
extension="${1#${1%????}}"

if [ "$MAGIC" = " PGP public key block" ]; then
    TEMPFILE=$(tempfile)
    echo "PGP public key block" > $TEMPFILE
    umask 077
    mkdir temp-gnupg-dir 
    gpg --homedir=temp-gnupg-dir --import "$1" 2> /dev/null
    gpg --homedir=temp-gnupg-dir --list-keys --fingerprint > $TEMPFILE
    rm -r temp-gnupg-dir
    gdialog --title "GPG Verify" --textbox $TEMPFILE 30 80
    rm $TEMPFILE
    exit 0
fi

if [ "$extension" = ".asc" ]; then
    TEMPFILE=$(tempfile)
    gpg --logger-file $TEMPFILE  --fingerprint --verify $1
    gdialog --title "GPG Verify" --textbox $TEMPFILE $(cat $TEMPFILE | wc -l) 80
    rm $TEMPFILE
    exit 0
fi

if [ "$extension" = ".sig" ]; then
    file="${1%????}"
    if [ -e $file ]; then
        if [ -r $file ]; then
            TEMPFILE=$(tempfile)
            gpg --logger-file $TEMPFILE --fingerprint --verify $1 ${1%????} 
            gdialog --title "GPG Verify" --textbox $TEMPFILE $(cat $TEMPFILE | wc -l) 80
            rm $TEMPFILE
        else
            gdialog --title "GPG Verify" --msgbox "Found 2 Files\nError: File not readable\n${1%????}" 20 80
        fi
    else
        gdialog --title "GPG Verify" --msgbox "Found 1 File\nError: SIG File needs a data file" 20 80
    fi
    exit 0
fi

if [ "$extension" = ".gpg" ]; then
    file="${1%????}"
    if [ -e $file ]; then
        gdialog --title "GPG Verify" --msgbox "Found 2 Files: File already exists\nError: GPG would have tried to overwrite your file!\n$file\nExiting" 20 80
    else
        TEMPFILE=$(tempfile)
        gpg --logger-file $TEMPFILE $1 
        gdialog --title "GPG Verify" --textbox $TEMPFILE $(cat $TEMPFILE | wc -l) 80
        rm $TEMPFILE
    fi
    exit 0
fi

```make the file executable
```
$ sudo chmod a+x /path/to/gpg-verify.sh
```then move it into the directory ~/.gnome2/nautilus-scripts/
and if everything went well, you should be able to right click on a '.gpg', '.asc', or a '.sig' file in nautilus then >> scripts then >> gpg-verify.sh

---

### Post by tubbygweilo on 2012-01-18
PDA1,
Although not being at an Ubuntu machine at the moment iirc installing seahorse-utils from the repos may well give you the power you require.

---

### Post by FuturePilot on 2012-01-18
> **tubbygweilo said:**
> PDA1,
Although not being at an Ubuntu machine at the moment iirc installing seahorse-utils from the repos may well give you the power you require.

The seahorse-plugins package isn't in 11.10. Hasn't been ported to Gtk3.

---

### Post by tubbygweilo on 2012-01-19
I apologise for my duff information my memory must be failing.
So sorry.

---

