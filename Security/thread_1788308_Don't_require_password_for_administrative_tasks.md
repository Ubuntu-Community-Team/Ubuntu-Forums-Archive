---
title: "Don't require password for administrative tasks"
date: 2011-06-22
forum: Security
---

### Post by brouiller on 2011-06-22
The title says it all. Is there a way to just click ok to administrative tasks instead of having to enter my password every time? Sort of like Windows 7's UAC. I'm using ubuntu 10.04 LTS. I don't want to log in as root. Thanks for your help!

---

### Post by haqking on 2011-06-22
> **brouiller said:**
> The title says it all. Is there a way to just click ok to administrative tasks instead of having to enter my password every time? Sort of like Windows 7's UAC. I don't want to log in as root. Thanks for your help!

you cant login as root because root is disbaled by default and the Ubuntu security model advises againt enabling it so hopefully you havent.

You use sudo or gksudo to give yoru account temporary root permissions.

The reason it asks you for your password everytime is to prevent services and possible malware and the like from being able to utilise root permission, if your password and hence root permission was stored everytime your system would be prone to catastrophe ;-)

---

### Post by brouiller on 2011-06-22
Thanks for your reply. I haven't logged in as root, nor do I intend on it. I was just wondering if there's a quicker way to give tasks administrative permissions. I understand why it asks for a password, but clicking ok would provide a similar level of protection against any malware because it would still require user input. I'm not asking for it to store root permissions indefinitely, I'm asking if I can just click ok to give permissions instead of typing my 16 character password every time.

---

### Post by haqking on 2011-06-22
> **brouiller said:**
> Thanks for your reply. I haven't logged in as root, nor do I intend on it. I was just wondering if there's a quicker way to give tasks administrative permissions. I understand why it asks for a password, but clicking ok would provide a similar level of protection against any malware because it would still require user input. I'm not asking for it to store root permissions indefinitely, I'm asking if I can just click ok to give permissions instead of typing my 16 character password every time.

what is quicker than typing sudo <app> then password

you could only click OK to give it permission if the password was stored and hence insecure.

if you want to be able to just click things without security then  there are many flavours of OS to suit ;-)

---

### Post by brouiller on 2011-06-22
Opening Update Manager, clicking Check, clicking Install Updates, then clicking Ok (instead of entering my password) is much quicker than opening Terminal, typing sudo apt-getupdate && sudo apt-get upgrade, then ****************. 

I know there are other OS's out there, but I like ubuntu. I just wanted to know if it can do what I've asked. You're being pedantic and unhelpful. If you don't know of an answer to my question, please feel free to ignore it.

---

### Post by haqking on 2011-06-22
> **brouiller said:**
> Thanks for your reply. I haven't logged in as root, nor do I intend on it. I was just wondering if there's a quicker way to give tasks administrative permissions. I understand why it asks for a password, but clicking ok would provide a similar level of protection against any malware because it would still require user input. I'm not asking for it to store root permissions indefinitely, I'm asking if I can just click ok to give permissions instead of typing my 16 character password every time.


OK well then im confused.  You are asking if you can just click OK instead of providing a password which would mean the button OK would authorise root permission which would mean any person or service could do anything they want.

sure it would be easier but no security.  For clicking OK to do that OK would need to have the password to invoke temporary root permission stored and as you said yourself you are not asking it to store your password.

I am not being pedantic, i am telling you it is insecure and does not adhere to the security model within Ubuntu and for good reason.

---

### Post by haqking on 2011-06-22
> **brouiller said:**
> Opening Update Manager, clicking Check, clicking Install Updates, then clicking Ok (instead of entering my password) is much quicker than opening Terminal, typing sudo apt-getupdate && sudo apt-get upgrade, then ****************. 

I know there are other OS's out there, but I like ubuntu. I just wanted to know if it can do what I've asked. You're being pedantic and unhelpful. If you don't know of an answer to my question, please feel free to ignore it.


Well my apologies for not giving you what you require, i will hand over the baton to the next more HELPFUL member ;-)

---

