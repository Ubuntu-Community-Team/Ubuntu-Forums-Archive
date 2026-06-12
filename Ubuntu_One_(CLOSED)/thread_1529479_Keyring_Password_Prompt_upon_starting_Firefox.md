---
title: "Keyring Password Prompt upon starting Firefox"
date: 2010-07-12
forum: Ubuntu One (CLOSED)
---

### Post by Durandal512 on 2010-07-12
A while ago, I removed the Ubuntu One entry from my Startup Applications because it was annoying having to activate the keyring every time I booted up/logged on.  Now, I am prompted for a password once I start Firefox (mind that it's only the first time I run Firefox after boot/login).  I'm assuming it's Ubuntu One because of the sequence of events, but feel free to correct me if you think otherwise.  How can I stop this?

Running standard Ubuntu 10.04.

P.S.  Please forgive me if this is a redundant post.  I tried searching for "web browser prompts for keyring password" but with no luck.

---

### Post by duanedesign on 2010-07-14
The keyring manager is integrated with Gnome such that when you login from the main screen, it will automatically unlock itself as well. However, if you use the auto-login function, Gnome will skip the keyring manager process and log the user in without unlocking the keyring manger.

If you use auto-login what you can do is to set a blank password for the keyring manager. Then it won&#8217;t prompt you  for password everytime you startup.

Do bear in mind that setting a blank password for your keyring manager will expose all your passwords to anyone that uses your computer.

**1.** Go to Applications > Accessories > Password and Encryption

**2.** Click on the Passwords tab

**3.** Right click over Passwords: login and select 'Change password'

**4. Option 1**
If you change your password to the same as your login password you won't get prompted for your default keyring password when you log in.

**4. Option 2** (If you use auto-login)
Type in current password and leave the next two fields empty. Then you will see a prompt letting you know this is unsafe. Click 'Unsafe Storage'

thank you,
duanedesign

---

### Post by Durandal512 on 2010-07-14
Thank you for the reply.  I was already aware that setting a blank password would expose my computer, so I definitely don't want to do that.  My keyring password is also the same as my login password, so therefore it does not prompt as soon as I log in.  As I already stated, it is only when I start Firefox for the first time of the session.

Oh well.  Guess I'll just have to deal with it.  Thanks for trying, though.

---

