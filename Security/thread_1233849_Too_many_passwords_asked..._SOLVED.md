---
title: "Too many passwords asked... SOLVED"
date: 2009-08-07
forum: Security
---

### Post by asbesto on 2009-08-07
I had a topic closed about "Annoying, BORING "System Policy" stuff!":

> 
It is the forum policy to support the Ubuntu security implementations. We assume that if you bypass those security implimentations, you do so at your own risk and assume that you have the technical knowledge to overcome any problems that may result in this decision.

Thread closed. Thank you for your participation.


Very, very bad for an open forum! :shock:

I was just asking a way to disable all those dedundant requests, NOT to use the system as root, as the Policy states here: [http://ubuntuforums.org/showthread.php?t=716201]("http://ubuntuforums.org/showthread.php?t=716201"). 

So I don't understand the censorship to my post. 

I don't want nor need root access to do stuff, I only need to write in my password one time to do that, and to use sudo/suauth stuff.

Well, the PolKit seem to be another thing that keep asking passwords again and again. [SNIP]

---

### Post by donato roque on 2009-08-07
I want to thank all the staff and admin of this forum.  They are doing the heavy lifting so to speak.  I happen to catch the previous thread.  I happen to agree with the forum staff's decision to impose some rule here.  Besides the community comes first, not one individual.

---

### Post by asbesto on 2009-08-07
Is this a technical forum or what? This is not about rules, it's about how to solve things and tune the distro as users want. And that thread has nothing to do with root as user, or security problems. This is UNIX, not Vista.

---

### Post by decoherence on 2009-08-07
> I think a fix for this is to edit /etc/PolicyKit/PolicyKit.conf adding the username:

Do you know what the security implications of this are?

---

### Post by cdenley on 2009-08-07
> **asbesto said:**
> Is this a technical forum or what? This is not about rules, it's about how to solve things and tune the distro as users want. And that thread has nothing to do with root as user, or security problems. This is UNIX, not Vista.

You basically made your account a root account, thus circumventing the ubuntu security model. If an application you are running were compromised so the attacker can execute arbitrary code, they can now easily escalate to root privileges. I agree with their policy for not allowing guides for enabling root. I think maybe giving a few pointers on configuring policykit should be allowed, but I certainly understand their reluctance. It is sort of a gray area as far as their policy is concerned. I personally wouldn't help a user weaken the security of their computer unless they knew what they were doing, but then they probably wouldn't need my help.

---

### Post by wojox on 2009-08-07
Actually this is Linux. Remember GNU's Not Unix.

---

### Post by asbesto on 2009-08-07
> **cdenley said:**
> You basically made your account a root account, thus circumventing the ubuntu security model. If an application you are running were compromised so the attacker can execute arbitrary code, they can now easily escalate to root privileges.

There are no other users than me on my computer here at my home. No open doors from outside. I agree with you about your security concerns, but this is not the case. And closing discussions is doing "security thru obscurity", that has to be avoided like hell.

And for sure I know what security means, 'cause i'm a VAX/VMS and UNIX sysadmin since 1985 :)

---

### Post by cdenley on 2009-08-07
> **asbesto said:**
> There are no other users than me on my computer here at my home. No open doors from outside. I agree with you about your security concerns, but this is not the case. And closing discussions is doing "security thru obscurity", that has to be avoided like hell.

And for sure I know what security means, 'cause i'm a VAX/VMS and UNIX sysadmin since 1985 :)

Are you using the same computer to browse this forum? If so, that can be considered an "open door". Anytime your computer has any interaction with the outside world (the forum you are reading right now), there is potential for an attack. The only way to make remote security a non-issue would be to unplug it from any network entirely. User privilege separation is not "security through obscurity". Also, "security through obscurity" should not be "avoided like hell". You just have to keep in mind it cannot replace taking real security precautions.

---

### Post by decoherence on 2009-08-07
> **asbesto said:**
> There are no other users than me on my computer here at my home. No open doors from outside. I agree with you about your security concerns, but this is not the case. 

you place a lot of trust in ubuntu. As I'm sure you're aware, the standard method of privilege escalation exists not just to protect you from outside threats but also from bugs in legitimate software that you have installed.

It's your decision to make these changes but don't be surprised if things start to break.

> 
And closing discussions is doing "security thru obscurity", that has to be avoided like hell.


closing that thread was absolutely not 'security thru obscurity.' Anyone following your advice would have a system that is in a state where it *could not be supported by members of this community*. Once the default security model has been circumvented, it introduces a raft of potential factors that must be considered by anyone who is trying to help.

The community support thing works because we all have a more-or-less common base to work from. The distribution expects security to work a certain way and, once you change that, the behavior of the distribution can change in ways that can't be predicted by a bunch of random people in cyberspace.

The thread had to be closed because people have to know that it's NOT okay to do this and then come looking for help. Any help given has a greater chance of breaking the system even more.

---

### Post by NotJustANewbie on 2009-08-07
<random thought>
I agree with both sides of the flaming for different reasons...

If asbesto (OP) isn't going to use the computer for networking other than an enclosed LAN, I think his problem shouldn't cause much harm to the Ubuntu community although it may compromise his LAN security...

But on the other hand, I completely see where the forum staff are coming from with the rules, which must be strict in order to keep the forum from falling apart...
</random thought>

---

### Post by phr33k-dc on 2009-08-07
this is quite serious stuff being talked about here. the only thing you can do is take the ubuntu's staff advice because hey know best. leave it at that

---

### Post by asbesto on 2009-08-07
> **cdenley said:**
> 
User privilege separation is not "security through obscurity".


I was talking about closing a topic. This IS "security thru obscurity". 
Also, what I was asking for in that topic was present in the manpage of PolicyKit.conf ... it's the exact example I've done. Maybe someone want to remove that manpage just to save users from being hacked ? :D

---

### Post by cdenley on 2009-08-07
> **asbesto said:**
> I was talking about closing a topic. This IS "security thru obscurity". 
Also, what I was asking for in that topic was present in the manpage of PolicyKit.conf ... it's the exact example I've done. Maybe someone want to remove that manpage just to save users from being hacked ? :D

Closing a thread so as not to instruct users how to circumvent ubuntu's security model is NOT security through obscurity. If they were attempting to hide a security problem with policykit, it would be. Instead, they are refusing to help you create a security problem in your policykit configuration. The intention is not to prevent you from configuring your system how you want, it is simply not to encourage or help you to configure your system in a way which would make it less secure. The information to circumvent ubuntu's security model is readily available, as you now know, just not on this forum.

---

### Post by aysiu on 2009-08-07
The forum policy exists for a reason and is stated at great length in [the log-in-as-root tutorial policy thread.](http://ubuntuforums.org/showthread.php?t=716201)

You don't have to agree with it, but we don't have to agree with you either. If you have a problem with the individual closure of a thread, post in the resolution center.

---

