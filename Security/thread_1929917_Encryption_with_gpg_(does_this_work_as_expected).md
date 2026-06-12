---
title: "Encryption with gpg (does this work as expected?)"
date: 2012-02-22
forum: Security
---

### Post by xzi on 2012-02-22
Hi

I have a question about encrypting files with gpg, and then ensuring that the original isn't accessible. Sorry if a similar question to this has already been posted; I did a search and couldn't find the answer.

Basically, I have a plain text file that is used to store information such as my bank account number, credit card number, driving licence number, NI number, etc. I find that I frequently need these and don't like having to search around for them. For security, I have encrypted the file with gpg and then deleted the plain text version. I then wrote the following script, which I placed in my ~/bin directory.

```
 #!/bin/bash

EXPECTED_ARGS=1
ERROR=1
FILE_LOCATION="/home/xzi/Documents/personal/"

if [ $# -ne $EXPECTED_ARGS ]; then
    echo "ask expects exactly one search term."
    exit $ERROR
fi

cd "$FILE_LOCATION"

if [ ! -f info.txt.gpg ]; then
    echo "The encrypted info file is missing!"
    exit $ERROR
fi

if [ -f info.txt ]; then
    rm info.txt
fi

gpg info.txt.gpg

if [ -f info.txt ]; then 
    grep -i "$1" info.txt | cut -d: -f2-3
    rm info.txt
else 
    echo "Unable to decrypt file."
    exit $ERROR
fi

exit 0
```This allows me to quickly search for an item and, after entering the password interactively, view the information. It seems to work as expected and is very useful. But I am concerned that there may be an obvious flaw, particularly with regard to temporary files still being left somewhere. I'm pretty new to Linux so I'm not too sure about this.

Is there any problem with using gpg like this, and are there any other files that should be deleted or precautions taken?

Any insight would be appreciated. Thanks.

---

### Post by kevdog on 2012-02-22
This question would best be answered via the gnupg mailing lists.  Werner Koch and others respond very quickly to questions such as this, and you'll hear your answer directly from the author of gnupg.

---

### Post by DZ* on 2012-02-24
If you want to view and modify content of a gpg-encrypted file, but keep the copy on the disk always encrypted, consider using a text editor that supports decryption in the buffer. Both emacs and vi support that. I use emacs, with the following added to ~/.emacs

```
;;; EasyPG: GPG support (decrypt in buffer; save encrypted)
(require 'epa-file)
(epa-file-enable)
(setq epa-armor t) ; use ASCII armored encryption
(custom-set-variables '(epa-file-name-regexp "\\.\\(asc\\|gpg\\|gpg~\\|asc~\\)\\'"))

```

Files with extensions asc, gpg are assumed to be gpg-encrypted. You can associate these extensions to be opened with emacs in your file manager (e.g. nautilus) properties, so when you click on an encrypted file, emacs launches a password prompt dialog and opens the file decrypted. When you make modifications, the file is saved back encrypted. For the dialog to work, you'll need pinentry installed (pinentry-gtk2 or pinentry-qt4 for KDE).

---

