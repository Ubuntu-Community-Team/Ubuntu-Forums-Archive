---
title: "Can't access my account after deleting mime.cache"
date: 2015-05-17
forum: Security
---

### Post by robert48 on 2015-05-17
Hello

I've done a silly. I have deleted /usr/share/mime.cache and that appears to have locked out of my account. When I log in I put in the correct password, the wheel spins for less than a secon and then goes back to the login screen. If I put the wrong password in it tells me the password is incorrect. When I put the correct one in it doesn't give me an error message, just dumps me back to the login screen.

I would dearly love to get back to my data.

Any advice gratefully accepted.

---

### Post by Bashing-om on 2015-05-17
robert48; Hummmm ....

I do not see how deleting 'mime.cache' could have  affected login.
1st up is to make sure that 'mime.cache' os all that was removed:
Do you get lots and lots of files returned;
```

ls -al /usr/share/

```

2nd: Have you lost authority to access "your" /home ?
```

ls -al .Xauthority
ls -al .ICEauthority

```

3rd: Who owns your "/home" ?
```

ls -al /home

```

Now maybe we know something
we can advise further

---

### Post by robert48 on 2015-05-17
I can't get in to run the commands, stuck at the login screen......I thought the way into GRUB menu was by holding down shift. How do I get to the GRUB menu?

---

### Post by robert48 on 2015-05-17
I can't get in to run the commands, stuck at the login screen......I thought the way into GRUB menu was by holding down shift. How do I get to the GRUB menu? I've managed to get to see my home drive by using a live usb. Allmy files seem to be there.

---

### Post by Bashing-om on 2015-05-17
robert48; Ouch !

You do say that at the login screen key combo ctl+alt+F1 does not allow you to log in terminally to the system ?

Maybe try and access from the "recovery console " .
On the legacy operating system (MBR vice UEFI);
Boot up the system and as soon as the BIOS (not UEFI) screen clears depress and hold the right-shift- key -> grub boot menu;
choose 'advanced" and in this next screen select to boot a "recovery" kernel -> recovery console ->"root".
This enables a terminal with 'root' access from which one can look at the system.
IF and when changes are to be made we will have to enable the ability to write to the hard drive from this access.

To exit out of the root terminal type exit abd you will be returned to the recovery console.

[INDENT][INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by robert48 on 2015-05-18
I can get access to a terminal with ctrl-alt-F1  from the login screen. I can log in with my username and password as expected. Neither the right or left shift keys get me to the grub menu.

I did a re-install from a live usb Vivid and all is well, even picked up on my separate home drive without tweaking of fstab.

---

### Post by Bashing-om on 2015-05-18
robert48; Ho Kay ;

The nuclear solution always works.

As this matter is now concluded;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]and just keep on keep'n on
[/INDENT]

---

