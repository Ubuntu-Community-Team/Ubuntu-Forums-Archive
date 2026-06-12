---
title: "Tips for offering good help on the forums..."
date: 2006-05-01
forum: The Cafe
---

### Post by aysiu on 2006-05-01
***Disclaimer**: These tips are what you should do *ideally*. I'm not saying I always follow my own advice; though, I do try to.*

**Make appropriate assumptions**
If someone's posting in the Absolute Beginner section, don't assume she knows where "the terminal" is. Worse yet, don't just post code without saying "copy and paste this into the terminal."

Likewise, you shouldn't assume that everyone is using Gnome. ```
gksudo gedit
``` will just turn up ```
bash: command not found
``` for KDE users, a growing contingent on these forums.

I think it's reasonable to assume the opposite, however. I always assume anyone posting in the development release section (currently, that's Dapper) knows where the terminal is. Dapper's a lot stabler now than it was a few months ago, but I still would not recommend it to absolute beginners.

**It's okay to post links**
If a question is frequently asked, don't burn yourself out by typing out long explanations every time. You're still helping by posting a link (as long as the link is appropriate). However, if the person asking for help tries the instructions in the link you post and still has problems, try to follow up with her and get her through any anomalies that might crop up.

**Read the first post... *really read it***
I'm guilty of this a lot myself. You see a subject heading like "How do I use MS Word?" and you immediately think, "Duh! Just use OpenOffice, Stupid." But in the first post, the person asking for help says she's already tried OpenOffice and it's missing X feature or messes up the formatting of documents she's sharing with friends and family.

Allow for special cases. Yes, most of the time people ask the same questions over and over again, but sometimes there are quirky situations that you should look out for.

**Encourage--don't scold**
People who frequent these forums see vague posts all the time: > My screen resolution isn't working. Help!!! Great. Thanks for telling us that. Instead of scolding people, just shoot back some questions letting them know that you need the answers in order to help them. An appropriate response would be something like > I understand that when things aren't working, it's frustrating to a new user, but if you want help, please post the answers to these questions:

1. What graphics card and monitor brand do you have?
2. What have you tried (if anything) to get your monitor resolution fixed?

**Don't get burnt out**
It can be tiring helping new users sometimes. If you're tired in the head and just don't have the patience to deal with things in a polite and patient manner, just don't deal with it. Rather than posting some stupid and angry response, just don't post at all. The forums are active enough that if you don't answer so-and-so's question, someone else probably will.

**Don't be afraid to say you don't know the answer**
Some will disagree with me on this, but I'm essentially a newbie. I really don't know that much about Ubuntu or Linux. Sometimes, though, I will know what a person *should* post in order to get appropriate help, and I think it's not out of line to say something like > I don't think I can help you with that problem, but if you post the contents of your /etc/sudoers file, I think someone else may be able to

Any additional advice from folks?

---

### Post by hollywoodb on 2006-05-01
[QUOTE=aysiu]
**Make appropriate assumptions**
If someone's posting in the Absolute Beginner section, don't assume she knows where "the terminal" is. Worse yet, don't just post code without saying "copy and paste this into the terminal."

Likewise, you shouldn't assume that everyone is using Gnome. ```
gksudo gedit
``` will just turn up ```
bash: command not found
``` for KDE users, a growing contingent on these forums.
[/QUOTE]

Overall good post, and a lot of good points.... I'm guilty of both of these... unless someone posts under Kubuntu support (where they should), I assume they're using Gnome.

The first point however, regarding the terminal.... In my opinion basic console commands are a must-learn, especially for new users.  It may not be *easy* or *convenient*, but it will make things easier and more meaningful in the long run.  I just hope when I give advice people aren't pasting commands into gedit or kate and waiting for something to happen. ;)

---

### Post by mstlyevil on 2006-05-01
Don't jump on users or be rude because they failed to search for a common problem or they posted in the wrong forum. Provide them with the appropiate link to the answer to their question and kindly inform them you found this using Google or the search function. Many users that are new to Linux have never used Google or the search function to find answers to their problems. Also searches do not always yield the appropiate thread. By teaching them to use the search function you are doing them and yourself a favor.

If they posted in the wrong forum, kindly let them know that such and such question would be better answered in this section. Then inform them that you are going to ask the thread be moved to the appropiate section so they will get better assistance. Then use the report thread function to let us know it is in the wrong forum and we will move it. It can be confusing to new users where to post sometimes so being rude is just counterproductive and may turn them off to Linux. Just remember, you were a new user at one time.

Linux can be frustrating for new users coming from the MSFT world. Things can sometimes be radically different from what they are used to. It is not appropiate to tell a new user to just go back to Windows. It is our responsibility to help these people make the transition. By guiding them kindly in the right direction we will help allieviate their frustrations and help them to adjust to the changes. Then these once frustrated newcomers will one day be valuable resources for others to lean on.

Just be paitient and kind to new comers. Most will come around eventually and do great things with Linux.

---

### Post by confused57 on 2006-05-01
Good Advice.  I've only been using Linux, Ubuntu mostly; but I've finally garnered enough knowledge and experience that I can answer some of the basic questions, that seem to get asked over & over, & I've found out that it takes a lot of patience when answering questions and proding the poster to explain more about their system specs, what they've done, how much experience they have with computers, Linux, etc.
I try to refer them to links that I've used to solve some of my problems, rather than retyping or rephrasing the instructions from the original poster of the link.
I think it would help beginners in their learning of Ubuntu to attempt to search for answers before starting a thread with their problem or question.  I try to let them know if something I suggest "may" work or if it has actually worked for me.

Linux is not something you're  going to learn in a day or two, especially if you're a complete novice to computers and Linux.  It takes time and the parts will fall into place bit by bit, I learn something new every day and hope to keep on learning and sharing when I'm able.

---

### Post by matthew on 2006-05-01
Great post, Aysiu! Thank you.

I would add, please model the sort of interaction you wish to see in these forums. If you want people to be polite, then choose to be polite yourself. If you want people to treat you with gentleness and respect, be gentle and respectful. This is possible even when dealing with the freshest of new users. Finally, it is generally not a good idea to abbreviate technical terms, even when you think it is obvious what you are referring to, and absolutely never use l33t speak.

---

### Post by aysiu on 2006-05-01
> **hollywoodb]
The first point however, regarding the terminal.... In my opinion basic console commands are a must-learn, especially for new users.  It may not be *easy* or *convenient*, but it will make things easier and more meaningful in the long run.  I just hope when I give advice people aren't pasting commands into gedit or kate and waiting for something to happen.  said:**
>  No, I'm in total agreement. I think the terminal is a great thing for new users to get to know. My point was really just that you shouldn't assume they know **where** the terminal is.

It's better to say: > Go to the terminal (in KDE, KMenu > System > Konsole; in Gnome, Applications > Accessories > Terminal) and copy and paste these commands than to say [quote]Copy and paste these commands into the terminal

---

### Post by mstlyevil on 2006-05-01
I forgot to mention great post aysiu. I believe it will help people put things in perspective.

---

### Post by htinn on 2006-05-01
"Read the first post" <-- that really should be tip #1

I would add that one should not just *read* the post, but really try to *listen* to what the poster is saying with their post. This is especially important because people just starting out don't always do a good job describing the problem.

Part of your advice is nearly always going to be helping the first poster *describe* the steps they take to produce the situation they have, so it really helps if you are in tune with what they are saying. If you aren't in tune, then you really shouldn't be posting advice.

---

### Post by aysiu on 2006-05-01
[QUOTE=htinn]
I would add that one should not just *read* the post, but really try to *listen* to what the poster is saying with their post. This is especially important because people just starting out don't always do a good job describing the problem.[/QUOTE] That reminds me--there's one other thing I left out.

**Try to figure out what the original post-er wants to accomplish, not what she thinks is the best way of accomplishing it. Present all the options and let her choose.**

For example, if someone says, "It says I need to be root to change this file. How can I log in as root?" I don't think the most appropriate response is to tell her how to log in as root. The user appears to care only about how to change the file and probably has no clue about *sudo*, *kdesu* or *gksudo*.

On the other hand, if someone says, "I already know about *sudo*, and I hate it. I just want a traditional root login. How do I set that up?" then it is appropriate to tell her how to log in as root, because she's concerned with a *method* for accomplishing the task and not the accomplishment itself.

Same goes for someone asking how to dual boot Kubuntu and Ubuntu. It's appropriate to mention that one does not *need* to dual boot them. If the original post-er says, "I know I don't need to dual boot, but I don't like each desktop environment cluttering up the others' menus. I just like them clean and separate," then you should help her set up the dual boot.

---

### Post by towsonu2003 on 2006-05-01
can we sticky this to the Absolute Beginners section? 

PS. I'm usually guilty of #1 and 3. But I remember bashing the hell out of a Windows user because s/he asked for help in here. I still couldn't find that stupid post of mine to apologize... 

As for the terminal thing, does this work in kde:
alt+f2 > type konsole > hit enter
?
It's much faster than describing the menu.

---

### Post by gingermark on 2006-05-01
[QUOTE=towsonu2003]can we sticky this to the Absolute Beginners section? 

As for the terminal thing, does this work in kde:
alt+f2 > type konsole > hit enter
?
It's much faster than describing the menu.[/QUOTE]
I nominate aysiu as the **Official Ubuntu Forums' Sticky Thread Writer**
He's pretty much doing that job anyway.


And yes, Alt+F2 opens a box in KDE into which you can type commands, such as 'Konsole'.

---

### Post by towsonu2003 on 2006-05-01
[QUOTE=gingermark]I nominate aysiu as the **Official Ubuntu Forums' Sticky Thread Writer**
He's pretty much doing that job anyway.
[/quote]second that!
[QUOTE=gingermark]
And yes, Alt+F2 opens a box in KDE into which you can type commands, such as 'Konsole'.[/QUOTE]
thanks :)

---

### Post by confused57 on 2006-05-01
I remember when I was starting out, someone would say to enter several lines of commands into the terminal...I didn't know if I was supposed to try and enter all at the same time...finally figured out I needed to copy and paste one line at a time, hit enter,etc.  Frequently, the commands are longer than the code "box" and require scrolling to see the entire command; someone familiar with computers would know to hold down the shift key, click at the beginning of the line, scroll, and click at the end of the line to highlight & copy the entire command.  It's pretty basic stuff, but not so apparent to someone utterly new to Ubuntu and relatively new to computers.

It really irks me when I see someone say they're going back to Windows, if someone can't solve their problems...I want to tell them "not to let the door hit them in the behind on the way out"...I just calmly state Linux is not for everyone & refer them to aysiu's sticky.  As easy as it is set up dual-booting, anyone can use their Windows and learn Linux also, if they really have the incentive and desire to do so.

The wide diversity of people using this forum never ceases to amaze me, I realize English is not the native language of many of the posters here and I try to take that into consideration as well.  I don't think I can honestly relate to the reason(s) some(English speaking or not) need to get Ubuntu or Linux functional on their computers.

---

### Post by YourSurrogateGod on 2006-05-01
[QUOTE=mstlyevil]I forgot to mention great post aysiu. I believe it will help people put things in perspective.[/QUOTE]
It would be cool if we could clone him, we can't have too few members such as aysiu.

---

### Post by confused57 on 2006-05-04
Think I'm getting "burnt out", for now, attempting to answer posts.  I don't know much about Ubuntu, but I try to give some advice if I have some knowledge(usually very little) about the poster's question.  Just the last few days, I and  others have replied to someone's post in one section of the forum only to see the same poster go to another section of the forum and ask the same question and get some of the same answers(I'm rambling).   It gets frustrating...and I know I'm taking this a little too seriously...just venting, I realize the poster is just trying to get answers and sometimes it's best to try another section, it's just that they do it within a matter of a few hours, if they don't get a satisfactory answer...rambling again.

---

