---
title: "Looking for Music folder through Virtualbox"
date: 2008-06-11
forum: Virtualisation
---

### Post by G!zZm0 on 2008-06-11
Is there any way I can access my Music folder in Ubuntu through Virtualbox???
I also wanted to know...why my virtualbox doesnt have any sound??? How can I fix that???

---

### Post by forestpixie on 2008-06-11
Turn on sound support in the vbox settings for the guest.

You need to share a folder through vbox settings.

---

### Post by G!zZm0 on 2008-06-11
Ok...Did that...But I don´t see the folder yet...How and where can I access it????   Any help???

---

### Post by forestpixie on 2008-06-11
Depends on what guest os you have?

In a windows guest os you access it as network drive if I remember correctly. In a linux guest os I don't know as yet.

Edit this is what I did to mount a shared folder from a ubuntu host in a ubuntu guest

1 - Create the shared folder in vbox settings with name muzak
2 - Open a terminal in the guest and make a directory to mount the shared folder in

    I created the folder with ```
sudo/media/music
```

3 - Then mount the shared folder (which I had named muzak) in the new folder with
    ```
sudo mount -t vboxsf muzak /media/music
```

4 - Opened nautilus and navigated to /media/music to access files from shared folder

---

