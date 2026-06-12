---
title: "GnuPG"
date: 2010-12-08
forum: Security
---

### Post by royace on 2010-12-08
When I use GnuPG to encrypt and decrypt a file the following happens. When I want to decrypt a file I use the following shell scripts:

     :~$ cat run1
      . wipe
      gpg --output crud1.txt decrypt crud1.txt.gpg
      cat crud1.txt
      cat
      . wipe



     :~$ cat wipe
      rm crud1.txt
      tput reset



     :~$. run1

      A pinentry window opens and I must enter a correct Passphrase. This works alright. I then do the following.

     :~$. wipe

      This erases the file crud1.txt and resets the terminal.
All is well but if I decrypt the same file again the file is displayed on the screen without entering the "Passphrese" again.
I have to restart the computer to for the program to work correctly. It seems the Passphrase is being chached and I don't know how to scrub the chache. Has anyone encountered this problem and do they have a solution other than turning off the computer?

---

