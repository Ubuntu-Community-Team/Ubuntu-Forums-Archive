---
title: "unable to resolve host"
date: 2011-05-31
forum: Security
---

### Post by ClientAlive on 2011-05-31
I have two things going on with my computer where I'm getting (error?) messages.

One is:

"The password you use to log in to your computer no longer matches that of your log in keyring."

This is in a window that pops up on my desktop after I log in and I have to enter my old password to get in the rest of the way.

I found this: [http://ubuntuforums.org/showthread.php?t=1036564](http://ubuntuforums.org/showthread.php?t=1036564) link and followed the path given in post #2. There, in the list, I find an entry named "uname@host" which shows my new/ changed host name. When I double click it and expand the "password" section at the bottom of the window I find that the password is indeed my new password, not the old one (you can tick box to "show password").

The other is, and I think this is connected:

When I use sudo in the terminal I get: "unable to resolve host"

I went to:

```

cd /etc; less hosts

```

and in the second line what I see is the old host name and not the new. I think that if I can correct this second thing, both will be resolved?? Or is that file even relevant to the situation??

If that is true, I want to make sure I go about it in the right way and not end up locking myself out of my own computer or something stupid like that.

Can anyone give me some direction on this?  :confused:

Thanks

---

### Post by JKyleOKC on 2011-05-31
Restart the machine and get the grub menu showing, then boot into the "recovery" entry rather than your usual one. This will set you up as the root user, so be very careful. You can then use a text editor to change the host name in /etc/hosts but be sure to also change it at /etc/hostname as well. Save the changes and restart normally. That ought to be all that's necessary for correcting the host name and sudo, but I'm not certain about the keyring problem.

---

### Post by CharlesA on 2011-05-31
Did you change your user account password from the commandline or via GUI?

As for the "unable to resolve host" thing, it happens when you change hostnames.

Edit the /etc/hosts file and replace the old name with the new name.

Note: sudo works fine, it just complains, so you can edit it with the machine running instead of having to boot into recovery mode.

---

### Post by ClientAlive on 2011-06-01
> **CharlesA said:**
> Did you change your user account password from the commandline or via GUI?

As for the "unable to resolve host" thing, it happens when you change hostnames.

Edit the /etc/hosts file and replace the old name with the new name.

Note: sudo works fine, it just complains, so you can edit it with the machine running instead of having to boot into recovery mode.


I changed the password via the gui (system > administration > users and groups > ). That's the only way I know how to do that. I'm having a hard time recalling which method I used to change the host name but I'm relatively certain I did that through the command line.

Is there anything I can to to cover myself if some mistake were to be made and I got locked out of my computer or something? Is there some file or something I can save to my thumb drive or some way I could roll things back in case something goes wrong?

Also I have never used recovery mode with Linux, nor have I ever read anything about how to do it or how it works. I'll google it right now though.

Thanks
-----------------------------------

Edit: The keyring thing is kind of concerning to me also. I mean, I can imagine two ways that things could go wrong on me. One is that when I edit the hostname in those files things become separated between the hostname and the keyring. The other is that the keyring be separated from the right password - except that I checked out what the password is set to in the keyring and it is the new one. Not sure if I'm thinking about these things right or not though. Maybe it doesn't even work that way.

It's just that these two things seem like they would be connected to one another - not separate. I gather that most things are connected to one another in some way. I think of the word - "systemic". Or, to use our solar system as an example - each part works together to form the whole. If one part gets thrown out of balance the rest of it messes up too. You know?

---

### Post by CharlesA on 2011-06-01
If you changed the password via the GUI, it should have changed your keyring password too. Hmm.

If you mess something up, you can always boot into recovery mode and reset your password or undo whatever change you made. :)

You can access it by holding down shift until the GRUB menu appears, then select "recovery mode" from the list.

---

### Post by ClientAlive on 2011-06-01
By the way

```

/etc/hostname

```

Only contains one item and that item is the new host name. And . . .

```

/etc/hosts

```

