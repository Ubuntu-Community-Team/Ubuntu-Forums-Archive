---
title: "GAH!!! Open Office needs to work on this..."
date: 2007-12-05
forum: The Cafe
---

### Post by SomeGuyDude on 2007-12-05
Okay, I need to vent a little because otherwise I'm going to break something.

I write. And yesterday I started on a new project, utilizing a document template I got. It was a .doc and so I opened it and then started writing. I clicked "save" every so often, all's well. Close OO, re-open, get it from the "recent documents" list.

It didn't click that the /tmp/ directory meant it would be GONE as soon as I rebooted.

I think the Open Office folk might want to consider changing how their program deals with temporary documents. There's no reason for me to save a document that's in the TMP folder, dammit, if I open a document from the web and click "save", I should get the "choose location" dialog.

I lost 20 pages of writing and I'm about to throw my computer out the window. This is ridiculous.

---

### Post by Lostincyberspace on 2007-12-05
I have had that happen a couple of time.

---

### Post by SomeGuyDude on 2007-12-05
Is there anything to be done about it? Linux seems pretty merciless in that if you accidentally lose something from the TMP folder it's just gone.

One thing I'd like to give Windows credit for. TMP files stick around for a while just in case you do something stupid.

---

### Post by Kingsley on 2007-12-05
Send a bug report to OpenOffice.org.

---

### Post by SunnyRabbiera on 2007-12-05
> **SomeGuyDude said:**
> Is there anything to be done about it? Linux seems pretty merciless in that if you accidentally lose something from the TMP folder it's just gone.

One thing I'd like to give Windows credit for. TMP files stick around for a while just in case you do something stupid.

well this is why I set open office to save itself every minute or so, I also tell it to create backup files.

---

### Post by Whiffle on 2007-12-05
Might I suggest learning LaTeX? :)

---

### Post by SunnyRabbiera on 2007-12-05
LaTeX is alright, but personally I can do without it

---

### Post by hanzomon4 on 2007-12-05
I could never figure out wat LaTex was exactly.

---

### Post by SomeGuyDude on 2007-12-05
> **SunnyRabbiera said:**
> well this is why I set open office to save itself every minute or so, I also tell it to create backup files.

That's the thing. I did save it every minute or so. The problem was that the document it saved was in the /tmp/ folder so it went away as soon as I restarted the system. My beef is that it's completely illogical to open up a document, house it in the /tmp/ folder, and then have the "save" button just keep saving it in an area that is inherently not going to remain "saved" for very long.

The backup idea seems good, however.

---

### Post by sloggerkhan on 2007-12-05
Mine only uses the tmp folder if I open a document off the internet direct from browser... or am I misunderstanding something?

---

### Post by SomeGuyDude on 2007-12-05
> **sloggerkhan said:**
> Mine only uses the tmp folder if I open a document off the internet direct from browser... or am I misunderstanding something?

That's exactly what happened. Opened up a document from the browser (a template, specifically), but when I clicked "save" it just saved. Me, being the idiot I am, assumed that if I'm hitting the "save" button, the document will be... saved. I suppose I didn't think about "where" the document was, since after I closed and re-opened OO, it was still in the recent documents list.

Apparently, though, since documents opened via the browser go into the /tmp/ folder, it doesn't matter how many times you save it, the thing's gone upon system restart.

Thus, my problem is that if you open a document from the internet, when you hit "save" you should get a dialog that asks you where you'd like to save it, just like if it's a new document. It's not like I'd ever WANT to save a document in the /tmp/ folder.

---

### Post by igknighted on 2007-12-05
> **SomeGuyDude said:**
> Okay, I need to vent a little because otherwise I'm going to break something.

I write. And yesterday I started on a new project, utilizing a document template I got. It was a .doc and so I opened it and then started writing. I clicked "save" every so often, all's well. Close OO, re-open, get it from the "recent documents" list.

It didn't click that the /tmp/ directory meant it would be GONE as soon as I rebooted.

I think the Open Office folk might want to consider changing how their program deals with temporary documents. There's no reason for me to save a document that's in the TMP folder, dammit, if I open a document from the web and click "save", I should get the "choose location" dialog.

I lost 20 pages of writing and I'm about to throw my computer out the window. This is ridiculous.

I didn't read this, and I'm not sure if I will... but I need to point out that regardless of whether or not the points you make have validity, you ended any and all worthwhile discussion that could take place with your title.  So while I feel for you having lost work, starting a flamewar isn't gonna help get OO.o fixed or your work back.

