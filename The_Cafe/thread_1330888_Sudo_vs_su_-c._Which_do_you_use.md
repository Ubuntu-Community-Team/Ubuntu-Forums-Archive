---
title: "Sudo vs su -c. Which do you use?"
date: 2009-11-18
forum: The Cafe
---

### Post by dragos240 on 2009-11-18
Most of us use a non-root account for general purposes. It's much safer. But what do you use for those applications and commands requiring root access? Sudo or su -c? Or perhaps just a root shell?

---

### Post by NoaHall on 2009-11-18
root on Arch, sudo on every other distro.

---

### Post by CJ Master on 2009-11-18
> **NoaHall said:**
> root on Arch, sudo on every other distro.
.

---

### Post by thegreenblob on 2009-11-18
I use sudo most of the time, unless I need to do a lot of commands with root privileges then I'll just use a root shell.

---

### Post by RiceMonster on 2009-11-18
the only reason I use sudo over su -c is you can get tab completion in bash (complete -cd sudo).

---

### Post by oldgeekster on 2009-11-18
sudo - whenever possible...

---

### Post by toupeiro on 2009-11-18
I use sudo.

su -c requires knowledge of a service account password e.g. root, oracle, or whatever service account you may be su'ing to.  Sudo allows command elevation by users (non-admins) to execute a pre-determined list of commands via a configuration file by any number service accounts (usually root).  It can just as easily be used by someone who already has the ability to get root on a specific machine, but the root password (or any other service account) may either remain private, or scrambled, as your security level requires. 

You may also restrict right down to a command switch level, the types of commands a person can run with sudo. su -c will not give you this flexibility.

---

### Post by alphaniner on 2009-11-18
> **toupeiro said:**
> Sudo is intended for command elevation by users (non-admins)

Maybe I'm misunderstanding, but in the Ubuntu model, sudo is intended to be used primarily by admins, and **not** by regular users.  Many even suggest a non-sudo-enabled account for regular use on single user machines.

For what it's worth, I use sudo, and sudo -i when I need to do a number of 'administrative actions'.  Which is quite often on my machine at work.  All the scripts I have written use sudo with individual commands when doing administratory stuff.

---

### Post by toupeiro on 2009-11-18
> **alphaniner said:**
> Maybe I'm misunderstanding, but in the Ubuntu model, sudo is intended to be used primarily by admins, and **not** by regular users.  Many even suggest a non-sudo-enabled account for regular use on single user machines.

yeah I sort of changed my wording around to say it allows elevation by users (non-admins) rather than to say its intended for non-admins.  Its intent is less for a particular group of people and more for a particular functional need, regardless of anything else.  Sorry about that.

sudo is used all the time in ubuntu, whether its sudo or gksu, its essentially providing the exact same functionality.  Canonical has encorporated that elevation model throughout their entire OS.  you basically cannot do system updates, or install Frozen Bubble, without a sudoers file telling you that you can, lets put it that way. :)

Sudo and the sudoers file is an incredibly powerful tool, and dangerous when wielded by the wrong hands.  Nobody should be hand authoring a sudoers file but an admin, but **using** sudo thats been configured properly can be used across the board.

I have some headless linux workstations that I support which without sudo, they would not be allowed to reboot them, and I would be creating a ton of work for myself.  Thats just one more example of how sudo can be used in a general manner on stand-alone machines.

---

### Post by The Funkbomb on 2009-11-18
I use su-su-sudio.

---

### Post by dragos240 on 2009-11-18
> **The Funkbomb said:**
> I use su-su-sudio.

Thanks for clearing that up.

---

### Post by The Funkbomb on 2009-11-18
> **dragos240 said:**
> Thanks for clearing that up.

Come on.. Phil Collins?  No?

---

### Post by dragos240 on 2009-11-18
> **The Funkbomb said:**
> Come on.. Phil Collins?  No?

Huh? :confused:

---

### Post by toupeiro on 2009-11-18
wow... Now I feel old.

---

### Post by Xbehave on 2009-11-18
> **toupeiro said:**
> su -c requires knowledge of a service account password
The way sudo is used in ubuntu makes that a null point. in ubuntu sudo is the same as su -c but
it uses a seperate password for root (sudo passwd can enable this on ubuntu)
it remembers your password for a set amount of time
ot handles variables better. (using su -c "command" is a PITA)

sudo CAN be used in a whole host of interesting ways and is more powerful than su, but you have to go out of your way to set that up.

---

### Post by The Funkbomb on 2009-11-18
> **dragos240 said:**
> Huh? :confused:

Phil Collins was part of a band called Genesis.  As part of his solo act, he had a song called Sussudio.  It was sort of an anthem in the 80s.  The 80s were a very popular decade in the 20th century.

---

### Post by Excedio on 2009-11-18
> **dragos240 said:**
> Huh? :confused:

WHAT!?!?!

[Classics my friend...listen to the classics]("http://www.youtube.com/watch?v=9OoYDb9DW7A&feature=PlayList&p=EF7AAC3F3D8781D2&playnext=1&playnext_from=PL&index=41")

Scroll about 1:00 in

---

### Post by dragos240 on 2009-11-18
> **The Funkbomb said:**
> Phil Collins was part of a band called Genesis.  As part of his solo act, he had a song called Sussudio.  It was sort of an anthem in the 80s.  The 80s were a very popular decade in the 20th century.

Sorry man. Born in '95. I wouldn't of known about them.

---

### Post by toupeiro on 2009-11-18
> **Xbehave said:**
> The way sudo is used in ubuntu makes that a null point. in ubuntu sudo is the same as su -c but
it uses a seperate password for root (sudo passwd can enable this on ubuntu)
it remembers your password for a set amount of time
ot handles variables better. (using su -c "command" is a PITA)

sudo CAN be used in a whole host of interesting ways and is more powerful than su, but you have to go out of your way to set that up.

I agree, to a certain extent, maybe functionally on the surface but not technically..  You're still using YOUR pasword, and through group membership, you could still revoke your ability to do that via sudo, the whole time keeping administrative passwords a secret.  My whole point is that, you CAN set that up.  I didn't want to debate the ethics of how they implemented the root password (because thats a sore spot for some in this community based on other threads), but if you are able to use su -c in ubuntu, I'm assuming you've manipulated the root password in some way or it would be impossible.   su -c can't handle any of this stuff we're talking about. The way I see it, they have two different use cases alltogether and are not really comparable.  Ubuntu uses a group for the ALL command alias, which you can control via a user profile when you create a new user, or by simply maintaining your groups. (**system - Administration - Users and Groups)**  You can choose Unprivliged, Desktop User, or Administrator.  Each one will allow you to do different things via sudo based on the groups you get put in.  Direct manipulation of the sudoers file is not necessary at all.  I don't see how you have to go out of the way the way ubuntu implemented it (considering user/group control) unless you are trying to build out a sudoers file like the one I described.

---