### Post by brouiller on 2011-06-22
> **haqking said:**
> Well my apologies for not giving you what you require, i will hand over the baton to the next more HELPFUL member ;-)
Thank you.

---

### Post by haqking on 2011-06-22
> **brouiller said:**
> Thank you.

and before i am preempted.  In DIRECT answer to your question then yes it is possible but the forum guidelines do not allow the posting of such information as it does not adhere to the canonical security model.

however i will PM you about how to do what is totally unrecommended and generally a VERY BAD IDEA ;-)

---

### Post by Lars Noodén on 2011-06-22
Look into customizing /etc/sudoers and make careful use of NOPASSWD

---

### Post by brouiller on 2011-06-22
I understand how to get around providing authentication altogether. Again, that's not what I'm asking about. I still want it to prompt me to give permission, but I want to be able to click through the permission dialog instead of entering a password. Security concerns aside, I'm wondering if this has been implemented or if it is possible.

---

### Post by haqking on 2011-06-22
> **brouiller said:**
> I understand how to get around providing authentication altogether. Again, that's not what I'm asking about. I still want it to prompt me to give permission, but I want to be able to click through the permission dialog instead of entering a password. Security concerns aside, I'm wondering if this has been implemented or if it is possible.

I PM'd you a response, like i said good luck with your responses i would be interested to see what others have to say on it.

and just clicking through OK is getting around authentication altogether ;-)

Hope you find your answer ;-)

---

### Post by brouiller on 2011-06-22
Your response was to use Windows 95. You're being pedantic and unhelpful again.

---

### Post by haqking on 2011-06-22
> **brouiller said:**
> Your response was to use Windows 95. You're being pedantic and unhelpful again.

I never said use windows 95, i said if you want an answer to if you can just click OK without authentication from the security model then yes its called Windows 95.

It is not pedantic to point out your contradictions, you said you dont want to get around authentication completely you just want to click through without providing the credentials to authorise or authenticate, that is a contradiction.

My last response, perhaps someone else can provide more help. i am done

---

### Post by cariboo on 2011-06-22
You do realize that the a password makes it harder for someone to take over your system, not to make it harder on you to administrate the system.

---

### Post by haqking on 2011-06-22
> **cariboo907 said:**
> You do realize that the a password makes it harder for someone to take over your system, not to make it harder on you to administrate the system.

You can take the baton, im tired out ;-)

---

### Post by aysiu on 2011-06-22
OP, I understand what you're asking, as I use Windows 7 at work. Unfortunately, I think short of reprogramming significant parts of Ubuntu (I don't know enough about the guts to know if it'd be GTK, Gnome, or something else), you won't get this feature you're asking for.

Ubuntu's built to use password authentication. It isn't built to have an "OK" click.

---

### Post by brouiller on 2011-06-22
Thanks aysiu, this is the response I was looking for.

---

### Post by haqking on 2011-06-22
> **aysiu said:**
> OP, I understand what you're asking, as I use Windows 7 at work. Unfortunately, I think short of reprogramming significant parts of Ubuntu (I don't know enough about the guts to know if it'd be GTK, Gnome, or something else), you won't get this feature you're asking for.

Ubuntu's built to use password authentication. It isn't built to have an "OK" click.

out of interest ?

Even if you reprogram GTK, Gnome etc to allow it do authenticate administrative tasks without supplying credentials then that would mean storing those credentials would it not ? which completely destroys the security model of *nix.

Wouldnt the security model need to be addressed which would then take away one of the reason we choose to use *nix ?

One of the reason we use it is because it requires this.

Which is what i said although i didnt actually just say NO like you did ;-) I was refraining from NO to discuss the security model itself and reasons for existence, perhaps i sounded pedantic, if i did then my apologies. i was just trying to give as much information as possible

---

### Post by brouiller on 2011-06-22
It may be one of the ways *you* use it. People have different reasons for choosing it. I like Ubuntu because it's free and there's a large (usually) helpful community built around it. I honestly don't care that much about security and that's ok too.

---

