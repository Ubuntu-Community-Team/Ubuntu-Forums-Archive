---
title: "Can editing .bashrc lead to security issues?"
date: 2012-09-01
forum: Security
---

### Post by newhere_m on 2012-09-01
I am trying to define some commands for my convenience but worried a bit if editing .bashrc can lead to security issues. (I read long ago that .bashrc or .bash_profile are often edited by intruders, if I remember correctly so it is better to know the correct way to edit.)

I plan to do use the commands: 
```

gksudo gedit .bashrc&
add: alias com1='command_1' 

```Also, what is the difference between editing .bashrc and .bash_profile? I am unable to locate the .bash_profile.

---

### Post by 2F4U on 2012-09-01
If an intruder is able to edit those files, then he/she has already broken into your system  and, in my opinion, every worry about the files is too late.

---

### Post by drmrgd on 2012-09-01
First let me say that you don't need gksudo to edit you .bashrc file.  Since it is your file and should be owned by you, you don't need admin rights to modify it.

I don't know that .bashrc is any more of a security concern than any other system file in the event your computer is compromised.  What I mean is, if an attacker has gotten control of your system, having a secure .bashrc file is not going to save you.  So, from that, feel free to add any aliases you like to the file.

With regard to .bashrc vs .bash_profile, this page sums it up nicely:

[http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html](http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html)

In short, .bashrc is executed everytime you start up a non-login shell, while .bash_profile is only executed when you launch a login shell.

---

### Post by malspa on 2012-09-01
> **newhere_m said:**
> I am unable to locate the .bash_profile.

There is probably no .bash_profile file on your system. However, you might see ~/.profile and /etc/profile (and, /etc/bash.bashrc).

---

### Post by Lars Noodén on 2012-09-01
It's no more or less secure than any other script.  .bash_profile will be found in your home directory under the name .profile.

If I understand correctly, .bashrc gets called whenever you start a shell.  .profile gets called only when you log in.

---

