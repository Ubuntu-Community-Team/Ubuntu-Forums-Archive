---
title: "Users+Passwords"
date: 2009-10-28
forum: Security
---

### Post by KrGAce on 2009-10-28
Hello,

We are a highschool that is beginning to test the Netbook Remix.  We want to be able to allow our students to be handed a netbook and begin their work.  I have created an admin account for us, and a student account for them.  I want to know how to disallow the ability for them to change the password.  I have logged in as them and it would appear that they could change the password and we would like all netbooks to have the same student account with the same password.  Possible? Am I missing something? I have made their account in the users group.


Many thanks in advance for anyone's help.

AceMan

---

### Post by koenn on 2009-10-28
you could probably accomplish this by setting permissions on /user/bin/passwd so that only root can run it. As it is, it has setuid root so that it runs with root privileges even when normal users invoke it, which allows them to modify /etc/passwd

so I'd try
```

chmod 750 /usr/bin/passwd

```

!! I haven"t tried this and i don't know what side effects it may have. You should try this first on a disposable test system

---

### Post by KrGAce on 2009-10-28
no side effects as of  yet, I also as an extra precaution deleted any menu (this is netbook remix)that wasn't needed, and I am about 99.9% sure no one knows much about terminal either.  

We shall see.  If there is an easier/better way to restrict users, I'd love to hear it.


Thanks again for any and all help.



AceMan

---

### Post by koenn on 2009-10-28
There's a number of tools to manage user configuration : pessulus, sabayon, gconf-editor, (Policy Kit ?), ...

I'm not entirely up to date with the newest developments here or what is currently the Ubuntu recommended best practise in this area.

On the other hand, you could just assume that as long as your users can't us sudo (and can't change to password and lock others out), it's fine. Depends on your (functional) requirements, really.

---

### Post by KrGAce on 2009-10-28
yeah I tried Pessilus, but i couldn't figure out how to manage the user I wanted to edit, while being logged in as admin.  The bitter-sweet side of this is that there aren't many users that know Linux, so we're probably safer than Windows, however that isn't real security either.  

Like I said I have limited the menus to only those applications I know they need (Writer, Calc, Firefox, etc)so that's a step.

---

### Post by Lars Noodén on 2009-10-29
Some of the desktop environments also have a kiosk mode, so that can be tried to lock things down.  

Also make sure that the student account is not in the group admin or adm.

---

