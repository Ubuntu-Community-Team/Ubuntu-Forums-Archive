---
title: "Small annoyance with apport dialogs"
date: 2012-09-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-19
We use the Development Release and so we're used to the apport dialog popping a hundred times everyday. It's OK, we signed up to this. 

There's only thing that bugs me about it. If you look at the dialog, it doesn't say what crashed unless you hit the "Show Details" button. See the examples below:

The error pop-up before you click "Show Details"
[ATTACH]224367[/ATTACH]
You don't know what crashed at this point. Maybe it's something you reported 30 seconds ago. Maybe it's something new. Apport already knows what crashed (see ls -lah /var/crash). But you won't know until you hit "Show Details". So you do.

[ATTACH]224369[/ATTACH]
The error pop-up after you click "Show Details". See the "ExecutablePath". You already knew about that via ls -lah /var/crash. Yeah, I already reported it. So it was pointless to click "SHow Details". If I had pressed Report it would be wasted time too.

Therefore, considering apport knows what crashed from the beginning, wouldn't it make more sense for the standard error dialog to just say what crashed, right after the "Sorry, Ubuntu has experienced something..." line? Then we would immediately know if we have to click "Show Details" or "Report" or if we should just ignore it.

It's a small UI change to display this string. But would make testing a little less annoying.

Regards,
Effenberg

---

### Post by dino99 on 2012-09-19
Indeed thats make sense; an other job for ayatana :p

---

### Post by balloons on 2012-09-19
> **effenberg0x0 said:**
> We use the Development Release and so we're used to the apport dialog popping a hundred times everyday. It's OK, we signed up to this. 

There's only thing that bugs me about it. If you look at the dialog, it doesn't say what crashed unless you hit the "Show Details" button. See the examples below:

The error pop-up before you click "Show Details"
[ATTACH]224367[/ATTACH]
You don't know what crashed at this point. Maybe it's something you reported 30 seconds ago. Maybe it's something new. Apport already knows what crashed (see ls -lah /var/crash). But you won't know until you hit "Show Details". So you do.

[ATTACH]224369[/ATTACH]
The error pop-up after you click "Show Details". See the "ExecutablePath". You already knew about that via ls -lah /var/crash. Yeah, I already reported it. So it was pointless to click "SHow Details". If I had pressed Report it would be wasted time too.

Therefore, considering apport knows what crashed from the beginning, wouldn't it make more sense for the standard error dialog to just say what crashed, right after the "Sorry, Ubuntu has experienced something..." line? Then we would immediately know if we have to click "Show Details" or "Report" or if we should just ignore it.

It's a small UI change to display this string. But would make testing a little less annoying.

Regards,
Effenberg


Makes sense -- have apport say something like blah crashed, and has been reported here. Click something to take you to the report, or simply ignore it.

---

### Post by effenberg0x0 on 2012-09-19
> **guitara said:**
> Makes sense -- have apport say something like blah crashed, and has been reported here. Click something to take you to the report, or simply ignore it.

Yep, a small update to apport/gtk/apport-gtk.ui (Glade will do), but can make things a little easier on testers. Is it worth reporting?

Regards,
Effenberg

---

### Post by dino99 on 2012-09-20
> **effenberg0x0 said:**
> Yep, a small update to apport/gtk/apport-gtk.ui (Glade will do), but can make things a little easier on testers. Is it worth reporting?

Regards,
Effenberg

Yes you should (i will vote for)  ):P

---

### Post by Elfy on 2012-09-20
so will I

---

### Post by effenberg0x0 on 2012-09-20
Here's the report guys, sorry for the delay:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1053637](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1053637)

Please feel free to change and improve the bug title and description as you see fit.

Regards,
Effenberg

---

### Post by Elfy on 2012-09-21
Thanks effenberg :)

---

### Post by funicorn on 2012-09-21
apport isn't for me, which only records bugs and mistakes that developers suppose to happen. It really does little to help fix those exposed to user experience, which have to be manually filed by users and which usually are commented "insufficient information" by developers. Ever since I figure this out I have apport uninstalled, completely.

---

### Post by effenberg0x0 on 2012-09-21
> **funicorn said:**
> apport isn't for me, which only records bugs and mistakes that developers suppose to happen. It really does little to help fix those exposed to user experience, which have to be manually filed by users and which usually are commented "insufficient information" by developers. Ever since I figure this out I have apport uninstalled, completely.

