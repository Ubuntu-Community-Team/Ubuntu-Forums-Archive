---
title: "Bad password vs. No password"
date: 2009-05-26
forum: Security
---

### Post by Jestersage on 2009-05-26
One of the policy that Ubuntu differntiate from others is that, any proper account (basically non-guest account) are forced to use a password, no matter what (unless either a modification that is different from Debian, which makes it not a feature intented, or have kubuntu, but then again kubuntu is never fully supported...)

I am definitely beating the dead horse quite a bit, but I do want to ask: how effective is it? When I mean how effective, I do not merely means how much it can lock out security vulnerabilities: I also mean how well it will allow proper users to access it.

An example I use is my mother: she tend to forget her password; except her bank account, she tend to forget the password of her email account, of her forum account, and other stuff. Knowing that I am usually away from home, she solve it by either saving the password, or writing it down (and make me remember her password as a backup). However, in Ubuntu, unlike an email account (or even a bank account), if you are lock out AND is a green user (which means you should not have touch much stuff), then you are probably locked out (luckily we do have a community to help solve that problem)

Now luckily (as far as I know), she does not take the third option, of writing a password that is simple to remember, which is a problem security that had been pointed out. [1]("http://www.whatsmypass.com/?p=415"),[2]("http://ca.tech.yahoo.com/experts/chrisnull/article/2261"),[3]("http://www.darkreading.com/blog/archives/2009/02/phpbb_password.html") have shown that users, for the most part, select a password that is basically non existence. In such case, why bother forcing user entering password?

Afterall, even OLPC realized that not many people can remember a password (especially young kids)&#8211; thus, for the OLPC, they employed a bitfrost, with a main keypoint of having no password required to log into the computer.

However, as I write this, I can think of a few reason why it's better if users set up a bad password or write them down (or use auto login), then to have no password at all:

1) A bad password, if according to the list, is only a probability. 1234 is still different from 123456 which is different from 1235678. Causal curious people  (or naughty kids) do not have the stamina to figure them out all.
2) Physically seperated password, unless it's post-it onto the monitor or the inside of a laptop, still allow some seperation. Say a laptop is stolen: Unlike a window password, a securely setted up box is harder to retreive.

I do agree: administrator should have a password, and definitely when sudoing (even Mac does this). However, I think it is slightly debatable whether a normal desktop user must also require a password to enter.

So I want to hear your opinion: is a desktop user (not admin, and definitely not a root user) allowed to access the computer without password? (Considering that they will set up bad password anyway, or place passwords in easy to see locations)

And just so you know, my password is 111... eh, 1. It allows me to reach my documents easily when a hacker had infiltrated my computer. (Mostly containing the pronography starring my enemy's mother)

---

### Post by cdenley on 2009-05-26
With password security, you're not just protecting yourself from local users, but also anyone who might attempt to authenticate remotely through a server such as ssh. Those attacks typically use a password dictionary, which makes it very likely any weak password (1234,123456,qwerty) will be compromised. No matter how clever you think you are, any pattern you use in your password is probably in a password dictionary used by some attacker.

Whether a typical desktop user should need to enter a password to login depends entirely on the user, the environment their system is physically located in, and the sensitivity of any data on their system. If they live alone, and aren't overly concerned about security, they may enable auto-login. If they live with someone they don't trust, or their system is a laptop or not always somewhere safe, then they would probably want a password.

You mentioned laptop theft. Any files that haven't been encrypted can be retrieved with physical access. It might be difficult to crack the user's password, but it would be trivial to reset the password.

For security, you need some method to differentiate legitimate users from malicious attackers (especially for root access). If a password is not a practical solution, you need a physical key such as a biometric fingerprint or USB drive.

[http://ubuntuforums.org/showthread.php?t=1091540](http://ubuntuforums.org/showthread.php?t=1091540)

---

### Post by Jestersage on 2009-05-26
Ahh... thank you for pointing out that the Ubuntu login password, be it Desktop, root, or admin (I seperate them) is also for protection against remote attack. Nonetheless, my point sill stand: if users is still going to either a) use obvious passwords or b) place an otherwise secure password at an easy to spot location, why even forces user to have a password? as I mentioned, unless a careful modification of PAM files is used, or on a Kubuntu, Ubuntu forbid that.

However, it allows autologin, so... slightly contradictory? If they are going to bypass the password, why force a password?

The only reason I can think of why Ubuntu forces a password in login windows is that, if users must go into a login window all the time, even one with faces, that implies the computer is shared by others &#8211; if one is an admin and the other is user, then the admin can probably easily access the other guy's stuff. If two of them are regular desktop users, then it's best not to encourage them to peak into each other files &#8211; besides, with windows being the sole exceptions, all OS I know, even MacOSX, forbid easy access to other users' home folder (the reason I mention this is that, one of the common trait Windows users do is to "transfer/read/write files directly" with each other users of same computer.)

If they really want to share stuff, even only for those of the same computer, they either use a sharing folder or "mailbox setting" of their foldier.

Ironically, if it's not because of the mandatory login passwords, such feature make Ubuntu very similar if not the same as a MacOSX. (Then again, both are unix...)

On a sidenote: Why didn't I ever hear a someone compare Ubuntu to Mac, be it a Ubuntu lover or Ubuntu hater? I find that if I compare it to a Mac (and get ardour), that shut them up instantly.

---

### Post by cdenley on 2009-05-26
I use the default configuration of a single user in the admin group. I enabled auto-login because I'm not too concerned about anyone with physical access. However, anytime my privileges are escalated to root, I am required to enter a password. This prevents processes running as my user from escalating privileges without my knowledge. Also, if I access it remotely, I need my password. Auto-login is not equivalent to an empty password.

If the user is not in the admin group, and there is no way to authenticate as that user remotely, and you don't want to require a password at login, then the password would be kind of pointless.

---

