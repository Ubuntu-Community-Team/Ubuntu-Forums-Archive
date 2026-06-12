---
title: "Hacking attempt..."
date: 2010-01-29
forum: Security
---

### Post by hammad1337 on 2010-01-29
Before continuing, this is not an attempt at boasting or showing off. The purpose is to learn.

Recently, I sniffed off an ssh password to a server on my local network in my university. (same ol' ettercap/wireshark stuff).

But that password was not the administrator password on the machine. (You needed to su to get the real privileges.)

I got this idea about creating a small, simple shell script which behaved like su, but stored the password in a .hidden file in the home directory. I then went on to create an alias to su. (I am not posting the script here to prevent script kiddies)

The attempt succeeded in getting the admin pass.

I don't hack with malicious intent. It's mostly for getting proof of concept, and to secure my own information (and prevent any smart tricks, if I am a LAN admin in the future).

My purpose for this post is, what would be steps/programs to prevent such simple attacks. (other than looking for .hidden files every time I log in.)?

Please don't reply if you are going to lecture me on the right and wrong of it all.

---

### Post by The Cog on 2010-01-29
I am coming to the conclusion that there will always be a weakness like this with accounts that are able to elevate their own privileges on demand, either with su or sudo. I think the only real solution is to only ever log in directly as root (not sudo or su from another potentially compromised account). Of course, while logged in as root, never, never, NEVER do things like web browsing or reading email - stick to trusted admin applications, and logout again ASAP.

---

### Post by adam814 on 2010-01-29
Well, you can probably avoid that *particular* kind of attack by not having '.' in your $PATH.  Or was the wrapper script installed in one of the usual system directories?

My guess is also that the user logged in using SSH version 1, which should be disallowed to prevent exactly that sort of thing from happening.

---

### Post by mkvnmtr on 2010-01-29
After doing some reading and playing with varios programs I have come to believe that every time someone develops an attack someone else develops a defence. Then when there is a defence someone develops an attack that works. It is so broad that only inspecting your system over and over again with the attack tools will give you a chance to defend or nitigate an intrusion.

---

### Post by bodhi.zazen on 2010-01-29
Thread closed. We do not support cracking here, even as proof of concept.

There are many many ways to leverage shell access -> root access, it is next to impossible to restrict them one by one.

If you have access to an admin account , root  is that much closer.

The trick is to prevent shell access in the first place.

The next best option is to use SElinux or apparmor.

Otherwise , there are many more appropriate sites for these types of conversations.

---

