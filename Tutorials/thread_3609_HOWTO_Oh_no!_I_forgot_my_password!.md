---
title: "HOWTO: Oh no! I forgot my password!"
date: 2004-11-07
forum: Tutorials
---

### Post by jdong on 2004-11-07
**Q: I am a complete moron and forgot my password. How can I get back into my system?**
*(Hey, YOU forgot it, I think that gives me the right to do some degrading before letting you back in!)*

A:
1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below...  #-o 
4. Turn your computer on.
5. Press **ESC** at the grub prompt.
6. Press **e** for edit.
7. Highlight the line that begins *kernel .........*, press **e**
8. Go to the very end of the line, add **rw init=/bin/bash**
9. press enter, then press **b** to boot your system.
10. Your system will boot up to a passwordless root shell.
**CAUTION**: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in **passwd <username>**. Set your password.
12. Type in **reboot**.
NOTE: steps 1-3 may help at this point.
13. Bow down to me....

---

### Post by plasmo on 2004-11-09
what if i put a password on grub and i forgot that as well?  \\:D/

---

### Post by fng on 2004-11-09
this doesnt look safe at all to me.
If a hacker gets physical access to my ubuntu box, he will get a full-access root shell :(

---

### Post by jdong on 2004-11-09
[QUOTE=fng]this doesnt look safe at all to me.
If a hacker gets physical access to my ubuntu box, he will get a full-access root shell :([/QUOTE]
Err, if a hacker gains physical access to **any** computer, it's just as good as compromised!

Whether it's Linux or Windows or any other OS, there are always little backdoors. The most common is a Knoppix LiveCD: perfect for changing /etc/passwd , /etc/shadow, and the SAM file on XP (i.e. zero'ing out passwords, etc).

the best way to guard against this "exploit" is to keep your computer safe (duh) and set up a GRUB password as a deterrent. Then again, **a Knoppix LiveCD (or Ubuntu LiveCD) is an easy way to mount the hard drive and edit /boot/grub/menu.lst to remove the password** (hint, hint, hint)!

---

### Post by oddabe19 on 2004-11-09
set a bios password for startup.  And assuming that they don't open your compy and reset the CMOS.... they won't get very far.

---

### Post by shimon on 2004-11-11
get lock on your box lock your room... lock everything

---

### Post by HungSquirrel on 2004-11-11
Both my case's side panel and the front panel covering the drives and switches have locks, I have a BIOS password, I have a GRUB password, I have set sudo sessions to three minutes, and I have xscreensaver set to come on after five minutes and lock the screen.

Not that I'm paranoid.

---

### Post by ghettobanana on 2005-04-18
what about this problem:

I was editing my /etc/sudoers file to remove firestarter and was talking to someone when i # the wrong line.  Now I can't sudo anything.

I #'ed the %admin ALL=(ALL) ALL

I need to edit this file and of course I can't.

# 1: (fail)
I edited my GRUB with init=/bin/bash
and once at the root prompt I nano /etc/sudoers
I was unable to save the file...says its read only.

Any advice?

---

### Post by jdong on 2005-04-18
Read the instructions more carefully. You need **rw** before init=/bin/bash...

---

### Post by rah on 2005-09-04
I tried to change my password using System > Administration > Users and Groups, but when I tried to login again, it wouldn't let me.  In order to rescue myself, I tried using this technique, but when I get to the root shell, my keyboard is non-responsive.  What should I do now?

EDIT:

Okay, instead of typing

```
rw init=/bin/bash
```

I typed

```
single
```

and it worked fine.

---

### Post by jdong on 2005-09-04
By default, "single" would work. But by reconfiguring /etc/inittab, you require a password for single-user mode, in which case single would not be effective anymore ;). init=/bin/bash works regardless of system configuration.

---

### Post by Digicon on 2006-08-27
Just wanted to say thanks you saved me alot of time.
I was just about to a reinstall. Thanks again!

---

### Post by cooldude95 on 2007-08-09
Just start in command mode, type in passwd yourusername, type in your new password, restart in normal mode, finish :)

---

