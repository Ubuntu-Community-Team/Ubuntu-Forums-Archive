---
title: "Remembering the Password for a Server Forever"
date: 2007-05-05
forum: Server Platforms
---

### Post by audax321 on 2007-05-05
Hello,

I'm not sure if this should be here or in the Desktop Environment board, but I figured more people probably use SSH in this forum.

I have a SSH server set up on my desktop and when I connect to it using my laptop (Feisty with Gnome 'Connect to Server...') it asks me for a password and gives me three options:

Forget password immediately
Remember password until you logout
Remember forever

I'm getting sick of entering the password all the time and was thinking about selecting the last option to remember forever. But I want to make sure the password will be accessible in the future if needed. So, if I select that option will the password get saved in the Keyring Manager??? If not, where does it get stored exactly?

Thanks. :)

---

### Post by MrHorus on 2007-05-05
> **audax321 said:**
> So, if I select that option will the password get saved in the Keyring Manager??? If not, where does it get stored exactly?


I would presume so, yes.

---

### Post by MJN on 2007-05-05
> **audax321 said:**
> But I want to make sure the password will be accessible in the future if needed.

What do you mean by accessible in the future? Whereever it's stored it's unlikely to be in an accessible (cleartext) format... And if you're worried about you not being able to change to a different password in the future don't be - as soon as the stored password fails to authenticate you will be re-prompted for a new one.

Or have I misunderstood?

Mathew

---

### Post by audax321 on 2007-05-05
I meant if for some reason I wanted it to stop remembering the password in the future but not change it. Or lets say I need the password for another computer to access the server but I forgot what it was and don't have immediate access to the server (unlikely, but I've forgotten passwords before) then I could just open up the keyring and get it. Sounds like a weird scenario but it has happened to me before.

---

### Post by MJN on 2007-05-05
Ah, I see. Having not stored passwords myself I didn't realise they would be kept in a viewable cleartext form for you to subsequently view.

Mathew

---

### Post by tr333 on 2007-05-05
since you are connecting with ssh, you might want to setup public/private key authentication so you dont need to type passwords when logging in to a remote computer via ssh.
[http://www.debuntu.org/ssh-key-based-authentication]("http://www.debuntu.org/ssh-key-based-authentication")

---

### Post by RTrev on 2007-05-06
> **audax321 said:**
> Hello,

I'm not sure if this should be here or in the Desktop Environment board, but I figured more people probably use SSH in this forum.

I have a SSH server set up on my desktop and when I connect to it using my laptop (Feisty with Gnome 'Connect to Server...') it asks me for a password and gives me three options:

Forget password immediately
Remember password until you logout
Remember forever

I'm getting sick of entering the password all the time and was thinking about selecting the last option to remember forever. But I want to make sure the password will be accessible in the future if needed. So, if I select that option will the password get saved in the Keyring Manager??? If not, where does it get stored exactly?

Thanks. :)

If you are asking what I think you are, I might have a solution for you.  I wrote a little web-based routine in PHP which will take a simple and easy-to-remember phrase of your choosing, and generate a complex and unguessable password from it.  If you ever need the password again, you just go back to my site and enter your little phrase again, and it will hand you the same password again.  Even if the "phrase" you pick is nothing but a period, it will give you as good a password as if you entered paragraphs.

Take a peek and see if you think this might help you.

[https://rtrev.com/utilities/passwords/](https://rtrev.com/utilities/passwords/)

---

