---
title: "Passwords visible in keyring"
date: 2009-02-20
forum: Security
---

### Post by lesser on 2009-02-20
I'm using Ubuntu 8.10 in an educational setting, amidst a lot of Windows machines. Data processing is much quicker under Ubuntu, that's why other people sometimes like to "borrow" my computer, which is fine with me.

However, I noticed that passwords (for email, network drives, etc) can be read by these users when they click Applications -> Accessories -> Passwords & encryption Keys (tab Passwords, doubleclick key, select "show password"). You'll then get the question whether or not seahorse should be allowed access to the password, but user-X just has to click "allow" to be able to read my passwords in plain text. 

In my case this is a big problem, I trust my colleagues to stay out of my mail etc when they are behind my computer, but I obviously do not want all of my passwords compromised. 

So my question is, how can I prevent my passwords from being visible, but still use the very handy keyring application?

Cheers

---

### Post by 505 on 2009-02-20
I think you can't. The reasons is that you're logged in - for which you had to type your password. After that, stored password are accessible.
What you can do is create an extra user account. Set a password on your account, and create a "guest" account for the other users.

---

### Post by lesser on 2009-02-20
thanks for your reply! 

Although I do get your point, I am puzzled by the question why an application like firefox is capable of storing passwords in such a way that they can be used but not read, and seahorse is not (where you would expect the latter to handle passwords more securely).

---

### Post by cdenley on 2009-02-20
> **lesser said:**
> thanks for your reply! 

Although I do get your point, I am puzzled by the question why an application like firefox is capable of storing passwords in such a way that they can be used but not read, and seahorse is not (where you would expect the latter to handle passwords more securely).

Firefox also allows you to view passwords.
Edit>Preferences>Security>Saved Passwords>Show Passwords
I guess the idea is if your user already has enough permission to decrypt and use the password, they can also view the password, so they might as well make a user interface which makes it easier. In firefox, you can set a master password to require that password before you can decrypt any remembered passwords. I thought there was a similar feature in seahorse, but I'm not that familiar with it.

---

### Post by xzero1 on 2009-02-20
> **505 said:**
> I think you can't. The reasons is that you're logged in - for which you had to type your password. After that, stored password are accessible.
What you can do is create an extra user account. Set a password on your account, and create a "guest" account for the other users.

