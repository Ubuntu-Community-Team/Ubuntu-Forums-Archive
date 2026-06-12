---
title: "about GNU-PG Registration"
date: 2011-01-27
forum: Security
---

### Post by jusis on 2011-01-27
Hello Ubuntu Community,
 I have a question about GNU-PG security for email clients. I have  read that this is the best email protection available. I have it among  available Ubuntu packages, too, but when I wanted to use it the  registration process asked my real name.
 considering full or the best possible privacy claim, why real name?
or is it ok just not to give the real name?
 I am not advanced in cryptography, could/can this not be avoided?
 I'll be glad and thankful for your insights.
 best greets!

---

### Post by tgm4883 on 2011-01-27
Maybe I don't see the whole picture, but if you plan to use a tool designed to sign and encrypt your email so that whoever receives an email from you can verify it was sent from you (and not an imposter) why wouldn't you want to use your real name?

---

### Post by Dr Small on 2011-01-27
Here is a beginner's guide to get you started that you can read:
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)

But to answer your question, GnuPG is like a big authentication method, and we use our real names (that show on a gov issued id card) so people can verify that the key is ours, for keysigning, which builds our web of trust.

---

### Post by jusis on 2011-01-27
thank you for your posts!! 

I didn't have a clear view of how the real name would play a role, which was the reason of my question for the most part.
I understand now that it is about authentication. I haven't used such a system before, and I don't know if it is safe to just go around with a most obvious identifier like own name.

yes, that's what gnupg is for. but even there.

---

### Post by Dave_L on 2011-01-27
The name only matters if you send someone a signed or encrypted email message, and you want them to know that the message is really from you.  In that case, they would need your public key to authenticate the message.

---

