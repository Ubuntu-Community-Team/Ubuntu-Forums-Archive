---
title: "can someone tell me the su password for Kanotix, please?"
date: 2006-04-11
forum: The Cafe
---

### Post by ice60 on 2006-04-11
hi, i've got a friend who's trying to get the Kanotix livecd working with his modem, but he says when he types su it asks for a password, do you know what the password is, or how to make/change the su password? thanks

---

### Post by MenZa on 2006-04-11
By default, the root (SU) password is disabled in Ubuntu: [more info](http://www.ubuntu.com/wiki/rootsudo/).

---

### Post by NeghVar on 2006-04-11
I don't think you can change the password on a live cd, although if you can I think the command is:

sudo passwrd su

Im not sure if that will work or not, and I have my doubts about it working on a live cd altogether.

---

### Post by ice60 on 2006-04-11
[QUOTE=MenZa]By default, the root (SU) password is disabled in Ubuntu: [more info](http://www.ubuntu.com/wiki/rootsudo/).[/QUOTE]
thanks for the replies, but i'm talking about he Kanotix livecd.

so do you think he's doing something wrong and when you type su in the Kanotix live cd it shouldn't ask for a password? 

knoppix based stuff hasn't ever worked for me so i have no idea about it.

---

### Post by bjweeks on 2006-04-11
[QUOTE=ice60]thanks, but i'm talking about he Kanotix livecd.

so do you think he's doing something wrong and when you type su in the Kanotix live cd it shouldn't ask for a password? 

knoppix based stuff hasn't ever worked for me so i have no idea about su.[/QUOTE]

Try crtl-alt-f1 and type passwd to set the root passowrd and then crtl-alt-f7 to get back to x.

---

### Post by ice60 on 2006-04-11
[QUOTE=bjweeks]Try crtl-alt-f1 and type passwd to set the root passowrd and then crtl-alt-f7 to get back to x.[/QUOTE]
brilliant, thanks for the help :)

---

### Post by jdong on 2006-04-11
By default, Knoppix (and therefore the Knoppix derivative Kanotix) generate an auto-scrambled, random password on every bootup for the root and default user accounts. The user account has sudo unlocked, while 4 root terminals are logged in at the virtual terminals.


So, you can either:

(1) from the GUI, use **sudo** in a Ubuntu like fashion.
(2) Do the console thing that's already been mentioned.

---

