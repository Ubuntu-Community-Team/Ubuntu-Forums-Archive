---
title: "Privilege escalation / compromising administrator rights"
date: 2011-07-24
forum: Security
---

### Post by twipley on 2011-07-24
I have been wondering if a guest user could compromise a machine which is set in the following way: they are not able to open the computer case, to boot from either an USB flash drive or an optical-disc drive, nor have any knowledge of the administrator-user password. Thus, they are landing on their guess account, and have to work their privilege escalation from there.

Therefore, what can they do to gain it? Could they download or otherwise install or run from a thumb drive an application that could be used to crack the administrator-user password? Because, it seems to me, could they enter into the system such a password-cracking application, the whole system could be compromised given the administrator-user password contains less than 9-or-so characters.

What do you think? Can I lend my computer to anybody without them having beforehand gained my trust in them? Is the reasoning reasonable?

---

### Post by bodhi.zazen on 2011-07-24
Physical access is root access and, IMO, despite all you say, I am not convinced you can lock down a machine as much as you seem to think.

With that in mind, I use the guest account on Ubuntu and confine it with apparmor.

As an alternate I use the xguest account on Fedora which is confined by selinux. I figure both are sufficient for the privacy of both parities when friends and family visit.

---

### Post by twipley on 2011-07-25
Confining the guest account through jailbashing:
[http://ubuntuforums.org/showthread.php?p=11087889](http://ubuntuforums.org/showthread.php?p=11087889)

(for users possessing sound knowledge of the "workings behind the wheels.")

---

### Post by twipley on 2011-07-25
> **bodhi.zazen said:**
> Physical access is root access
Sorry. What are you meaning by that? The whole first post went by presuming both were not necessarily equal. Care to elaborate?

to bodhi.zazen metaphysics.

---

### Post by bodhi.zazen on 2011-07-25
I believe if someone has physical access the have root access in that they can boot a live CD or pull the hard drive or do what it takes to access and alter your data.

The only protection you have, IMO, is encryption.

IMO if you wish to protect your data, encrypt it, ie LUKS. That way, even if someone pulls the hard drive, they still can not decrypt the data.

I do not place much trust in most of what you listed to restrict such activity (BIOS passwords, grub passwords, etc), there are too many ways to work around those measures.

Sure they may stop casual users/crackers (I do not expect guests in my home to pull our my box and start loosening the screws), but they will not significantly deter an experienced cracker.

---

### Post by twipley on 2011-07-25
> **bodhi.zazen said:**
> I do not expect guests in my home to pull out my box and start loosening the screws.
I think you are right in that matter. You know, if you expected them to do that, I think you would not permit them to enter your home in the first place.

---

### Post by bodhi.zazen on 2011-07-25
> **twipley said:**
> I think you are right in that matter. You know, if you expected them to do that, I think you would not permit them to enter your home in the first place.

So , what I am saying, is just use the so called guest account and you will be fine. 

Make sure your home directory has "private" settings (770) .

If you are truly paranoid, use the xguest account on Fedora, it is basically a kiosk mode confined by selinux. This means your guests can log in to web interfaces, and as soon as they log out of the guest account, any information they entered is wiped clean. Sort of protects both parties ;)

---

### Post by Dangertux on 2011-07-25
> **twipley said:**
> I have been wondering if a guest user could compromise a machine which is set in the following way: they are not able to open the computer case, to boot from either an USB flash drive or an optical-disc drive, nor have any knowledge of the administrator-user password. Thus, they are landing on their guess account, and have to work their privilege escalation from there.

Therefore, what can they do to gain it? Could they download or otherwise install or run from a thumb drive an application that could be used to crack the administrator-user password? Because, it seems to me, could they enter into the system such a password-cracking application, the whole system could be compromised given the administrator-user password contains less than 9-or-so characters.

What do you think? Can I lend my computer to anybody without them having beforehand gained my trust in them? Is the reasoning reasonable?

In addition to the very good info you've already been given a more simple answer to your question is yes, escalation is VERY possibly from a guest account. 

