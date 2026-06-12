---
title: "Disadvantages of setting a root password?"
date: 2013-03-23
forum: Security
---

### Post by na5h on 2013-03-23
I was just wondering: are there any actual disadvantages to setting a root password in Ubuntu...especially if you re-disable the root account after setting the password? Setting a root password would also render the password reset method mentioned in the article below useless, right?

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

P.S. I have no need to perform any actions that would require actual root access...I'm just wondering whether setting a strong password for root would be a good security measure or not...

---

### Post by The Cog on 2013-03-23
One disadvantage that I can think of is that the ssh guessing bots have a ready-made username to aim for. With Ubuntu, they can guess different root passwords for as long as they like.

---

### Post by CharlesA on 2013-03-23
> **na5h said:**
> I was just wondering: are there any actual disadvantages to setting a root password in Ubuntu...especially if you re-disable the root account after setting the password? Setting a root password would also render the password reset method mentioned in the article below useless, right?

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

P.S. I have no need to perform any actions that would require actual root access...I'm just wondering whether setting a strong password for root would be a good security measure or not...

If you enable the account, set the password then disable it again, what was the point of adding a password in the first place?

It would probably be easier/more convenient just to stick to using sudo from your main account because you will only have to remember one password instead of two. ;)

> **The Cog said:**
> One disadvantage that I can think of is that the ssh guessing bots have a ready-made username to aim for. With Ubuntu, they can guess different root passwords for as long as they like.

As long as you set PermitRootLogin to no or without-password, you wouldn't have to worry about bots bruteforcing the root account, but it is still something to think about.

---

### Post by na5h on 2013-03-23
> **The Cog said:**
> One disadvantage that I can think of is that the ssh guessing bots have a ready-made username to aim for.
But that's not really a problem if the root account is disabled, right? As far as I know, you'd also need to be running an SSH server that allows root access for that to be possible.

---

### Post by CharlesA on 2013-03-23
> **na5h said:**
> But that's not really a problem if the root account is disabled, right? As far as I know, you'd also need to be running an SSH server that allows root access for that to be possible.

Correct.

---

### Post by na5h on 2013-03-23
> **CharlesA said:**
> If you enable the account, set the password then disable it again, what was the point of adding a password in the first place?
Setting a root password would render the password reset method mentioned in the psychocats article above useless, right? Though the root account itself would be disabled, wouldn't the password still remain intact?

---

### Post by CharlesA on 2013-03-23
> **na5h said:**
> Setting a root password would render the password reset method mentioned in the psychocats article above useless, right? Though the root account itself would be disabled, wouldn't the password still remain intact?

I just tested it on my debian test box and it asks for the root password or to hit ctrl+d to bypass, but it didn't prompt me for the stuff Ubuntu does.

However, what you said has been brought up before, so the only way you will know what happens for sure is to test it yourself. ;)

---

### Post by na5h on 2013-03-23
> **CharlesA said:**
> I just tested it on my debian test box and it asks for the root password or to hit ctrl+d to bypass, but it didn't prompt me for the stuff Ubuntu does.

What do you mean by "prompt me for the stuff Ubuntu does"?

It did ask you for the password so it should be all good....um, you can't really just bypass it by simply hitting ctrl+d, right? That would kinda go against the point of having a password in the first place... ;)

---

### Post by CharlesA on 2013-03-23
> **na5h said:**
> What do you mean by "prompt me for the stuff Ubuntu does"?

It did ask you for the password so it should be all good....um, you can't really just bypass it by simply hitting ctrl+d, right? That would kinda go against the point of having a password in the first place... ;)

Debian doesn't have the "friendly recovery menu" thing that Ubuntu does.

Either that or it isn't installed on my version as I did a minimal install.

---

### Post by na5h on 2013-03-23
> **CharlesA said:**
> Debian doesn't have the "friendly recovery menu" thing that Ubuntu does.

Either that or it isn't installed on my version as I did a minimal install.

Heh...I see! ;) Anyways, thanks for all the answers...I'll probably go try it out myself in virtualbox...

---

### Post by CharlesA on 2013-03-23
> **na5h said:**
> Heh...I see! ;) Anyways, thanks for all the answers...I'll probably go try it out myself in virtualbox...

Have fun!

---

### Post by 1clue on 2013-03-23
FWIW, my absolute number one favorite thing about *buntu is what they did about the root user access.

I think the best way to figure out how much you like it is to run some other distro for awhile.

---

