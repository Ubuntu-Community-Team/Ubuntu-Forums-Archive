---
title: "automatic updates"
date: 2006-03-13
forum: Server Platforms
---

### Post by ssam on 2006-03-13
in light of recent events i wondered what people thing about some sort of automatic upgrade system. this would allow the ubuntu devs to mark a security upgrade as urgent, and it would be automatically download and installed by all ubuntu machines.

i think it would be techincally feasable for a script to run maybe every 24 hours that checks a list for urgent upgrades. if there are any they would be downloaded and installed with apt. it would use a signing system to prevent people exploiting it.

i imagine some users have stong feelings about automatic downloading and installing of code. (i heard people complain about the popup messages for updates). but does faster bug patching ballance out the risks.

---

### Post by stuporglue on 2006-03-13
> no   	
yes, but only for critcal securtiy fixes 	
yes, for all updates 		
not sure

I voted "no" because of the given options, "no" is the closest to what I would choose. My real preference would be for it to be an option, but not turned on by default and for the user to be able to decide which repos could issue updates. 

On my normal machine then, I could then say that security.ubuntu.com could issue auto-updates but nothing else. On my dapper machine though, I might want it to just pull all the updates all the time. 


btw. Wouldn't this be something pretty easy to set up as a cron job?

---

### Post by 5-HT on 2006-03-13
[quote=stuporglue]I voted "no" because of the given options, "no" is the closest to what I would choose. My real preference would be for it to be an option, but not turned on by default and for the user to be able to decide which repos could issue updates. 

On my normal machine then, I could then say that security.ubuntu.com could issue auto-updates but nothing else.

btw. Wouldn't this be something pretty easy to set up as a cron job?[/quote] 
Same feelings here. 
While it can be important to ensure systems are getting patched in a timely manner when critical security bugs are found, I'm a little uneasy about forcing automatic installation of updates.

Being able to chose which updates (i.e. urgent security ones vs. application bug fixes, or something along those lines), if any, can be automatically installed is a great idea. 

About adding as a cron job, it would be a simple thing to do, but how could one differentiate between security vs. non-security app bug updates? 
Wouldn't that be more of an all-or-nothing?

---

### Post by vayu on 2006-03-13
NO!  The whole "we know what's good for you" philosophy can stay with M$ thank you very much.

---

### Post by nocturn on 2006-03-14
Dapper actually has this option.

And as long as it's an option, I'm all for it.

---

### Post by tribaal on 2006-03-14
[QUOTE=vayu]NO!  The whole "we know what's good for you" philosophy can stay with M$ thank you very much.[/QUOTE]
Same position. I chose linux because it allows me to decide what's good for me myself, and I want it to remain that way.

And you can do a cron job to auto-upgrade for you if you really feel like it, by the way

- Trib'

---

### Post by Barrakketh on 2006-03-14
[QUOTE=vayu]NO!  The whole "we know what's good for you" philosophy can stay with M$[/QUOTE]
And GNOME.

---

### Post by engla on 2006-03-14
[QUOTE=nocturn]Dapper actually has this option.

And as long as it's an option, I'm all for it.[/QUOTE]
Sounds good. Where is this option? Is it in synaptic ("Install all updates from repo *") or in update manager (The more sober "Install security updates automatically")

---

### Post by syg00 on 2006-03-14
[QUOTE=vayu]NO!  The whole "we know what's good for you" philosophy can stay with M$ thank you very much.[/QUOTE]+1 ...
If any prick can get through to my systems before I get the updates on, good on 'em.

---

### Post by ssam on 2006-03-14
if it was an option switched on by default, then people who are confident enough to manage there own system can turn it off. and the new to linux people  who would be safer with it on can just leave it.

ubuntu does lots of things automatically already, is there a reason why installing urgent security updates should not be added to that list.

---

### Post by MetalMusicAddict on 2006-03-14
I like it just how it is. As an "option". ;)

---

