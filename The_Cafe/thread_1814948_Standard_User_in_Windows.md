---
title: "Standard User in Windows"
date: 2011-07-30
forum: The Cafe
---

### Post by mamamia88 on 2011-07-30
In windows I always heard that you should create 2 user accounts 1 admin and one standard user.   But, when I used a standard user account some applications refused to work correctly.   My question is what good does a standard user account really do besides make you think twice before installing an app or making changes to your computer?   I look at it this way.   All a standard user account does it add 1 extra layer between you and the guy with the gun but if you are stupid enough to give the guy with the gun the key to your house than it doesn't matter how good the key is it won't protect you.  I scan all my exes for programs I've never tried through malwarebytes and mse before I even run them, and I run my browser in a sandbox.    Is there any real reason to run as a standard user and not admin?

---

### Post by DangerOnTheRanger on 2011-07-30
Well, you prevent yourself from accidentally shooting yourself in the foot from time to time. :)

---

### Post by haqking on 2011-07-30
> **mamamia88 said:**
> In windows I always heard that you should create 2 user accounts 1 admin and one standard user.   But, when I used a standard user account some applications refused to work correctly.   My question is what good does a standard user account really do besides make you think twice before installing an app or making changes to your computer?   I look at it this way.   All a standard user account does it add 1 extra layer between you and the guy with the gun but if you are stupid enough to give the guy with the gun the key to your house than it doesn't matter how good the key is it won't protect you.  I scan all my exes for programs I've never tried through malwarebytes and mse before I even run them, and I run my browser in a sandbox.    Is there any real reason to run as a standard user and not admin?


yes...if you run everything as admin then so can malware and illegal or malicious processes and leave executables and possible backdoors with eleveated privelege.

windows or linux.

its that simple.

it is a concept known as least privelege and should always be adhered to keep inline with the security models that exist to help prevent such things from happening.

unless of course you are a new linux user and new to the forum and want to disable all security mechanisms to make linux like windows and thus give reason to post here later with lots of support questions relating to an enabled and used root account ;-)

---

### Post by mamamia88 on 2011-07-30
> **haqking said:**
> yes...if you run everything as admin then so can malware and illegal or malicious processes and leave executables and possible backdoors with eleveated privelege.

windows or linux.

its that simple.

it is a concept known as least privelege and should always be adhered to keep inline with the security models that exist to help prevent such things from happening.

unless of course you are a new linux user and new to the forum and want to disable all security mechanisms to make linux like windows and thus give reason to post here later with lots of support questions relating to an enabled and used root account ;-)
i understand you.  but how does it prevent someone who is hellbent on shooting themselves in the foot from shooting themselves in the foot?   just curious.   i am using windows on my netbook now and want to keep it as safe as possible.

---

### Post by haqking on 2011-07-30
> **mamamia88 said:**
> i understand you.  but how does it prevent someone who is hellbent on shooting themselves in the foot from shooting themselves in the foot?   just curious.   i am using windows on my netbook now and want to keep it as safe as possible.

it is a preventative measure not an assurance.

If someone is hellbent on it then it will probably happen.

Security is a process not a product, it is a collection of mechanisms and user vigilence and common sense that helps contribute towards the confidentiality, integrity and availablity of a system.

there are many facets involved to aid security, least privelege is one of them.

but if you remove least privelege then you are just creating unnecessary potential for headaches.

you dont have to check your oil and water in your car every week but it helps if you do, and even if you do that does not prevent the car from overheating if you know what i mean

---

### Post by aysiu on 2011-07-30
> **mamamia88 said:**
> In windows I always heard that you should create 2 user accounts 1 admin and one standard user.   But, when I used a standard user account some applications refused to work correctly. Yes, this is annoying, but it's really because Windows defaults to making the first account an administrator account that people started making applications with the assumption that you are running them as admin. Unfortunate, but such is the Windows eco-system. > My question is what good does a standard user account really do besides make you think twice before installing an app or making changes to your computer?   I look at it this way.   All a standard user account does it add 1 extra layer between you and the guy with the gun but if you are stupid enough to give the guy with the gun the key to your house than it doesn't matter how good the key is it won't protect you. The difference is that the standard user account doesn't have the key to the house. The standard user is locked in a bedroom and has no key even outside the bedroom. So, yes, the thief can get into the bedroom and steal everything in the bedroom but not take over the entire house. > I scan all my exes for programs I've never tried through malwarebytes and mse before I even run them, and I run my browser in a sandbox.    Is there any real reason to run as a standard user and not admin? It's more secure. That said, if your programs don't run except as admin, then you should run as admin. You can set up UAC to prompt for a password for modifying system files. You can also use the NoScript extension in Firefox, even though you already say you run your browser in a sandbox.

I think if you're super-paranoid, you should make a CloneZilla back-up of your installation, and then regular back-ups of your personal files to an external hard drive.

---

### Post by mamamia88 on 2011-07-30
> **aysiu said:**
> Yes, this is annoying, but it's really because Windows defaults to making the first account an administrator account that people started making applications with the assumption that you are running them as admin. Unfortunate, but such is the Windows eco-system.  The difference is that the standard user account doesn't have the key to the house. The standard user is locked in a bedroom and has no key even outside the bedroom. So, yes, the thief can get into the bedroom and steal everything in the bedroom but not take over the entire house.  It's more secure. That said, if your programs don't run except as admin, then you should run as admin. You can set up UAC to prompt for a password for modifying system files. You can also use the NoScript extension in Firefox, even though you already say you run your browser in a sandbox.

