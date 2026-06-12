---
title: "Virus discussion"
date: 2008-07-01
forum: The Cafe
---

### Post by anotherdisciple on 2008-07-01
I am in no way trying to write a linux virus (I'm a complete newbie and couldn't do it if I wanted to), but I have been wondering what the possibilities are for people to do so. I mean... I know that they could sneak "sudo rm -rf /" (Just so I don't get in trouble for typing that: DON'T USE THAT COMMAND EVER! IT WILL DELETE EVERYTHING!) into a script and try to find some way to get you to run the script as root... but how could they just make it run as root without you helping them along? I'm hoping that the answer is "they can't", but I don't know.

My thought is this... is there were some way that you could use a command to look-up a user's password and use it... you could create a linux virus. Aren't these passwords saved to your disk somewhere? Still, you would have to make an executable file that I would think would need to be run by the user, but that is easier to do than getting them to sudo a file from the terminal.

Now, about deleting a user's personal files. Wouldn't it be really easy to write a script that deletes all of the files in the user's /home/user directory? That wouldn't need root access. I mean... I can always reinstall linux free of charge, but I can't recover my personal files if I failed to back them up. Just an idea... wouldn't it be a good idea to make deleting a single file easy, but make you need root access to delete entire folders in a user's home/user/* folders?

Again... I'm not trying to figure out how to make a virus... I've just been wondering if there is any way to actually do it. And what the linux community is doing to prevent this. I know about ip tables and permissions, so I don't need all of that... just some general discussion about the possibilities.

---

### Post by troy896 on 2008-07-01
there is no possible way for a script to do sudo rm -rf / since it will ask you for your password.

---

### Post by RATM_Owns on 2008-07-01
They could sneak it in next time you use something as sudo. You never know.

And there are worse things.
(The dd is put in [ ] to prevent accidental copy paste)
```
[dd] if=/dev/urandom of=/dev/hda
```

---

