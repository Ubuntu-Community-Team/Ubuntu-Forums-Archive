---
title: "How to access a SHARED folder in Virtualbox"
date: 2010-07-09
forum: Virtualisation
---

### Post by timtincher on 2010-07-09
HOST OS: Windows XP
Guest OS: Ubuntu Lucid Lynx
I was just wondering how you access a shared folder in Ubuntu. I have already installed Guest Additions. What do I do? haha, sorry, major "noob" (wow, that's so nerdy)

---

### Post by JustinR on 2010-07-09
When you are editing the settings for your virtual machine, when you click the shared folders tab it tells you how to do this!

```

sudo mount -t vboxfs FOLDERNAME /media/ANYFOLDER

```

Where FOLDERNAME is the folder name that you are sharing. ANYFOLDER is a folder that you have to create with sudo privileges.

---

### Post by timtincher on 2010-07-09
This is what happened when I tried that command:
mount: mount point /media/ANYFOLDER does not exist

---

### Post by timtincher on 2010-07-09
Oh, I feel stupid. I know what you meant.. Feel free to not insult me. :)

---

### Post by timtincher on 2010-07-09
Thanks! Worked like a charm!

---