### Post by Epilonsama on 2007-08-09
Damn not even linux is safe against hackers :(

---

### Post by psusi on 2007-08-09
> **Epilonsama said:**
> Damn not even linux is safe against hackers :(

Such a statement is both meaningless and baseless.

---

### Post by fatsheep on 2007-08-09
Thanks for the guide.  Hopefully I will never need it! ;)

---

### Post by Spam Banjo on 2007-08-30
Awesome... Can confirm that this method worked for me.

I'm a little gutted now... I didn't think it would be that easy to get in without a password. Not only get in... but potentially lock me out.

Ah well..! I'm used to upgrading my security methods... that's one of the reasons I swapped from Windows in the first place.

---

### Post by jdong on 2007-08-30
Physical security is an important thing. If someone has physical access to your computer, **no piece of software in the world can protect you** from what he wants to do.

Bottom line is that your computer should be totally out of reach from dangerous people.

---

### Post by Neo_Me on 2007-09-22
I dunno much abt Ubuntu .. still 

My Username was nm

From Boot Menu .. Selected recovery mode

passwd nm
typed new pass
again typed new pass
reboot

Logined successfully with new pass

---

### Post by penguinv on 2007-10-28
Thanking you JDong for this last bit.
And for being clear at it.
   OK one thing. What is GRUB? I inferred that when I am asked for my password on bootup that that is GRUB. But I am not certain of that.

(I went to the Ubuntu IRC and the FUD was thick. But that is another post.)

I won't make the sin of changing the thread and asking anything new
and
I see that this is the way I can change "who" (which username) is the "master admin" (the one who has the sudo password).

I started out being "sam" and then realized that I wanted the group (who own the computer) to have the master password so I created an account for some future person "sadmin" then found out only my password worked for installing updates, not the sadmin account.

I want to give them an admin account and the master password but not the one to MY account.  --Yes I know they could find it but they are not that clever and "before I would leave" or anything, they should be able to always have the sudo-password.

And that way I can just ditch my entire account and not have to fuss with the details.

I have written this to check my thinking and to help others. 
I prolly could have said this more clearly.
Thanks Jdong ultimate coffee master.

PenguinV
Los Angeles Newbie and very happy to be in GUIland Linux

---

### Post by jdong on 2007-10-28
Nope -- the thing that plays the drums and prompts for your password is "GDM" (GNOME Display Manager)

GRUB is the textmode thing that provides the boot menu (or the PRESS ESC TO SEE MENU countdown) the very first thing during bootup.

---

### Post by penguinv on 2007-10-29
Jdong you said:
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.

In my world:
Turn on
see the Unix rebooting slider
pressed esc
see it reboot in text
see the grub page
pressed esc
--Now I see a set of choices that includes 4 lines that all say kernel.
but here I am supposed to press e, so I do
then I choose that one that starts with kernel (very long line)
press e
add the text at the end
see the prompt for root ((shiver))
put in the exact text
   passwd<sam>
then enter
I get  bash: syntax error near unexpected token 'newline'
then I cant enter text any more.

(sam is the user name)
Turn computer off.
Begin again.
(this time it takes several tries till I can hit escape at the right time. I have to go for the keep hitting it till I see the unix slider before grub.)
...
I try the password instead of passwd<sam> I do
gooble12<sam>

same result

Would appreciate assistance.
And Thanks In Advance.

---

### Post by penguinv on 2007-10-29
> **penguinv said:**
> Thanking you JDong for this last bit.
And for being clear at it.
   OK one thing. What is GRUB? I inferred that when I am asked for my password on bootup that that is GRUB. But I am not certain of that.

(I went to the Ubuntu IRC and the FUD was thick. But that is another post.)

I won't make the sin of changing the thread and asking anything new
and
I see that this is the way I can change "who" (which username) is the "master admin" (the one who has the sudo password).

I started out being "sam" and then realized that I wanted the group (who own the computer) to have the master password so I created an account for some future person "sadmin" then found out only my password worked for installing updates, not the sadmin account.

I want to give them an admin account and the master password but not the one to MY account.  --Yes I know they could find it but they are not that clever and "before I would leave" or anything, they should be able to always have the sudo-password.

And that way I can just ditch my entire account and not have to fuss with the details.

I have written this to check my thinking and to help others. 
I prolly could have said this more clearly.
Thanks Jdong ultimate coffee master.

PenguinV
Los Angeles Newbie and very happy to be in GUIland Linux

Update:
I discovered that I was still in a functioning bash shell 

by typing something I knew was safe, ls

so what happened was that my input- text was not being echoed after the first input.

and inputing the same thing

passwd<sam>
or 
passwd <sam>

gave the same error message.

---

### Post by psusi on 2007-10-30
There is no "master sudo password".  By default sudo is configured to allow members of the admin group to use sudo with their OWN password.  If you want someone else to have sudo access, just add them to the admin group.

---

### Post by JohnnyGuest on 2007-10-31
Thanks for posting!  Saves me from a reinstall... again :P

What about if you forgot your user name as well?  Should you create a new user with **useradd**?

---

### Post by jdong on 2007-10-31
If you forgot your username, cat /etc/passwd and look for your username, or the user with ID 1000 (username:x:1000:1000:.....)

---

### Post by Limpan on 2007-10-31
You're not supposed to leave the brackets, < and >.
If you try without them I'm sure it'll work.

---

### Post by haldean on 2007-11-01
@penguinv: take out the brackets and it'll work.

---

### Post by penguinv on 2007-11-01
- penguinv 
I got it working. I had changed the user name.

I still wonder about these things.
1. after the first line in the bash shell the input text is not echoed
 but the command I type in works just the same.
2. There might be something (basic) about linux that I could read and get the <brackets dont count> and other valuable pieces of information for which I do not know enough to ask.

To help others, these pieces of information were good.

- psusi
There is no "master sudo password". By default sudo is configured to allow members of the admin group to use sudo with their OWN password. If you want someone else to have sudo access, just add them to the admin group.
 ---- YES, I really needed to know that. 

- jdong
If you forgot your username, cat /etc/passwd and look for your username, or the user with ID 1000 (username:1000:1000:.....)
  ---- Examining /etc/passwd revealed that 
        the (human) user accounts are numbered starting with 1000

- limpan
You're not supposed to leave the brackets, < and >.
If you try without them I'm sure it'll work.
- haldean
@penguinv: take out the brackets and it'll work.

Thanks to all.

---

### Post by Linux BASHer on 2007-11-04
This isn't working for me.

I get a black screen after the reboot and when I switch to another terminal view (Control-Alt-F1) I get a message akin to "No resume image, doing normal boot."

But then it either just hangs there forever (if I appended to the line), and upon restart gives me the regular graphical login screen, or just immediately restarts in the regular login screen as well (if I delete the original line and replace it with the new line). Either way, the result is the same.

Has anything changed in 7.10, is it my configuration (it is a brand new, clean install-- I must have set the password or username wrong at install), or am I doing something wrong here?

Edit: Ah nevermind. Since it was a fresh-install, I realized I could just use recovery mode. Then I followed steps 11-12 to reset the password (sorry, no step 13 :P )

---

### Post by doorknob60 on 2008-01-17
I'm bumping an old thread, but this saved me from a reinstall on my brother's Xubuntu box :P Thanks this worked great!

EDIT: Hmm it doesn't have the star button thing to give you a "thanks" oh well

---

### Post by Coastalguy on 2008-11-21
I too forgot my password when I installed Ubuntu. I followed the instructions provided on the above posts to use GRUB. I did and at the prompt, I entered "passwd" following by my username.

I did receive the "Enter New Password" prompt, however it only allowed my to enter a single character which then automatically gave me the "Enter Password Again" prompt, which also only allowed one character before getting a new command prompt.

I tried entering a single character twice, however when entering this as the login password, it still gave me a wrong password error.....

I had installed Ubuntu as a Windows XP Home application (I believe they call it wubi?). However, when I try to uninstall it via the Control Panel, or directly using the uninstall executable file, I get a little HD activity, which then just stops. If I try to do a re-install using the CD, the same thing happens. 

So... I can neither login to my current install, nor can I remove it to reinstall it to obtain a new password.

---

### Post by Kow on 2008-11-22
> **fng said:**
> this doesnt look safe at all to me.
If a hacker gets physical access to my ubuntu box, he will get a full-access root shell :(

This may have already been said but if a hacker gets physical access to your computer then you might as well tell them the password (or not even set one.)

---

### Post by Zipp Dementia on 2009-04-19
Great thread, thanks!

---

### Post by Niksko on 2009-07-20
Thanks for this. It's a good thing to know, partly for the potential lulz when you're at a friend's house and partly for the practical applications.

-Nik

---

### Post by techiejoe on 2009-07-23
this was also very helpful (from nandemonai):

                                  **Re: Lost Username and Password**             
                                                                You must have setup a user and password. It's impossible to not have at least one user (in essence anyway).

I'm assuming you setup automatic login.

What you'll need to do is boot into recovery mode.

Then:

     Code:
     ls /home/ 
That will list the user directories. Whatever name is in there is the name of your user.

Then:

     Code:
     sudo passwd username 
*username being the name you saw in /home/

Set a new password. Reboot and you should be able to login.
                                                                                               __________________
                [COLOR=DimGray][SIZE=1]Linux Mint 7 64 Bit | Intel Core 2 Duo CPU E8500 @ 3.80GHz (OC) | 4GB Kingston RAM | Asus P5Q Delux Motherboard | Asus EN9800GT (NVIDIA) | WD 120GB / WD 720GB SATA2 HDDs[/SIZE]

[SIZE=1][http://rendai.homeunix.net/nandemonai/](http://rendai.homeunix.net/nandemonai/)


AND THIS...


[/SIZE][/COLOR]At the Grub boot menu hit "e" 
Select the line that begins with "kernel" 

Hit "e" again 

Move the cursor to the end of the line and add " init=/bin/bash" then hit enter 

Press "b" to boot the system 

At the bash prompt that comes up, type the following: "mount /proc" then hit enter 

next type "mount / -o rw,remount" then hit enter 

next type "passwd" then hit enter 

now enter your new password twice 

You should receive a notice stating "All authentication tokens updated successfully". This confirms your password has been changed. 

next type "mount / -o ro,remount" then hit enter 

now press control-alt-delete to reboot 

logon with new password to verify

Credit to Buddha and his LUG

____

LIkeNowUranXpert

---

### Post by MaxIBoy on 2009-07-24
HAHA, I did this myself just a few weeks ago when my initscripts got borked (If you're going to mess with your initscripts, ALWAYS prevent the "initscripts" package from being updated.)



I came out of the experience with an easy-to-deploy emergency-backup boot system (rewrote sysv init in one line of BASH!)



I also now know to add a GRUB password to stop anyone from gaining a root shell.

---

### Post by hariks0 on 2009-09-12
In my case, using the "rw init=/bin/bash" and "passwd user" prompted for a new password. But before typing the second character of my password, the prompt changed to "reenter your new password". So i guessed that the method accepts only sigle character as new password and i pressed only "a" twice. Now my password became "a" and later i changed it after logging in with the same "a".

Thank u for the information. I wonder how you people have answers for any queries !

---

### Post by -_- Joseph -_- on 2009-09-12
> **jdong said:**
> **Q: I am a complete moron and forgot my password. How can I get back into my system?**
*(Hey, YOU forgot it, I think that gives me the right to do some degrading before letting you back in!)*

A:
1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.


very nice and good tutorial

                   ,Joseph

---

### Post by RATM_Owns on 2009-09-14
Just putting "1" instead of "rw init=/bin/bash" should also work. :P
Much easier to remember in my opinion.

It's like what would a first grader more easily remember for the great lakes?
HOMES or SMEHO?

---

### Post by PowerSource on 2009-10-07
but if you're such an idiot so that you write down your password and forget your username, *then* what am I supposed to do? :'(

---

### Post by bfr-dwn on 2009-11-04
> **PowerSource said:**
> but if you're such an idiot so that you write down your password and forget your username, *then* what am I supposed to do? :'(

This has been answered many times. 
Log in as stated before (e, rw init=/bin/bash, b)
then when you are in 

ls /home

There's your username.

---

### Post by shayemo on 2013-05-01
Hey, I'm a total idiot and I have a problem at step 7. I can't find any line that begins with kernel. Anywhere. Now what?

---

### Post by QIII on 2013-05-01
This is a five year old thread.

Closed.

---

