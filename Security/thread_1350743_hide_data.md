---
title: "hide data"
date: 2009-12-09
forum: Security
---

### Post by xieu90 on 2009-12-09
hi
I need a program like Hide Folders ([http://www.fspro.net/hide-folders/index.html](http://www.fspro.net/hide-folders/index.html)) 
are there any similar program in ubuntu ?


I need these features:

#When Hide Folders application is not running, hidden files and folders are invisible anyway. Moreover, you can remove your Hide Folders 2009 application folder and the hidden files and folders will stay invisible. Fantastic?!


#Hide & Lock - The protected file or folder will not be visible to a user and it will not be possible to access them.   (nobody see it, and it still have password)

# Effective password protection when uninstalling program.
# Removing Hide Folders 2009 folder from the system will not uncover hidden folders

---

### Post by xieu90 on 2009-12-09
hi
I need a program like Hide Folders ([http://www.fspro.net/hide-folders/index.html](http://www.fspro.net/hide-folders/index.html))
are there any similar program in ubuntu ?


I need these features:

#When Hide Folders application is not running, hidden files and folders are invisible anyway. Moreover, you can remove your Hide Folders 2009 application folder and the hidden files and folders will stay invisible. Fantastic?!


#Hide & Lock - The protected file or folder will not be visible to a user and it will not be possible to access them. (nobody see it, and it still have password)

# Effective password protection when uninstalling program.
# Removing Hide Folders 2009 folder from the system will not uncover hidden folders

---

### Post by jsp21c on 2009-12-09
Take a look at TrueCrypt, [http://www.truecrypt.org/](http://www.truecrypt.org/)

I've added the linux version to my Ubuntu 9.10 thumbdrive but not had chance to set it up although I do use it on my Vista PCs.

TrueCrypt creates a file which can be mounted as a drive to open, the location of the file can be moved, it can auto dismount after a set time of not being used or if the user logs off and many other options too.

---

### Post by stoogiebuncho on 2009-12-09
> **jsp21c said:**
> take a look at truecrypt, [http://www.truecrypt.org/](http://www.truecrypt.org/)
+1

---

### Post by bodhi.zazen on 2009-12-09
Nothing like that exists on Linux.

On linux one restricts access with permissions. 

If permissions are insufficient, next comes encryption.

I would wonder how good a job that application does at "hiding" folders anyways. Unless it is using encryption they likely are easily discovered , and if they use encryption, one can easily find them, but not read the contents (would be my guess).

---

### Post by aysiu on 2009-12-09
You can see hidden folders by just pressing Control-H.

---

### Post by bodhi.zazen on 2009-12-09
Threads merged.

@ xieu90 : Please do not start multiple threads on the same topic. It causes duplication of effort and confusion.

---

### Post by juancarlospaco on 2009-12-09
to make it "invisible":
chmod -r filename.txt

to make it "visible":
chmod +r filename.txt

:) pretty fake security...

---

### Post by ayenack on 2009-12-09
It's possible to use TrueCrypt to hide one encrypted file inside another which makes it quite difficult to see the hidden files. If you go to truecrypts web site it explains how to do this also pretty good instructions when doing this in the gui.

---

### Post by xieu90 on 2009-12-10
hi, 
thanks everyone

Ctrl + H is nice and quick, works against newbie, but not that secure against pro ^^ I used it too

actually I found truecrypt and tried it before i made this thread.
aes 256 + whirlpool, i wonder if it is already cracked, so far i heard that it isnt cracked yet.
serpent is slow

I also tried the hidden volume on partition. the idea is good. but i have a problem there.

for example i create a 10 mb partition
3 mb for decoy/outer volume 7 mb for hidden volume
then i delete the decoy files (so i have 3 mb free from outer volume) and replace them with other files.
let it be a 2,5 mb files, and i choose protect the hidden volume option. then i always get the errors: cannot write the file because it is written to hidden volume area. something likethat.



if i can solve that problem then i think i will use truecrypt 
are there any idea to solve that problem ?

and truecrypt is quite dangerous too.
if i forget to choose protect hidden volume and just copy to outer volume i might lose my data forever. ^^
i lost a lot of time when i tried truecrypt (luckily that was only trying, i lost nothing important that time ^^  only time ^^ )

@bodhi.zazen   thanks for your hardworking ^^ sorry for posting 2 thread. i wont do it again ^^

---

### Post by xieu90 on 2009-12-11
are there any ways to keep data in over volume far from hidden volume?

and are there any ways to tell truecrypt where to write the data to ?

---

### Post by bodhi.zazen on 2009-12-11
> **xieu90 said:**
> are there any ways to keep data in over volume far from hidden volume?

and are there any ways to tell truecrypt where to write the data to ?

Make a data partition. If you do not give permission for users to mount it, only root can mount the partition.

Then use Linux permissions on the contents, unmount the partition when done.

---

### Post by Soul-Sing on 2009-12-11
There are some obscure nonubuntu encrypt progs like steghide and elettra to hide encrypted files etc.
But why should you use this sort of progs??

---

### Post by xieu90 on 2009-12-12
@bodhi.zazen thank you, I will try it
@leoquant  i think elettra is ok, but there are only versions of it until interpid (8.10), otherwise i would give it a shoot too ^^

i want to encrypt my laptop.so if i lose it then my data will be protected.
if i could i would add some tracking tool to it too. or may be something to self destruction like [this]("http://www.youtube.com/watch?v=uObDE_HsV3E")
but i have no idea about hardware ^^

---

