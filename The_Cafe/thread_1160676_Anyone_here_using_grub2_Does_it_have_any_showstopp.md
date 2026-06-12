---
title: "Anyone here using grub2? Does it have any showstoppers?"
date: 2009-05-15
forum: The Cafe
---

### Post by MaxIBoy on 2009-05-15
I'm investigating the possibility of installing grub2. However, the documentation is very sparse, and the project's website hasn't been updated since early 2008, leaving me in doubt as to the state of the project. I've googled it, but there haven't been any *recent* forum/usegroup posts on the topic, so I don't know if the stuff I found still applies.

I don't mind using an "immature" product, as long as I can get things to boot. 

Does anyone here use grub2? Is it stable enough to "just work?" If not, what level of tweaking will be required to get it to work? Does it hold any performance benefits over grub legacy? How is the ext4 support?

---

### Post by dragos240 on 2009-05-15
I have it, but sadly had to downgrade because of win7. It wiped my MBR, so I had to manually compile the grub files and copy them to the boot directory and finally load that into the mbr. And what do you know... it worked! But grub2 worked better.

---

