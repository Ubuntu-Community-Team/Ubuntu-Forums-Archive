---
title: "ecryptfs encrypted $HOME Jaunty - change login password"
date: 2009-07-26
forum: Security
---

### Post by Aang Aero on 2009-07-26
I'm using Ubuntu 9.04 (Jaunty) after turning my back on Windows, and I read about encrypting my /home directory here ([http://blog.dustinkirkland.com/2009/02/jaunty-encrypted-home-directories.html](http://blog.dustinkirkland.com/2009/02/jaunty-encrypted-home-directories.html)).  

I ran into one problem.  If I change my login password, I can't get back into my user folder after restart.  

I read somewhere that I could "rewrap" the passphrase file with - "ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphase".  However, that didn't work for me.

So my question:  Once I change my login password (which syncs with ecryptsfs encrypted /home directory), how do I get that relationship between my login and encrypted home directory back?

---

### Post by electromage on 2010-07-27
"Same thing just happened to me" bump... I can still mount it manually by switching over to console, but I don't see a logical way to do this.

I can change my login password back manually, or mess with the command line, but I've got customers who won't or can't do this! This needs to be automatic somehow.

In the meantime, what's a simple way to fix this?

---

### Post by bodhi.zazen on 2010-07-27
> **electromage said:**
> "Same thing just happened to me" bump... I can still mount it manually by switching over to console, but I don't see a logical way to do this.

I can change my login password back manually, or mess with the command line, but I've got customers who won't or can't do this! This needs to be automatic somehow.

In the meantime, what's a simple way to fix this?

You change you password graphically (in the "about me" menu) or if you change your password in the command line you also need to manually update ecryptfs.

See also this page :

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

Scroll down to the "Change password" section (screen shots included as are both graphical and command line instructions).

---

### Post by electromage on 2010-07-27
Thanks, I found that guide and it worked for me. I believe the OP tried that process however, and still had a problem.

---

### Post by abuster on 2010-12-14
Link is [http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs), without the slash[IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

---

### Post by roomey on 2011-02-02
[INDENT]I read somewhere that I could "rewrap" the passphrase file with - "ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphase".  However, that didn't work for me.
[/INDENT] 
Hi Mate,
I think the command should be 
ecryptfs-rewrap-passphrase /home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase

[INDENT] So my question:  Once I change my login password (which syncs with ecryptsfs encrypted /home directory), how do I get that relationship between my login and encrypted home directory back?[/QUOTE]
[/INDENT]Sorry, not sure if this answers your question. When you make the encryption passphrase and your login passphrase the same, you should only have to login once as normal and your directory should auto decrypt.
For future reference, if you use the graphical password change tool, you should not have to change the encryption passphrase separately.

---

### Post by lgmdaniel on 2011-08-15
> **roomey said:**
> [INDENT]
Hi Mate,
I think the command should be 
ecryptfs-rewrap-passphrase /home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase

[INDENT]

Cheers for this, as mine had some how become unlinked from the password change I made as the system forced me to make a change.  This enabled me to re-wrap with the password I had.

Messages saw on login where -

/home/$USER/.ICEauthority
/home/$USER/Desktop
/home/$USER/.nautilus

---

### Post by CampLife on 2012-10-19
Never mind...sorry.

Thanks.

---

### Post by overdrank on 2012-10-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

