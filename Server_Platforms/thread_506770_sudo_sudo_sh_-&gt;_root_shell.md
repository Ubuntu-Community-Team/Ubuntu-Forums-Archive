---
title: "sudo sudo sh -&gt; root shell"
date: 2007-07-22
forum: Server Platforms
---

### Post by B-Con on 2007-07-22
From "man sudoers":
> root_sudo   If set, root is allowed to run sudo too.  Disabling this
                   prevents users from "chaining" sudo commands to get a root
                   shell by doing something like "sudo sudo /bin/sh".  Note,
                   however, that turning off root_sudo will also prevent root
                   and from running sudoedit.  Disabling root_sudo provides no
                   real additional security; it exists purely for historical
                   reasons.  This flag is on by default.
What confuses me is the mention "chaining" of sudo commands to get a root shell. Wouldn't "sudo sh" give you a root shell? Why would you need to do "sudo sudo sh"? The [RootSudo](https://help.ubuntu.com/community/RootSudo) tutorial itself says that "sudo -s" will give you a root shell.

---

### Post by Gannin on 2007-07-22
Yes, they all work.  The person writing the document either didn't realize that the other methods would work, or things have simply changed a bit since it was written.

---

### Post by jaffamuffin on 2007-07-22
sudo su root

Works for me.

---

### Post by B-Con on 2007-07-22
So then, what could ever be the purpose of chaining sudo? What would "sudo sudo" do that "sudo" wouldn't?

---

### Post by Gannin on 2007-07-22
Nothing, to the best of my knowledge.  Just another way of doing it.

---

### Post by Mr. C. on 2007-07-22
The chaining idea is that by running multiple sudo's, each running another sudo, one could defeat restrictions placed in the sudoers files.  With increasingly deeper subshells, to the sudoers file parser, the commands look completely different.  Eg:
```

sudo sh
sudo sudo sh

```
look different to a lexical parser, but functionally, they both create root shells.  Since there are numerous methods to defeat such restrictions, they setting as mentioned is historical.

MrC

---

### Post by Mr. C. on 2007-07-23
> **jaffamuffin said:**
> sudo su root

Works for me.

So does:

```
sudo -s
```

There is no reason to use sudo to run su to create a root shell!

MrC

---

### Post by B-Con on 2007-07-23
> **Mr. C. said:**
> The chaining idea is that by running multiple sudo's, each running another sudo, one could defeat restrictions placed in the sudoers files.  With increasingly deeper subshells, to the sudoers file parser, the commands look completely different.  Eg:
```

sudo sh
sudo sudo sh

```
look different to a lexical parser, but functionally, they both create root shells.  Since there are numerous methods to defeat such restrictions, they setting as mentioned is historical.

MrC
OK, that makes some sense, but I'm having a hard time trying to picture an actual example of that. Wouldn't the sudo's evaluate outwards, meaning that each one is run with it's normal user permissions? Could you craft an example of this?

---

### Post by Mr. C. on 2007-07-23
Most sudoers files allow root to do anything.  Eg: 

```
root            ALL=(ALL) ALL
```

Now imagine an admin wanted to allow a user to run some adminstrative tasks, but prevent ordinary users from gaining a root shell. So the admin modifies the sudoers file to prohibited the running by ordinary users of the command **sudo sh** (but didn't disallow it strictly for root).  Since the aforementioned all-inclusive root-can-do anything sudoers line exists, there is nothing in the sudoers file that prohibits the command [COLOR="SeaGreen"]sudo sh[/COLOR] from behing run:

[COLOR="Red"]sudo[/COLOR] [COLOR="SeaGreen"]sudo sh[/COLOR]

So sudo exec's the command named [COLOR="SeaGreen"]sudo[/COLOR] with the argument [COLOR="SeaGreen"]sh[/COLOR], and behold, a root shell is created.

The setting was trying to prevent this from occuring.  However, it was shortsighted.  There are far too many other commands that can be run, that will spawn a shell, or user's with root privs who can run chmod to set the setuid/setgid bit, can create root shells.  This is very difficult to defeat, and is a general chink in the sudo armor (especially for new users who believe it is secure or more secure than su).

MrC

---

### Post by B-Con on 2007-07-24
OK, I get it. Thanks for the example. :)

---