Contains seven items (plus a description line that is commented out). Below is what mine looks like now - but I've changed the actual name to "oldhost" because that is what it is - the old host name. I mean I changed it here on the post not in the file itself. I have not changed anything in the file yet. I'm going to copy both of those files (as they are before any changes) to my thumb drive before I do anything. Maybe it will make a difference to have the original on there just in case. I suppose I should make a copy on the local system too and append something like ".original" to the copied file name.

```

127.0.0.1       localhost
127.0.1.1       "oldhost"

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by CharlesA on 2011-06-01
Change "oldhost" to "newhost" and it should work fine.

---

### Post by ClientAlive on 2011-06-01
> **CharlesA said:**
> Change "oldhost" to "newhost" and it should work fine.


Ok. Here we go. Wish me luck.

I'm just not the same person I was before that one thing happened. You remember the one. That really changed me with regard to my relationship with Linux. What an eye opener!

:)

---

### Post by ClientAlive on 2011-06-01
> **ClientAlive said:**
> Ok. Here we go. Wish me luck.

I'm just not the same person I was before that one thing happened. You remember the one. That really changed me with regard to my relationship with Linux. What an eye opener!

:)


Ok . . .

```

cd /etc; nano hosts

```

Edited the second line to match the new host name; then, ctrl X to exit. Prompted to save the changes. Entered "y" (without quotes) and then press enter.

Then:

```

sudo reboot

```

Those solved the problem with the "unable to resolve host" thing when using sudo. I still have the keyring issue though. I think when I changed the password in the keyring I used the gui and first went into "users and groups" and then went to: "Applications > Passwords and Encryption Keys"  double clicked the entry that showed "uname@host" clicked the plus at the bottom of the window to show the password then ticked the "Show password" box and replaced what was in the field with the new one then exited out.

I wonder what I should look for to fix that? I think maybe I just didn't go about it the right way?

---

### Post by CharlesA on 2011-06-01
Try changing the password from System > Preferences > About Me

---

### Post by ClientAlive on 2011-06-01
> **CharlesA said:**
> Try changing the password from System > Preferences > About Me


Tried that and through users and groups again. (1) If I enter in the old password in the current password field (for the About Me route) and click "Validate" it tells me "The Password Was Incorrect." I enter the new password and it accepts it. I enter the same one into the new password fields below and click "Change Password" and it tells me "The Old and New Passwords are the same." If I go the Users and Groups route the result is similar.

It recognizes the new password and doesn't give me any problems logging in and using the machine - just that the window keeps popping up telling me it's not the same as the keyring one. When I look at the password in the keyring it is actually the same. I don't get it.

There are two things that come to mind though (1) Perhaps it is not the item: "uname@host" but some other item? OR (2) Something I noticed. In the window for "Passwords and Encryption Keys" there are two columns. The first is "Name" the second is "Key ID". In that key ID field the item "uname@host" is number 8 but if I count the number of items in total I see there are 7 and not 8. Also, if I trace the numbers in the "Key ID" field (1, 2, 3, 4, etc, etc) I see that there is no item 7.

Do you think either of those things has any merit?

---

### Post by CharlesA on 2011-06-01
I'm not sure what is causing it.

You could try manually changing the keyring password:

[http://blog.roberthallam.org/2010/07/current-password-does-not-match-keyring-fix/](http://blog.roberthallam.org/2010/07/current-password-does-not-match-keyring-fix/)

---

### Post by ClientAlive on 2011-06-03
> **CharlesA said:**
> I'm not sure what is causing it.

You could try manually changing the keyring password:

[http://blog.roberthallam.org/2010/07/current-password-does-not-match-keyring-fix/](http://blog.roberthallam.org/2010/07/current-password-does-not-match-keyring-fix/)


Awesome! That worked (at the link). I went with the first route by changing the password. I didn't want to mess with that other thing of deleting the file. Works though.

Thanks Charles.

:)

---

### Post by CharlesA on 2011-06-03
Glad to help. :)

---

### Post by safwankhan on 2013-03-21
> **CharlesA said:**
> Change "oldhost" to "newhost" and it should work fine.

This works fine on Ubuntu 12.04. I don't know why others are still complaining. Please make sure all that you are using the correct version of ubuntu and haven't messed it up enough from the default installation.

---