Would it be possible to force the user to use sudo to access the keyring by editing the "sudoers" file?
See [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by lesser on 2009-02-21
That sounds like a good solution! It is definitely something I'm gonna try next week.

Thanks for your help

---

### Post by koenn on 2009-02-22
> **lesser said:**
> That sounds like a good solution! It is definitely something I'm gonna try next week.

Thanks for your help

It may sound like a good solution, but it's fixing the wrong problem. 
Apparently, you're allowing others to log on with your account, or let others use a session you logged on in. 
Not only could these people access sensitive information such as stored passwords (as you've found out), they could also quite easily set up traps to capture passwords you type in interactively. There's quite a number of ways to do that, some of which have been discussed on these forums.

On top of that, your account is probably an account with sudo rights, so if they somehow get hold of your password, the whole system is open to them.

The only right way to fix this is set up accounts for the people that use your computer, or at least 1 common account for all of them. You're using a multi-user system with a security model that hinges on user separation and has the features such as 'switch user' to make it all quite painless. Why don't you use it ?

Going against the grain of that security model only forces you to try and plug every possible hole in every application that might, by itself or with a bit of tweaking, reveal information that you don't want revealed.

---

### Post by bodhi.zazen on 2009-02-22
The "problem" is three fold.

First, physical access = bad news. If someone has physical access they can access your data. The only thing which protects you from this is encryption.

The second issue, each user should have a unique account. I presuem you gave them yoru password, which then gives them root access, ie you are giving free reign on your computer, **very very bad**. Make a guest account.

Small clarification, re: Firefox. At least on my box, you need to enter a password before you can see password.

Likewise you *should* , IMO, need to enter a password with key ring.

The two caveats are then :

1. Use Launchpad to file a bug (against key ring), not the Ubuntu forums.

2. This is a minor issue compared to physical access and using a shared account.

---

### Post by lesser on 2009-02-24
Okay, I do see the advantages of a guest account. You must understand however, that I'm working in a setting where we are working on complex problems as a team. This means that when I let people behind my computer (I don't supply them with my password, I just log in for them), I want them to be able to access all resources they may need and that I made "automatically" available. Don't forget that they are all Windows users, so they are used to drive letters and if a drive letter is not there, they are helpless.

I don't know if they can install keyloggers without the sudo password, but I don't believe people would go through so much trouble. I'm simply not that interesting. On the other hand, I do not want to advertise my passwords.

I agree with bodhi.zazen, requiring a password to make stored passwords visible would be a good idea. I'm sure most users don't lock their computer when they go grab a cup of coffee. It takes only 5 s now to view all stored passwords. I would consider that a vulnerability.

---

### Post by hyper_ch on 2009-02-24
you could setup a "coworkers" account and configure it the same way as yours. So they can have the same access and stuff like when they use your account. Only that they will not be messing around with your user account and won't have sudo rights.

---

### Post by lesser on 2009-02-24
It is that configuring-an-account part that makes it so tricky. One example is RKWard, a very handy R GUI, but it took me forever to get it working. I tried it under the guest account, but it turns out to crash again as it used to do under my own account. Should have been more careful....

I'm still hoping to find a "good enough for me" solution, comparable t the master-password in firefox

---

### Post by koenn on 2009-02-24
> **lesser said:**
>  Don't forget that they are all Windows users, so they are used to drive letters and if a drive letter is not there, they are helpless.

I don't know if they can install keyloggers without the sudo password, but I don't believe people would go through so much trouble. I'm simply not that interesting. On the other hand, I do not want to advertise my passwords.

I agree with bodhi.zazen, requiring a password to make stored passwords visible would be a good idea. I'm sure most users don't lock their computer when they go grab a cup of coffee. It takes only 5 s now to view all stored passwords. I would consider that a vulnerability.

They don't actually need to install keyloggers - there are simpler methods than that, that only involve editing files your account has access to without sudo.

You might also ask yourself if it's such a good idea to have one linux in an all windows team if you need to be able to swap computers. Or maybe you need a way of sharing work / info / ... without exchanging computers.
That's a whole other discussion, I know, but it might actually be the underlying poblem.

like bodhi.zazen said: the passwordless keyring is a minor issue compared to your insecure computing habits, but ok, maybe a password option might be a good idea. Should you / anyone using your account be allowed to reset that master pass ?

---

### Post by hyper_ch on 2009-02-26
you can just copy over your settings for that tool to the other user account (and chown accordingly then).

That's the good thing about having config files.

---

### Post by hyapadi on 2009-03-17
I have voiced my opinion about this in Firefox forum and yet it receive same reactions. I haven't though talk about keyrings that have similar behaviour which is "revealing password in cleartext"

They told me that my insecure computing habits that should be fixed and I should put and entered master passwords everytime I opened Firefox.

I agree with that both Firefox and keyrings will be very secure if master password were set and asked about. However us, the desktop users desire some balance between convenience and security, unlike servers or other highly secure setups that put security at the top.

What we want is that there should be an option to put password-required-access to reveal the password in cleartext, instead of locking everything.

I'm sorry if I use Firefox as the example since they behave similarly in making password in cleartext accessible easily through GUI.

I think this is an important matter, especially for people who recently or will switch to open source application from windows, since this can literally make the box less insecure than windows. * imagine people can look directly at the password. Yeah..insecure computing habits, but still many people will do it like what they did in windows. Isn't it? "

I love opensouce community for their hardwork and free as beer software. I shouldn't have asking( or complaining ? LOL ) for things that I use freely. But I think small matter like this will determined the future of opensource and linux desktop in the sense making linux more friendly and secure for everyone.

---

### Post by bodhi.zazen on 2009-03-17
> **hyapadi said:**
> I have voiced my opinion about this in Firefox forum and yet it receive same reactions. I haven't though talk about keyrings that have similar behaviour which is "revealing password in cleartext"

They told me that my insecure computing habits that should be fixed and I should put and entered master passwords everytime I opened Firefox.

I agree with that both Firefox and keyrings will be very secure if master password were set and asked about. However us, the desktop users desire some balance between convenience and security, unlike servers or other highly secure setups that put security at the top.

What we want is that there should be an option to put password-required-access to reveal the password in cleartext, instead of locking everything.

I'm sorry if I use Firefox as the example since they behave similarly in making password in cleartext accessible easily through GUI.

I think this is an important matter, especially for people who recently or will switch to open source application from windows, since this can literally make the box less insecure than windows. * imagine people can look directly at the password. Yeah..insecure computing habits, but still many people will do it like what they did in windows. Isn't it? "

I love opensouce community for their hardwork and free as beer software. I shouldn't have asking( or complaining ? LOL ) for things that I use freely. But I think small matter like this will determined the future of opensource and linux desktop in the sense making linux more friendly and secure for everyone.

No real need for you to rant like this, you are making false generalizations.

First, if you read my post I suggested this was a problem and that is should be reported as a bug.

Second, you need to enter a password in Firefox to view stored passwords in clear text.

---

### Post by Seanman on 2009-03-17
I whole-heartedly agree with the original poster.

The fact that Seahorse simply allows you to view passwords is tremendously insecure.

The main reason is that 90% of users don't even know that it's possible.  I've been an avid Ubuntu user since Feisty and just found out about this functionality three months ago -- and totally by accident.  I chanced on to it when I needed to change my default keyring password.

The second reason is that people constantly step away from their computers for a moment or two to get coffee and forget to lock it.  Sure, that's the user's fault.  But the worst thing that should happen is that the user's email gets compromised.  

For someone to easily get the password to an Exchange server, for example, and thus domain credentials -- is terrifying.  

I'm now extremely paranoid about leaving my computer unlocked even after uninstalling Seahorse.  (Are there other programs that do this same thing?  I just don't know.)  I'm not sure how to design it better.  And I do understand that people will be annoyed at having to enter their password more than once.  Regardless, the current design is flawed.

This has already been reported as a "feature request".  I checked when I first found the functionality.  I personally think that it's a show-stopper.

---

### Post by hyapadi on 2009-03-17
@all
I have received infraction for this post. I personally apologized for this.

@seanman
can I have the link for the "feature request" about this?

Thanks

---

### Post by bodhi.zazen on 2009-03-17
> **hyapadi said:**
> @all
I have received infraction for this post. I personally apologized for this.

Thank you hyapadi, it took a lot of courage to post that and shows a lot of maturity.

In recognition of your actions, I am going to reverse the infraction. Your post clearly shows you understand my message.

---

### Post by Seanman on 2009-03-18
@hyapadi:  

Bug #189774 reported by  Rocko  on 2008-02-06 
"seahorse shows passwords without verification"

---

### Post by aaronrus on 2011-05-17
I'm having a similar issue. We are not allowed to give our users the WIFI Code. We set it up for them and they should not be able to access it but the key ring allows them to see the code in plain text. and with out access to the keyring they cant access the WIFI. Its Simply a deal breaker for using Ubuntu in our environment.

---

### Post by doas777 on 2011-05-17
nothing to see here. sorry for the necromancy.

---

