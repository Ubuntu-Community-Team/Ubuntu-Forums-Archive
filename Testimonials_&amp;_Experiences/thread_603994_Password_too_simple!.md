---
title: "Password too simple?!"
date: 2007-11-05
forum: Testimonials &amp; Experiences
---

### Post by anabelle on 2007-11-05
I'm currently installing Ubuntu in as many PCs as I can, almost on 4 PCs a week, most of them are hosehold Family PCs used by children. And i find the **password too simple **warning at login *root enforced password change* a hard obstruction into the usability of the machine. All kids want their passwords to be real simple like candy, or dog, or secret... but they cant because of this _dumb_ message, this is one thing that really annoyes me in newer releases of ubuntu. i found in another thread ([http://ubuntuforums.org/showthread.php?t=275457](http://ubuntuforums.org/showthread.php?t=275457)) a way to disable it but, still its an annoying procedure.

I think its fine that the ubuntu team cares about the user security but Blocking the use of simple passwords its abusive. I think if a warning showed up, kind of:
[B]
Your password is too simple and may be insecure
[Change Password]        [Use Anyway][/B]

It would be secure but you still be able to set your password too 0 if you want to.

Im i being clear, i really hope this will be a reality :)

---

### Post by -grubby on 2007-11-05
if it has to be a complicated password why not just tape it to the monitor or something?

---

### Post by SyCo123 on 2007-11-13
I agree from the userbility point of view but security is still all important. Easy passwords open'up the possibility of Linux zombie armies just like the 1,000,000's of windows pcs that are used in DDOS attacks. 

I understand that kids need easy passwords but 'candy' and 'candy123'  are both easy for kids and one is much more secure than the other. If a kid asks lots of 'why' questions about their password, take the time to explain basic security. They are already aware there are bad people out there so they have to be careful when playing outside, just extend that to playing on the PC too.

---

### Post by frafu on 2007-11-13
Hello, 

As the Accessibility forum is intended to talk about software related to disabilities, I am moving this thread to a more appropriate forum. 

Have a nice day. 

Francesco

---

### Post by zero244 on 2007-11-14
I agree...make it something like cat123 or candy123. Also you can bypass the log in password all together. On feisty my login password is 1234 which I set when it was installed. Its curious Im not getting that warning. Though I might if I were to create a new user.
Its good your installing this for the kids great idea.

---

### Post by kpkeerthi on 2007-11-15
Yes. Just enable auto-loggin for the kids.

---

### Post by runemaste644 on 2007-11-16
I just use a master password. That way it is almost impossible to forget it, though if someone finds out my password, they have access to everything! Here are some tips for making passwords:

1. Choose something vague but easy to remember, like 'titanic'
2. Use symbols, like make your password titanic% . Nobody would ever guess that! Also, if you have a special character on your keyboard  (i.e. the euro symbol) use that.
3. Also use numbers in your password.
4. Master passwords are very easy to remember, but if somebody finds out your password, they have access to everything!

---

### Post by conehead77 on 2007-11-16
> **runemaste644 said:**
> I just use a master password. That way it is almost impossible to forget it, though if someone finds out my password, they have access to everything! Here are some tips for making passwords:

1. Choose something vague but easy to remember, like 'titanic'
2. Use symbols, like make your password titanic% . Nobody would ever guess that! Also, if you have a special character on your keyboard  (i.e. the euro symbol) use that.
3. Also use numbers in your password.
4. Master passwords are very easy to remember, but if somebody finds out your password, they have access to everything!

Another trick: Make a sentence and take the letters from the beginning of every word.

U-Stmp!
Ubuntu - Solution to my problems!

Easy to remember and pretty safe because theres not only letters in it. Maybe make a longer sentence to improve security further...

---

### Post by notepad on 2008-01-16
anabelle, the simple answer you are looking for is to set passwords as root (sudo passwd [username])

this was posted by MJN in the thread that you posted the link to. i tried the sudo passwd and it worked perfectly.

---

### Post by sa-mejia on 2008-03-27
I also need really simple passwords.  My kid is just learning to read, and it would be too demanding to ask him to write 1candy#23.   

All one needs to enable non--secure passwords, is to open the file /etc/pam.d/common-password and in the line where it says: 

password required pam_unix.so nullok obscure min=4 max=8 md5

eliminate the "obscure", so that it reads:

password required pam_unix.so nullok min=4 max=8 md5

---

### Post by error420 on 2008-11-14
> **sa-mejia said:**
> I also need really simple passwords.  My kid is just learning to read, and it would be too demanding to ask him to write 1candy#23.   

All one needs to enable non--secure passwords, is to open the file /etc/pam.d/common-password and in the line where it says: 

password required pam_unix.so nullok obscure min=4 max=8 md5

eliminate the "obscure", so that it reads:

password required pam_unix.so nullok min=4 max=8 md5

Thank you! This worked perfectly!

---

### Post by Sef on 2008-11-15
>  					Originally Posted by **sa-mejia** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=4598565#post4598565") 				
 				I also need really simple passwords. My kid is just learning to read, and it would be too demanding to ask him to write 1candy#23. 


Run a few words together: dogtigerdingo, 

or a sentence: Thedogatecatfood.

---

### Post by Claus7 on 2010-04-21
Hello,

> **notepad said:**
> anabelle, the simple answer you are looking for is to set passwords as root (sudo passwd [username])

this was posted by MJN in the thread that you posted the link to. i tried the sudo passwd and it worked perfectly.

it worked as it should!

Regards!

---

### Post by oldfred on 2010-04-21
It told me my password was too simple but I just kept installing and had no issues with the install.

---

### Post by Sef on 2010-04-22
Necromancing, so locked.

---