---

### Post by Whiffle on 2007-12-05
I honestly see nothing wrong with the title and think its a valid point.  I know how it feels to save something late at night and then not have it in the morning...it sucks.

---

### Post by igknighted on 2007-12-05
> **SomeGuyDude said:**
> That's exactly what happened. Opened up a document from the browser (a template, specifically), but when I clicked "save" it just saved. Me, being the idiot I am, assumed that if I'm hitting the "save" button, the document will be... saved. I suppose I didn't think about "where" the document was, since after I closed and re-opened OO, it was still in the recent documents list.

Apparently, though, since documents opened via the browser go into the /tmp/ folder, it doesn't matter how many times you save it, the thing's gone upon system restart.

Thus, my problem is that if you open a document from the internet, when you hit "save" you should get a dialog that asks you where you'd like to save it, just like if it's a new document. It's not like I'd ever WANT to save a document in the /tmp/ folder.

EDITED (didn't read far enough :P)

I would bet that if you check your browser temp files (somewhere in ~/.mozilla if you are using firefox) you will find the saved document.

EDIT#3 (and bad news if you are using gnome, unfortunately)...

Gnome seems to create a directory in home, its randomly named (.fr_df432 was my one when testing IIRC) and put the file being used in it, then deletes the folder upon close of the file... nothing in trash either.

Like you had mentioned it was also in /tmp, but that (as you well know, unfortunately, is wiped upon shutdown).  If this is really critical stuff you could ghost you harddrive, but having booted again, it might have been written over and I don't know how successful it would be.

---

### Post by sloggerkhan on 2007-12-05
man igknighted, you have sitck up yours?
Anybody'd be pissed after losing a bunch of work.

I always thought the temp folder made sense for docs of the net, 'cause usually if I want to keep them, I save them to disk, instead of open directly. But I do think that when you start working on a template and go to save, it should ask where. Because it should be saving a new file based off of the template.

---

### Post by igknighted on 2007-12-05
> **Whiffle said:**
> I honestly see nothing wrong with the title and think its a valid point.  I know how it feels to save something late at night and then not have it in the morning...it sucks.

Valid point, yes.  We're here to solve probs (tho not so much in the cafe, but w/e).

Title is like a trolling title.  How many threads do we get here that start "________ App needs to do _______ better", especially with some awesome onomotopeia like "gahh" thrown in for good measure, along with some all caps and excessive exclaimaition marks... they are always trolls or first time users who think they are offerring some great insight.  The thread didn't fit that vein, but you get people who open it expecting that and you've ruined the discussion.  The discussion he wants to have is legit, that's not my point.  My point is the title biases the readers to expect trolling.

---

### Post by Whiffle on 2007-12-05
I honestly did not expect to see trolling, otherwise I wouldn't have opened the thread.

---

### Post by SomeGuyDude on 2007-12-05
If you'll notice, the titles of each of your posts has been edited because I attempted to change the thread title. But apparently I can't do that.

I don't apologize for the "GAH!!!" or the rest, just that I didn't specify what I was talking about. I lost a few hours of work and I actually was pretty restrained in writing the title. Worse still, it's impossible to "re-write" what you've lost and keep it loyal to what you ad before any more than if you're telling a story you can start over when you're already partway through. So just to get back to where I was is going to take a lot longer than it took to get there in the first place.

All because OO/Swiftweasel/GNOME/whatever decided that it makes sense to open in and save to a folder that cannot be recovered when you reboot.

Working on finding the Mozilla folder, though.

---

### Post by kelvin spratt on 2007-12-05
You need to go to tools options paths In Open Office change your temp files from temp folder, just as you would in any operating system, mine are in my home folder under office saved files its all very elementary to me, that does mean you have to remove them manually,  temp files are temp files and  removing temp files  in the temp  folder keeps the system lean. Read about the Linux operating system it goes into great detail why temp files are removed when the system is restarted.

---

### Post by anaconda on 2007-12-05
there IS a way to undelete files if you haven't overwritten them yet (ie. overwritten the same space that had them..)

sorry.. cant remember the names of those undelete programs now..
photorec?

---

### Post by mdsmedia on 2007-12-05
> **kelvin spratt said:**
> You need to go to tools options paths In Open Office change your temp files from temp folder, just as you would in any operating system, mine are in my home folder under office saved files its all very elementary to me, that does mean you have to remove them manually,  temp files are temp files and  removing temp files  in the temp  folder keeps the system lean. Read about the Linux operating system it goes into great detail why temp files are removed when the system is restarted.Agreed, temp files are temporary for a reason, which is why I agree that OOo should probably change where it saves files to, if you SAVE the file after editing.
However, and this is coming from a 2yo nOOb, what IS the difference between the /tmp folder and any other folder, as far as OOo is concerned? You've opened the file in /tmp and saved it in /tmp.....how does OOo know the difference?
Then there is the question of it being a template file. If that's the case, and you're not simply editing the template, (a)Why wouldn't you save it to a different location OR (b)If you've opened a template and you're creating a document, why doesn't OOo recognise the difference and ask where to save the new document. The Template is SUPPOSED to be retained as is, isn't it?

---

### Post by gn2 on 2007-12-05
One of the first things I was ever taught about using computers was to always "Save As" rather than "Save" the first time you want to save any work.

I'm astonished that anyone who has used computers for a while wouldn't do this? :confused:

---

### Post by Darkhack on 2007-12-05
> **gn2 said:**
> One of the first things I was ever taught about using computers was to always "Save As" rather than "Save" the first time you want to save any work.

I'm astonished that anyone who has used computers for a while wouldn't do this? :confused:

My high school computer teacher always told us to do "Save As..." rather than Save the first time as well.  Most people simply assume that the computer isn't going to do something stupid like save it in /tmp and thus they don't feel it is crucial.

I type all of my documents on Google Documents so in case my computer bursts into flames, I can just login at another computer and resume writing.  I then copy and paste the text over to a word processor and apply any formatting I need and then print.  I just type essays for school, so I don't need any super advanced word processing features.

---

### Post by mozetti on 2007-12-05
> **gn2 said:**
> One of the first things I was ever taught about using computers was to always "Save As" rather than "Save" the first time you want to save any work.

I'm astonished that anyone who has used computers for a while wouldn't do this? :confused:

I actually have my MS Word toolbar for work set up this way to avoid problems - remove "Save" button and replace it with "Save As...".

---

### Post by igknighted on 2007-12-05
Lets not forget that there is a reason that files are saved in /tmp and deleted upon shutdown... otherwise crap build up in the system just like windows.  I open many writer/calc/impress docs from the internet, and very rarely do I want them saved locally.  Every day in class I get an Impress presentation, and usually a few code samples and flowcharts... I don't want this cluttering my computer.

---

### Post by popch on 2007-12-05
A 'funny' thing happened to me just now. One of my users called and told me he had opened a text document which he had received by mail. After working some two hours on that document he saved and closed both the document and the mail. Now he can not find the changed document any more. Neither can I.

He used MS Word 2003 to work on the document. The mail system is MS Outlook 2003. The OS is Windows XP.

---

### Post by Crashmaxx on 2007-12-05
> **gn2 said:**
> One of the first things I was ever taught about using computers was to always "Save As" rather than "Save" the first time you want to save any work.

I'm astonished that anyone who has used computers for a while wouldn't do this? :confused:

I thought that if you press "Save" in most any program and you haven't yet saved it, it will prompt you the same as "Save As". Unless you mean to imply that people save stuff to wherever the default is, which I couldn't believe either.

To the OP, I agreed that "Save" should act like "Save As" for stuff in /tmp and in general when you load a new file. But I hope this teaches you a lesson that you should keep your files organized and always save them where you need them to be. I wouldn't have this problem, because unless I know I have a copy of a document in the format I want, where I want, I do "Save As" to try to put it where I want it, in the right format, with a proper name, and worse case is its already there and I overwrite it and then can use "Save".

Part of the reason I don't use tracker or any of these new fangled "Desktop Search" stuff is that I keep my stuff organized so I don't need to find it. And I think it really encourages bad practices of leaving files wherever in a big mess and just finding them later.:x

What I have found to be great for schoolwork, is first to save it to a network drive if you can, so you can get the files anywhere. In my case, they gave us SSH access so I just mounted it as a share and save everything for school there. Second, I was told of a great way to organize the files, first by semester, then by class, instead of just "Documents". Makes finding my schoolwork no problem, too bad it doesn't make doing it any easier.#-o

---

### Post by lswest on 2007-12-05
you can also save it do disk when downloading it from firefox...THEN open it and it gets saved where the file is, so in this case where ever firefox saves its downloads "to disk" (i have a downloads folder in my home folder).  It's a good happen to get in to...

---

### Post by macogw on 2007-12-05
> **hanzomon4 said:**
> I could never figure out wat LaTex was exactly.
It's a typesetting language.  You have total control over layout, and you can do massive "change everything that's like x to have this style" things like when you use CSS instead of inline styles on a webpage.  It also lets you make *amazing* formulas.  That's how they get the nice-looking formulas in math books instead of the funny way they'd look if you tried to type them inline.  It's also how Wikipedia gets nice formulas on their pages.

---

### Post by macogw on 2007-12-05
> **Darkhack said:**
> My high school computer teacher always told us to do "Save As..." rather than Save the first time as well.  Most people simply assume that the computer isn't going to do something stupid like save it in /tmp and thus they don't feel it is crucial.


I wouldn't really call it stupid.  "Save" means "I want to save it wherever it is currently located."  "Save As" means "I want to save another copy somewhere else."  Anything from the internet is temporary, otherwise you'd have a big chunk of the internet cached on your hard drive.

---

### Post by Darkhack on 2007-12-05
> **macogw said:**
> I wouldn't really call it stupid.  "Save" means "I want to save it wherever it is currently located."  "Save As" means "I want to save another copy somewhere else."  Anything from the internet is temporary, otherwise you'd have a big chunk of the internet cached on your hard drive.

I'm aware of the technical meaning behind it, but it's bad usability to have something be "saved" and then disappear on the next reboot.  When a file is "opened" from a source where it is not possible to save back to, such as a CD-ROM, RO drive, or a link from a webpage or email attachment, then it should be treated as a new document that hasn't been saved; even if it is technically saved in /tmp.  And as you know, when you select "Save" on a new document, it treats it like a "Save As...".

---

### Post by bruce89 on 2007-12-05
People should have a reasonable knowledge of how to use a file system before trying to do anything.

---

### Post by Darkhack on 2007-12-05
> **bruce89 said:**
> People should have a reasonable knowledge of how to use a file system before trying to do anything.

True, and there are some users who are beyond help who must have an administrator set up permissions to keep them from deleting their entire disk and must stand over their shoulder to help them do anything.  However, I also believe that a reasonably knowledgable person should be able to use a computer and expect predictable behavior.  I don't think expecting a computer to save a document when clicking save was out of the question.  As I said before, when a document is opened from a read-only source, it should be treated as a new document where upon "Save", the "Save As..." dialog appears.  It might even be reasonable to have a dialog with, *"Are you sure you wish to save to this location?  All documents here are temporary and deleted upon the next boot."* with a checkbox saying "I know what I'm doing, don't ask me again for this document" and "I know what I'm doing, don't ask me again ever".  After that point *then* we can point and laugh while declaring PEBKAC.

Going slightly off topic, I overheard a conversation a guy was having today in which his brand new laptop (with Vista) had gotten 500+ viruses and would no longer boot.  It's the week before finals and he said he had to rewrite an entire research paper for Friday (today is Wednesday).  While I think the guy was an idiot for not backing up his documents and visiting all those porn sites, I also believe the computer should try to at least stop people from stabbing themselves over and over, while at the same time, not treating them like they ride the short bus to daycare.  You have to find a balance and I think this thread is an example of where the OP had a reasonable expectation and the computer made his life more difficult than it needed to be.

---

### Post by the yawner on 2007-12-05
> **popch said:**
> A 'funny' thing happened to me just now. One of my users called and told me he had opened a text document which he had received by mail. After working some two hours on that document he saved and closed both the document and the mail. Now he can not find the changed document any more. Neither can I.

He used MS Word 2003 to work on the document. The mail system is MS Outlook 2003. The OS is Windows XP.
Have him check on folder C:\Document and Settings\<username>\Local Settings\Temp

On a related note, how is it the the .doc template got saved on /tmp?

---

### Post by bruce89 on 2007-12-05
> **the yawner said:**
> On a related note, how is it the the .doc template got saved on /tmp?

I suspect they created a new document from a template, and it got saved to /tmp.

I notice that all files downloaded from Epiphany go into ~/Downloads.

---

### Post by Vadi on 2007-12-05
Ouch that sucks.

And really they should give a warning.

---

### Post by Palmyra on 2007-12-05
I am thinking there is a way.  There's nothing that is literally deleted on a computer, except for what is wiped.

---

