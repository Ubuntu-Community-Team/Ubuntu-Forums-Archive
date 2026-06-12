---
title: "I just got root access to my University faculty server, what do I do?"
date: 2010-03-23
forum: The Cafe
---

### Post by Jarmen_Deffs on 2010-03-23
I wasn't trying to, I did it by accident, and I don't want/need to cheat, I just want to survive this experience unscathed.

I was just trying to access my account from home, but instead an error occurred and I was logged into the root directory with full rwx access to everything. (I don't want to provide any more detail, because if other students from my university follow suit I'll only be in bigger trouble)
I didn't actually realise at first, and had a hunt around for my home directory.  I couldn't find it but I did find all the staff accounts for my school...
That's when I realised I was probably somewhere I shouldn't be.

What I want to know is should I report it, or just forget it happened?
Will the admins notice that I was there (without actually searching specifically)? (If yes, I feel like I should report it) 
If I report it what are the chances the uni will take disciplinary action against me?
I didn't open any files, write anywhere or execute anything but I did open the account directory of a staff member to see if there were any files in there (*"Am I really looking at the actual staff accounts?"*); if I report it will logs be able to confirm all this to whoever is investigating? (If no, I don't really want to report it because I could be accused of accessing files...)

I'm especially interested in hearing the opinions of any network admins, and university staff who might have to deal with a situation if it arose at their uni.

I always thought getting root access where I wasn't supposed to would be exciting, but I'm actually finding it kind of scary...

---

### Post by dyingsun on 2010-03-23
I can't tell you exactly what the Uni will do if you report it, but if it was me, I'd tell them straightaway. If you do report it, it shows you are not trying to do anything sneaky. If you don't report it, and your intrusion is logged, they may well go off their brains!

Also, if I was a network admin, I would want to know ASAP about any vulnerabilities. 

If I were you, I'd try to contact technical staff, rather than teachers or faculty people. The networking techs will probably not want to broadcast the fact that someone could access their servers with full rwx perms!

---

### Post by michaeldt on 2010-03-23
I would send a "bug" report to the IT department. Tell them about the problem you had accessing your home folder and that after the error occurred you appeared to have access to the entire server. Treat it as such, not as, "I'm sorry I accidentally had root access and snooped around." After all, it was a bug and you did have access to more than you should. It's clearly a fault and needs fixing asap.

---

### Post by bullet311 on 2010-03-23
Log out, and try it again. See if its repeatable. If so I would tell Network Admin asap. Either that or change your grades and sabatoge your professors. Your call.

---

### Post by 3rdalbum on 2010-03-23
The first thing you should do is type:

```
touch /root/(yourusername)_accidentally_can_access_root_i_will_report_it
```

This confirms to whoever looks later, that you do actually have root access.

Then type:

```
exit
```

Get out of there before you do any damage.

Then report the issue. They will know you're not lying, because you've just created a file in /root. I don't think their logging will show your username to be associated with getting root; I don't think Unix/Linux work that way.

---

### Post by Swagman on 2010-03-23
Type.. "Would you like to play a game" ?

---

### Post by fatality_uk on 2010-03-23
> **3rdalbum said:**
> The first thing you should do is type:

```
touch /root/(yourusername)_accidentally_can_access_root_i_will_report_it
```

This confirms to whoever looks later, that you do actually have root access.

Then type:

```
exit
```

Get out of there before you do any damage.

Then report the issue. They will know you're not lying, because you've just created a file in /root. I don't think their logging will show your username to be associated with getting root; I don't think Unix/Linux work that way.

Agree 100%. It's not worth the hassle that would ensue from being on the server without permission.

---

### Post by _h_ on 2010-03-23
> **fatality_uk said:**
> Agree 100%. It's not worth the hassle that would ensue from being on the server without permission.

Which could mean possibly being arrested and/or suspended from the university.

---

### Post by collinp on 2010-03-23
Report it to the network staff/server administrator. Show, in front of them, you reproducing it.

Either they'll be reasonable and thank you for telling them, or they'll throw you out for cracking their servers.

---

### Post by new_tolinux on 2010-03-23
> **Hellow said:**
> Either they'll be reasonable and thank you for telling them, or they'll throw you out for cracking their servers.

Most likely they can not even do that themselves, although they may ban you from their servers.
But if I was the admin there I would think twice before reporting it to the staff, as "fired because root-by-accident was possible" not really is a nice entry on your joblist.

