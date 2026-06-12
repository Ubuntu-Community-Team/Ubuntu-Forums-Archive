---
title: "Change sudo behaviour"
date: 2010-06-14
forum: Security
---

### Post by yeleek on 2010-06-14
Hi,

I've enabled root under Ubuntu (i know frowned upon), I'd like to change the default behaviour of sudo so that rather than requesting my password (the password I logon with), it requires the root password.

Have searched the forums but can't find the answer.  Any ideas pls?

Thanks

---

### Post by Ryan Dwyer on 2010-06-14
I don't know of any way to do that.

Also, you're making your system less secure by doing this. Someone could brute force your root password. When root is disabled they have to guess your username too which is highly unlikely.

---

### Post by Rubi1200 on 2010-06-14
> **Enabling the root account**

   [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconWarning3.png[/IMG]
    **Enabling the root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent root login, the best alternative is to simulate a root login shell using the following command...**
   [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconWarning3.png[/IMG]
  

sudo -i 
To enable the root account (i.e. set a password) use: 
sudo passwd root** Use at your own risk!**

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In my opinion, the more you do to lower the security of your system, the more likely you are to pay dearly!

---

### Post by Bachstelze on 2010-06-14
> **Rubi1200 said:**
> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In my opinion, the more you do to lower the security of your system, the more likely you are to pay dearly!

In my opinion, enabling the root account does not in itself lower the security of a system in any way. A lot of other OSes do it, and no one in their right mind would say they're less secure than Ubuntu. At the end of the day, it is the user that does the difference, not whether or not the root account is enabled.

@yeleek: The answer is in [font=monospace]man sudoers[/font]. No offense meant, but if you can't figure it out, I don't think it's wise to enable the root account.

---

### Post by Rubi1200 on 2010-06-14
> **Bachstelze said:**
> In my opinion, enabling the root account does not in itself lower the security of a system in any way. A lot of other OSes do it, and no one in their right mind would say they're less secure than Ubuntu. At the end of the day, it is the user that does the difference, not whether or not the root account is enabled.

I agree, in principle, with what you say.

But, here is what I would like to know:

Why enable the root account in the first place since using it incorrectly could potentially destroy your system?

Why take chances with the security and stability of your system?

Why trust the user when the user has proven himself/herself to be so unreliable (I am referring specifically to the number of posts here and on other forums from people who have messed things up by enabling the root account/messing with sudoers etc.)?

---

### Post by yeleek on 2010-06-14
> **Ryan Dwyer said:**
> I don't know of any way to do that.

Also, you're making your system less secure by doing this. Someone could brute force your root password. When root is disabled they have to guess your username too which is highly unlikely.

Less secure?!?  I disagree, and many other distros (Debian, Opensuse, etc) do exactly as I'm asking by default.  Furthermore industry best practice (yes i work in IT security) states the requirement for separate administrator and user accounts i.e. Users should not have admin access - full stop.

Ubuntu is great, but it is aimed to make things easier for users.  If making changes to my system requires the root password then two accounts/passwords are required to make changes to my system.
1) my account - to logon with (as logon with root is disabled).
2) root - to make changes

Anyway back on topic, anyone know the answer pls? - edit thanks bachstelze.

---

### Post by sisco311 on 2010-06-14
never mind

---

### Post by Bachstelze on 2010-06-14
> **Rubi1200 said:**
> 
Why enable the root account in the first place

Why use KDE instead of Gnome, which is default in Ubuntu? zsh instead of Bash, which is default in Ubuntu? Pidgin instead of Empathy, which is default in Ubuntu? Personal preference and/or suitability for the particular needs of a given user. No model is inherently more secure or better than the other, so that's what it all boils down to.

> **Rubi1200 said:**
> since using it incorrectly could potentially destroy your system?

Same could be said of sudo. And in a broader context, of cars, kitchen knives or alcoholic beverages.

> **Rubi1200 said:**
> Why take chances with the security and stability of your system?

See above.

> **Rubi1200 said:**
> Why trust the user when the user has proven himself/herself to be so unreliable (I am referring specifically to the number of posts here and on other forums from people who have messed things up by enabling the root account/messing with sudoers etc.)?

Who is "the user"? I've never met him. I've met a lot of people who have or have not enabled the root account, have or have not "messed things up", and I could not draw any correlation between the two.


The problem in Ubuntu is different. Ubuntu uses sudo and disables the root account by default, so a lot of things are geared towards that model and expect it to be that way. If a user wants to change that, more power to him, but he needs to know what he's doing. I believe this is why advice on that subject is not permitted here: a user who wants to do that should know enough to figure out the answer by himself (hence my answer to yeleek above).

---

### Post by yeleek on 2010-06-14
gosh - right rootpw is the way to set it - thanks for the pointer Bachstelze

As for the other comments - The Ubuntu way is not the only way to do things, and yes whilst in this forum it may be recommended against.  Those of you who seem to have such strong views should spend time reading NIST and SANS documentation, then perhaps also study for exams such as CISSP.  Then you'll understand the request.

---

### Post by bodhi.zazen on 2010-06-14
> **yeleek said:**
> gosh - right rootpw is the way to set it - thanks for the pointer Bachstelze

As for the other comments - The Ubuntu way is not the only way to do things, and yes whilst in this forum it may be recommended against.  Those of you who seem to have such strong views should spend time reading NIST and SANS documentation, then perhaps also study for exams such as CISSP.  Then you'll understand the request.

Glad you got it sorted.

In the future, I find these pages helpful :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

See also targetpw ;)

[http://www.gratisoft.us/sudo/man/sudo.html](http://www.gratisoft.us/sudo/man/sudo.html)

There is an entire security section if you are so inclined.

---

