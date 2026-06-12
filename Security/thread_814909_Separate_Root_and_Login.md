---
title: "Separate Root and Login"
date: 2008-06-01
forum: Security
---

### Post by heiowge on 2008-06-01
I'm setting up a Hardy install on my Brother-in-Law's PC this afternoon.  He is 13, and has a windows box, but has a habit of infecting it with 3 million viruses / adware / spyware, and the machine runs at a crawl.

I suggested Ubuntu as an easy to use setup with few issues.  They jumped at the idea, but due to his ham-fistedness, I want to restrict root access to his dad.  The problem is that he needs to be able to login, but that's the same password as the root password that I want him not to have.

Is there a way to let him login but keep the root password as something else that I can keep hidden from him?

---

### Post by abhiroopb on 2008-06-01
You can setup to logins, one with desktop priveleges and one with admin priveleges.

---

### Post by heiowge on 2008-06-01
Sounds good. :) How?

---

### Post by The Cog on 2008-06-01
For a user to be able to acces the admin functions (use sudo), they must be a member of the **admin** group. This is controlled by the GUI in System->Administration->Users and Groups (you need to be a member of admin to edit user/group properties).

The first user you create, the one the installer wants a name for is of course a member of admin. I suuggest you add his dad as the first username. Then use the GUI to add your Brother-in-law, and make sure you don't add him to the admin group.

---

### Post by Anus Willcrap on 2008-06-01
> **abhiroopb said:**
> You can setup to logins, one with desktop priveleges and one with admin priveleges.

What's the diff between a "desktop priveleges" and a
"no priveleges" user.

---

### Post by abhiroopb on 2008-06-01
I'm not actually sure, I just saw that myself. There are three options admin, desktop, and unpriveleged.

---

### Post by Anus Willcrap on 2008-06-01
unpriveleged, yeah, thats the one.

I made one up, and I could access important folders
 (a newbie here), but I think I had the account in the
admin group. I'm at my Windows machine now.

---

### Post by heiowge on 2008-06-02
> **abhiroopb said:**
> You can setup to logins, one with desktop priveleges and one with admin priveleges.

Cheers for that.  I actually set it up using the unpriviledged status, which is perfect for his habit of allowing his mates to install all kinds of cr*p on his PC.

None of them use linux, and it means that we can set up the basics and he gets to change nothing.

Can we install stuff for him on his user with our admin level password?

---

### Post by Oldsoldier2003 on 2008-06-03
> **heiowge said:**
> Cheers for that.  I actually set it up using the unpriviledged status, which is perfect for his habit of allowing his mates to install all kinds of cr*p on his PC.

None of them use linux, and it means that we can set up the basics and he gets to change nothing.

Can we install stuff for him on his user with our admin level password?

Usually installing a program on the computer makes it available for all users. So the answer is yes.

---

### Post by Cursed-Reiver on 2008-07-30
> **heiowge said:**
> Can we install stuff for him on his user with our admin level password?

Is it possible for a user without "admin" priviledges to run a GUI that requires admin priviledges by temporarily using the credentials of a user that does have admin priviledges?

I have tried logging in as the other user through bash and trying to launch GUI's through sudo/gksudo but keep getting display errors, and xephyr/Xnest do not want to play ball with me.  Surely there mus be a way of running a single GUI admin utility without logging in to a full desktop environment?

Any help appreciated.

Thanks

---

