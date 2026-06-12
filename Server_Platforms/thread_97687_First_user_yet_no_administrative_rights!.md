---
title: "First user yet no administrative rights!"
date: 2005-12-01
forum: Server Platforms
---

### Post by don_samji on 2005-12-01
Hello, I am a new user of UBUNTU, also this is my first post.
I had ordered a free distribution of UBUNTU and I received the Installation CD and Live CD today.
I installed it and I gave the first user as Don.
I noticed I have no administrative rights when Iam in UBUNTU, I don't remember them asking for any root password. 
The only password I was asked was the password I wanted for user : Don.
I get messages like, "you are not the owner", "you do not have permissions" etc etc whenever I try to do things that would otherwise be available in root.
What is wrong, when there is no other user created besides Don?
How can I overcome this difficulty and be able to view and edit my windows partitions?
Thankyou.
(P.S. I am new user of Linux, if you could give a bit detailed answers, it would help a lot.)

---

### Post by cactus on 2005-12-01
Linux operates on a slightly different security paradigm (principle of least privilege) than that of the Windows world. It is a least privelege first, and general users aren't granted administrative rights by default (generally this is administrator implementation specific, but it is a reasonable generalization when considering *nix style systems).

The permissions are provided/implemented based on a 'discretionary access control' model. Permissions are shown, for files, with the ls command ('ls -l' will show them). They form a bitmask, that is used to test permissions. That is neither here nor there for the current discussion. You can research all this if you are interested.

Simple solution for you is to use the 'sudo' command. This will elevate your rights, and allow you to perform certain things as a "root" user..who posesses more rights. This is a security feature.

You use it as follows:
'sudo command_name'

for example
'sudo mkdir bonk'

the sudo command will ask you for a password. This is *your* user password, not the root user password.

I am sure others can fill in the details..
welcome to linux. :)

---

### Post by invalid on 2005-12-01
Your fakeroot password is your users password.

See the link in my signature for information on how Ubuntu uses sudo to work with root privledges.

Cb

---

### Post by aysiu on 2005-12-01
I have "administrative rights" to my money, but that doesn't mean I can just waltz into the bank and go into the safe and dig it out.

I have an ATM card with a pin number. If I don't have it handy, I have to go to the bank when it's open, stand in line, and give proper identification to make a withdrawal.

It's something called "security."

You have access to all files on your computer. You just don't have direct access. For more info, see: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