### Post by haqking on 2011-06-22
> **brouiller said:**
> It may be one of the ways *you* use it. People have different reasons for choosing it. I like Ubuntu because it's free and there's a large (usually) helpful community built around it. I honestly don't care that much about security and that's ok too.

fair enough.

peace

---

### Post by Ezlivin on 2011-06-24
I'm using a minimal 10.04 LTS iso with Openbox that I built up slowly, it doesn't include a login manager like GDM so it boots into a TTY1 login prompt. When I was building the system I set a new root password as part of the initial security. Just out of sheer interest I rebooted and confirmed I could login as root. Without going into all the (serious) reasons why (this is bad security) it would provide a password free Ubuntu environment if security really is an afterthought.

---

### Post by haqking on 2011-06-24
> **Ezlivin said:**
> I'm using a minimal 10.04 LTS iso with Openbox that I built up slowly, it doesn't include a login manager like GDM so it boots into a TTY1 login prompt. When I was building the system I set a new root password as part of the initial security. Just out of sheer interest I rebooted and confirmed I could login as root. Without going into all the (serious) reasons why (this is bad security) it would provide a password free Ubuntu environment if security really is an afterthought.

if you login as root of course it will be password free because you are root, the point is this doesnt need to happen and is a bad idea, you should never login as root and leave it disabled and use sudo or gksudo.

If you are at tty then there is no click through option anyways as it is CLI.

everyone know you can enable the root account and login and do everything administratively without prompt, thats the point....its not a good idea to do it ;-)

---

### Post by snowpine on 2011-06-24
> **Ezlivin said:**
> I'm using a minimal 10.04 LTS iso with Openbox that I built up slowly, it doesn't include a login manager like GDM so it boots into a TTY1 login prompt. When I was building the system I set a new root password as part of the initial security. Just out of sheer interest I rebooted and confirmed I could login as root. Without going into all the (serious) reasons why (this is bad security) it would provide a password free Ubuntu environment if security really is an afterthought.

It is not "bad" to log in to a terminal as root. There are millions of mission-critical servers out there in the world happily running non-Ubuntu distros where root account is enabled. Root terminal is a powerful and widely accepted technique for system administration.

That being said, it is Ubuntu's policy, for a variety of reasons, to disable root login and encourage users to use "sudo" instead ("sudo -i" for a root terminal).

And it is *definitely* never recommended to log in to the GUI as root! (i.e. "startx" from a root terminal) If you do so, you give every application and process, from your web browser to the little clock in the corner, full and total control to change or delete anything and everything on your system! Better to do your admin tasks from the terminal and/or GUI tools (like Software Center or Update Manager) that are authenticated using "gksu".

---

### Post by Ezlivin on 2011-06-24
> **haqking said:**
> if you login as root of course it will be password free because you are root, the point is this doesnt need to happen and is a bad idea, you should never login as root and leave it disabled and use sudo or gksudo.

I know this I've used Linux for years! Clearly OP is not interested in the security so I didn't get into the very valid reasons why this is bad for general use, but I appreciate the well intentioned warning.

> **haqking said:**
>  If you are at tty then there is no click through option anyways as it is CLI. 

Yeah but the point I'm making is Ubuntu GDM does not allow root and then password. I don't believe you can log in as root unless your at run level 3. Then you can use startx .... As before it's just a solution as the OP seems to dislike the password authentication. I like you wouldn't recommend it!

> **haqking said:**
>  everyone know you can enable the root account and login and do everything administratively without prompt, thats the point....its not a good idea to do it ;-)

RE above -  but OP is not worried about security and this removes the password issue.

---

### Post by Ezlivin on 2011-06-24
> **snowpine said:**
> It is not "bad" to log in to a terminal as root. There are millions of mission-critical servers out there in the world happily running non-Ubuntu distros where root account is enabled. Root terminal is a powerful and widely accepted technique for system administration.

That being said, it is Ubuntu's policy, for a variety of reasons, to disable root login and encourage users to use "sudo" instead ("sudo -i" for a root terminal).

