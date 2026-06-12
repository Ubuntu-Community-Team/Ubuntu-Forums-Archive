---
title: "Adding SUDOers ???"
date: 2005-01-02
forum: Server Platforms
---

### Post by britishtrident on 2005-01-02
How do I give a newly created ordinary user sudo access ?

---

### Post by CowPie on 2005-01-02
[QUOTE=britishtrident]How do I give a newly created ordinary user sudo access ?[/QUOTE]
 Hi, add them to the gorup wheel.  Then add this to /etc/sudoers:

%wheel  ALL=(ALL) NOPASSWD:ALL

(you can just remove the nopasswd: part if you want passwords enabled so):

%wheel  ALL=(ALL) ALL



Ensure nothing is typed wrong!

OR for just an indicudial user you add the name:
newuser ALL=(ALL) ALL

---

### Post by amedico on 2005-01-07
[QUOTE=CowPie]Hi, add them to the gorup wheel.  Then add this to /etc/sudoers:

%wheel  ALL=(ALL) NOPASSWD:ALL

(you can just remove the nopasswd: part if you want passwords enabled so):

%wheel  ALL=(ALL) ALL
[/QUOTE]

Important: use the "visudo" command to edit the file, not just any text editor. The "visudo" wrapper will check the edited file's syntax and won't install the changes if the file is invalid. This prevents you from locking yourself out of sudo with a typo, etc.

---

### Post by CowPie on 2005-02-02
[QUOTE=amedico]Important: use the "visudo" command to edit the file, not just any text editor. The "visudo" wrapper will check the edited file's syntax and won't install the changes if the file is invalid. This prevents you from locking yourself out of sudo with a typo, etc.[/QUOTE]
 Very good point!!  This actually happened to me once and hten Ir ememberred there was no root account.

---

### Post by mike_c on 2005-02-06
Important: use the "visudo" command to edit the file, not just any text editor. The "visudo" wrapper will check the edited file's syntax and won't install the changes if the file is invalid. This prevents you from locking yourself out of sudo with a typo, etc.

OK, this just happened to me-- utter Ubunto noob who's used to simply editing config files with vi.  Now how can I fix it?  I was somewhat shocked to realize that I couldn't simply log in as root.

---

### Post by mike_c on 2005-02-06
> Important: use the "visudo" command to edit the file, not just any text editor. The "visudo" wrapper will check the edited file's syntax and won't install the changes if the file is invalid. This prevents you from locking yourself out of sudo with a typo, etc.

OK, this just happened to me-- utter Ubunto noob who's used to simply editing config files with vi.  Now how can I fix it?  I was somewhat shocked to realize that I couldn't simply log in as root.

---

### Post by CowPie on 2005-02-11
[QUOTE=mike_c]OK, this just happened to me-- utter Ubunto noob who's used to simply editing config files with vi.  Now how can I fix it?  I was somewhat shocked to realize that I couldn't simply log in as root.[/QUOTE]
 change the boot options on grub ubuntu options to

 init=/bin/bash rw 

Then do passwd root
and enter a password.

Now you should be able to edit sudoers with VISUDO! :).

( but don't use sudo prefix because you are root!)

---

### Post by gonzalogn on 2005-07-16
Hello

I need execute iptables from PHP 

How can config  Apache or Sudo ? (step by step please).

Thanks!

---

### Post by LordHunter317 on 2005-07-16
Don't do what the first poster recommended on Hoary.

You can just add the user to the admin group to give them full admin rights.

Be sure you trust them before doing so.  IF not, give them restricted rights.

---

