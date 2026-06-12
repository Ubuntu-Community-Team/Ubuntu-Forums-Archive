---
title: "Intrusion detection with GRUB's 'cmp' command? What files would you compare?"
date: 2008-12-22
forum: Security
---

### Post by Herman on 2008-12-22
Hello,
I was taking a look through the GNU GRUB Manual today and there are a few GRUB commands that nobody ever uses, mainly because they're not very well explained in the manual.

I'm trying to think about what some of these obscure commands might be useful for.

One of them is the 'cmp' command, [13.3.5 cmp]("http://www.gnu.org/software/grub/manual/grub.html#cmp")
After a little time spent experimenting with the cmp command at GRUB's command line, I ventured to try it out as an entry in my menu.lst file and it worked!

To get it to work, it just needs to be typed in somewhere under a 'title' line, and be followed by the  'pause' command.
```
title                Intrusion detection
cmp                 (hd0,2)/dir/file1 (hd0,2)/dir/file1.back
pause
``` When you're booting up you can select that from the GRUB menu and it will display whether or not there's any difference between the two files.
Pressing any key returns you to the GRUB Menu and then you can go ahead and boot if you want.
It's easy and quick to use the cmp command to tell  if certain files have been changed in the system since the last time a backup copy of them was made, even without booting. 

But what files would be interesting ones to check?
Ideas anyone?

Regards, Herman :)

---

### Post by lswb on 2008-12-22
That does look interesting. The kernel image seems like the obvious choice but really a root kit can get an entry point through any kernel module as well, so that makes a <b>lot</b> of files to check. Look here: [http://www.securityfocus.com/infocus/1811](http://www.securityfocus.com/infocus/1811) 

BTW, your grub & dual boot web site is great!

---

### Post by Herman on 2008-12-23
:) Thank you, lswb,
That's a great link. 

I copied my current kernel to a different partition and ran GRUB's cmp command on the kernel and the backup copy of it and GRUB didn't report any differences.
Then I ran the cmp command again on the current kernel and an older (previous) kernel.
GRUB didn't return the verbose output I was hoping for, a byte for byte list of every difference, but instead just reported that the two files are differ in size.
It only took a second to come up with that answer, so it's hard to believe GRUB has performed the comparison in the detail we'd need for that kind of work.
Yesterday it was giving me very verbose outputs. I don't know what behaviour is programmed into GRUB's cmp command, maybe when we give it a file over a certain size it goes into a different mode and doesn't do such a thorough check.

More testing and experimenting will be needed.

Thanks for your input and the great link!
I'll work on it some more.
Regards, Herman :)

---

### Post by x3roconf on 2008-12-23
I would compare /etc/shadow and /etc/passwd :)

---

### Post by teddks on 2008-12-24
> **x3roconf said:**
> I would compare /etc/shadow and /etc/passwd :)

...but those would always be different, wouldn't they?

---

### Post by Herman on 2008-12-25
> I would compare /etc/shadow and /etc/passwd> ...but those would always be different, wouldn't they?     :) My idea would be to make a backup copy of certian files like /etc/shadow and /etc/passwd, in a different partition maybe, and then compare /etc/shadow with the backup copy of /etc/shadow and /etc/passwd with the backup copy of /etc/passwd.

That way the attacker would have to find out the spare copies of those files existed first, then duplicate whatever changes are made. Chances are a program or script of some kind will be used for an attack, so the attacker might not actually be able to take a look around and see what other files (backup copies of the original files), are there anyway, especially if they're in a separate partition. GRUB can look in any partition in any disk very quickly and easily, whereas it's a little bit slower to do that from an OS-bound program. Normally you need to find out about the other partitions first, then mount them. It depends on what kind of program or script the attacker uses I imagine. Would they think of that?

Another neat thing about GRUB is, it can look at raw areas of the hard disk. I haven't tried yet, but it should be possible to 'dd' some of these back-ups of original files to places like the unused area of the first track of the hard disk, between sector 21 and sector 63, where they'll be invisible. I haven't tested that yet, I will sometime soon though.  :)

---

### Post by teddks on 2008-12-25
> **Herman said:**
> :) My idea would be to make a backup copy of certian files like /etc/shadow and /etc/passwd, in a different partition maybe, and then compare /etc/shadow with the backup copy of /etc/shadow and /etc/passwd with the backup copy of /etc/passwd.

That way the attacker would have to find out the spare copies of those files existed first, then duplicate whatever changes are made. Chances are a program or script of some kind will be used for an attack, so the attacker might not actually be able to take a look around and see what other files (backup copies of the original files), are there anyway, especially if they're in a separate partition. GRUB can look in any partition in any disk very quickly and easily, whereas it's a little bit slower to do that from an OS-bound program. Normally you need to find out about the other partitions first, then mount them. It depends on what kind of program or script the attacker uses I imagine. Would they think of that?

Another neat thing about GRUB is, it can look at raw areas of the hard disk. I haven't tried yet, but it should be possible to 'dd' some of these back-ups of original files to places like the unused area of the first track of the hard disk, between sector 21 and sector 63, where they'll be invisible. I haven't tested that yet, I will sometime soon though.  :)

D'oh, right.

It seems like a TPM and Trusted GRUB would be a Good Thing here.

---

### Post by Herman on 2008-12-25
> It seems like a TPM and Trusted GRUB would be a Good Thing here. 	LOL, that's something I hadn't thought of yet. [Trusted Platform Module]("http://en.wikipedia.org/wiki/Trusted_Platform_Module").
That hilights a problem in my thinking though, anyone intested in security would have an encrypted file system in the first place, and therefore a separate /grub partition. That could be a problem... :-k

---

### Post by teddks on 2008-12-25
> **Herman said:**
> LOL, that's something I hadn't thought of yet. [Trusted Platform Module]("http://en.wikipedia.org/wiki/Trusted_Platform_Module").
That hilights a problem in my thinking though, anyone intested in security would have an encrypted file system in the first place, and therefore a separate /grub partition. That could be a problem... :-k

Yes, but that encryption can be compromised if, say, one were to put a kernel module on /boot with a keylogger in it. Trusted Grub or cmp hackery both ensure that the system is clean.

---