I think if you're super-paranoid, you should make a CloneZilla back-up of your installation, and then regular back-ups of your personal files to an external hard drive.

except in this case the users are one in the same and all it takes is entering the admin password to grant admin rights.

---

### Post by aysiu on 2011-07-30
> **mamamia88 said:**
> except in this case the users are one in the same and all it takes is entering the admin password to grant admin rights.
Then that's not a standard user account. That's an admin account.

A standard user account in Windows *cannot* escalate to admin privileges without authenticating as another user.

---

### Post by mamamia88 on 2011-07-30
> **aysiu said:**
> Then that's not a standard user account. That's an admin account.

A standard user account in Windows *cannot* escalate to admin privileges without authenticating as another user.

the way i have it setup as that i log in as a standard user and when a process needs admin privilidges it asks for my admin password.  what i meant was that the users are the same person.

---

### Post by haqking on 2011-07-30
> **mamamia88 said:**
> the way i have it setup as that i log in as a standard user and when a process needs admin privilidges it asks for my admin password.  what i meant was that the users are the same person.

are you talking about windows or linux now ?

in windows if it requires admin priveledge then you supply it with admin credntials.

in linux you sudo to that user.

either way it is least priveledge as it requires authentication either way.

are you referring to UAC in windows ?

---

### Post by mamamia88 on 2011-07-30
> **haqking said:**
> are you talking about windows or linux now ?

in windows if it requires admin priveledge then you supply it with admin credntials.

in linux you sudo to that user.

either way it is least priveledge as it requires authentication either way.

are you referring to UAC in windows ?
i'm talking about windows and no i'm not talking about uac. what i'm saying is that you are trying to protect yourself from yourself

---

### Post by aysiu on 2011-07-30
> **mamamia88 said:**
> the way i have it setup as that i log in as a standard user and when a process needs admin privilidges it asks for my admin password.  what i meant was that the users are the same person. So you have a separate admin account you authenticate as? That's about as secure as you'll practically get. Yes, if you were dumb and authenticated for malware, then the malware would have control over your entire installation.

---

### Post by mamamia88 on 2011-07-30
> **aysiu said:**
> So you have a separate admin account you authenticate as? That's about as secure as you'll practically get. Yes, if you were dumb and authenticated for malware, then the malware would have control over your entire installation.

yep i have 2 accounts 1 admin and 1 standard user.  i login as standard user and when something needs admin i get a popup asking for admin password.

---

### Post by haqking on 2011-07-30
> **mamamia88 said:**
> i'm talking about windows and no i'm not talking about uac. what i'm saying is that you are trying to protect yourself from yourself

if you are talking about windows then must be an admin user as you said you enter the same credentials.

and it is not just from yourself, like said already it is from processes and malware etc.

and of course nayone is a dnager to themselves.

the fact is dont run everyhing with elevated privelege, only what needs it.

---

### Post by haqking on 2011-07-30
> **mamamia88 said:**
> yep i have 2 accounts 1 admin and 1 standard user.  i login as standard user and when something needs admin i get a popup asking for admin password.


ok then in which case that is how it should be.

and if you want to trash your system you could do easily, as stated before alot of it is common sense

---

### Post by Paqman on 2011-07-30
> **mamamia88 said:**
> what i'm saying is that you are trying to protect yourself from yourself

Well, you would be, if you were the only person or agent using the machine. But if the machine is connected to the interent, that's not the case. Every system needs to behave like a multi-user system once it's connected to the internet.

---

### Post by el_koraco on 2011-07-30
> **mamamia88 said:**
> yep i have 2 accounts 1 admin and 1 standard user.  i login as standard user and when something needs admin i get a popup asking for admin password.

It's the same in Linux, only the UAC privilege separation mechanism is more advanced than sudo or gksudo. The days of running IE6 with manic active controls as admin and without privilege separation of any kind are long gone. Now, the fact that the malware writers have had 20 years experience with designing nasty crap for Windows shows when you run it, but that's another thing :D

---

### Post by aysiu on 2011-07-30
To go further with your earlier analogy, you would be stupid to hand your key over to someone, but it would be even more stupid to just leave your house unlocked (why even have a key, then?).

A key doesn't mean nothing bad can ever happen to you, but if you don't want to be robbed it's better to have a key and to leave your house locked than to not have a key and leave your house unlocked.

---

### Post by haqking on 2011-07-30
> **aysiu said:**
> To go further with your earlier analogy, you would be stupid to hand your key over to someone, but it would be even more stupid to just leave your house unlocked (why even have a key, then?).

A key doesn't mean nothing bad can ever happen to you, but if you don't want to be robbed it's better to have a key and to leave your house locked than to not have a key and leave your house unlocked.

+1

i was just about to type pretty much the same thing and you beat me to it.

You the house owner is the admin user, if you go out and lock everthing people can still break in but you did all you could.  iF you lend someone your key that you trust (you are elevating privelege to a user or process) if you lose your key or it gets stolen from you then that is something else (cracked).

do what you can to minimise chances of people entering your house, least privelege on your system.

---

