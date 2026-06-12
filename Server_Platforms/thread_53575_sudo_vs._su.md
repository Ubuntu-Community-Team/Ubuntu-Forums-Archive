---
title: "sudo vs. su"
date: 2005-08-01
forum: Server Platforms
---

### Post by ghostryder on 2005-08-01
Hi,

maybe I unrestood something wrong when I read the lines about sudo and su in the Ubuntu-Wiki. I mean if somebody is able to login with my normal username he has to crack the root password to get root rights. With sudo he just has to crack user password  that is maybe already known, because he was able to login as me. Isn't that less secure?  :roll: 

tia G.

---

### Post by adwait on 2005-08-01
The question here is, how does somebody login as you? Ideally, there should be a separate account for everyone. Also, if you want, you can setup a separate user who is not in the sudoers list, and use that regularly. That way, even if somebody logs in as you, they can't use sudo.

---

### Post by LordHunter317 on 2005-08-01
No. 

In most situations where one could recover the user's password, they'd be able to recover the root password as well.

Moreover, using sudo(1) requires a user to only remember one password, not two, which generally reduces the chances of them participating in such bad behavior as writing the passwords down, which causes the above situation.

The reality is that finding a user's password isn't a common entry vector, it's more common for a social engineering attack to occur (e.g., pose as technical support) or for it to be simply guessed (e.g., automated dictionary attack).  In the former case, getting the root password is just as easy; in the latter, certain forms of attacks can render all the passwords in minutes.

---

### Post by LordHunter317 on 2005-08-01
[QUOTE=adwait]The question here is, how does somebody login as you? Ideally, there should be a separate account for everyone. Also, if you want, you can setup a separate user who is not in the sudoers list, and use that regularly. That way, even if somebody logs in as you, they can't use sudo.[/QUOTE]This is functionally almost no different from using a root account, and if you're going to go through this bother, realistically, it's probably just eaiser to re-enable the root account.

---

### Post by ghostryder on 2005-08-01
Ok. Thanks for the answers.

---

### Post by adwait on 2005-08-01
[QUOTE=LordHunter317]This is functionally almost no different from using a root account, and if you're going to go through this bother, realistically, it's probably just eaiser to re-enable the root account.[/QUOTE]
 Hmm....I guess....

---

### Post by UbuWu on 2005-08-01
[QUOTE=LordHunter317]This is functionally almost no different from using a root account, and if you're going to go through this bother, realistically, it's probably just eaiser to re-enable the root account.[/QUOTE]

No, it is safer, because there is less risk of accidentily screwing things up than when logged in as root, and of other programs screwing things up, as you have to explicitely start them with the sudo command.

and if someone somehow gets access to the computer when you are logged in but not around, they can't do much without the password, but if you were logged in as root, they could just do about anything.

---

### Post by LordHunter317 on 2005-08-01
[QUOTE=UbuWu]No, it is safer, because there is less risk of accidentily screwing things up than when logged in as root,[/quote]I think I noted that above.

>  and of other programs screwing things up, as you have to explicitely start them with the sudo command.Nope.  One can assume that if an application needs privilege, the user is going to run it privileged, so sudo doesn't save a thing.

It only saves you if you ran a malicious program.  And a clever one could still trick a user into running it with privilege anyway. 

> and if someone somehow gets access to the computer when you are logged in but not around, they can't do much without the password, but if you were logged in as root, they could just do about anything.Interactive root accounts had better be passworded, so no, this isn't a valid concern.

---

### Post by UbuWu on 2005-08-01
[QUOTE=LordHunter317]
It only saves you if you ran a malicious program.  And a clever one could still trick a user into running it with privilege anyway. [/QUOTE]

But it requires more effort, so it is safer.

[QUOTE=LordHunter317]
Interactive root accounts had better be passworded, so no, this isn't a valid concern.[/QUOTE]

Yes it is, because when you are logged in, the password is not needed anymore to do anything with a root account, but with sudo it is. (e.g. during your coffee break....)

---

### Post by LordHunter317 on 2005-08-01
[QUOTE=UbuWu]But it requires more effort, so it is safer.[/quote]Nope, that's not necessarily true, as much as people would like to believe it is.  Just because something involves more effort doesn't make it harder for an attacker to exploit that vector.

Building a program that needs privilege and asks them to run it over sudo isn't substantially enough effort to worry about it, anyway.

> Yes it is, because when you are logged in, the password is not needed anymore to do anything with a root account,And if you leave your terminal and don't lock it, you deserve what you get.

>  but with sudo it is. (e.g. during your coffee break....)Nope.  Not all the time, anyway.

---

### Post by UbuWu on 2005-08-01
[QUOTE=LordHunter317]Nope, that's not necessarily true, as much as people would like to believe it is.  Just because something involves more effort doesn't make it harder for an attacker to exploit that vector.
[/QUOTE]

Well that's what security is all about, making it harder/requiring more effort/time to do bad things. It is like the locks on your house. It will never be impossible to break into your home, but you better make it as hard as possible to do.

[QUOTE=LordHunter317]And if you leave your terminal and don't lock it, you deserve what you get.[/QUOTE]

Well some people have bad habits, and they are hard to get rid of. From the Ubuntu wiki:

> 
On a more esoteric level, sudo provides some features which encourage different work habits, which can positively impact the security of the system. sudo is commonly used to execute only a single command, while su is generally used to open a shell and execute multiple commands. The sudo approach reduces the likelihood of a root shell being left open indefinitely, and encourages the user to minimize their use of root privileges.


For all the benefits, see:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by LordHunter317 on 2005-08-01
[QUOTE=UbuWu]Well that's what security is all about, making it harder/requiring more effort/time to do bad things.[/quote]Yes, but if you don't make the level substantially more difficult, one has to question the economic value of doing so in the first place.

As a justification to prevent privileged phishing or trojan attacks **run by the user**, sudo has no value.   It's already been demonstrated that I can send a person an email with instructions to unzip the attachment and run the contents and get them to do so.  Changing the instruction to run the command from './myhackerprog' to 'sudo ./myhackerprog' would not be difficult, nor do I believe it would decrease the success rate of such attacks.

> It will never be impossible to break into your home, but you better make it as hard as possible to do.That's just not true.  There's a point where the cost outweights the benefit.  You can't ignore the economic issues chosing a solution.

> Well some people have bad habits, and they are hard to get rid of. From the Ubuntu wiki:And I noted those potential benefits a long time ago.  They're not up for discussion.  Moreover, in response to my comment, sudo doesn't always protect against this problem, at least in Ubuntu's default configuration.

---

