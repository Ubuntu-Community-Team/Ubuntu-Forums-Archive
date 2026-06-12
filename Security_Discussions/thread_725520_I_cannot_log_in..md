---
title: "I cannot log in."
date: 2008-03-15
forum: Security Discussions
---

### Post by delsydebothom on 2008-03-15
I don't know if this is the right category to post this in, but I need some serious help!

I was *trying* to install the ePSXe using the directions at this link [http://ubuntuforums.org/showthread.php?t=612021](http://ubuntuforums.org/showthread.php?t=612021)

I don't know what happened, but now I can't log in to my profile. When I try to log in, I get this message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session from being saved. File should be owned by the user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others."

Before it kicks me out, there is another dialog box that comes up. It says:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix the problem.

[] View details (~/xsession-errors file)

(process: 6049) GTK-WARNING **: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. 

For further details, see: [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)  

Refusing to initialize GTK+

(Process 6053) [At this point, it repeats the same message, and then tells me it can't create any of my main folders--the ones that would be under the "places" tab]

(x-session-manager: 6046): libgnome fs- WARNING **: unable to create ~/.gnome2 directory: Permission denied. Could not create per-user gnome configuration directory [lists directory]: permission denied."

Is there anything I can do??

---

### Post by Dr Small on 2008-03-15
Login to the console (CTRL + ALT + F1) and post back the output of this:
```
ls -l | grep .dmrc
```

And also:
```
ls -l /home/ | grep $USER
```

---

### Post by p_quarles on 2008-03-15
I'm guessing that you slightly mis-typed one of the chmod commands in the instructions. 

In any case, this is a common occurrence when playing around with permissions, and it's relatively easy to fix. First, you'll need to boot into recovery mode from the boot menu (press "esc" to see it if it doesn't show up automatically). This will give you a root console. 

Now, try to correct the ownership and permissions on the file in question.
```
cd /home/*your-user-name*
chmod 644 .dmrc
chown *your-user-name* .dmrc
```
Now, type the following to reboot into normal mode:
```
shutdown -r now
```
That's the first thing to try. If that doesn't work out (sometimes it doesn't), you will have to simply remove the broken file. Again, boot into recovery mode, but run the following instead:
```
cd /home/*your-user-name*
rm .dmrc
```
Reboot again, and the system will create a replacement file.

---

### Post by Dr Small on 2008-03-15
Why is booting into recovery mode necessary?

---

### Post by delsydebothom on 2008-03-15
I'm logged in to my wife's profile, since I can't get into mine. When I imput the first line, I get nothing. The second gives me 

drwxr-xr-x  48 *username*      *username*       4096 2008-03-15 20:19 *username*

---

### Post by p_quarles on 2008-03-15
> **Dr Small said:**
> Why is booting into recovery mode necessary?
I could be mistaken, but I think a broken .dmrc prevents any successful login to that account. 

> **delsydebothom said:**
> I'm logged in to my wife's profile, since I can't get into mine. When I imput the first line, I get nothing. The second gives me 

drwxr-xr-x  48 *username*      *username*       4096 2008-03-15 20:19 *username*
Does your wife's account have sudo privileges? If so, it will be easy to fix the issue from there.

---

### Post by delsydebothom on 2008-03-15
Yes, she has sudo privileges.

If it helps, when I attempted to follow your instructions, it told me that it could not access ".dmrc":No such file or directory. When I changed it to 644.dmrc (just putting them together) it said "Missing operand after 644.dmrc

---

### Post by p_quarles on 2008-03-15
> **delsydebothom said:**
> Yes, she has sudo privileges.

If it helps, when I attempted to follow your instructions, it told me that it could not access ".dmrc":No such file or directory. When I changed it to 644.dmrc (just putting them together) it said "Missing operand after 644.dmrc
That's because there's a space between "644" and ".dmrc". ;)

Since you have access to a sudo account, just use that instead. The commands will require you to use sudo with them this way, though:
```
sudo chmod 644 /home/username/.dmrc
```
etc.

---

### Post by delsydebothom on 2008-03-15
Strange...when I type in the directory for my home folder, it says that there is "no such file or directory". But when I browse through to my home folder, it's there. I just can't access any of the files. Honestly, I'd be happy if I could just get those files out of their veritable lock down.

---

### Post by delsydebothom on 2008-03-15
> **p_quarles said:**
> That's because there's a space between "644" and ".dmrc". ;) 

I tried it both ways, that's why the output was different both times. I don't know if I'm missing something, but I've tried every variation I can thing of, and still nothing :(

---

### Post by p_quarles on 2008-03-15
> **delsydebothom said:**
> Strange...when I type in the directory for my home folder, it says that there is "no such file or directory". But when I browse through to my home folder, it's there. I just can't access any of the files. Honestly, I'd be happy if I could just get those files out of their veritable lock down.
Can you post the output of this command?
```
ls -la /home/username/.dmrc
```

---

### Post by delsydebothom on 2008-03-15
ls: /home/username/.dmrc: No such file or directory

---

### Post by p_quarles on 2008-03-15
Heh. You need to replace "username" with your actual username.

---

### Post by delsydebothom on 2008-03-16
I did; I just replaced my real username with the word "username" in this post. ;p

---

### Post by p_quarles on 2008-03-16
Ok, got it.

Did you perhaps successfully remove that file before running that command? Have you tried logging into that account again?

By the way, if nothing else works, you can simply create a new user account and move all of your data over to that. That will certainly resolve the issue, but try logging into the current one once more.

---

### Post by delsydebothom on 2008-03-16
Thank you for your help; after a long time tinkering with the advice you and others have given me, I've finally got it working! :)

---

