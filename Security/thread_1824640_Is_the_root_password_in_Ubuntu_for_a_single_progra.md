---
title: "Is the root password in Ubuntu for a single program, or for all programs?"
date: 2011-08-14
forum: Security
---

### Post by dr1094 on 2011-08-14
Hey...I'm wondering if my computer has viruses. I have ubuntu 11.04 installed along side windows. And I often share files with windows computers. 

My question is this. If I am installing a new package from ubuntu software center, and consquently I have to log in as root to do so, which means I have given the system 'privileges' as the program is being installed, I decide to go open mozilla, and surf suspicious sites on the net. Is it possible in that case for me to get a virus? 

Essentially, My question comes down to this: When we enter the password for the root user in order to run one program such as ubuntu software center, does that mean that all programs have root privileges for the time being (as the software center is installing the program)?

Thanks in advance.

---

### Post by raja.genupula on 2011-08-14
for which program you are giving root password only that program going to have root privileges  remaining all other dont have access unless you give root  privileges . 

                under my knowledge i didnt heard a term called virus  in ubuntu(linux )

---

### Post by The Cog on 2011-08-15
You need not worry. When the software centre asks for your password to install something, it is only the software centre that gets the elevated privileges. Other programs that you are running (or start later) still only get your normal privileges. A program is able to use the password to raise its own rights, not to elevate other programs. As you have already figured out, that would be a security nightmare.

---

### Post by haqking on 2011-08-15
> **dr1094 said:**
> Hey...I'm wondering if my computer has viruses. I have ubuntu 11.04 installed along side windows. And I often share files with windows computers. 

My question is this. If I am installing a new package from ubuntu software center, and consquently **I have to log in as root to do so**, which means I have given the system 'privileges' as the program is being installed, I decide to go open mozilla, and surf suspicious sites on the net. Is it possible in that case for me to get a virus? 

Essentially, My question comes down to this: **When we enter the password for the root use**r in order to run one program such as ubuntu software center, does that mean that all programs have root privileges for the time being (as the software center is installing the program)?

Thanks in advance.

just to be clear, you are not entering the root password for the root user.  You are authenticating yourself as having sudo privelege which gives that task elevated privelege for a short amount of time.

The root user itself is disabled by default in Ubuntu.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I just wanted to clarify this for others reading who may get confused.

---

