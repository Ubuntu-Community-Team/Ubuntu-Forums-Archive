---
title: "Guide to simple yet awesome privacy !"
date: 2010-04-19
forum: Security
---

### Post by johnkills on 2010-04-19
I am a newbie and the tips are simple, if you find any flaws with my theories, let me know. Thanks :)
[B]
1. Using a Virtual Machine, safe way[/B]

When you create a virtual machine, you also have to create a virtual hard disk, it is a file. On virtualbox it is usually something like HD.vdi. I create that file inside a truecrypt file. It is always encrypted. If I turn off the computer, the file is always safe. If I have to delete the virtual hard disk, since you will be deleting the encrypted file, it is also more safe. I think the speed of the virtual machine is the same. I never noticed if it is slower. 

**2. Make any encryption method impossible to open**

This works with any encryption method from truecrypt to zip or rar files. 
Lets say you have a encrypted file: SecretArchives.zip
You take that file and open it on a hex editor. Then move to the last line. 
You will find something like: 
69 6E 65 0A

You then copy the last bytes. Any amount you want, only one is fine. You copy the last one. 0A, then you delete it from the file.
It will be 69 6E 65 then you save that. You have a corrupt zip file. It will not open. Never, even with the right password. Since it is corrupt. 
If you want to open the file again. Open the hex editor once again and put 0A in the end. 
Your encrypted file will work again. 


That is it. Two simple tips. I hope you liked it and it works for you. 
Any comments? Thank you :)

---

### Post by Felix-the-Cat on 2010-04-20
I would just run an entire encrypted disk instead of running a vdi inside a encrypted folder.

---

### Post by HermanAB on 2010-04-20
Yup.  A virtual machine inside an encrypted disk is no more secure than a real machine with an encrypted disk.

Disk encryption only protects the data at rest.  In other words, when the machine is switched off.  It does diddly squat for security when the machine is running.

---

