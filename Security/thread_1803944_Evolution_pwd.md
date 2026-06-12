---
title: "Evolution pwd"
date: 2011-07-14
forum: Security
---

### Post by matuskap on 2011-07-14
Hi,

id like to know if theres way to make Evolution ask for password on start. I dont mean the mail-password, but its own application password. Couldnt google anything about it. 

Thx for help in advance.

---

### Post by dino99 on 2011-07-14
check for evolution rights and tweak it as you like with chown

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by matuskap on 2011-07-14
Well i didnt want to do that cause it only caused tons of problems with various apps mostly wine, so i dont have a good experience with this kind of solution... Everything starts to have problems with writing and reading and whatever... Besides everyone always tells me not to run apps as root unless im dying in 10 minutes and so i dont have to worry about consequences. Isnt there any other way how to make app password protected on start? I was hoping theres a plugin or something like that for Evolution/Empathy.

---

### Post by FuturePilot on 2011-07-14
Having a password like this just gives you a false sense of security. If you don't want other people in your email, create them their own account and lock the screen when you're away from your computer.

---

### Post by bodhi.zazen on 2011-07-14
> **futurepilot said:**
> having a password like this just gives you a false sense of security. If you don't want other people in your email, create them their own account and lock the screen when you're away from your computer.

+1

---

### Post by matuskap on 2011-07-14
Thats it... ? I ask if theres some way to do something and all i get is advice to lock my damn computer? Theres like 6546513546 possible scenarios why i need to let pc go while im out and others need to use it (just one out of the blue sky: were studying with friends, we have study materials open and i have to go off for a sec - i wont lock the damn nb so they cant learn just cause i need to take a wiz). I asked if anyone knows how to do it, not how not to do it. If i wanted to have things the way they are with no way of customizing and control whatsoever id be using Win right now. There is a way, last resort being "ownership solution", now im asking for alternative so dont give me crap about locking my computer cause thats not a solution thats crap. P.S.: I dont care if its illusion or not, it will be good protection against at least 95% of earths population since barely half of them can read and write. And thats good enough. 

So again, is there anyone who can help me get this thing going? Thx for any valid suggestions.

---

### Post by bodhi.zazen on 2011-07-14
> **matuskap said:**
> Thats it... ? I ask if theres some way to do something and all i get is advice to lock my damn computer? Theres like 6546513546 possible scenarios why i need to let pc go while im out and others need to use it (just one out of the blue sky: were studying with friends, we have study materials open and i have to go off for a sec - i wont lock the damn nb so they cant learn just cause i need to take a wiz). I asked if anyone knows how to do it, not how not to do it. If i wanted to have things the way they are with no way of customizing and control whatsoever id be using Win right now. There is a way, last resort being "ownership solution", now im asking for alternative so dont give me crap about locking my computer cause thats not a solution thats crap. P.S.: I dont care if its illusion or not, it will be good protection against at least 95% of earths population since barely half of them can read and write. And thats good enough. 

So again, is there anyone who can help me get this thing going? Thx for any valid suggestions.

This is what the so called guest account is for, allowing others to share your computer without sharing your account. Even windows uses separate accounts for different users, and a guest account as well.  Share your account/login at your own peril, in this case the loss of privacy.

---

### Post by haqking on 2011-07-14
> **matuskap said:**
> Thats it... ? I ask if theres some way to do something and all i get is advice to lock my damn computer? Theres like 6546513546 possible scenarios why i need to let pc go while im out and others need to use it (just one out of the blue sky: were studying with friends, we have study materials open and i have to go off for a sec - i wont lock the damn nb so they cant learn just cause i need to take a wiz). I asked if anyone knows how to do it, not how not to do it. If i wanted to have things the way they are with no way of customizing and control whatsoever id be using Win right now. There is a way, last resort being "ownership solution", now im asking for alternative so dont give me crap about locking my computer cause thats not a solution thats crap. P.S.: I dont care if its illusion or not, it will be good protection against at least 95% of earths population since barely half of them can read and write. And thats good enough. 

So again, is there anyone who can help me get this thing going? Thx for any valid suggestions.

If you are going to let other people use or share your login then you are asking for trouble.
If you want to make sure they dont read your mail that implies you think they may, if they are the sort of people who would then they shouldnt be sharing your login.

The security model exists for a reason, it is when people do away with the mechanisms in place that problems happen and the next you thing you know you are here asking for help becuase you want emails back that were deleted or your something is corrupt etc.

Use a guest account

---

### Post by matuskap on 2011-07-14
Ok just stop trying to avoid my original question by giving me hints pls. I asked if theres a way to make app ask for pass. I dont care what anyone thinks, if app asks for pass it >>>>>>>>ADDS<<<<<<<< to every single freaking security feature in place. Ur posts sound like if i made a big security hole in my whole system by making it ask that pass. And i wont make any guest account cause sometimes i actually need those mails while working and sometimes im working on projects that need multiple software apps and switching between accounts is unacceptable. Im not going to explain my reasons, i asked a question so stop going off-topic. Its universal and best solution for my current situation and its the only thing i want anyone to help me with. So third time already im asking the same question which was partialy answered just once in this thread: 

Does anyone know how to make app to ask a pass on start (besides changing ownership). Thx

P.S.: Dont try to lecture me on security risks. The only thing i want is an answer to my question. If ur 100% positive (i mean uber-sure like uve never been sure before) that it cant be done other than by ownership change then just tell me its impossible or if u know a way, post it here. Everything else is useless off-topic.

---

### Post by haqking on 2011-07-14
a dirty way would be to remove permission from yourself.

create a new user and give them permission.

then su to that user.

it is horrible way and i wouldnt recommend it as i am sure most people on here wouldnt.

the program running as another user wont be able to access your local home directory and files.

but to answer your question then yes probably it is possible.

I may be wrong and i am sure someone else might be able to shed light, i suspect Bodhi ^ can answer more succinctly on this

to just make evolution ask for a startup password under your own account i dont think is possibe and would be something the Evolution dev team would need to build into the app

---

### Post by DZ* on 2011-07-14
I use something like that with thunderbird on one computer. $HOME/.thunderbird there is a symlink to an encfs-encrypted folder (can made like this) --
```

sudo apt-get install encfs zenity
mkdir -p $HOME/Fuse/encr
mkdir -p $HOME/Fuse/decr
encfs $HOME/Fuse/encr $HOME/Fuse/decr
mv $HOME/.thunderbird $HOME/Fuse/decr
pushd $HOME; ln -s Fuse/decr/.thunderbird .thunderbird; popd
fusermount -u $HOME/Fuse/decr

```

I use a script that first launches zenity to pop up a password prompt box. Then the encrypted folder is mounted and thunderbird is started. When I close thunderbird, the encrypted folder is unmounted, and the script terminates. I do change the folder permission there, but that is only to prevent myself from launching thunderbird while the folder is not mounted. That way, thunderbird simply dies:

```
#!/bin/bash

bah=$(zenity --entry --hide-text --title="EncFS Password" --text="Type in password.")
chmod 755 $HOME/Fuse/decr
echo $bah | encfs --stdinpass $HOME/Fuse/encr $HOME/Fuse/decr
if [ $? == 0 ]
then
   thunderbird
   sync
   fusermount -u $HOME/Fuse/decr
else
   zenity --title="mount failed" --info --text="bad password" 0x0
fi
chmod 000 $HOME/Fuse/decr

```

---

