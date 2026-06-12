---
title: "how to create a script??!!"
date: 2009-03-31
forum: Virtualisation
---

### Post by simon.hanna on 2009-03-31
I'm using virtualbox vista host and ubuntu guest...
I managed to share some folders but now I'd like to write a script to mount these folders automatically after booting...
sudo mount -t vboxsf music /media/music
that would be the line I write in the Terminal...
I just don't know how to write a script...
I'd be really thankful to anyone who knows how to do this....
Simon

---

### Post by dmizer on 2009-04-02
Just for your information, I've moved this thread to the virtualization section of the forums. People here should be able to help you.

The "Tutorials and Tips" section is only for providing tutorials and tips, not for requesting them.

Thank you :)

---

### Post by Dedoimedo on 2009-04-02
You can place the mount command into the rc.local file, this way, it will be executed on every boot. Alternatively, you can place the entry into the /etc/fstab file.

If you need more help, do tell.

Dedoimedo

---

### Post by kpatz on 2009-04-02
Add this to your /etc/fstab file:

```

music      /media/music vboxsf rw    0       0

```

---

### Post by simon.hanna on 2009-04-02
Thanks alot...
it finally worked!!!

---

