---
title: "Login security and data on disk"
date: 2008-11-06
forum: Security
---

### Post by johnuk on 2008-11-06
I'm wondering how difficult it is for someone to side step my login, or try to pull the data on my linux partition directly from the disc somehow by some smart disc analysis tool

I realise the login can be brute forced - passwords should be long(ish), alphanumeric with different cases.

So first up, I'd want to set a delay on the password attempts to make brute force entirely unrealistic.

But then what? Is there any method by which someone could try to boot in a root mode or assign themselves a new super user without going through my (initial and only) super user account?

Then onto the data on disc problem. Is there a tool I can get to encrypt all or preferably just some folders so there's no way the data can be cloned from the disc and then dropped into some host operating system where it can be accessed?

Thanks for the help!

---

### Post by Coreigh on 2008-11-06
Regarding file, folder, or even hard drive encryption I like TrueCrypt, but there are several solutions to choose from. I picked TrueCrypt because I have to support it on Windows from user who are computer novices, but need mobile information secured.

Here is a thread from the forums about TrueCrypt and Ubuntu: [http://ubuntuforums.org/showthread.php?t=149561]("http://ubuntuforums.org/showthread.php?t=149561")


EDIT:
Oh and regarding login control it is all a moot point if the attacker has physical control of the computer. They just pop out the hard disk and access it from another computer. This is why encryption is important to prevent data access. To prevent stealth attacks via remote just disable remote access, and remote login. This of course can be frustration for you if you need to remote access to or from your own machine.

---

### Post by hyper_ch on 2008-11-06
if you're worried about someone getting physical access to your data, use encryption.

---

