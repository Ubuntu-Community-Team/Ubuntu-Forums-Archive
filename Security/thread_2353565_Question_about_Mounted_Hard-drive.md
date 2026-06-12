---
title: "Question about Mounted Hard-drive"
date: 2017-02-22
forum: Security
---

### Post by ferfykins on 2017-02-22
So I have 2 hard-drives, 1 for windows, 1 for linux
although it appears the windows hard-drive is mounted, i was wondering if i should unmount it for security reasons, so if i get malware on my linux, it wont spread to windows?

---

### Post by DuckHook on 2017-02-22
Excellent question; excellent solution.

If you don't have any shared files between the two, then it's best to keep things clean and simple.

What you are asking about is but a variation of the 'nix philosophy of "least privileges" and "least access". Allow only what is necessary to get the job done.

In truth, it is probably more important to keep your Linux disk isolated from Windows, since chances are an order of magnitude higher that any infection would flow from Windows to your Linux disk rather than the other way around. Unfortunately, modern Windows malware (like ransomware, for example) are sophisticated enough to actually mount everything it can lay its hands on before doing its dirty work.

---

### Post by ajgreeny on 2017-02-23
It is also worth considering using a shared partition for all your data so that it can be available to both OSs but kept separate from the system files of both.

There's a useful thread at [https://ubuntuforums.org/showthread.php?t=2315714](https://ubuntuforums.org/showthread.php?t=2315714) which is old but still very relevant so worth a look, but I am certain you will be able to find a lot more if you search "shared data partition"

---

### Post by CharlesA on 2017-02-23
> **ajgreeny said:**
> It is also worth considering using a shared partition for all your data so that it can be available to both OSs but kept separate from the system files of both.

There's a useful thread at [https://ubuntuforums.org/showthread.php?t=2315714](https://ubuntuforums.org/showthread.php?t=2315714) which is old but still very relevant so worth a look, but I am certain you will be able to find a lot more if you search "shared data partition"

Vouching for this. But do keep in mind that NTFS permissions will not carry over between Windows and Linux (assuming you do use NTFS). :)

---

### Post by Bucky Ball on 2017-02-23
> **DuckHook said:**
> Unfortunately, modern Windows malware (like ransomware, for example) are sophisticated enough to actually mount everything it can lay its hands on before doing its dirty work.

Exactly. So you're keeping your fingers crossed and tossing a coin whether it's mounted or not. It can easily be mounted by a smart enough nasty, and there's plenty of them.

---