Even if you use Apparmor/SELinux, there is a possibility that an escalation can occur.

I think some of the problem here is that you may not understand fully how local escalation works. If you would like , you can read this article, it is a little bit old, but still very interesting and should help you understand better how escalation works.

[http://news.softpedia.com/news/Ubuntu-Bug-Allows-Local-Users-to-Gain-Root-Privileges-146854.shtml](http://news.softpedia.com/news/Ubuntu-Bug-Allows-Local-Users-to-Gain-Root-Privileges-146854.shtml)

Also -- I agree with anyone who is saying physical access is root access. Especially if you're talking about LENDING someone the computer. For instance, like another poster said, nobody is going to start taking your computer apart in your home. However, if they have it in THEIR home, they can pretty much do what the want with it without you knowing. 

Just something to think about. If you're going to lend out your computer , why not do something like what retail stores do when they lend a computer while someone else's is in the shop, just re-image it when it comes back.

That is my thought on the subject, if you really get into it, if someone wants into something bad enough. They will get it, nothing is 100% secure. That is why "theoretical" discussions are somewhat pointless. You have to look at what is REALISTICALLY going to happen. Now if someone is realistically going to have physical access to your machine outside of your view. Then, no it is not secure. No matter what you do to it.

---

### Post by doas777 on 2011-07-25
> **twipley said:**
> Sorry. What are you meaning by that? The whole first post went by presuming both were not necessarily equal. Care to elaborate?

to bodhi.zazen metaphysics.
I understand that you are trying to eliminate vectors, but with physical access, where there is a will there is a way. no computer case will stop a guy with a hacksaw. in the long run you can never completely eliminate the physical vectors.

---

### Post by bodhi.zazen on 2011-07-25
> **Dangertux said:**
> Even if you use Apparmor/SELinux, there is a possibility that an escalation can occur.

While all things are possible, I would not dismiss either apparmor or selinux so fast. Both would stop the vulnerability you cited short in it's tracks.

---

### Post by Thewhistlingwind on 2011-07-25
> **Dangertux said:**
> 
That is my thought on the subject, if you really get into it, if someone wants into something bad enough. They will get it, nothing is 100% secure. That is why "theoretical" discussions are somewhat pointless. You have to look at what is REALISTICALLY going to happen. Now if someone is realistically going to have physical access to your machine outside of your view. Then, no it is not secure. No matter what you do to it.

In a realistic view, no one you loan your computer to will be able to find the computing power to crack your encryption. (Or any people that person knows.) Assuming it's done properly.

Of course, if your leaving them alone with physical/root access and the system directory tree, I'm sure theres ways to get it to stream your data AFTER you decrypt it.

---

### Post by bodhi.zazen on 2011-07-25
> **Thewhistlingwind said:**
> In a realistic view, no one you loan your computer to will be able to find the computing power to crack your encryption. (Or any people that person knows.) Assuming it's done properly.

No, they would use easier techniques , but this is not the place to discuss such things.

---

### Post by Dangertux on 2011-07-25
> **bodhi.zazen said:**
> While all things are possible, I would not dismiss either apparmor or selinux so fast. Both would stop the vulnerability you cited short in it's tracks.

You're absolutely right about the link I posted (if that is the vulnerability you were referring to). 

It was just a generalization, to emphasize that nothing is perfect and a healthy sense of paranoia is good :-P

> **Thewhistlingwind said:**
> In a realistic view, no one you loan  your computer to will be able to find the computing power to crack your  encryption. (Or any people that person knows.) Assuming it's done  properly.

Of course, if your leaving them alone with physical/root access and the  system directory tree, I'm sure theres ways to get it to stream your  data AFTER you decrypt it.

Again correct - however this whole thread is a very hypothetical situation, and it would appear to me at least the TS is asking what are the possibilities. Of which there are many. Now , if you loan your computer to a friend for the weekend, the odds that any of this is going to happen are slim to none (assuming they are a half decent friend lol)

---

