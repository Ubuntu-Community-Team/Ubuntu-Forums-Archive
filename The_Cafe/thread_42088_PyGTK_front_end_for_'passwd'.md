---
title: "PyGTK front end for 'passwd'"
date: 2005-06-16
forum: The Cafe
---

### Post by solomarv on 2005-06-16
Hello Everybody,

I wrote a little PyGTK front end for 'passwd' utility. I would appreciate it if you tried it out, told me your opinion, and (if i'm lucky) pointed out some bugs.

it can be found at [http://people.clarkson.edu/~solomarv/gpass](http://people.clarkson.edu/~solomarv/gpass) . There is a screenshot at [http://people.clarkson.edu/~solomarv/gpass-screenshot.png](http://people.clarkson.edu/~solomarv/gpass-screenshot.png) . The reason I did it is the document at [http://udu.wiki.ubuntu.com/GraphicalConfigTools](http://udu.wiki.ubuntu.com/GraphicalConfigTools) .

Thanks,
Rouslan

---

### Post by TravisNewman on 2005-06-16
nice, works for me

Much needed, thanks! Have you submitted this to the developers?

---

### Post by solomarv on 2005-06-16
No, I have not submitted it. How do I do that?

---

### Post by jdong on 2005-06-16
Wait... ubuntu doesn't have the "userpasswd" tool?

---

### Post by jdong on 2005-06-16
[http://linuxsoft.cern.ch/repository/73X/usermode-gtk-1.53-2.i386.html](http://linuxsoft.cern.ch/repository/73X/usermode-gtk-1.53-2.i386.html)

In the RedHat world, there's already GNOME tools for this, in the usermode-gtk RPM.

> 
The usermode-gtk package contains several graphical tools for users: userinfo, usermount and userpasswd. Userinfo allows users to change their finger information. Usermount lets users mount, unmount, and format filesystems. Userpasswd allows users to change their passwords. Install the usermode-gtk package if you would like to provide users with graphical tools for certain account management tasks.

---

### Post by somuchfortheafter on 2005-06-16
well now we have our own.. ucredential or uPasswordUtil...

---

### Post by UbuWu on 2005-06-16
Have a look here at the development mailing list: [http://www.ubuntuforums.org/showthread.php?t=40607](http://www.ubuntuforums.org/showthread.php?t=40607)

> That small program might actually be a frontend to different "passwd"
implementations, so it wouldn't need to be suid (and could be written
in some language more suitable for text-parsing such as Python or
Perl, just like system-tools-backends are written in Perl).


Sound like your little program  :razz:

---

### Post by solomarv on 2005-06-16
Indeed, it does sounds like my little program  :) . I think someone should update the bounty page with links to all of these projects.

Althogh, Tilleuil was having some problems with getting pexpect to work with 'passwd' in his app.  So I offered him to use code from my app. Hopefully, the power of the community will overcome the power of incommunication and something very good will come out of this mess  :-P

---

### Post by jdong on 2005-06-16
[QUOTE=somuchfortheafter]well now we have our own.. ucredential or uPasswordUtil...[/QUOTE]

Umm, that's fine and dandy, but I think the point of Open Source isn't that we reinvent the wheel. It took hundreds of revisions and security patches to RedHat's tool before it was free of bugs.

Especially in a locked down kiosk environment, obtaining a shell escape through a GUI proxy is a pretty common problem.


At least see if it compiles under ubuntu before tossing it aside. I know there's a deep sense of pride when you write your own solution, but please remember that it's always better to use a tried and true solution.

---

### Post by solomarv on 2005-06-16
Pride aside -- I just want to help the final product to be  better  :grin:

---

### Post by somuchfortheafter on 2005-06-16
i have a desire to u brand everything......

---