I think what you are saying made sense some cycles ago. Many testers already said something in that sense. 

But now, due to technical changes in Ubuntu, changes in the way Ubuntu is managed from a developer point of view and changes in QA, it doesn't make sense anymore. Apport is useful.

If you haven't yet, visit [https://errors.ubuntu.com/](https://errors.ubuntu.com/) and wait for it to load the data (it is slow, unfortunately). Also read [https://wiki.ubuntu.com/ErrorTracker](https://wiki.ubuntu.com/ErrorTracker). The info you see there is really important. It allows testers and devs to know the state of the OS and to have a summarized view of the main current issues in real time. We can all prioritize the time we invest in Ubuntu using that info, instead of browsing through hundreds of LP reports. It allows for faster bug fixing by devs despite LP reports being answered or not (which is a slower manual task done by triaging). 

Regards,
Effenberg

---

### Post by thotz on 2012-09-21
I like your idea effenberg :)

---

### Post by funicorn on 2012-09-24
I don't think you fully know what I'm talking about. A simple but realistic example:
> 
The other day Unity upgraded to version 6.6.0, since when I found sometimes window animation went wrong: when you minimize a window and restore it from the unity panel, you see a totally black window there. If you drag it and move around, there is chance the window can be displayed normally, or there is not.

It's absolutely a bug. And it's a realistic bug, in that has negative impact on routine desktop operation. However apport won't see it. Users know it's a bug but developers do not because apport does not.

So how could I file this bug to launchpad and make sure it's SERIOUSLY treated by the developers ? If you do this more than one time, you know it's likely impossible. Most of the time this kind of bug report would be marked as 'lack of information' and laid aside.

The ironic thing is, usually the bugs only seen by human eyes are important and should be placed ahead.

> **effenberg0x0 said:**
> I think what you are saying made sense some cycles ago. Many testers already said something in that sense. 

But now, due to technical changes in Ubuntu, changes in the way Ubuntu is managed from a developer point of view and changes in QA, it doesn't make sense anymore. Apport is useful.

If you haven't yet, visit [https://errors.ubuntu.com/](https://errors.ubuntu.com/) and wait for it to load the data (it is slow, unfortunately). Also read [https://wiki.ubuntu.com/ErrorTracker](https://wiki.ubuntu.com/ErrorTracker). The info you see there is really important. It allows testers and devs to know the state of the OS and to have a summarized view of the main current issues in real time. We can all prioritize the time we invest in Ubuntu using that info, instead of browsing through hundreds of LP reports. It allows for faster bug fixing by devs despite LP reports being answered or not (which is a slower manual task done by triaging). 

Regards,
Effenberg

---

### Post by cariboo on 2012-09-24
You don't have to wait for apport to automgically notify you of the problem, you can manually report the bug using:

```
ubuntu-bug unity
```

Then follow up the report with as much extra information as possible, including screenshots.

---

### Post by effenberg0x0 on 2012-09-24
> **funicorn said:**
> I don't think you fully know what I'm talking about. A simple but realistic example:

It's absolutely a bug. And it's a realistic bug, in that has negative impact on routine desktop operation. However apport won't see it. Users know it's a bug but developers do not because apport does not.

So how could I file this bug to launchpad and make sure it's SERIOUSLY treated by the developers ? If you do this more than one time, you know it's likely impossible. Most of the time this kind of bug report would be marked as 'lack of information' and laid aside.

The ironic thing is, usually the bugs only seen by human eyes are important and should be placed ahead.

Ok, let me start at apport, because that's what this thread was about. And we must consider that other users will read this eventually, so it's important to spread correct information. Then I'll move on to the problem you are referring to (lack of a roadmap/transparency/formal process)

**APPORT**
Here's the thing: We can't expect developers to look at all bugs. Not now, not ever. Why? There are almost 100.000 open bugs with new ones coming in every minute. Have a look [here]("https://bugs.launchpad.net/ubuntu."):  Ubuntu will never have enough people to undertake this task. No proprietary software company does. We believe more people will adopt Ubuntu in the future and the flood of bug reports (valid, invalid, complete, incomplete, etc) will only increase. It's impossible for humans to even rank them, much less work though each of them.

