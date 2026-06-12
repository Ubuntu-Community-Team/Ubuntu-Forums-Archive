---
title: "Changing user permissions"
date: 2012-06-15
forum: Security
---

### Post by Shakey Hands on 2012-06-15
Hi All

so the back story is as follows. i was a happy mac user who backed up all important data on two external HDD's, however my mac then crashed and burned. I then went and bought a PC replacement and am now using ubuntu 12.04 LTS. I then discovered that all data on the externals is set to read only. 

I need to change the permissions of the data on the external HDD's so i can read & right it freely OR somehow align my Ubuntu system user profile to my external HDD's.

The data is quite large. 100's of GB of .MP3, .wave and ISO installers make up the majority. It quite important i am able to recover this data. if i have to (for corruption safety) change files one at a time, i will. 

ive tryed the forums with moderate luck, i was looking at baltix 2.7? or some kind of elaborate terminal procedure?
but before i start mucking with important files i thought a straight (and personally specific) explanation would be smart. 

I'm running Ubuntu 12.04 LTS
My mac run (i think) the latest snow leopard.

thanks
:guitar:

---

### Post by nothingspecial on 2012-06-15
If your external drives have macs hfs+ file system then you either need to disable journaling or force mount them read/write. Neither approach is particularly safe as afaik, especially if your data is important to you. 

The best option if you plan on using Ubuntu for the forseeable future would be to transfer the data to a drive with a linux compatible filesystem.

---

### Post by yiannis66 on 2012-06-15
Give the follow command in terminal
```
gksudo nautilus
```
Then type your passward and then in the files
you want right click
 and choose properties, there u can change the properties u like to.

---

### Post by firekage on 2012-06-15
> **yiannis66 said:**
> Give the follow command in terminal
```
gksudo nautilus
```Then type your passward and then in the files
you want right click
 and choose properties, there u can change the properties u like to.

Maybe i'm wrong but there is faster metod:

```
chown -R profile:users /
```chown - change ownership
-R - recursively (all contents in folders)
profile - your profile (in my case it is firekage)
users - group

and

```
chmod 700 /folders/
```chmod - change files permission

(for owner)

```
chmod 770 /folders/
```(for owner and groups)

```
chmod 777 /folders/
```(for owner, groups, all)

Am I right?


If i have to do something like this i just do:

```
chown -R firekage:users /mnt/ (because on mnt i have mounted my hard drive disks)
chmod xxx /mnt/ (the same)
```

that's all. If i use truecrypt container than

```
chown -R firekage:users /media/
chmod xxx /media/
```

---

### Post by Shakey Hands on 2012-06-19
thx for the replies

i should of also mentioned that i still have the HDD from my old mac (this hdd is the user of the external hdd im trying to access). 

so im going to use a friends macbook to boot of my hdd. once thats done ill just change the user permissions  read and write. that should work right?

---

### Post by Shakey Hands on 2012-06-19
ok so i booted the old internal mac harddrive on a friends mac, then changed the user permissions of the external harddrive in question (and all files on it) to read/write. 

however i after connecting the new read/write external to my ubuntu laptop i still cant write files on the external harddrive.... ?

---

### Post by swatPellegrino on 2012-07-03
I am having a similar problem. bump.

---

### Post by Cheesemill on 2012-07-03
> **nothingspecial said:**
> If your external drives have macs hfs+ file system then you either need to disable journaling or force mount them read/write.
Have you done this yet?

---