### Post by Martje_001 on 2008-07-01
> **anotherdisciple said:**
> Aren't these passwords saved to your disk somewhere?
No only [hashes]("http://en.wikipedia.org/wiki/Cryptographic_hash_function") are stored. So you need a lot of computer power (and even then it can takes 1000's of years) to crack the password.

> .. but how could they just make it run as root without you helping them along? I'm hoping that the answer is "they can't", but I don't know.
Sometimes, when an exploit is found, a user can become root without having to give a password. A good example is the one of ~half a year ago. If you just entered some commands into the terminal (which caused something), you became root. Fortunately this bug was fixed within a day.

> but make you need root access to delete entire folders in a user's home/user/* folders?
No because then you can do the following:
```
cd ~
find . | xargs *donotrun* rm
```
This would delete every single file one-by-one. Try it for yourself! '**find . **' outputs every file it can access in the current and subdirectory's. '**xarg**' runs for every output line of '**find .**' the command '**rm**'.

So.. the only problem is that you have to execute the virus.. *except* if there's found a exploit in firefox (or any browser), which you can use to run a file; there is no way a virus is going to affect you.

---

### Post by init1 on 2008-07-01
If the script used sudo, it might work because I think it only asks for your password every 15 minutes. So if someone had used sudo recently, a script could potentially get root access.

---

### Post by g2g591 on 2008-07-01
actually with john the ripper and a decent wordlist or two, it could be a matter of hours (if you use a <6 digit password, that doesn't have numbers/odd charecters) . it cracked a four letter word used as a password in about 10 min (im pretty sure it was on the wordlist, but...) The good news it didn't crack my 8 digit password not based on a word in the 6 hrs i let it run.

Good thing John needs root access to run. (that file the hashes are stored in is only readable by root)

---

### Post by no1wantdthisname on 2008-07-01
Yeah, I've always been worried about ~/.gnomerc.  This file gets executed by default when you start gnome.  For example:
```

echo "foo" > ~/foo

```
Put that in ~/.gnomerc.
Log out and log back in.  And you'll have a file "foo" in your home directory.  It would be really easy to do worse.

---

### Post by ladr0n on 2008-07-01
Well, I think we've established that it would be theoretically possible for a virus to wipe a user's home folder, or even the entire drive.  However, a virus that did this would instantly fail.  Viruses are successful when they are able to spread across many, many machines.  Linux provides an environment in which it is *extremely* difficult for a virus to spread.  This being the case, yes, a "virus" could wipe your system, but it would have to be one you write yourself.  Have fun with that ;)

---

### Post by ladr0n on 2008-07-01
> **no1wantdthisname said:**
> Yeah, I've always been worried about ~/.gnomerc.  This file gets executed by default when you start gnome.  For example:
```

echo "foo" > ~/foo

```
Put that in ~/.gnomerc.
Log out and log back in.  And you'll have a file "foo" in your home directory.  It would be really easy to do worse.

Hm.  You could set the .gnomerc permissions to 544 (removing write access for even the owner) and then  in the sudoers file let all users sudoedit their own .gnomerc file.  That wouldn't be hard to pull off automatically with the creation of new users, and it would prevent the possibility to a malicious script adding unwanted code to the file.

---

### Post by days_of_ruin on 2008-07-01
> **anotherdisciple said:**
> I am in no way trying to write a linux virus (I'm a complete newbie and couldn't do it if I wanted to), but I have been wondering what the possibilities are for people to do so. I mean... I know that they could sneak "sudo rm -rf /" (Just so I don't get in trouble for typing that: DON'T USE THAT COMMAND EVER! IT WILL DELETE EVERYTHING!) into a script and try to find some way to get you to run the script as root... but how could they just make it run as root without you helping them along? I'm hoping that the answer is "they can't", but I don't know.

My thought is this... is there were some way that you could use a command to look-up a user's password and use it... you could create a linux virus. Aren't these passwords saved to your disk somewhere? Still, you would have to make an executable file that I would think would need to be run by the user, but that is easier to do than getting them to sudo a file from the terminal.

Now, about deleting a user's personal files. Wouldn't it be really easy to write a script that deletes all of the files in the user's /home/user directory? That wouldn't need root access. I mean... I can always reinstall linux free of charge, but I can't recover my personal files if I failed to back them up. Just an idea... wouldn't it be a good idea to make deleting a single file easy, but make you need root access to delete entire folders in a user's home/user/* folders?

Again... I'm not trying to figure out how to make a virus... I've just been wondering if there is any way to actually do it. And what the linux community is doing to prevent this. I know about ip tables and permissions, so I don't need all of that... just some general discussion about the possibilities.
There really isn't a good way to stop scripts from deleting personal files.Except making everything that gets deleted go to the trash folder
and have that only be deleted manually and asking for a users password
(sudo or not)

---

### Post by Martje_001 on 2008-07-02
> **init1 said:**
> If the script used sudo, it might work because I think it only asks for your password every 15 minutes. So if someone had used sudo recently, a script could potentially get root access.
No, that's not exactly true. For example; go to a terminal a type:
```
sudo echo Hello!
```
next, click on **File --> New Tab** and go to the new tab. Again type the code and you'll see that you have to type your password again. This is also how it goes with script (I believe).

---

### Post by lisati on 2008-07-02
> **g2g591 said:**
> actually with john the ripper and a decent wordlist or two, it could be a matter of hours (if you use a <6 digit password, that doesn't have numbers/odd charecters) . it cracked a four letter word used as a password in about 10 min (im pretty sure it was on the wordlist, but...) The good news it didn't crack my 8 digit password not based on a word in the 6 hrs i let it run.

Good thing John needs root access to run. (that file the hashes are stored in is only readable by root)
Yes - I've seen that too, and checked it out. Just as well it needed my password to run.......

In order for a virus/worm/trojan/spyware/malware to do any serious mischief on a Linux, a number of things need to happen, and this usually includes being given permission to run.

---

