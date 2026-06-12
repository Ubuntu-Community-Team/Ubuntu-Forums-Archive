---
title: "The How-To Must Say: HOW-TO"
date: 2013-06-29
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2013-06-29
After 2 days of circling the instructions (lines in the terminal, e.g., fdisk -l; I have come to the epiphany that the MythTV/Mythbuntu How-To's are not written with the beginner in mind. I say this as I have been to numerous sites trying to understand how to make MythTV-Buntu NOT put the recordings in the root ("/") directory at: /var/lib/mythtv/recordings. I, like most users, have my /home for storage. The root is for the OS files.

So after wading through many pages of highly confusing ideas, some of which are out of date (e.g., someone told me to install the video plugin, which is now not part of Myth). At last I have come to understand that I must set the mythtv-backend/Storage Directory/Storage Groups/Default/Add New Directory to see the 'other' directory. And here is the killer: but nobody, nowhere says: 

cd /home

sudo mkdir /home/any-name-you-like-for-myth-recordings

and then return to the Myth TV backend and point the "Add New Directory" to the above newly made directory. And even more: nobody has said what file permissions are or are not available or required.

SO if I ever get this resolved to my satisfaction, I will write up a short How-To to allow beginners to do this safely, simply, and securely.

Thank you for your time reading this.

---

### Post by ajgreeny on 2013-06-29
I do not use myth, mythbuntu or need to do so at the moment, but I can warn you that if you use **sudo mkdir /home/any-name-you-like-for-myth-recordings** for a folder in your home, that folder will belong to root, not to you as a user, and it may therefore not be possible to save your recordings or other files in it without changing the owner back to you.

Just use **mkdir /home/any-name-you-like-for-myth-recordings** and it will be your folder, ie without the **sudo** prefix.

---

### Post by HermanAB on 2013-06-30
BTW, there are pre-installed Myth virtual machines available.  I won't recommend trying to install this thing yourself.  Rather get a VM.

---

