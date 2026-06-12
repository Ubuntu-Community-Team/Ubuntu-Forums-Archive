---
title: "Awkward Situation"
date: 2011-12-10
forum: The Cafe
---

### Post by coolguy918 on 2011-12-10
I know that this is a forum for technical support, not social advice, but this remotely relates to Ubuntu and I'm pretty sure there's a Systems Adminstrator somewhere on here that's been in a similar situation before and can provide me with a little advice.

So there's a family friend that I made the mistake of giving a user account on my Linux server to (he wanted to explore Linux a little bit without actually installing it so that's why). He's really smart, but it seems that he's actually been going backwards in terms of maturity and I honestly don't trust him anymore. As this is a very delicate situation, I don't want to hurt his feelings, but I need an excuse to kick him off my server before he does something stupid (even as a standard user, he could easily forkbomb the system, fill up my hard disk, try and elevate his privileges through hacking (authenticated users have a LOT more attack surface than unauthenticated ones), and possibly a bunch of other possibilities I've never considered). Do any of you have any ideas for what I should say and how I should say it? And while security advice is great and everything, that's not what I'm looking for... I simply want him off my server.

---

### Post by IWantFroyo on 2011-12-10
Just use your admin status to delete his account or mess it up, and then pretend you don't know what happened and lock down your server "so that it won't happen again."

---

### Post by CharlesA on 2011-12-10
I'd disable his account, to be honest.

By "disable" I mean, just lock it:

```
sudo password -l username
```

No login = no problem, unless they are using SSH with keys..., which in that case remove their key from authorized_keys

EDIT: I suppose you could always create a VM for him to mess around on and just give him free reign over it.

How are they accessing the server ?

---

### Post by coolguy918 on 2011-12-10
> **CharlesA said:**
> I'd disable his account, to be honest.

By "disable" I mean, just lock it:

```
sudo password -l username
```No login = no problem, unless they are using SSH with keys..., which in that case remove their key from authorized_keys

EDIT: I suppose you could always create a VM for him to mess around on and just give him free reign over it.

How are they accessing the server ?

SSH/SCP, VNC, and Usermin

Can you point me in the right direction in terms of making a VM that's accessed over the network?

---

### Post by cprofitt on 2011-12-10
If you create a VM then you just use a bridged connection and then open the guest up as you would normally.  

An easy way would be to run ProxMox, but that would redo your server as well...
 [http://pve.proxmox.com/wiki/Documentation](http://pve.proxmox.com/wiki/Documentation)  

The other way would be to use KVM[U]
[/U][https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by coolguy918 on 2011-12-10
> **cprofitt said:**
> If you create a VM then you just use a bridged connection and then open the guest up as you would normally.  

An easy way would be to run ProxMox, but that would redo your server as well...
 [http://pve.proxmox.com/wiki/Documentation](http://pve.proxmox.com/wiki/Documentation)  

The other way would be to use KVM[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Thanks! I'll consider it, but I just generally despise him and don't think he's worth the server resources. I'll probably go the deactivation or deletion route.

---

### Post by coolguy918 on 2011-12-10
> **IWantFroyo said:**
> Just use your admin status to delete his account or mess it up, and then pretend you don't know what happened and lock down your server "so that it won't happen again."

What do you mean when you say "mess it up?"

---

### Post by Old_Grey_Wolf on 2011-12-10
> **coolguy918 said:**
> What do you mean when you say "mess it up?"

Probably by deleting random folders from the user's home directory that start with the "." symbol; such as, .config ;)

---

### Post by CharlesA on 2011-12-11
> **Old_Gray_Wolf said:**
> Probably by deleting random folders from the user's home directory that start with the "." symbol; such as, .config ;)
Well forkbombs are nasty, but you can set limits on processes so they won't totally lock the machine up.

Er, I totally misread that.

I suppose IWantFroyo meant mess with the account like changing the password or something.

I'd just lock them out of the server entirely but that's just me.

---

### Post by Dangertux on 2011-12-11
> **coolguy918 said:**
> SSH/SCP, [SIZE=4]**VNC**[/SIZE], and Usermin


As stated already...just disable the account. Although in reference to what I quoted if you're really worried about your friend messing up your system, I think that is probably the least of your worries.

Disable VNC.

---

### Post by CharlesA on 2011-12-11
> **Dangertux said:**
> As stated already...just disable the account. Although in reference to what I quoted if you're really worried about you friend messing up your system, I think that is probably the least of your worries.

Disable VNC.
Huge +1 to that. I really hope that VNC isn't exposed directly to the internet.

That is one of the most frequent ways a box is cracked.

---

### Post by Primefalcon on 2011-12-11
> **CharlesA said:**
> Huge +1 to that. I really hope that VNC isn't exposed directly to the internet.

That is one of the most frequent ways a box is cracked.
I'd say there's your excuse.... say you've noticed some unusual activity trying to access the box, and some very security conscious friends/acquaintances have advised you to disable VNC/SSH... whatever

and that you'll see about setting him him in a more secure way, sometime in the (infinite)future......

---

### Post by grahammechanical on 2011-12-11
It sounds to me that you feel that you are being taken advantage of. It is not good to feel that way. Even if this fellow is a nice guy and not just a family friend but your friend, it is not good to be taken advantage of or to feel that you are being taken advantage of.

"I may be paranoid but that does not mean that people are not out to get me." We sometimes get taken advantage of even by our own nice friends.

I would say that it is better to upset a family member by upsetting their friend than to continue upsetting yourself because you have allowed a situation to exist that you do not like.

I would recommend that you take control. You decide. If the decision is to leave the situation as it is, then that is a decision that you have made. And you accept the stress that comes from it.

If you decide to change things, then that is also a decision that you have made and you accept the stress that comes from that. It is better that you make the decision.

I use to get a lot of stress because I could not say no to people. There were times when my wife noticed this and refused to let additional burdens be put on to me. I am thankful for that. I have found that I can cope with stress better when I decide to accept responsibility for something than when a burden is dumped on me against my better judgement.

Regards.

---

### Post by mamamia88 on 2011-12-11
Why is anyone not mentioning the obvious?  Talk to your friend first and explain why you are upset.   Just locking him out without notifying him first will probably just **** him off.

---

### Post by CharlesA on 2011-12-11
> **mamamia88 said:**
> Why is anyone not mentioning the obvious?  Talk to your friend first and explain why you are upset.   Just locking him out without notifying him first will probably just **** him off.

+1. I'd talk to them first before doing anything.

---

### Post by F.G. on 2011-12-11
i'd suggest asking him if he still needs it, you can say that you want to make some changes to the system, maybe you really want to use the space of his home directory for something else? maybe you want to let someone else use that account? either way, you can make some unrelated excuse for wanting to get rid of it and let him know, after all it's your machine so i'm sure he'll understand.

---

### Post by BrokenKingpin on 2011-12-12
Tell him you are going to disable the account for maintenance or whatever. You could tell him upfront of doing it, but I wouldn't give much time between telling him and disabling the account (in case of any retaliation lol).

If he has already played around on it for a bit, I would just tell him to install Ubuntu if they would like to continue exploring it. He could use something like vbox if they don't want to dedicate a partition to it yet.

---

