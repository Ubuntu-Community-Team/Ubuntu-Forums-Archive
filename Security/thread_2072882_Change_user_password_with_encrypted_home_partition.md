---
title: "Change user password with encrypted home partition?"
date: 2012-10-18
forum: Security
---

### Post by kleenex on 2012-10-18
Hi, after changing user password with '[COLOR=Green]passwd[/COLOR]' command I was blocked out on the next login (after entering password, screen was black for a second and login manager appeared again). I manage to login by pressing **ctrl + alt + F2** keys.  After login I changed (with password utility) user password to that one used before and after reboot I managed to login with LightDM.

I am using encrypted home directory (.Private etc.) so I think it is related to encryption password created during system installation. How to change user password when home directory (on separate partition [COLOR=Blue]/dev/sda*[/COLOR]) is encrypted? Can I use for example this method?[COLOR=SeaGreen] [COLOR=Black]click ===>>>[/COLOR] [U][B][Setup Encrypted Private Direcotry]("https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Setup_Your_Encrypted_Private_Directory").

[/B][/U][COLOR=Black]One more thing: does [COLOR=Blue]/dev/shm[/COLOR] is related to [COLOR=Blue]/run/shm[/COLOR]? I am asking, because when I tried to mount [COLOR=Blue]/dev/shm[/COLOR] with [COLOR=Green]mount[/COLOR] command, it is mounted but as [COLOR=Blue]/run/shm[/COLOR]. After mounting I have two entries about [COLOR=Blue]shm[/COLOR]. Is it normall behaviour?

[/COLOR][/COLOR]```
[COLOR=SeaGreen][COLOR=Black]**[COLOR=Green]kleenex@apo32[~][COLOR=Red]$[/COLOR] mount |grep shm[/COLOR]**
none on /run/shm type tmpfs (various_mount_options)
none on /run/shm type tmpfs (various_mount_options)[/COLOR][/COLOR]
```

---