---

### Post by steev182 on 2010-03-23
Just make sure you're polite when you tell them. (Of course you will be, you use Ubuntu...)

---

### Post by sdowney717 on 2010-03-23
I would probably not say anything. You did not do anything to the system, you knew you should not be there and so you got out. You could send in an anonymous tip to their IT people showing them how to gain access.

---

### Post by the yawner on 2010-03-23
> **sdowney717 said:**
> I would probably not say anything. You did not do anything to the system, you knew you should not be there and so you got out. You could send in an anonymous tip to their IT people showing them how to gain access.

This would be the best answer. You don't know how they would react if you tell this to them personally. Just give them a head's up, but don't let it become a correspondence.

---

### Post by iponeverything on 2010-03-23
Me (as a long time network admin) would leave it and not look back.

A place where I worked had someone come forward, the management immediately contacted the feds and had the person arrested.

Sure, the person could have fought it - but who has the resources for that. Touching a file in root directory, really sounds like bad idea -- it will make prosecution very easy.

And -- the login banner's say something like "for authorized use only, if you are not authorized to use this system log out immediately" 

Not "leave some droppings, so that you can prove you were here"

---

### Post by Docaltmed on 2010-03-23
> **swagman said:**
> type.. "would you like to play a game" ?

+1

---

### Post by Jarmen_Deffs on 2010-03-23
Thanks guys. It was a tough call, but I've reported it to IT.

Along the lines of "I tried to get to my home directory but it didn't work. Help!" rather than "I have root access on the server"

I didn't leave a file to prove I could (to be honest I'll be just as content if they don't believe me, I'm only interested in covering my a***.); that seemed like a good(bad) way to get lots of unwelcome attention...

I'll post anything interesting that happens, and how I got access after it's been fixed  - nothing shady or special, just a problem on their end.

---

### Post by MasterNetra on 2010-03-23
> **sdowney717 said:**
> I would probably not say anything. You did not do anything to the system, you knew you should not be there and so you got out. You could send in an anonymous tip to their IT people showing them how to gain access.

+1

But make sure your not anonymously emailing them from your personal email account especially if it's registered with the school. ;)

---

### Post by undecim on 2010-03-23
I had this kind of thing happen to me once at my old HS. I had heard several horror stories about kids accidently getting where they weren't supposed to be and being charged with hacking because of it, so I sent an anonymous message to the admins, and left a small text file as root on the server to prove access, and explain everything and detailing how to fix it (since it was a horrible obvious mistake left there by the IT admin from last year)

If I were you, I would avoid putting your name to it, but let the sysadmins know about it. Make sure they know exactly what steps they need to take to reproduce the problem, and exactly what can be done with it.

---

### Post by Doctor Mike on 2010-03-23
Is it possible your computer was under the control of a third party? It's a good way for someone to hide their tracks, or the IT department needs to look at their account registration system.

---

### Post by tilixibr on 2010-03-24
I would tell the system admin ASAP!

---

### Post by juancarlospaco on 2010-03-24
> **Swagman said:**
> Type.. "Would you like to play a game" ?

Epic :D

---

### Post by Doctor Mike on 2010-03-24
> **juancarlospaco said:**
> Epic :D + End of line...

---

### Post by BramWillemsen on 2010-03-24
As long as you are honest why make such a big thing about it? You didnt damage anything and you by contacting them you show that you have nothing to hide... But you got this answer already i think ; )

---

### Post by lisati on 2010-03-27
I'm sure a number of forum users have had similar situations occur, where they've obtained access to something they shouldn't have through no fault of their own. There's a good chance that on many of these occasions there has been something written to the system logs.

I've written elsewhere on the forums of how something similar happen to me: while waiting for a university's minicomputer to boot up, I was idly tapping every now and again on the "Enter" key and somehow when the machine got to the point where it could accept logins, I was logged into another student's account without actually having to put in a userid or password. Because the student was one who studied off campus, a warning popped up on the operator's console, prompting an awkward situation where the operator came through from the next room to find out what the "adjectives deleted" I was doing. Immediate opportunity to file a verbal bug report! (The system was still fairly new at the time and there were still one or two gremilins to be tracked down.) :)

---

### Post by bwhite82 on 2010-03-27
> **Swagman said:**
> Type.. "Would you like to play a game" ?

Lol. Make sure to pick: GLOBAL THERMONUCLEAR WAR

---

