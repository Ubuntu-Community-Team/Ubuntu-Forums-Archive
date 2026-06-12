---
title: "Packages now GPG-signed"
date: 2005-05-05
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-05
After reading up on debsign, I've added GPG signatures to all my packages (yep -- all 409!).

This is still uploading, and will take a bit of time to upload!

To take advantage of this, run:

```

wget http://backports.ubuntuforums.org/backports/pubkey.gpg -O- | sudo apt-key add -

```

---

### Post by XDevHald on 2005-05-05
[QUOTE=jdong]After reading up on debsign, I've added GPG signatures to all my packages (yep -- all 409!).

This is still uploading, and will take a bit of time to upload!

To take advantage of this, run:

```

wget http://backports.ubuntuforums.org/backports/pubkey.gpg -O- | sudo apt-key add -

```[/QUOTE]
 As well needed indeed! thanks jdong, all 1,422 signed, that's a lot to me, but you guys might have more ;)

Good stuff jdong :D

---

### Post by jdong on 2005-05-05
Ugh, doesn't seem to be working... :(

---

### Post by XDevHald on 2005-05-05
[QUOTE=jdong]Ugh, doesn't seem to be working... :([/QUOTE]
 what error you getting?

---

### Post by jdong on 2005-05-05
Still getting "The Following Packages are not Authenticated"

---

### Post by XDevHald on 2005-05-05
[QUOTE=jdong]Still getting "The Following Packages are not Authenticated"[/QUOTE]

Very interesting, I'm not getting that error like I did before I added the GPG signatures to the packages :-k

---

### Post by jdong on 2005-05-05
Can you elaborate on how you did it?

Maybe I'm doing something wrong :)

---

### Post by RastaMahata on 2005-05-05
[QUOTE=jdong]Can you elaborate on how you did it?

Maybe I'm doing something wrong :)[/QUOTE]
 Yeah, I'm still getting "The Following Packages are not Authenticated" :(

---

### Post by XDevHald on 2005-05-05
Ok, I take that back I am still getting the error, such as samba from the backports.

I contacted Michael Vogt who is the developer of Synaptic with regards of the error we're getting and also a way to find out on how to get this resolved if not turned off.

---

### Post by jdong on 2005-05-05
It's not Synaptic's/APT's fault -- I'm just being retarded at learning how to sign debs :)

I'll keep on trying in the meantime. However, I don't want to shift too much focus off backporting to sign debs :)

---

### Post by XDevHald on 2005-05-05
[QUOTE=jdong]It's not Synaptic's/APT's fault -- I'm just being retarded at learning how to sign debs :)

I'll keep on trying in the meantime. However, I don't want to shift too much focus off backporting to sign debs :)[/QUOTE]

Ok, I take that back I am still getting the error, such as samba from the backports.
 
 I contacted Michael Vogt who is the developer of Synaptic with regards of the error we're getting and also a way to find out on how to get this resolved if not turned off.

I'll keep you updated jdong through PM

---

### Post by jdong on 2005-05-06
Ok, debsigs is DEFINITELY the wrong way -- dpkg spews weird errors about packages being in invalid format.

I'm rolling all packages back to pre-signed status.

---

### Post by slava on 2005-05-11
Hello 
I am also having authentication problems...
i called
wget [http://backports.ubuntuforums.org/backports/pubkey.gpg](http://backports.ubuntuforums.org/backports/pubkey.gpg) -O- | sudo apt-key add -
and it printed out 
OK
but the packages from backports are still not authenticated
i checked sudo gpg --list-keys and it seems not have the new key.

---

### Post by Firetech on 2005-05-11
[QUOTE=slava]Hello 
I am also having authentication problems...
i called
wget [http://backports.ubuntuforums.org/backports/pubkey.gpg](http://backports.ubuntuforums.org/backports/pubkey.gpg) -O- | sudo apt-key add -
and it printed out 
OK
but the packages from backports are still not authenticated
i checked sudo gpg --list-keys and it seems not have the new key.[/QUOTE]
 1. Read the whole thread, jdong couldn't work out how to sign them the right way
2. the correct way to list the keys used by apt is "apt-key list".

---

