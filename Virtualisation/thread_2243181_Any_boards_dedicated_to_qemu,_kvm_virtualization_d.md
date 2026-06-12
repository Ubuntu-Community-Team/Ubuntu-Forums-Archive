---
title: "Any boards dedicated to qemu, kvm virtualization discussion?"
date: 2014-09-07
forum: Virtualisation
---

### Post by Remten on 2014-09-07
I am sorry to be asking so many questions here about basic virtualization problems. But I don't know of any boards dedicated to qemu, kvm. Does anyone know any?

---

### Post by TheFu on 2014-09-07
None - to my knowledge.

Any machine capable of VT-x or AMD-v should be fine for home use.
If you want more capabilities, perhaps VT-d?  There might be newer virtualization extensions - haven't used them myself.

If running at home, this stuff is easy to get up and working on modern hardware. Performance considerations probably don't matter all that much - besides not using USB for storage.

If running for work, things become more complex - network I/O, disk I/O, memory bandwidth are all issues for consideration.  Budget usually matters.

---

### Post by Remten on 2014-09-07
I am running into problems with Linux Mint (no sound; software rendering mode, with display freezes and graphical aberrations). It seems that most VM users who tend to participate in the Linux Mint forums use Vbox or VMWare, not KVM, so not much info available there.

---

### Post by TheFu on 2014-09-07
Sorry - don't know anything about Mint.

---

