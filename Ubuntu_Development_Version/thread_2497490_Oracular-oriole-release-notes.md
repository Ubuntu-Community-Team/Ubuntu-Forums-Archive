---
title: "Oracular-oriole-release-notes?"
date: 2024-05-07
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-05-07
[https://discourse.ubuntu.com/t/oracular-oriole-release-notes/44878](https://discourse.ubuntu.com/t/oracular-oriole-release-notes/44878)
... but seems just a copy of Noble Numbat Release Notes

---

### Post by #&amp;thj^% on 2024-05-07
I'm setting this one out due to
>  We are reintroducing support for ZFS guided installations, enhancing the flexibility and choices available for your storage management needs. This is a new implementation in the Subiquity-based installers, and is without encryption by default. The encrypted ZFS guided option will be developed in a future release.
And did I read correctly:
> Known limitations:

    Requires TPM 2.0.
    Only a limited set of hardware is supported.
   **_ No external kernel-modules support. For example, no support of NVIDIA graphics cards._**

I don't remember seeing that On Noble -release-notes.

---

### Post by ian-weisser on 2024-05-07
One of the nice things about Ubuntu Discourse is that you get to see actions in progress.
Including the incomplete release notes as it gets pecked at by various engineers.

---

### Post by MAFoElffen on 2024-05-07
> **1fallen said:**
> 
I'm setting this one out due to
> 
We are reintroducing support for ZFS guided installations,  enhancing the flexibility and choices available for your storage  management needs. This is a new implementation in the Subiquity-based  installers, and is without encryption by default. The encrypted ZFS  guided option will be developed in a future release.


And did I read correctly:
 [Quote]
Known limitations:

    Requires TPM 2.0.

    
> 
Only a limited set of hardware is supported.

   **_ No external kernel-modules support. For example, no support of NVIDIA graphics cards._**                      

I don't remember seeing that On Noble -release-notes.         [/QUOTE]
Wait a minute... That way those are worded...

#1) "subiquity". That would imply that they are adding a ZFS option to the Server Edition installer(?) Desktop has been flutter since Lunar.

#2) Requiring TPM 2.0 backed encryption was a disaster with the ubuntu-desktop-installer. I can't remember if that was Mantic or Noble. (Will have to check my notes.) It was so bad, with my bug reports that they pulled it.

#3) No external Modules??? How is that going to even work? I'm pushing ZFS, BUT... Doesn't saying no external modules conflict with their push for ZFS? (Devil's advocate).

#4) No NVidia... I will not comment on that, but that alone, is big.

Curious to see how this goes, and what it means.

---

### Post by IanW on 2024-05-08
> **corradoventu said:**
> [https://discourse.ubuntu.com/t/oracular-oriole-release-notes/44878](https://discourse.ubuntu.com/t/oracular-oriole-release-notes/44878)
... but seems just a copy of Noble Numbat Release Notes
Looks like they just did a ```
$sed 's/Noble/Oracular/' release-notes.txt
```, but forgot the title.
I've messaged the author on Discourse about that last bit.

---

### Post by #&amp;thj^% on 2024-05-08
> **MAFoElffen said:**
> Wait a minute... That way those are worded...

#1) "subiquity". That would imply that they are adding a ZFS option to the Server Edition installer(?) Desktop has been flutter since Lunar.

#2) Requiring TPM 2.0 backed encryption was a disaster with the ubuntu-desktop-installer. I can't remember if that was Mantic or Noble. (Will have to check my notes.) It was so bad, with my bug reports that they pulled it.

#3) No external Modules??? How is that going to even work? I'm pushing ZFS, BUT... Doesn't saying no external modules conflict with their push for ZFS? (Devil's advocate).

#4) No NVidia... I will not comment on that, but that alone, is big.

Curious to see how this goes, and what it means.

I too am very curious how all this shakes out.

---

### Post by este.el.paz on 2024-05-14
Ran what was just a 143 or so package upgrade to oracular by editing the sources.list data . . . from "noble"?? to "oracular" . . . .  On reboot all appears to be running fine on my '12 Mac pro with Nvidia 780?? card.  I run "nouveau" rather than proprietary . . . .

So far so good.

---