As you know, when you have a bug that generates a crash, and therefore is detected by the whoopsie/apport system, you are prompted to let apport report that. Apport looks at your logs and grabs the crash specifics, which operate as "signature" of each bug. If this is in fact a severe bug, which affects many users, many reports that have the exact same "signature" will be automatically reported. This bug will quickly escalate to the top of the list you see in errors.ubuntu.com. Developers will look at the bugs that are in the top of the list (the most reported ones), and work on them. 

Considering that...
- We have limited resources. There's not enough people to rank/handle all bugs manually;
- The number of bug reports will only increase; It will become even harder for devs to handle them manually;
- There won't ever be enough people to work through each bug;
- Even if we try, we can't be as precise and correct as automated processes;
... it makes sense that we try to:
- Automate bug reporting and ranking;
- Focus efforts on the most reported / most frequent bugs, because they impact more users negatively.

Right now, that's how things are being handled. It's not perfect. As you have mentioned, some bugs are not seen by apport. If you have a look at apport repo, you will see that it is under active development.

And one of the things that you can see in apport Launchpad page, is that many contributions are "bugpatterns" (which "teach" apport to recognize more bugs - apport is gradually learning to handle more bugs, thus it will be better in the future).

So, although not perfect, apport is not only a good way to handle bugs in Ubuntu, it is also the only viable strategy in long term. So that's apport. There's nothing wrong with it. It's the only way we'll ever be able to handle bugs in Ubuntu. It's not perfect and it  will definitely improve over time. Hopefully someone will think of something smarter in the future. Right now I don't know of an alternative.


**LACK OF A ROADMAP, TRANSPARENCY AND FORMAL PROCESSES**
Now, what you put into question doesn't relate to apport and this thread. It relates to the fact that we don't have a proper place to report "characteristics" of the OS that, while not being the result of wrong code or creating a crash, have the potential to negatively impact end-users experience. We don't even have a word to define these, to be honest. There are localization errors, UX/UI that needs improvement and documentation that needs to be changed, updated or improved, just to mention a few. All of these are not properly bugs, in the most strict technical definition, but they have the potential to impact users negatively.

Then what? Well, we need to start formalizing these things. We should start by creating proper definitions and names to them. 

And users/contributors should be able to know how these "inconsistencies" (for the lack of a proper word) they will report will be handled (if they will be handled at all). We should think what would be the best way to report them, how and where. We need to define who will look at them, how, when. How will things that are not properly bugs be ranked? How will it ever be automated? 

There's no public, easily accessible, transparent roadmap and processes. Now only in this area but in many other areas in Ubutu and FOSS in general. We can't know these things right now, because we don't have this information. And I believe no one does. 

It's no one's fault. This is FOSS: A collage of code and other contributions coming from thousand of sources. There's an enormous amount of work being done everywhere and, as I mentioned, limited resources to deal with everything. 

A sort of "new" form of contribution, in which I believe strongly, is to define formal processes and a roadmap, as well as tools to allow everyone to have access to this information. 

As I already said here: There's no best practices we can import, adapt, adopt. Whatever we design, define, propose, approve, enforce, will be the best practices.

I think it is inevitable that we will eventually detach from the daily testing and the basic stuff, accept the fact that this is now a largely adopted and successful OS and allow ourselves to think in long-term strategies, such as what I mentioned above.

Regards,
Effenberg

---

### Post by funicorn on 2012-09-24
Thanks for this detailed explanation, Effenberg.  I understand lack of transparent/formalized roadmap to define/describe and/or report a problem is  suffering, for both users and developers. My point is, all the bugs behind this suffering are usually more important. But apport can never solve this.

For the above example, I'm sure it's a bug because it doesn't exist in the previous unity versions, and it happens right after unity upgrade. There is no crash, no warning, more precisely speaking it's a 'regression'. But these are artificial concepts and definitions. The reason behind all this is quite unique, there must be something wrong with the 'codes'. 

What I'm trying to prove is, there must be one way for the users to make the developers to believe there is something wrong with their 'codes'. That's really important, because I believe the problem can be very quickly solved once they believe it's a bug and start to check the 'codes', in which there are some parts they just changed in this upgrade and caused the problem. However apport can not do that. We need a totally different way to do this.



Maybe. I'll try your steps and see what happens.

---