And it is *definitely* never recommended to log in to the GUI as root! (i.e. "startx" from a root terminal) If you do so, you give every application and process, from your web browser to the little clock in the corner, full and total control to change or delete anything and everything on your system! Better to do your admin tasks from the terminal and/or GUI tools (like Software Center or Update Manager) that are authenticated using "gksu".

I totally agree and appreciate yours and haqking's warnings of best practice. I know with the low post I could seem to be a noob. The only reason for my post was to provide a method for OP to use Ubuntu without password authentication. Even mulling over visudo I can't think of a way to disable any form of authentication other than logging in as root.

Having studied and used quite a few Linux system over the years I'd never want to run as root for general practice. This might be what OP is looking for though so I thought I'd suggest a method to achieve it.

---

### Post by haqking on 2011-06-24
> **Ezlivin said:**
> I totally agree and appreciate yours and haqking's warnings of best practice. I know with the low post I could seem to be a noob. The only reason for my post was to provide a method for OP to use Ubuntu without password authentication. Even mulling over visudo I can't think of a way to disable any form of authentication other than logging in as root.

Having studied and used quite a few Linux system over the years I'd never want to run as root for general practice. This might be what OP is looking for though so I thought I'd suggest a method to achieve it.

yeah i understand what you are saying.  I also didnt mean necessarily it was "bad", it is just that after a PM reprimand by moderators the other idea about adhering to the ubuntu security model i guess i was taking it too far ;-)

i meant it is not canonicals best practice and they do not recommend it.

But yes for the OP you are right, though the OP was referring to GUI specifically as he stated click through and click ok etc.

anyways i think this thread has resolved itself now ;-)

peace

---

### Post by Ezlivin on 2011-06-24
> **haqking said:**
> yeah i understand what you are saying.  I also didnt mean necessarily it was "bad", it is just that after a PM reprimand by moderators the other idea about adhering to the ubuntu security model i guess i was taking it too far ;-)

i meant it is not canonicals best practice and they do not recommend it.

But yes for the OP you are right, though the OP was referring to GUI specifically as he stated click through and click ok etc.

anyways i think this thread has resolved itself now ;-)

peace

I agree about the thread resolving itself! I think going by your alias perhaps we are both kindred spirits in achieving hard to find solutions...

I think the method I suggested is what OP is looking for but I'll take what you said about the reprimand cautiously and try to take a more globally conscious view to my suggestions in the future.

Win 95... I really did laugh out loud!

---

### Post by haqking on 2011-06-24
> **Ezlivin said:**
> I agree about the thread resolving itself! I think going by your alias perhaps we are both kindred spirits in achieving hard to find solutions...

I think the method I suggested is what OP is looking for but I'll take what you said about the reprimand cautiously and try to take a more globally conscious view to my suggestions in the future.

Win 95... I really did laugh out loud!

yeah i certainly wasnt being pedantic when i said windows 95, i meant it humorously for sure but to demonstrate a point that was all...LOL

but yeah there is a reason we are on a Ubuntu Forum, for Ubuntu and Ubuntu has guidelines and so we adhere to them for the most part especially when it refers to support and the fact that the forum guidelines and stickys give us plenty of warning which is fair enough.

I just need to be careful how i word things in future so not to offend anyone or say something out of place, i am enjoying the community and here to learn and to help where i can ;-)

as for my alias, it is also an equestrian activity ;-)

---

### Post by Ezlivin on 2011-06-24
> **haqking said:**
> yeah i certainly wasnt being pedantic when i said windows 95, i meant it humorously for sure but to demonstrate a point that was all...LOL

but yeah there is a reason we are on a Ubuntu Forum, for Ubuntu and Ubuntu has guidelines and so we adhere to them for the most part especially when it refers to support and the fact that the forum guidelines and stickys give us plenty of warning which is fair enough.

I just need to be careful how i word things in future so not to offend anyone or say something out of place, i am enjoying the community and here to learn and to help where i can ;-)

as for my alias, it is also an equestrian activity ;-)

