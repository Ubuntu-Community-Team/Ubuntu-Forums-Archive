---
title: "ubuntu security"
date: 2006-07-22
forum: Server Platforms
---

### Post by MaximB on 2006-07-22
from the last security thread I learnt that a virus can delete your home folder
so I thought of a way to defend it.
1.what if your home folder would be "read only"
I mean the folder only , not the folders and files within that folder
2.and what if all the critical files would be read only and if you will need
 to write somting it would premote you for a password and then make thouse files read/write until you finish/close them ?

what do you think about it ?

---

### Post by imagine on 2006-07-22
You can always change the access rights or the owner of the files in your home folder. But since the applications you run store and read their settings in your home folder, that would mean you have to type in a password for basically everything you want to do. This would be annoying and I guess most users would get rid of that "protection" after five minutes. There were some images floating around the web how a user had to go through seven different popups just to delete a file from some folder. I don't think anybody wants something like that.
The only way to prevent a script from deleting your home folder is not to let such a script on your computer in the first place.

---

### Post by bruce89 on 2006-07-22
Where did you hear about this virus?

---

### Post by MaximB on 2006-07-22
you didn't get me...
I meant your "home folder" would be read only
not the content
and the thing I've said about the critical files

---

### Post by kabus on 2006-07-22
> **MAXDDARK said:**
> 
1.what if your home folder would be "read only"
I mean the folder only , not the folders and files within that folder


I don't see the point?

> **MAXDDARK said:**
> 
2.and what if all the critical files would be read only


Critical files already have appropriately restricted permissions.

---

### Post by MaximB on 2006-07-22
the point is that noune could delete your home folder

---

### Post by kabus on 2006-07-22
> **MAXDDARK said:**
> the point is that noune could delete your home folder

So what if I don't delete your home folder but fill up all the writable files in it with gibberish?

```
cat /dev/urandom>/home/user/yourfile
```

