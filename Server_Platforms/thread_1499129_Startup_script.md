---
title: "Startup script"
date: 2010-06-01
forum: Server Platforms
---

### Post by boba_80 on 2010-06-01
Hi all...
I work as an PR in my company and they've sent us on this Linux education and I need help! :) I have no knowledge about programming and I have to pass this. So plz help. [-o<
I have a task to write a boot startup script for a application that is called tolva (it means computer in icelandic) and it is based on mysql. This script should be performed in runlevel5 and connection to script for mysql should have name S19mysql.

Thnx :)

---

### Post by arrrghhh on 2010-06-01
Wait... are you supposed to be learning about how this works?  Did they send you to a class and this is the homework?

I don't want to hand-feed you an answer so you can pass a test on false pretenses.  I can point you to some stuff that may help, but I'm not going to write it for you.

[This](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit) looks like it would be a good place for you to start...

---

### Post by boba_80 on 2010-06-01
I need this to pass the test. I'll probably never start linux again in my life. Whole my work is based on excel worksheets and nothing else. I''ve opened that debian policy and I dont understand a thing. :(

---

### Post by new_tolinux on 2010-06-01
I've got no real script knowledge too, but when I read the given link it's obvious where the script should be placed and where you should place a symbolic link to the script to run it at init level 5.

Besides that it's common policy around these forum that we do not solve homework questions. They're homework because you are supposed to learn from it by doing it yourself.

Edit: I actually guessed the first part myself before I read that, but the symlink you'll have to make was something I just read from the given link.

---

### Post by arrrghhh on 2010-06-01
> **boba_80 said:**
> I need this to pass the test. I'll probably never start linux again in my life. Whole my work is based on excel worksheets and nothing else. I''ve opened that debian policy and I dont understand a thing. :(

Sorry dude, not going to help you pass a test by feeding you the answer.  They want you to learn it for a reason, right?  If I just feed it to you, you learn nothing.

---

### Post by pricetech on 2010-06-01
Besides, we would be doing a disservice to your employer.  If they sent you to the training, they deserve to receive their money's worth.

---

### Post by new_tolinux on 2010-06-01
> **pricetech said:**
> Besides, we would be doing a disservice to your employer.  If they sent you to the training, they deserve to receive their money's worth.
That's no reason to me.

Since we're not going to get payed by his employer.... we don't have responsibilities towards his employer.
As soon as employers start to fund my bank-account properly, I may have responsibilities towards them, most likely defined by a contract. Before that, I don't.

---

### Post by arrrghhh on 2010-06-01
> **new_tolinux said:**
> That's no reason to me.

Since we're not going to get payed by his employer.... we don't have responsibilities towards his employer.
As soon as employers start to fund my bank-account properly, I may have responsibilities towards them, most likely defined by a contract. Before that, I don't.

Alright guys, enough of this banter.  We don't need this thread deteriorating any more than it has.

---

### Post by pricetech on 2010-06-04
> **new_tolinux said:**
> That's no reason to me.

Since we're not going to get payed by his employer.... we don't have responsibilities towards his employer.
As soon as employers start to fund my bank-account properly, I may have responsibilities towards them, most likely defined by a contract. Before that, I don't.

I think you misunderstand.  I'm not suggesting we owe his employer anything.  I'm merely saying that it's not our place to shortcut him to passing a test when his employer is paying for the training.

We don't owe his employer, but he does, at least to the extent that he should make an honest effort to learn what his employer is paying for him to be taught.

---

