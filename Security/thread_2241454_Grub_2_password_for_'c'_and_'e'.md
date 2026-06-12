---
title: "Grub 2 password for 'c' and 'e'"
date: 2014-08-26
forum: Security
---

### Post by rasmus6 on 2014-08-26
[QUESTION]

Hello. 
I have a laptop (Samsung 305U-A1) with Lubuntu 14.04. I have Windows 7 and Lubuntu dualboot. My question is how can i put a password to grub so if someone else powers on the laptop they can only choose if they want to boot into windows 7 or Lubuntu, NOT press 'c' or 'e'. 
So i want to know how can i password protect the grub 2 menu so it asks a password if someone tries to press c to get into the command line or e.
I have googled a lot and tried to find an answer but without luck. 

-Thank You.

---

### Post by sudodus on 2014-08-26
Welcome to the Ubuntu Forums :-)

I don't know a way to put a password in grub.

But maybe we can solve your problem in some other way. Please describe what is your problem, what do you want to protect?

---

### Post by cariboo on 2014-08-26
I've never felt the need to password grub, but there is a wiki page [here]("https://help.ubuntu.com/community/Grub2/Passwords").

---

### Post by rasmus6 on 2014-08-26
Actually i found an answer.
I had to put

[B]set superusers="username"
password username password[/B]

in /etc/grub.d/40_custom

But thanks anyway !

---

### Post by rasmus6 on 2014-08-26
Actually a new problem occured. It worked at first for a couple of times. If i started up the laptop it went to grub and i could boot to anything. The password was only needed if i tried to enter "e" or "c" on my keyboard. But now when i rebooted the laptop, it asked a password when i tried to boot into Lubuntu? 
What has happened and how can i fix this?

-Thanks

//EDIT//

when i put

[B]set superusers="username"
password username password
[/B]
it asks for username and password for everything. If i can't just password protect e and c, can i password protect everything (with superuser) and then somehow unrestrict my menuentries, which are in this case, Lubuntu and Windows 7.
So what i'm trying to achieve here is that i could boot into Lubuntu and Windows 7 without any passwords, but if i try to press e or c it asks for a password.

---

### Post by sudodus on 2014-08-26
Please describe what is your problem, what do you want to protect?

There is probably a solution, and it might be quite different from setting a password in grub.

---

### Post by rasmus6 on 2014-08-27
I wan't to make this laptop ''secure'' because this is a school laptop. I got an assignment from school to dual boot linux and windows 7. I figured out if i disable USB/CD-dvd boot from bios, no one can boot to a live cd for an example. The students would be using the guest account on this machine. I'm just worrying that someone who have a littlebit more knowledge could do something if they could access the 'e' or 'c' in the grub menu. Hope you understand what i mean

And they're using it in school so no one takes the hdd of the computer and so on. This was also a request from my math teacher.

---

### Post by cariboo on 2014-08-27
This is one of those issue where I think security by obscurity comes into play. The chances of someone having enough knowledge to edit grub, especially in a school setting are pretty low, unless there are Ubuntu specific courses widely available. 

I'd be more worried about recovery mode, and allowing general access to Window than having the ability to edit grub.

---

### Post by rasmus6 on 2014-08-27
But are they able to mess up something if they for and example press 'e' and screw around with the lines, even if it was a mistake? And i deleted recovey mode with grub-customizer, does that help?  Or are they able to go from the command line into recovery? And the Windows is very restricted, our city deals with the citys computers so their IT-department have done their job on the school computers.

---

### Post by sudodus on 2014-08-27
If you want the regular Ubuntu user account(s) to be unavailable, then I suggest that you re-install it/them with ***encrypted home***. It will still be possible to mess with the computer, but there is no access to the private data of the user accounts without the correct password.

I think it is *very unlikely*, that someone will try and succeed, but yes, it is possible to go from the command line into recovery. And recovery runs the computer with superuser privileges, that is, they can destroy the system.

So with a good password and a good backup, the private data and Ubuntu will be well protected. (Restore the dual boot system from the backup, if someone has messed with it, or if someone has stolen the hard disk drive.)

---

### Post by rasmus6 on 2014-08-27
Okay thank you.

---