(and couldn't a virus use some vulnerability to get root privileges, making permission settings essentially useless?)

---

### Post by jordilin on 2006-07-22
> **MAXDDARK said:**
> from the last security thread I learnt that a virus can delete your home folder
so I thought of a way to defend it.


What virus? I haven't heard anything about this. Is this a joke?? Well, obviously anyone can do rm -rf /home, right?

---

### Post by T700 on 2006-07-22
> **MAXDDARK said:**
> from the last security thread I learnt that a virus can delete your home folder

Authoritative citation, please (i.e. *not* "someone said it in a thread so it must be true).

Paul

---

### Post by UbuntuniX on 2006-07-22
I think you could possibly change the name of the home folder and rewrite the configuration for it...

---

### Post by MaximB on 2006-07-22
I don't know of any virus for linux
BUT - we don't want to be like MS that sees their mistakes and bugs only after somting happens.
we must prevent viruses now
we must make linux more secure
all the things you've said are an examples of how linux can be vanrable
and how easy it can be to make a linux virus.
we must not let this happen.
please do somting about it.

---

### Post by aysiu on 2006-07-22
Here's what you can do:

1. Back up your important files regularly. That way, in case they get erased, you have... a back up.

2. Don't keep any confidential material on the computer you have connected to the internet. If you have only one computer (and it's connected to the internet), don't keep *any* confidential material on it.

3. Install *firestarter*

4. Use the NoScript extension on Firefox

5. Install software only through the Ubuntu repositories (Synaptic, *apt-get*, *aptitude*, Adept)

6. If you're really paranoid, do a reinstall every now and then--just in case a rootkit that can't be detected happened to have snuck in there somehow.

7. Change the timeout for *sudo* to be one minute instead of the default (which I think is ten minutes).

8. Use separate passwords for your banking or any financially-related internet activity.

9. Favor ssh over telnet. Favor sFTP over FTP.

---

### Post by Iandefor on 2006-07-22
It would only marginally help. Sure, if there were no such thing as privelege-escalation exploits which allow a user with normal priveleges to gain superuser priveleges by taking advantage of the way the software is structured, then this would probably help more, Then again, critical files are almost NEVER kept in /home. Just user-specific files. And, honestly, how bad is it if your Nautilus settings get borked?

---

### Post by MaximB on 2006-07-22
that's a very easy to say and do
but that's like running from the problem
not preventing it

---

### Post by John.Michael.Kane on 2006-07-22
**Deleted..... since my post was misinformation,and fundamentally wrong and fundamentally bad. **

---

### Post by Ptero-4 on 2006-07-22
> **UbuntuniX said:**
> I think you could possibly change the name of the home folder and rewrite the configuration for it...

Is it really possible to change the name of the /home folder and get ubuntu to recognize it as the /home folder? If it is possible, how? and if it isn't, what did you mean in your post?

---

### Post by Iandefor on 2006-07-22
> **MAXDDARK said:**
> that's a very easy to say and do
but that's like running from the problem
not preventing it If aysiu's advice is "running away" from the problem, the only real way to "prevent" the problem is to preemptively destroy any and all possible malicious crackers. The best way to keep your system safe is to close security holes as fixes come. Follow aysiu's advice- it's good, sound advice for closing security holes that you can't fix with a patch, like JavaScript and software acquired from a third-party source.

---

### Post by MrHorus on 2006-07-24
> **MAXDDARK said:**
> that's a very easy to say and do
but that's like running from the problem
not preventing it

To be perfectly frank mate, you don't really appreciate the reality of the situation.

Security is not, and I repeat *NOT* a goal, nor is it an achieveable end point - security is an ongoing process.

---

### Post by LordHunter317 on 2006-07-24
The amount of technical misinformation in this thread is overwhelming.  I'm not going to quote anyone in specific because almost everyone said something fundamentally wrong and fundamentally bad.  I'm going to correct these wrongs in no specific particular order, but please pay attention.  Rarely does one see so much bad information paraded around at once:[list][*]There are viruses for Linux, just not many.  Far important are simple working exploits and trojans of which there are far more.  This includes software on a regular desktop, like Firefox.  If you don't believe me, go read secunia.org for a while.[*]Making /home/$USER read-only wouldn't do a thing.  The virus would just chmod the directory to have write access, and then delete everything.  Making something read-only doesn't remove your ability to change it's permissions.  They're totally independent.  Making the file/dir immutable would, but only root can do that and it's an obviously unworkable solution.[*]It's more than possible to have a home directory anywhere you want.  Most "users" on your system have their home directory somewhere other than /home.[*]"Critical files" aren't application files.  They're mostly the user's data, which is stored in /home and is quite accessible to any virus that might start running.[*]Reinstalling won't protect you from a rootkit that snuck on unless you audit all data you restore to the box.  Once a system is suspect of compromise, ***everything*** must be audited before it can be put on the box again.[*]A virus can delete your home folder trivally:```
#!/bin/sh
echo "I AM A VIRUS"
cp $0 /tmp
chmod -R u+rwx /home/$USER
rm -rf /home/$USER

```It copies itself somewhere and deletes your home directory.  Simple.  Obvious.[*]Installing firestarter is wholly unncessary on a desktop Ubuntu system and shouldn't be done unless you know you need it.  If you're not running services, you won't need it.  It doesn't add any security.[*]Changing the sudo timeout doesn't add any security.  The password can be hijacked, ultimately you're screwed if your account is compromised.[/list]That about covers it, I think.

---

### Post by aysiu on 2006-07-24
LordHunter, when you first appeared on these forums--I have to confess--I found you really obnoxious. Now, I have to say I've grown to really respect your opinion on security.

When you say a "everything must be audited," what exactly does that mean? And how does a rootkit perpetuate itself even after the hard drive has been reformatted--is there some secret place it can store itself?

I realize that Firestarter doesn't add security in and of itself, but doesn't it allow an easy GUI way to monitor what's going on with the IPtables that are already there?

I'm asking these as honest questions I want to know the answers to. I'm not trying to argue with you. Any help you can give and security tips of your own would be much appreciated. Thanks in advance.

By the way, what's the point of the sudo timeout?

---

### Post by LordHunter317 on 2006-07-24
> **aysiu said:**
> When you say a "everything must be audited," what exactly does that mean?Exactly what it says.  Every file that is put back on the system must be verified to ensure they have not been tampered with.  For data, that may be as simple as a virus scan.  For custom-code, this may require a full source audit.

>  And how does a rootkit perpetuate itself even after the hard drive has been reformatted--is there some secret place it can store itself?By tampering with a script to reinstall itself or do something else nasty?  I have several scripts in ~/bin that one could edit to reinstall a rootkit and I'd never know.

> I realize that Firestarter doesn't add security in and of itself, but doesn't it allow an easy GUI way to monitor what's going on with the IPtables that are already there?But there's nothing to monitor.  That's actually a worse situation, IMO.  There's nothing a user should do about the stuff firestarter will report, nor is there anything they can do most of the time.  So it just creates a problem out of nothing.  That stuff shouldn't be monitored, it should just be ignored.  And most of that noise is ignored at the business / enterprise level.

---

### Post by aysiu on 2006-07-24
Thanks for answering my questions.

So, assuming I have no scripts in my /home directory, I would just have to do a virus scan (I wouldn't use a rootkit scanner?) on my personal files and then reinstall?

Also, as with the sudo timeout issue... what's the point of Firestarter?

---

### Post by LordHunter317 on 2006-07-24
Perhaps.  Do you develop code in any language?  Better check all that.  

As for firestarter?  I frankly don't see much use for GUI iptables tools.  People who need to use iptables ought to be competent enough to use it on the command-line.  

I see a small potential use case for laptops, but my personal experience has been that if I have listening services on a portable machine, I probably don't care if some untrusted network I connect to (e.g., Wi-Fi at a coffee shop) has access to that service.  Services by their very nature are public.

However, I may want a service to only be accessible when I'm home, in which case firestarter could be useful.  But the reality is a tool that simply turns the service off when I'm not at home would be better.

---

### Post by MaximB on 2006-07-24
LordHunter317 - you just drove me to panic
you said that there is nothing I can do to defend ubuntu , except for turning scripts off and not visiting some dangerus sites.
but if somone will try to brake my ubuntu from far - I'm doomed.

better say how can we defend ourselves (except from the obius updates).
cuz if you compare it to winxp - yes ubuntu is by far more secure , but still if somone will develop a virus for it - what can we do ?

---

### Post by aysiu on 2006-07-24
I don't develop any code. I know virtually nothing about programming. Thanks for checking that, though.

So basically Firestarter is more or less useless. Good to know.

What about the sudo timeout? What purpose does that serve, if any? I mean, if there's no point in changing it from 10 minutes (or whatever the default is) to 1 minute, why not just have it be 200 minutes... or not turn off at all?

---

### Post by T700 on 2006-07-24
> **MAXDDARK said:**
> LordHunter317 - you just drove me to panic
you said that there is nothing I can do to defend ubuntu , except for turning scripts off and not visiting some dangerus sites.
but if somone will try to brake my ubuntu from far - I'm doomed.

better say how can we defend ourselves (except from the obius updates).
cuz if you compare it to winxp - yes ubuntu is by far more secure , but still if somone will develop a virus for it - what can we do ?

Let's put this into a human light.  You can avoid bad neighborhoods late at night, not pal around with drug dealers, and lock your doors and windows, but if someone is deterimined to rob, rape, or kill you, they almost certainly will.  For most of us in our physical lives, taking basic safety measures is enough.  If a person is a high value target (political leader, very wealthy, very hated, etc.), more measures need to be active.  

At the very root of all of it, any system, organic or mechanical, is able to be robbed, owned, destroyed, or whatever, if the attacker sufficently motivated and capable.

I'd do the usual stuff and not worry too much about being "doomed".

Paul

---

### Post by Iandefor on 2006-07-24
> **LordHunter317 said:**
> The amount of technical misinformation in this thread is overwhelming.  I'm not going to quote anyone in specific because almost everyone said something fundamentally wrong and fundamentally bad. If you wouldn't mind, what did I say that was fundamentally wrong/bad (If I did, but I'm pretty certain I did)?

---

### Post by LordHunter317 on 2006-07-24
> **MAXDDARK said:**
> LordHunter317 - you just drove me to panic
you said that there is nothing I can do to defend ubuntuNo, what I said was making /home/$USER read-only was senseless.  But this is true on Windows too, and just about every other operating system I can think of.  If you own the files, you can always change the permissions.

[quiote]better say how can we defend ourselves (except from the obius updates).[/quote]Don't visit dangerous sites and run code you don't trust.  But that's true on Windows too.

> cuz if you compare it to winxp - yes ubuntu is by far more secure ,No, it isn't.

> but still if somone will develop a virus for it - what can we do ?Largely nothing beyond AV and not being dumb, like on Windows.  When viruses that AV would be effective against appear in sufficent quantity on Linux, you can install AV and run it.

[quote=aysiu]What about the sudo timeout? What purpose does that serve, if any? I mean, if there's no point in changing it from 10 minutes (or whatever the default is) to 1 minute, why not just have it be 200 minutes... or not turn off at all?[/quote]From a security perspective, I'm not sure there is.

That being said, hijacking the password in some situations might be difficult, so there is some security advantage.   You have to actively race to do it if there is no timeout.

But reducing it to one minute from 10 minutes is still a large enough window for a smart attacker to break through.  Better is to lock down the logs so detecting the window is impossible, regardless of length.

---

### Post by LordHunter317 on 2006-07-24
> **Iandefor said:**
> If you wouldn't mind, what did I say that was fundamentally wrong/bad (If I did, but I'm pretty certain I did)?Well, you pointed out critical files aren't in /home.  Critical system files certainly aren't, but from a security perspective we don't care about them nearly as much.  I can replace those trivally.  

A user's data OTOH, may be difficult to replace or irreplacable.  Stolen bank information is an example of this: the accounts must be closed if they're stolen.  That's not trivial.

It's a common misconception to think system files are the most critical thing to protect.  In a certain sense they are, since the box ceases to function correctly if they are compromised.  But from a recovery standpoint, they're not.  And desktop users are generally more interested in recovery after a compromise instead of functionality.

---

### Post by Iandefor on 2006-07-24
> **LordHunter317 said:**
> Well, you pointed out critical files aren't in /home.  Critical system files certainly aren't, but from a security perspective we don't care about them nearly as much.  I can replace those trivally.  

A user's data OTOH, may be difficult to replace or irreplacable.  Stolen bank information is an example of this: the accounts must be closed if they're stolen.  That's not trivial.

It's a common misconception to think system files are the most critical thing to protect.  In a certain sense they are, since the box ceases to function correctly if they are compromised.  But from a recovery standpoint, they're not.  And desktop users are generally more interested in recovery after a compromise instead of functionality. I see. That makes sense. Leave it to me to not think of the obvious :).

Thanks!

---

### Post by LordHunter317 on 2006-07-24
I'm not sure it really is obvious to a human.  We tend to automatically think, "What do I have to do to make my machine run again," because the obvious symptom in a compromise is that the machine isn't running correctly.  As such, we fix that.  It's not natural to think of the consequences a compromise may cause and treat those.

---

### Post by MaximB on 2006-07-24
LordHunter317 - you should really work for the ubuntu team, to improve the security of ubuntu...you loosing your potential  :)

---

### Post by John.Michael.Kane on 2006-07-24
I deleted my post since LordHunter317 seems to feel his thoughts,and way are the only ones that work,and matter.

---

### Post by LordHunter317 on 2006-07-25
:rolleyes:  The amount of immaturity on these forums is absolutely overwhelming.  You said something wrong.  It's not a big deal, unless you choose to make it a big deal.

---

### Post by John.Michael.Kane on 2006-07-25
You said that everyone of the post in this thread was wrong. that means that only your post,and thoughts in this thread are right. if you want to call it immature to speak what one feels fine. since you give off the notion that you know everthing,and only your right then this forum should see no post from you asking for help ever.in fact everyone who needs help should seek only your advice since you can make statement saying everyones wrong,and your right.

---

### Post by Iandefor on 2006-07-25
I'm going to request that SD-Plissken and LordHunter 317 keep it civil. 

Thank you.

---

### Post by LordHunter317 on 2006-07-25
> **SD-Plissken said:**
> You said that everyone of the post in this thread was wrong.No, I said *almost* everyone was wrong.  I was very careful with my word choice on purpose.

> that means that only your post,and thoughts in this thread are right.Which doesn't let you conclude the statement you made, remotely.  Just because there was misinformation in this thread and I corrected it doesn't allow you to generalize in the least, which is what you are doing.

> since you give off the notion that you know everthing,Nonsense. I've made it perfectly clear that I do not know everything, and in fact that I'm wrong multiple times a day.  Your refusal to believe that isn't my problem.

> and only your right then this forum should see no post from you asking for help ever.It doesn't simply because I don't generally ask for advice here.  Normally I can't ask for advice publically because most of my professional jobs are under NDA, or my questions are of a specific nature such that I ask questions in more focused places.  But I do ask for help even with "basic" issues, believe it or not.  I can post chat logs if you don't believe me.

> in fact everyone who needs help should seek only your advice since you can make statement saying everyones wrong, and your right.I never said that.  I specifically said **"almost"** on purpose, and didn't name any names because I didn't want to specifically point anyone out for making a technical error.  I didn't feel it was appropriate to do so.

In college, when almost a whole class gets a problem wrong, the teacher doesn't generally point out who got it wrong or who got it right.  He/she just says, "Most of you got this wrong" and then goes over it.  If you have a problem with that then I'm  sorry but I don't know what else to say.

---

### Post by aysiu on 2006-07-25
LordHunter317, with all due respect, I think you have a lot of good tips on security and a good understanding of what works, what doesn't work... and how well security measures work.

Your original post in this thread started out: > The amount of technical misinformation in this thread is overwhelming. I'm not going to quote anyone in specific because almost everyone said something fundamentally wrong and fundamentally bad. I'm going to correct these wrongs in no specific particular order, but please pay attention. Rarely does one see so much bad information paraded around at once Now, even though you have some good information/corrections to make, you'd probably get more people receptive to your advice if you started out something like this instead: > If people don't mind, I'd like to correct a few mistaken assumptions about security There wasn't really a need to say > Rarely does one see so much bad information paraded around at once any more than it's necessary to say > Your mom's the ugliest piece of shit I've ever seen if you meet someone's mom and she's ugly.

I, like SD-Plissken, was initially very turned off--not by *what* you had to say--but by the way you said it. Now, I've just learned to accept that you're a little harsh in your tone, just like Stormy Eyes (and I was initially very turned off by his posts as well).

To SD-Plissken, don't take it personally. I think LordHunter317 has some good advice and a lot of knowledge. Could her or his posts be phrased in a better way? Sure. Nevertheless, I don't see that as any reason to delete your own posts.

---

### Post by MaximB on 2006-07-25
I respect you ALL very much - all of you have a great knowlge and I hope we can work together.
after all thouse missunderstandings are now clear
shell we go to the subject of our thread again ?

---

### Post by aysiu on 2006-07-25
Bottom line--Ubuntu's pretty secure out of the box. There are a few good practices for being more secure on the internet, but if someone's really out to get you, she will.

If you're super paranoid, don't use the internet.

---

### Post by Metacarpal on 2006-07-25
Just wanted to chime in and say thanks to you all, especially LordHunter and aysiu - I've learned a lot here.

**quietly goes off to un-install Firestarter**

---

