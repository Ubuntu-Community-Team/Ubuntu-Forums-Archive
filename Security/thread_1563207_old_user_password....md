---
title: "old user password..."
date: 2010-08-28
forum: Security
---

### Post by penholder on 2010-08-28
Just got  a ibm thinkpad t21 off ebay.  works great etc EXCEPT that it has the old users admin password for everything.  i have no way of getting the password.  i really need to wipe him out but i would ideally like to do it without wiping my hard drive.  there is no other evidence of the previous users belongings.  

pointers?- running ubuntu v 8.10. there currently is not meeting the system req to upgrade til i get to play more.

TIA-Julie

---

### Post by cariboo on 2010-08-28
You can create a new user password, by booting in recovery mode and typing the following command at the prompt:

```
passwd <user>
```

where <user> is your username. If you just want to get rid of the username that was on the system when you got it, you canuse the following command:

```
sudo deluser --remove-home user
```

For more info on the deluser command have a look at:

```
man deluser
```

---

### Post by penholder on 2010-08-28
Where do i putthis in. I am a novice.

---

### Post by BkkBonanza on 2010-08-28
All in all, I think your easiest approach is the Recovery Mode and just change the password. Recovery Mode is when you boot the system and in the first few seconds of Linux (it usually counts down 3.2.1...) you hit SHIFT and enter the boot menu and choose "Recovery". This puts you into a root console where you can do the **passwd** command directly. And then **reboot** command.

This is your only option if you don't have the password for the current and only user, as you can't gain admin rights to change anything.

Also, I should mention, if you care about security and privacy then you REALLY should re-install Ubuntu from a Live CD. If there is data you want then back it up first.

If you fully trust who you got the machine from then ok, you're probably ok. But if it's just some random guy, then it's not hard for him to pre-infect the system such that some day in the future he can gain access and get at any data/info you have. Not saying that's likely but safe is safe. Also, I say "guy" but everyone knows "gals" can be malevolent too. :)

---

### Post by Rubi1200 on 2010-08-28
> Also, I should mention, if you care about security and privacy then you REALLY should re-install Ubuntu from a Live CD.
Have to say I totally agree with this.

Even if you know the person really well, who can say whether there was something on the system they were not aware of?

---

### Post by penholder on 2010-08-28
i have just about 0 faith in the person i got it from (ebay) other than it was pretty must as described other than this password deal. i am in the middle (almost) of downloading 10.04 to burn and then i hope to write over from disk and be spanking clean.  there are no files i want to save since i have only had this a few days.

---

### Post by BkkBonanza on 2010-08-29
You're on the right track then.

---

### Post by penholder on 2010-08-29
can not get into recovery!  help me!

---

### Post by penholder on 2010-08-29
i need to get into recovery first.  i downloaded 10.04 and it went guess where- to "david".  hours wait for nothing.  so i need to get around that or figure out a way to same a new download off of david-which i am totally not sure of yet

---

### Post by BkkBonanza on 2010-08-29
Usually during boot you'll see the GRUB message and can hold down SHIFT to get the boot menu. Is this not working? Sometimes people disable boot messages so it's silent. But holding down SHIFT should still work. 

What do you see during booting?

Ummm. How did you download the ISO file without having access? I would think you'd be able to burn the CD too, but then maybe the software isn't installed and you need a pwd to install it?

---

### Post by cariboo on 2010-08-29
Hardy is much different from the current LTS, you need to press Esc to get into the grub menu. Just after Post, press Esc, and you should see the grub-legacy menu. Use the arrow keys to select recovery mode, once you select recovery mode, you will be taken to a menu, select drop to root prompt. You will be taken to something that looks like this:

```
root@alexis-maverick:~#
```

note root at the beginning of the line. Use the command in my first post:

```
password <user>
```

If you don't know what the user name is at the prompt type:

```
ls -l /home
```

the result should look something like this:

```
ls -l /home
total 24
drwxr-xr-x 61 cariboo cariboo  4096 2010-08-28 15:57 cariboo
drwx------  2 root    root    16384 2010-08-02 10:40 lost+found
```

The user name in the example above is cariboo

Once you know the user name you can change the password. After you have sucessfully change the password type:

```
exit
```

at the prompt, when you are back at the menu, use the arrow keys to select resume. this should take you to a login prompt, enter your user name and password when asked, your password will not be echoed back or there will be no indication as you enter it, this is a security precaution.

When you have successfully logged in, type:

```
sudo reboot
```

you will be asked to enter your password, and then the system will reboot.

---

### Post by penholder on 2010-08-29
I was not holding the shift down during boot-I will try that. 

I just redownloaded 10.04 during church (was not going to sit thru it for the 3rd time!).  I am burning right now and hoping that it will work.  just finished-let's find out!  I know my CD drive in the tinkpad works because i tested it with another cd.

---

### Post by penholder on 2010-08-29
got further than i have...well see!

---

### Post by penholder on 2010-08-29
didn't work. let's try again.

---

### Post by cariboo on 2010-08-29
As we discovered via your pm's you have a system with no users.

Start in recovery mode, and once at the prompt type the following command:

```
useradd -d /home/user -m user
```

substitute the name you want to use for user in the above command. Next set a passwd:

```
passwd user
```

where user is the user name you used in the first command

now you need to add the new user to the standard groups:

```
gpasswd -a adm,dialout,cdrom,plugdev,lpadmin,admin, sambashare user
```

Where user is the name you used in the first command. Once you have created the new user you can reboot, and you should be able to log in.

---

### Post by penholder on 2010-08-29
i could kiss you!

---