There really should be a "high five" button! Myself and I'm sure others can tell you had the best (and humorous) intentions. I think it's impossible to understand why OP would challenge the entire Unix model in favour of UAC. Never mind... see ya round.

---

### Post by Thewhistlingwind on 2011-06-24
Make the sudo timeout like a day long, then drop privileges when your done.

Note, like enabling root and other bad practices, while not as bad, this is terrible for maintaining the *nix security model, and I don't recommend doing it.

---

### Post by Veazer on 2011-08-10
EDIT: Apologies for the thread revival, I originally thought the discussion was more current. [Donning my fireproof suit in anticipation of flames....]

I'm in the same situation as the OP. Under most working conditions, I greatly agree with the standard model requiring password authentication for elevation. Soon though i'm going to be in a rather hostile environment with a high potential of surveillance if i'm working in restaurants, cafe's, etc. Essentially anywhere in public. I'd much rather use my password to login discreetly, then use a much simpler authentication, whether it be click (gasp!!!) or a simple 4 digit pin. My home folder uses encryption and using a short password would not but safe, but neither is repeatedly typing in the long password in public places again and again.

> **haqking said:**
> ... if you can just click OK instead of providing a password which would mean the button OK would authorise root permission which **would mean any person or service could do anything they want**. sure it would be easier but no security. 

How? I don't allow others to use this machine while I'm logged in, period. If I need to step away then i either lock it or shutdown. There wouldn't be a situation where others could do what they want.

As for services doing whatever they want, I don't see how this would occur either, but feel free to explain as I don't claim to be an expert. If I'm in the middle of doing routine tasks and suddenly a UAC-ish prompt popped up, or gksu for that matter, I'd dismiss it. If I or the OP were logged in as superuser, there would be no prompting and it would just go ahead and do it and that's not what we want. There *is* some degree of added security of requiring the user to authorize potentially harmful changes, even if it is as simple as a click through.

I'd love a compromise actually. I like the option, i stress *option*, of a dual authentication system in which a strong password could be used for login and encryption of the home folder but something simpler like a 4 digit pin could be used during the session. It wouldn't matter whether or not people saw me enter it, once i'm logged out it's worthless to them.

---

### Post by Chayak on 2011-08-11
Again it falls back to the dancing bunny theory of security.

You can warn users all day long about security and the dangers of dancing bunnies with big pointy teeth.  Users will still go out to see the dancing bunny unless you physically prevent them and then they'll whine about restrictions and do their best to find a way around them.

The default of not letting users log in as root and making them type in their password to perform admin functions is protecting the user from *themselves*.

Ubuntu is designed around accessibility for a broad audience also known as general users.  Anyone who has administrated a large network will tell you how stupid users can be.  Anyone in the security field will tell you that the biggest threat to network security is user stupidity.

If you find the use of the word 'stupid' offensive here's the world tiniest violin. --> <-- it's *really* tiny so you have to look very hard to see it.

Ignorant users are people who just don't know any better.  If you find *that* offensive refer to the tiny violin and open a dictionary as it's appropriately used.

Stupid users are *theoretical* individuals who have been trained, warned, and even signed things acknowledging those warnings and training sessions.  Then they *still* do it.

*Note: **Users** are under the definition of a meta group and does not indicate any specific individual, race, nationality, religion, sexual orientation, belief system, planet of origin, universal origin, mmorpg gamer, clowns, native culture, windows user, os x user, mimes, world leader, environmental activist, Linux user, carbon based lifeform, or silicon based life form.  If you've included yourself in any classification of such it is categorized as self profiling and is not the responsibility or fault of the author.  If you have self profiled and have offended yourself the author finds this offensive and suggests sensitivity training.*

---

### Post by Veazer on 2011-08-12
> **Chayak said:**
> Again it falls back to the dancing bunny theory of security.

You can warn users all day long about security and the dangers of dancing bunnies with big pointy teeth.  Users will still go out to see the dancing bunny unless you physically prevent them and then they'll whine about restrictions and do their best to find a way around them.

The default of not letting users log in as root and making them type in their password to perform admin functions is protecting the user from *themselves*.

