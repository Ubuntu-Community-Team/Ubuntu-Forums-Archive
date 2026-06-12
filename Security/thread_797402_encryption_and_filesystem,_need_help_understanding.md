---
title: "encryption and filesystem, need help understanding"
date: 2008-05-17
forum: Security
---

### Post by Cew27 on 2008-05-17
hey all i just figured out how to encrypt files in hardy heron, my question is will windows pc's and macs be able to receive and open these files with the given pass phrase ?
if i enter a password i keep closely guarded into an encrypted file to set as the pass phrase is it safe there? can any get my personal password from the file? 
also what is a journaled file system and what does it do ? 
lastly i saw an article in sofpedia talking about fully encrypting ubuntu is there a way to do this when i have already installed ubuntu? i dont want to re-install and loose all my hours of setting it up (also i want to encrypt so that when i send my laptop off for repair the repair men cant take a peak) 
many thanks 
i hope you can answer my questions :)

---

### Post by hyper_ch on 2008-05-17
depending on what encryption you used..... you don't give here any clue.

---

### Post by Cew27 on 2008-05-17
its a private pgp key

---

### Post by hyper_ch on 2008-05-17
if you want to fully encrypt ubuntu you will ahve to reinstall everything... however you can make a backup and save files and configuration... then you just copy that stuff back...

however windows cannot access/make transparent the fully encrypted system. If you want encryption to be open for multiple OSes use trucrypt... although I don't think you can encrypt ubuntu with it (yet).

As for gpg encryption, there are tools for linux, windows, mac.... so that shouldn't be an issue.

---

### Post by Cew27 on 2008-05-17
thanks, where is the tool that will let me back up my files and applicaion preferances? 
also is this type of encryption hard to crack

---

### Post by hyper_ch on 2008-05-17
just backup your /home folder with all hidden files in it....

maybe backup also the /etc folder and /var folder...

---

### Post by Cew27 on 2008-05-17
is there anyway to back up my whole filesystem if i just go into filesystem and drag and dop it all onto an ext hdd then drag and drop it all back in replacing all the old files?

---

### Post by hyper_ch on 2008-05-17
there is but it won't work with a fully encrypted system just like that...

---

### Post by Cew27 on 2008-05-17
oh ok so what can i do to get my system like it is now with the least ammount of hassle?

---

