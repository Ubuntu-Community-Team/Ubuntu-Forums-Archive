---
title: "'scrreen' command produces no prompt"
date: 2010-09-08
forum: Server Platforms
---

### Post by sipickles on 2010-09-08
Hi

I am using Ubuntu 9.04 Server.

I use screen alot for persistant sessions and suddenly I have a problem.

When I type 
```
screen -R -DD
```
as usual, I get into screen but there is no command prompt. There is a cursor and I can type commands which work, eg ls. However I don't know which directory I am in, so it makes using it rather hard.

What have I done to break it?

Thanks

Simon

---

### Post by arrrghhh on 2010-09-08
Perhaps you should try killing that screen session and starting a new one...?  I've never had this issue.

---

### Post by sipickles on 2010-09-08
Yeah tried that. It says 'New screen' when I start.

Also, weirdly, if I press ctrl-A X to lock the screen, my password doesnt work to log back in!

---

### Post by arrrghhh on 2010-09-08
Hrm... I'm going to pull a Windows tatic on you and ask you to reboot the box :P

---

### Post by sipickles on 2010-09-09
I can't believe I haven't tried that!

However, still the same :(

I also tried 
```
sudo apt-get remove screen
sudo apt-get install screen
```

Same results eg:

tbh, I am pretty low skill level on linux so am not sure how to do a clean uninstall of a package.

EDIT - Sorted, for some reason it helped to select a new profile:
```
sudo select-screen-profile
screen
```

I didn't know about the ubuntu screen profiles - very useful bar along the bottom!

---

### Post by arrrghhh on 2010-09-09
Huh... Good to hear!  I did not know there were 'screen' profiles either ;)

---

### Post by sipickles on 2010-09-09
No, its still broken.

I get the command prompt now, but also these spurious messages in the screen window
```
/var/lib/screen-profiles/updates-available: line 43: /dev/null: Permission denied
                          /var/lib/screen-profiles/updates-available: line 44: /dev/null: Permission denied
                           /var/lib/screen-profiles/updates-available: line 75: /dev/null: Permission denied
                            /var/lib/screen-profiles/updates-available: line 76: /dev/null: Permission denied
```

wtf?

---

### Post by sipickles on 2010-09-09
I tried
```

sudo apt-get --purge remove screen
```

and reinstalled - still broken

---

### Post by sipickles on 2010-09-09
Ok FIXED!

I had to follow the instructions found here:

[http://www.linuxforums.org/forum/linux-newbie/27030-bash-dev-null-permission-denied-why.html](http://www.linuxforums.org/forum/linux-newbie/27030-bash-dev-null-permission-denied-why.html)

whatever /dev/null is!

---

### Post by CharlesA on 2010-09-09
/dev/null is a null device - it goes to "no where," you redirect output to make it "disappear"

See here: [http://en.wikipedia.org/wiki//dev/null](http://en.wikipedia.org/wiki//dev/null)

---

### Post by arrrghhh on 2010-09-09
But how did you screw up the permissions on /dev/null...?  Do I even want to know?

---

### Post by sipickles on 2010-09-24
This has occurred again after restarting server.

Fix:

```
sudo rm /dev/null
sudo mknod -m 0666 /dev/null c 1 3
```

---