Ubuntu is designed around accessibility for a broad audience also known as general users.  Anyone who has administrated a large network will tell you how stupid users can be.  Anyone in the security field will tell you that the biggest threat to network security is user stupidity.

If you find the use of the word 'stupid' offensive here's the world tiniest violin. --> <-- it's *really* tiny so you have to look very hard to see it.

Ignorant users are people who just don't know any better.  If you find *that* offensive refer to the tiny violin and open a dictionary as it's appropriately used.

Stupid users are *theoretical* individuals who have been trained, warned, and even signed things acknowledging those warnings and training sessions.  Then they *still* do it.

*Note: **Users** are under the definition of a meta group and does not indicate any specific individual, race, nationality, religion, sexual orientation, belief system, planet of origin, universal origin, mmorpg gamer, clowns, native culture, windows user, os x user, mimes, world leader, environmental activist, Linux user, carbon based lifeform, or silicon based life form.  If you've included yourself in any classification of such it is categorized as self profiling and is not the responsibility or fault of the author.  If you have self profiled and have offended yourself the author finds this offensive and suggests sensitivity training.*

Have you even read my post??? You totally and completely failed to argue a valid point of why my suggestion is less secure. I have pointed out that my login password is lengthy and complex, more than adequate for protecting my account and encrypted data against brute force passwords attacks.

I've also pointed out that I'm going to be working in an environment where repeatedly entering my login credentials for sudo elevation poses a security threat because there is a reasonable chance of having a camera pointed at me. This is why I believe a second shorter password system for elevation makes sense, even if someone visually recorded those keystrokes they can't do anything about it or use them later to access my system. Why is this a difficult concept for you?

If you have actual points or counter arguments to make, i'm listening. If you want to make actual suggestion for my situation , i'm listening. If you want to ramble on with insults while sporting less charisma than  ["comic book guy"]("http://en.wikipedia.org/wiki/Comic_Book_Guy"), find another thread to troll.

---

### Post by Chayak on 2011-08-12
> **Veazer said:**
> Have you even read my post??? You totally and completely failed to argue a valid point of why my suggestion is less secure. I have pointed out that my login password is lengthy and complex, more than adequate for protecting my account and encrypted data against brute force passwords attacks.

I've also pointed out that I'm going to be working in an environment where repeatedly entering my login credentials for sudo elevation poses a security threat because there is a reasonable chance of having a camera pointed at me. This is why I believe a second shorter password system for elevation makes sense, even if someone visually recorded those keystrokes they can't do anything about it or use them later to access my system. Why is this a difficult concept for you?

If you have actual points or counter arguments to make, i'm listening. If you want to make actual suggestion for my situation , i'm listening. If you want to ramble on with insults while sporting less charisma than  ["comic book guy"]("http://en.wikipedia.org/wiki/Comic_Book_Guy"), find another thread to troll.

The problem is with your environment, not the system.  If you *really* want short passwords while you're working, and assuming you don't do something stupid like allowing remote login while you're doing it, modify the password rules then script a password change when you log in and log off.

Though seriously, apologies, the threat caught me after a meeting with a bunch of high ranking military officers who were self assessed experts on *cyber* security and their actual collective understanding would easily fit on a post-it note.  My snarky sarcasm venom was overflowing.

---

### Post by cariboo on 2011-08-12
I have to ask what type of work you do that you need elevated permissions fairly often, especially in a very insecure environment.

---

### Post by aysiu on 2011-08-12
> **cariboo907 said:**
> I have to ask what type of work you do that you need elevated permissions fairly often, especially in a very insecure environment.
If you're constantly adding and removing users, I think you can just unlock Users and Groups and keep it open. Things like Software Center and Update Manager will stay unlocked for 15 minutes after authentication.

And dragging and dropping files you can solve with a ```
gksudo nautilus
``` keyboard shortcut.

I don't see why anyone would be in a situation in which there is constant elevating of privileges that needs password authentication.

---

### Post by nitrogensixteen on 2011-08-13
Can't you just replace the pam module?

---

