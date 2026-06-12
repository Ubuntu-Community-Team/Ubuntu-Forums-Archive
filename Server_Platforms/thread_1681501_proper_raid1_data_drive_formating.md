---
title: "proper raid1 data drive formating"
date: 2011-02-04
forum: Server Platforms
---

### Post by alliance1975 on 2011-02-04
I have a ubuntu sever with a raid1 data drive formated in native linux ext3. I have searched for answers to my question but most likely I'm not asking it correctly. I want to use the data drive to store backups of files from various ubuntu and windows machines. Do I need to reformat the drive as ntfs to enable windows use or can it remain as ext3? For that matter can I reformat as ext4 as a soultion? Again, I wish to use the data drive as a backup storage.

---

### Post by psusi on 2011-02-04
You can and should use ext4.

---

### Post by sh1ny on 2011-02-04
Use ext4. You don't need it to be ntfs, to be able to see it from windows, as long as you set up samba to share it ( or depending on your backup software ).

---

### Post by alliance1975 on 2011-02-04
Thank you very much for your answers. I was fairly certain that ext# would work for my purpose but wanted to make sure. I have nothing stored on the data drives yet so converting them from ext3 to ext4 will be no problem.

Again, Thank you.

---

