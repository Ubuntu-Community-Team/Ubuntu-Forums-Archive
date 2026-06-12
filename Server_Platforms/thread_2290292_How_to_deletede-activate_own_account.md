---
title: "How to delete/de-activate own account?"
date: 2015-08-11
forum: Server Platforms
---

### Post by lads on 2015-08-11
Dear all,

My present work contract is coming to an end. I will leave behind two dozens of servers (a melange of Ubuntu 12.04 and Ubuntu 14.04) that I am presently administrating with sudo rights. About half of these servers are exposed in the DMZ. I would like to delete my user account in each of the servers, but no one has been assigned to replace me. There is only one person at the IT with enough Linux knowledge, but has been absent with illness for some weeks.

What strategy(ies) would you employ to either delete or de-activate your own accounts in these servers, guaranteeing the account would not be misused in the future?

Thank you.

---

### Post by TheFu on 2015-08-11
DO NOT DELETE ANYTHING!!!!!  This could be seen as trying to disrupt their business. You could be sued.  Change all the passwords and ssh-keys on all the machines and hand it over to the IT boss in a sealed envelop.  Make the password like - 60 characters that are impossible to type on all the machines except 1 - your workstation.  Ensure the passphrase to unlock the gpg and ssh keys are complex enough too.  Do not take any of these access methods with you.  In about a week, someone will probably call and it is best to just send them to the boss for whatever access is needed.  Inside that envelop, put an hourly rate about double your last contract rate for ad-hoc consulting.  They may turn into a good part-time client for you.  Get 20 of those and you have a flexible business that will likely pay more than you'd make on any long-term contract.

If you really are done and there is someone else with sudo there on each of the boxes - you can get an interactive root shell with **sudo -i** and do whatever is needed (locking the account would be smart, not deleting it).  At 5pm on your last day, their security isn't your problem any more without a SoW (Statement of Work) and agreed rate.

There is ZERO guaranty that the account won't be abused in the future.  It isn't your machine/domain anymore.  Is every "john@domain.com" liable for badness 1 5, 18 months after leaving the job?

---

### Post by pfeiffep on 2015-08-11
+++++^
Excellent advice

---

### Post by shawnblanchette on 2015-08-11
TheFu is right about disrupting the business. Let me ask you a question. What if the only other person with sudo quits, becomes seriously ill, or dies, and your account is disabled or deleted. What then? They're stuck in a rut (for a lack of better 'G' rated words).

I am going to eventually hire someone to take care of my servers for me. I have enough experience to maintain if that person can't work for any reason. And, I will have sudo. I will also have sudo pass (backup) in a secure place, locked in a vault where only a couple of people have access. If something happens to my IT person, then me, there's something they can do to get another IT person to maintain the tech. I'm smart that way. They are probably not. If you leave without an account and the other guy leaves for whatever reason then their a screw and driver (you know, screwed, like a screw. lol). How would you like to lose $100,000 (or the equivalent in whatever currency)? How about $1,000,000? That's easy enough. Do exactly what TheFu said. If the above happened to me and no one had access to my servers, I'd be suing. You betcha. You also look more professional when you hand over the passwords to people who don't know how to verify your account is deleted. Those really are the ones that hire you. You're showing them that you're trust worthy. Hand over the envelope, a statement of non-liability signed with your name at the top (easy to get on-line, just as Google), and a handshake, telling them you enjoyed your time and you hope to do continued business in the future. That last part is optional, everything else is essential. Get that trust. Keep that trust.

[I]


If anything in the above statement does not make sense, the author has had less than 8 hours of sleep in a week and a half, and way too much coffee. Anyone should be able to read between the lines.[/I]

---

### Post by TheFu on 2015-08-11
Well, if the system isn't whole disk encrypted, not having sudo or root isn't a big deal. Physical access and 3 minutes - I'm in. That applies to any competent admin.  Pretty trivial.  

With whole drive encryption ... it is hard to impossible to get admin/root access.  Just depends on how well patched it is and if the passphrase for disk access is available (often plugged into a usb slot).

---

### Post by lads on 2015-08-11
> **TheFu said:**
>  If you really are done and there is someone else with sudo there on each of the boxes - you can get an interactive root shell with **sudo -i** and do whatever is needed (locking the account would be smart, not deleting it). 

This sounds good. Even if wanted to, there is no one above me with enough competences on Linux to deliver the envelope you suggested in first place. 

How would you exactly lock the account?

Note: I am not a sys admin, nor do I aim at becoming one.

---

### Post by lads on 2015-08-11
> **shawnblanchette said:**
>  Let me ask you a question. What if the only other person with sudo quits, becomes seriously ill, or dies, and your account is disabled or deleted. What then? 

The other Linux savy person seems to be already seriously ill (beyond the fact of knowing very little about the software/services running on these servers). The decision to end my contract was a conscious one, the consequences are well known to all the parties involved. 

The scenario you lay down in that long paragraph is a remote one; neither I nor the institution are really interested in that sort of relationship.

I appreciate the time you took for the detailed answer in any case.

---

### Post by TheFu on 2015-08-11
> **lads said:**
> This sounds good. Even if wanted to, there is no one above me with enough competences on Linux to deliver the envelope you suggested in first place. 

How would you exactly lock the account?

Note: I am not a sys admin, nor do I aim at becoming one.

You are missing the point. It doesn't matter whether they should or shouldn't have the access. It is your responsibility to hand that over to your boss there. Period. Then it is her/his problem to either gain the skills or hire someone who has them. It isn't your problem at 5:01pm that last day.

Exactly?  I would google for an answer - "lock account linux"  There is a specific state called "locked."  The other way is to just manually add 1 character to the password shadow file. That way nobody will know the password - but anyone with root/sudo can reset it easily.  If the boss tries to use the account using the credentials from the envelop and it doesn't work, you've just lost all credibility.  I wouldn't lock my account.

Handing over the envelop is NOT optional.

---

### Post by lads on 2015-08-11
> **TheFu said:**
> Handing over the envelop is NOT optional.

Between the lines I understand there is a legal basis for your argument. Could you point me to some place where I could get the details?

Never before I handed over passwords when leaving a position.

---

### Post by lads on 2015-09-14
As an epilogue to this thread, after some more reading, I decided to simply disable my accounts at each of the servers concerned with:

```
sudo usermod <username> --expiredate 1
```

This way the user will no longer be able to log on but no service is affected. A superuser can later log on and re-activate or otherwise delete my account.

---

### Post by MAFoElffen on 2015-09-15
Having dealt with this... Was asked to lock various accounts down. As root:
```

passwd -l {username}
# or
usermod -L -e 1 {username}

```
Anyone with root could change that later by creating a password to the account..

---

