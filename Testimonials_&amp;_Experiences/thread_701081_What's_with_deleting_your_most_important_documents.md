---
title: "What's with deleting your most important documents?"
date: 2008-02-19
forum: Testimonials &amp; Experiences
---

### Post by adi116 on 2008-02-19
one fine night - tonight, actually - i was well close to done with a very important paper when i decided to take a break and grab some dinner. as i left my workstation, i left my computer without saving the document- seeing as an operating system would not randomly close a program that i left running - especially something like open-office word processor. i was terribly mistaken. i went to lunch, and came back to see that my screen was off. thinking nothing of it, i moved my mouse and my screen immediately turned back on - but none of the windows i had open were open anymore - including this paper. this shocked me - and i proceeded to search my recent documents to find nothing. at this point, i came to total panic. i then proceeded to open the program, and was greeted with a dialogue that asked if i wanted to recover the document. i thought to myself "why would it have to recover it? all i did was leave my workstation on - is this grounds for a fatal error?" i then proceeded to recover, and found that it only recovered my last save point - about halfway into the paper. this is about where i lost it and created the little pile of particles i used to call my cell phone laying next to me. i hadn't even TOUCHED the computer and it decided to close my paper without saving.

i suggest someone from either the ubuntu team (i'm suspecting the problem was caused by the operating system and not the program) or the open office team SERIOUSLY look into fixing this problem, as it may cause many more piles of shattered plastic and LCD over the course of the two software's lives. 

if someone could bring this to the attention of the ubuntu team for me, i would greatly appreciate it. if someone could also cook up half my essay that's due in about six hours, i would be incredibly grateful - but i doubt that would happen.

---

### Post by adi116 on 2008-02-19
note - i feel this has to be an operating system problem because i also had firefox, pidgin, and another instance of openoffice open when i had left. all of these had disappeared.anything you can do about it?

---

### Post by aysiu on 2008-02-19
> **adi116 said:**
> i left my computer without saving the document- seeing as an operating system would not randomly close a program that i left running - especially something like open-office word processor. i was terribly mistaken. Yes, you were terribly mistaken.

I don't care what operating system you're using (Windows, Mac, Ubuntu)--you should **always** save your documents frequently, and especially if you walk away for a long break.

---

### Post by azimuth on 2008-02-19
Sorry for your loss but, maybe you should use the auto-save to avoid this happening again, for whatever reason. It's just good work habits.

To save recovery information automatically every n minutes
1.Choose Tools - Options - Load/Save - General.
2.Mark Save AutoRecovery information every and select the time interval.
This command saves the information necessary to restore the current document in case of a crash. Additionally, in case of a crash OpenOffice.org tries automatically to save AutoRecovery information for all open documents, if possible.


edit: The above instructions were taken from the help files. The option is no longer in that location???? Oh well, just a Cont-S between paragraphs works well and gives you time to collect your thoughts before you continue.

---

### Post by tvdxer on 2008-02-19
> **adi116 said:**
> one fine night - tonight, actually - i was well close to done with a very important paper when i decided to take a break and grab some dinner. as i left my workstation, i left my computer without saving the document- seeing as an operating system would not randomly close a program that i left running - especially something like open-office word processor. i was terribly mistaken. i went to lunch, and came back to see that my screen was off. thinking nothing of it, i moved my mouse and my screen immediately turned back on - but none of the windows i had open were open anymore - including this paper. this shocked me - and i proceeded to search my recent documents to find nothing. at this point, i came to total panic. i then proceeded to open the program, and was greeted with a dialogue that asked if i wanted to recover the document. i thought to myself "why would it have to recover it? all i did was leave my workstation on - is this grounds for a fatal error?" i then proceeded to recover, and found that it only recovered my last save point - about halfway into the paper. this is about where i lost it and created the little pile of particles i used to call my cell phone laying next to me. i hadn't even TOUCHED the computer and it decided to close my paper without saving.

i suggest someone from either the ubuntu team (i'm suspecting the problem was caused by the operating system and not the program) or the open office team SERIOUSLY look into fixing this problem, as it may cause many more piles of shattered plastic and LCD over the course of the two software's lives. 

if someone could bring this to the attention of the ubuntu team for me, i would greatly appreciate it. if someone could also cook up half my essay that's due in about six hours, i would be incredibly grateful - but i doubt that would happen.

This is interesting.  Definitely either a serious error or some very strange but honest user error, even if you should save your files.

Was your computer stable when you got back to it, even with the windows closed?

---

### Post by Wiebelhaus on 2008-02-19
If the power was suddenly cut off by electrical noise , fluctuation or a "brown out" then your data may be lost (this by the way happens with all OS's) on the other hand Open office has a nifty document recovery function which you may want to try , I've even been able to get it to recover an MS Office doc that was destroyed on a persons computer , basically what it does is it tries to salvage what it can from the hidden .temp mirror of the document.




but as a matter of course , always save your work.

---

### Post by Nirevus on 2008-02-20
Perhaps in future have your auto-recovery save set to every minute? Unfortunately I don't know much about this kind of issue, I've never seen anything like it although sx66gns sounds reasonable. Also, do you have auto-login? It may be that a surge or another fault reset your system.

---

### Post by tvdxer on 2008-02-20
> **Nirevus said:**
> Perhaps in future have your auto-recovery save set to every minute? Unfortunately I don't know much about this kind of issue, I've never seen anything like it although sx66gns sounds reasonable. Also, do you have auto-login? It may be that a surge or another fault reset your system.

It almost sounds like that.

I've had X go flaky on me before many times, but never how the OP described.

And yeah, OO.o's Document Recovery is very nice.

---

### Post by lespaul_rentals on 2008-02-20
[QUOTE=adi116]as i left my workstation, i left my computer without saving the document- seeing as an operating system would not randomly close a program that i left running - especially something like open-office word processor.[/QUOTE]

**Wow**.

Just, **wow**.

Ctrl+S.  I press it every paragraph at the very minimum.  That way, if the power suddenly goes out in the middle of a long document, or a bug in the application or operating system occurs, I don't lose my data.

I don't care if you're working in Notepad, Wordpad, Word, OpenOffice.org, AbiWord, Kate, Nano, The GIMP, Photoshop, Flash, Emacs...you save your data.  And when something does happen, you don't blame the software when the problem lies with you!

Ubuntu didn't "delete your most important documents."  When I saw that thread title I expected an angry complaint about how all the files in your */home* directory had, for no apparent reason, disappeared.  Instead, you just didn't save your document.

[QUOTE=adi116]i suggest someone from either the ubuntu team (i'm suspecting the problem was caused by the operating system and not the program) or the open office team SERIOUSLY look into fixing this problem, as it may cause many more piles of shattered plastic and LCD over the course of the two software's lives[/QUOTE]

Ubuntu most certainly did not cause your hand to grow a mind of its own and snatch your cell phone, hurling it to the floor in a fit of anger.  Unless maybe this is yet another bug the developers need to iron out -- take note programmers, please fix this mind-control bug when you release Hardy Heron!

While I was writing this very post, I was almost done and needed to quote you.  So I pressed a key shortcut I thought would do it, but instead it closed Opera.  Excuse me, I must go post a complaint thread on the Opera support forums, as it must be their fault!  I'm also running Windows XP here at work, so I think I'll let them know about their poor operating system too!

[img]http://www.uncov.com/assets/2007/9/16/picard-facepalm.jpeg[/img]

---

