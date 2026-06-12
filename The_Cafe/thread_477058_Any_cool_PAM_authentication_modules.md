---
title: "Any cool PAM authentication modules?"
date: 2007-06-17
forum: The Cafe
---

### Post by Mr. Picklesworth on 2007-06-17
I've become curious about something I probably shouldn't risk messing with, but I just can't help myself...

That is, PAM authentication modules!
I want everything. Voice recognition, face recognition, skill testing questions, USB keys... whatever is out there!

If you know any good articles on such things, or any particularly fantastic modules, post them here!

---

### Post by slimdog360 on 2007-06-18
PAM -- pulse amplitude modulation??

---

### Post by Mr. Picklesworth on 2008-03-09
Heh, I was about to recreate this thread, then realized I have already created it myself!


Slimdog:
Bit late, but pam stands for Pluggable Authentication Modules. It is what reads your password and decides whether or not to let you in, and it is used everywhere you need to enter your password, be it the locked screen prompt, sudo or the login screen. The neat thing with PAM is that it is absolutely not limited to classic text input, and can in fact work entirely without it! (Having said that, typed passwords are excellent because those systems use very powerful one way hashes).

Just discovered / rediscovered two:

-[pam-usb](http://www.pamusb.org/). I had to compile it from source because the one in the repositories is not actually detecting devices, but that was pretty quick and painless. Very cool, although maybe a bit dangerous when it comes to sudo, since if I leave the key in I get absolutely no warning. (A million pieces of malware could have just granted themselves sudo privileges without a chance to deny them. Then again, sudo doesn't seem aimed at that case anyway).
Quite cool being able to physically pull my account's access privileges in and out. Is there a way to stop Ubuntu from complaining about unsafe device removal, though? It pulls me out of the fun.

-fprint. I still can't get it going from source; someone has a repository for *Hardy* and x64, so I guess I'll be waiting for a little while.
Edit: Hooray! Got libfprint working! All it took was finding the right package for imagemagick's libraries, which is libmagick9-dev. ( Inconsistent package naming! :( )

---

### Post by 3rdalbum on 2008-03-09
I'd like a Captcha-based PAM :-)

---

### Post by NIT006.5 on 2010-09-26
A few years later, but pam_face_authentication.so is very cool, using opencv. Have also done pam_usb.so and pam_blue.so. Now looking for a voice authentication plugin.

---

### Post by Austin25 on 2010-09-26
I might try pam_fprint.

---

### Post by Bachstelze on 2010-09-26
[Smart cards]("http://ubuntuforums.org/showthread.php?t=1557180")?

---

### Post by mdhunn on 2010-11-10
I love the face recognition module, but it needs to be supported by the Gnome Keyring somehow.  Logging in only to have to type my password after I'm in kinda defeats the purpose.

---

### Post by czr114 on 2010-11-10
Facial recognition is a huge security risk.

Remember all those movies where a palm scan was defeated when the bad guy chopped somebody's hand off?

Thieves don't have to chop your head off to fool facial recognition. All they need is a good cameraphone.

Facial recognition and all other biometrics are also a huge failure against identity thieves sophisticated enough to use a live CD. Facial recognition doesn't produce a determinate and truly secret cryptographic key, which means it can't be used to encrypt whole drives or home directories.

The password is here to stay.

---

### Post by undecim on 2010-11-10
> **czr114 said:**
> Facial recognition is a huge security risk.

Remember all those movies where a palm scan was defeated when the bad guy chopped somebody's hand off?

Thieves don't have to chop your head off to fool facial recognition. All they need is a good cameraphone.

Facial recognition and all other biometrics are also a huge failure against identity thieves sophisticated enough to use a live CD. Facial recognition doesn't produce a determinate and truly secret cryptographic key, which means it can't be used to encrypt whole drives or home directories.

The password is here to stay.

It's not so much that it's defeated with a picture as much as facial recognition doesn't let you use encryption. If someone has the freedom to stick a picture of your face in front of a computer without you noticing, they can boot into single user mode just as easily.

---

