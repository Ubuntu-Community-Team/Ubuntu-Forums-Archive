---
title: "So... what IS the root password in Ubuntu?"
date: 2009-10-20
forum: The Cafe
---

### Post by hoppipolla on 2009-10-20
Is there just... not... one? Is it random? I mean I guess it's still secure because you need to know the user password to change it anyway, but I was just wondering if it is set to ANYTHING at all by default?

People always ask what the default is but of course it can't be just one password or it would be a hacker's dream lol xD

Hoppi o.O

---

### Post by BslBryan on 2009-10-20
It's whatever the first user's first password was.

---

### Post by hoppipolla on 2009-10-20
> **BslBryan said:**
> It's whatever the first user's first password was.

oh so THAT'S why when it asks me for the admin password I just enter my own! I thought it was some clever roundabout thing that Ubuntu had come up with, but the lazy buggers had just made that my admin password as well! lol

That's clever though - a little weird! - but clever!

---

### Post by BslBryan on 2009-10-20
Though sudo is a different story.  If you add a user to your sudoers file, they will use their own password.

---

### Post by hoppipolla on 2009-10-20
> **BslBryan said:**
> Though sudo is a different story.  If you add a user to your sudoers file, they will use their own password.

ah ok :)

---

### Post by lisati on 2009-10-20
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

<aside>Some other "root privileges" that come to mind are beyond the scope of these forums</aside>

---

### Post by NoaHall on 2009-10-20
The root account is disabled by default in Ubuntu. You use sudo in place, to give you short-time status of root. The root default password is root.

---

### Post by cariboo on 2009-10-20
If you look at /etc/shadow you will see that the password for root is !. :)

---

### Post by anaconda on 2009-10-20
The root account is disabled, and that means that root has no password. so no random string, and it is NOT the first users first password.

But if you need to activate the root account, all you need to do is to give root a password.

---

### Post by Exodist on 2009-10-20
There never is a default password. It is always set by the admin (like yourself) at startup.

---

### Post by the yawner on 2009-10-20
It's 123456. Silly.

---

### Post by NCLI on 2009-10-20
As you can see in the /etc/shadow file, [COLOR=Red]**_THERE IS NO ROOT PASSWORD_**[/COLOR]. All users in the sudoers group can use their own password to gain root privileges for a limited time, and you can give root a password in several ways I won't post here.

---

### Post by adeypoop on 2009-10-20
> **the yawner said:**
> It's 123456. Silly.

haha 123456!  Actually you are mistaken that is the windows Administrator password. :P

I used to enable root with a password so that I could use root account when doing admin stuff, instead of having to type sudo all the time. Recently I realised 'sudo bash' can give me a root terminal so I don't bother with 'su' anymore.

---

### Post by JillSwift on 2009-10-20
> **adeypoop said:**
> haha 123456!  Actually you are mistaken that is the windows Administrator password. :P

I used to enable root with a password so that I could use root account when doing admin stuff, instead of having to type sudo all the time. Recently I realised 'sudo bash' can give me a root terminal so I don't bother with 'su' anymore.
sudo -i  is easier, no?

---

### Post by 3rdalbum on 2009-10-20
> **JillSwift said:**
> sudo -i  is easier, no?

It's a heck of a lot easier than what the Mac uses to open a root terminal, which is:

```
osascript -e 'tell app "ARDAgent" to do shell script "whoami"';
```

---

### Post by coolbrook on 2009-10-20
[http://www.youtube.com/watch?v=dzm8kTIj_0M](http://www.youtube.com/watch?v=dzm8kTIj_0M)

---

### Post by stuart.reinke on 2009-10-20
> **the yawner said:**
> It's 123456. Silly.

That's the same as my luggage combination. :)

---

### Post by sisco311 on 2009-10-20
> **cariboo907 said:**
> If you look at /etc/shadow you will see that the password for root is !. :)

+1

The /etc/shadow file stores the passwords in encrypted format.

The root account password is locked by default. ! matches no possible encrypted value.


[uhelp]community/RootSudo[/uhelp]
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/]("http://www.cyberciti.biz/faq/understanding-etcshadow-file/")
```
man passwd | less --pattern\="-l, --lock"
```

---

### Post by RiceMonster on 2009-10-20
> **the yawner said:**
> It's 123456. Silly.

It's letmein in Jaunty and Karmic.

---

### Post by mcduck on 2009-10-20
> **3rdalbum said:**
> It's a heck of a lot easier than what the Mac uses to open a root terminal, which is:

```
osascript -e 'tell app "ARDAgent" to do shell script "whoami"';
```

Never even seen such a command. I always use "sudo -i" on OSX as well.. ;)

---

### Post by MaxIBoy on 2009-10-20
In Ubuntu, the root password is a totally randomized at install time. However, with sudo you can **also** use the password of the first user you created, giving you equal privileges to root. You can then set a root password if you like, and "su" now works as well as sudo.

---

### Post by FuturePilot on 2009-10-20
> **MaxIBoy said:**
> In Ubuntu, the root password is a totally randomized at install time. However, with sudo you can **also** use the password of the first user you created, giving you equal privileges to root. You can then set a root password if you like, and "su" now works as well as sudo.

No, it is not randomized. There is no root password at all.

---

### Post by Daveski on 2009-10-20
Crikey - does it matter? Your account (with sudo) has the ability to reset the root password at any time anyway.

---

### Post by calrogman on 2009-10-20
> **adeypoop said:**
> haha 123456!  Actually you are mistaken that is the windows Administrator password.

Actually, unless the user changes the password after installation (very rare), the Windows Administrator account can be accessed by anyone, without a password, although you have to use Ctrl Alt Del @ the login screen.

---

### Post by Bachstelze on 2009-10-20
> **FuturePilot said:**
> No, it is not randomized. There is no root password at all.

There is one. It is just impossible to get it right. ;)

---

### Post by sisco311 on 2009-10-20
> **Bachstelze said:**
> There is one. It is just impossible to get it right. ;)

optimist.

---

### Post by aysiu on 2009-10-20
There's too much misinformation here. This is not a matter of opinion or debate.

Here are the straight facts, and then I'm closing the thread: [list][*]There is no root password in Ubuntu. Root logins are disabled by default[*]You don't need to set a root password, because *sudo* and *gksudo* allow you to execute commands at a root level from your user account (after password authentication)[*]*sudo -i* gives you a persistent root prompt (without a root password, only the *sudo* password), and this works in both Ubuntu and Mac OS X[/list]

---

