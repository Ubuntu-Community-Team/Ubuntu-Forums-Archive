---
title: "Advice on 22.04 Folder Encryption"
date: 2023-04-13
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2023-04-13
I have a friend who had to encrypt a folder in his Documents folder.  I installed encfs when he had 18.04 and it has been running fine since then and now on 20.04.  I have revisited him as I want to move him to 22.04 and now find that encfs has been depreciated.  We are talking about a stand-alone Desktop that is connected to the internet.  What is the best/easiest method of encrypting a folder (that contains sub folders) on 22.04?

---

### Post by TheFu on 2023-04-13
Use LUKS encryption for the entire OS, including the LV that contains /home/.

---

