---
title: "Case sensitivity"
date: 2006-09-29
forum: The Cafe
---

### Post by sicofante on 2006-09-29
I've heard OSX has got rid of UNIX case sensitivity. I believe that's a good thing. We humans use case to very different things than computers, and computers should work as close as we humans do. So my question is: do you guys know if there are any plans to free Ubuntu users from case sensitivity?

---

### Post by morphodone on 2006-09-29
I'm going to go out on a limb here and say that most
of us think case sensitivity is a good thing.

I doubt ubuntu has any such plans.

---

### Post by llamakc on 2006-09-29
I can promise you I'll leave Ubuntu forever if it makes such an idiotic move.

I'd also like to see your sources for such a claim.

---

### Post by aysiu on 2006-09-29
[Here](http://www.kernelthread.com/mac/osx/arch_fs.html)'s a source: > Insensitive!

Note that HFS+ is a case preserving, case insensitive filesystem, which can be rather jarring in situations such as the following:
```

# tar -tf freebsd.tar 
FreeBSD.txt 
freebsd.txt 
# The tar file contains two files 
# tar -xvf freebsd.tar 
FreeBSD.txt 
freebsd.txt 
# ls *.txt 
freebsd.txt
```
The Apple Technical Note titled [HFS Plus Volume Format](http://developer.apple.com/technotes/tn/tn1150.html) describes HFS+ internals in great detail. 

---

### Post by noynac on 2006-09-29
Personally, I would like to see case sensitivity done away with. This would be an interesting subject for a poll.

noynac

---

### Post by sicofante on 2006-09-30
First thing for discussing anything in a civilized way is not calling the other side "idiotic". There are obvious reasons for a computer to be case sensitive, being the main one that is easier *to program*. But computers and most especially desktop systems are built to be used by humans and, I must insist, humans don't believe that "dog", "Dog", "dOg", "doG" or "DOG" are different names for a thing. A document (a file) for a human is a thing with a name and it makes little sense to make the distinction of file names based on case sensitivity.

When designing a system to be used by humans, there has to be a clear separation between the system's needs and the user's needs. I really don't care if filenames only used by the system are case sensitive, but names used regularly by the user MUST be case insensitive if we intend the system to be easy on humans. It's up to the programmers to decide if they have it easier by making the whole system case insensitive or a mix of both ways, but there's little doubt about how humans put names to things.

---

### Post by llamakc on 2006-09-30
To be fair, when I said "idiotic" it was in reference to the word "it" of which I am a large part of, as is many others. I should have chosen more carefully because I don't want to insult others with my late night poor choice of words.

My apologies to the communitY.

---

### Post by alecjw on 2006-09-30
Case sensitivity rocks! If case sensitivity was removed, when you upgraded to a case insensitive version of Ubuntu, your ext3 partition might still have multiple files with the same name in different cases. Ubuntu would probably do something like merge the 2 files together, or dlete one (or both). Not nice.:(

Edit: I have an idea to make things easier:
If you were to try to open a file called fIlEnaME.eXt, but there was no file with that name, but there was one with the same name in a different case (eg Filename.EXT, it should open that one.

---

### Post by maniacmusician on 2006-09-30
case sensitivity can be a pain sometimes when you're using terminal, but in the end its a very good thing.

---

### Post by sicofante on 2006-09-30
> **maniacmusician said:**
> case sensitivity can be a pain sometimes when you're using terminal, but in the end its a very good thing.
May I ask why is it "a very good thing" for the Regular User? Let me make clear that I'm talking about a desktop system designed for the home/office user. AFAIK this is the target of the Ubuntu OS in its desktop version (server OSs are a whole different story, since they're used by computer trained people). I know programmers like things as they are (after all, they created them and got used to them for decades!), but the other two OSs for the desktop understood what I've stated: in the world of ordinary people (i.e. non-geeks) things are named without case in mind. Why would it be good to do it otherwise?

---

### Post by maniacmusician on 2006-09-30
All good filesystems are case sensitive...to make an OS that doesn't use the case sensitivity would cause problems as aysiu showed in his post above.

Other than that, I don't know. I like case sensitivity.

---

### Post by bruce89 on 2006-09-30
You can't expect Ubuntu to remove a age-old UNIX thing such as this, or indeed the no feedback on password thing.

---

### Post by morphodone on 2006-09-30
What examples are there where case sensitivity is troublesome to 
a desktop user?

Most of the time this problem arises in the terminal where a desktop
user may not even venture too often.  Also, bash has the nice utility
built in where it autocompletes when you hit the 'tab' key.

So if you had a funny cased word bash would be able find it anyway.

By the way, how would make a file called dOG, dOg, doG, anyway?

---

### Post by maniacmusician on 2006-09-30
but if you forget the first letter is capitalized (which is usually the case), you'll keep hitting tab and wonder wtf is going on. then you backspace, do ls, and go "ohhh, it's capitalized." and then do it right. so that's sometimes annoying. 

but i'm pro-case sensitivity.

---

### Post by sicofante on 2006-09-30
I'm sorry but the problem depicted by Aysiu comes _after_ the original filesystem (where that tar file comes from) is designed as case sensitive. There's no place for such things happening if the system is properly designed and partners working for the system know that beforehand. The problem depicted is caused because Mac OSX has its origins in a case sensitive system, but everyone working for OSX is, or should be, aware of that.

On the other hand, I don't quite buy that file systems are designed to be case sensitive or its performance would suffer from being case insensitive. I rather believe that, regarding case sensitivity, they have been left "as is" right from the beginning because UNIX, the mother of it all, was designed without a home user in mind (there were no "Personal Computers" back then...)

---

### Post by morphodone on 2006-09-30
> **maniacmusician said:**
> but if you forget the first letter is capitalized (which is usually the case), you'll keep hitting tab and wonder wtf is going on. then you backspace, do ls, and go "ohhh, it's capitalized." and then do it right. so that's sometimes annoying. 

but i'm pro-case sensitivity.

I'll concede that one example, but doing a 'ls' isn't that big
of a deal to me. Maybe I just got used to it over time.

I ran into an issue in Windows one time because of case INsensitivity.

For some reason I made another folder called 'progams' instead of 'Programs'
and Windows would not let me delete the folder because it was protected.
So I was stuck with both a 'Programs' and 'programs' folder because Windows
did not see a difference in them. 

Bogus

---

### Post by sicofante on 2006-09-30
> **morphodone said:**
> What examples are there where case sensitivity is troublesome to 
a desktop user?

Most of the time this problem arises in the terminal where a desktop
user may not even venture too often.  Also, bash has the nice utility
built in where it autocompletes when you hit the 'tab' key.

So if you had a funny cased word bash would be able find it anyway.

By the way, how would make a file called dOG, dOg, doG, anyway?
I'm not sure I understand your last question. But let me guess: you have a file called Dog.jpg and another one called dog.JPG. They are the same picture of the same dog. Would you say this is both the right way to name these two pictures and that is how an ordinary person would think? My whole point is that systems should be designed with the user in mind, not the developer.

You're right that most of the time, the problem lies in the terminal. As a matter of fact, there's another annoying problem there when it comes to filenames in Linux systems: using spaces or accented characters (the Real World wasn't made in English...) will get you in trouble. Again, this is not how people "think". I (and most of my compatriots) would name a folder "Fotos de España" rather than "fotos_de_espana", but I'm digressing... I agree though that a higher goal is to keep the home/office user away from the terminal. This is far from happening and case sensitivity adds still another layer of user "unfriendliness" to it.

Away from the terminal, I can think of people "Saving As..." a document and naming it with the same name but different case, then getting mad at the computer for having two "identically named" files and yelling "Now which one is the good one?". I've seen it happening...

Another typical situation arises when you are talking about the files. You ask your friend to send you that dog.jpg picture and he just sends you the other DOG.JPG one...

> **bruce89 said:**
> You can't expect Ubuntu to remove a age-old UNIX thing such as this, or indeed the no feedback on password thing.

Oh yes I can and I actually do. If everything should be as UNIX was designed 40 years ago, most people like myself would have ran away from this thing years ago. Thanks god, there are a number of developers thinking of the non-geek user and I hope they're just listening here... :)

---

### Post by aysiu on 2006-09-30
Isn't it a moot point, though, as the only time case sensitivity would screw up a user would be *in* the terminal, anyway?

If the user is using GUI, why would case sensivity frustrate her?

---

### Post by Kindred on 2006-09-30
As long as you're aware of it, I don't see how it's ever a problem.  I'm a fan of case sensitivity anyway.  Not that I can see this ever changing..

---

### Post by Shay Stephens on 2006-09-30
I don't see any personal benefit to case sensitivity.  It goes against how most people are taught.  And I believe it to be just an old technique used when resources were slim.  But come on, we have plenty of disk space and processing power now to deal with this right?!?!

I would welcome seeing case insensitivty.  Since it obviously doesn't do anything beneficial for me (prove me wrong with a non-obscure example or two).  At least case insensitivity would let me be lazier, which is always a welcome treat :-)

---

### Post by sicofante on 2006-09-30
Exactly. I could bet that everyone in favor of case sensitivity loves computers and is just used to it, while every casual user (the famous "rest of us") just doesn't understand why the computer is so "stupid" to believe a .JPG is not the same as a .jpg...

I believe this is why Apple took so much effort in removing case sensitivity from OSX.

---

### Post by bruce89 on 2006-09-30
> **comomolo said:**
> Exactly. I could bet that everyone in favor of case sensitivity loves computers and is just used to it, while every casual user (the famous "rest of us") just doesn't understand why the computer is so "stupid" to believe a .JPG is not the same as a .jpg...

Nautilus recognises a JPEG if it has a .JPG or a .jpg extension.  In fact, extensions are not required in Linux at all as the programs recognise a file type by its content, not by its extension.

---

### Post by sicofante on 2006-09-30
That's a good thing done by Nautilus. I know the extensions are not necessary in Linux (neither in OSX, AFAIK and in some Windows programs that will read the file headers instead of trusting the extension). THAT is a very good thing and if this were a Windows forum I'd be ranting against extensions, which are as "unnatural" as case sensitivity (and the way Windows just hides the extensions to Limited Users is just sooo wrong...) It was probably a bad example. I think the point has been made anyways.

---

### Post by aysiu on 2006-09-30
I'm in favor of case sensitivity the way it's implemented now because one of the appeals of Ubuntu for me is the mix of advanced, intermediate, and beginner users.

If you get rid of case sensitivity in the terminal, advanced users will stop using Ubuntu, and many intermediate users will follow.

Right now, in the GUI, it's a non-issue. Both Nautilus and KDE sort by default regardless of case, and both have a GUI find that is also case-insensitive.

As I tried to point out earlier (and was handily ignored), it's a moot point:

1. If you're afraid of case sensitivity, you're also likely afraid of the terminal, and you're not likely to run into case sensitivity problems in the GUI.

2. If you're using the terminal, you're a slightly more advanced user, and you'd better get used to case sensitivity and stop whining.

---

### Post by alecjw on 2006-09-30
> **aysiu said:**
> I'm in favor of case sensitivity the way it's implemented now because one of the appeals of Ubuntu for me is the mix of advanced, intermediate, and beginner users.

If you get rid of case sensitivity in the terminal, advanced users will stop using Ubuntu, and many intermediate users will follow.

Right now, in the GUI, it's a non-issue. Both Nautilus and KDE sort by default regardless of case, and both have a GUI find that is also case-insensitive.

As I tried to point out earlier (and was handily ignored), it's a moot point:

1. If you're afraid of case sensitivity, you're also likely afraid of the terminal, and you're not likely to run into case sensitivity problems in the GUI.

2. If you're using the terminal, you're a slightly more advanced user, and you'd better get used to case sensitivity and stop whining.

All hail aysiu! You can't have a non-case sensitive OS running on a case sensitive FS. If you have an ext3/resiserfs/hfs partition, it is likeley to have multible files on it with the same name in a different case. Ubuntu would need it's own case-insenstive file system. - noncasesensitiveext3fs or caseinsensitivereiserfs maybe? HELL NO!

---

### Post by sicofante on 2006-09-30
aysiu: it's obvious you like your system as it is. I tend to "handily ignore" people telling others to stop whining and the like. I made my points which are perfectly valid. It's not a competition to see who's right or wrong. I'm happy you're happy with your non-human system for naming things.

---

### Post by alecjw on 2006-09-30
> **comomolo said:**
> I'm happy you're happy with your non-human system for naming things.

And I'm happy that you're happy that ayisu's happy for the same reason that I'm happy.

---

### Post by bruce89 on 2006-09-30
> **comomolo said:**
> aysiu: it's obvious you like your system as it is. I tend to "handily ignore" people telling others to stop whining and the like. I made my points which are perfectly valid. It's not a competition to see who's right or wrong. I'm happy you're happy with your non-human system for naming things.

Well, it is a UNIX thing that has been around for a long time, what issues are there that could be solved by breaking this 40 year old tradition?  Even NTFS is case sensitive (but windows isn't) - [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features)

You could say that the way that PNG's are encoded are non-human top, as it is binary data which can't be read by humans.

---

### Post by aysiu on 2006-09-30
I'm actually not telling people to "stop whining and the like." I'm actually telling people there's no point in arguing about this.

The way it is now suits most users:

Advanced users are happy it's case sensitive in the terminal.

Beginning users are happy it doesn't *appear* to be case sensitive in the GUI.

If you want to keep ignoring my point (instead of what you *think* my point is), then I'll "handily ignore" you, too.

---

### Post by sicofante on 2006-09-30
> **bruce89 said:**
> what issues are there that could be solved by breaking this 40 year old tradition?
That's just a computer tradition. Since personal computers were invented (the Mac first and then Windows) Regular Users have never seen a bit of that tradition (thankfully). I understand the geekiness in it, but it has nothing to do with ordinary people who use their computers as a tool. The issue to be solved is a computer behaving like humans do instead of behaving like computers do. That's what usability is all about.

> You could say that the way that PNG's are encoded are non-human top, as it is binary data which can't be read by humans.No. The computer can encode things as much as it likes. It can even put the names of the files in its own alphabet, as long as it behaves the same way as humans do when it comes to interface with humans. The PNG image is shown as a picture and by that it behaves like a "real life" picture. File names in real life are case insensitive. Nautilus seems to deal somehow with that and that's a good thing. What I'm saying is that as long as the user has to deal with file names, they should behave like real life names. I don't really care how the FS encodes these real life names. All a Regular User needs is that they behave like they should.

I might just say: what's the benefit for the computer itself to have two file names IN THE SAME DIRECTORY only differentiated by its case?

---

### Post by Bloodfen Razormaw on 2006-09-30
I would much prefer a case-insensitive OS, but the UNIX world settled on case sensitivity long ago, and we are stuck with it until UNIX finally dies and is replaced with something saner.  Ubuntu should definitely not try to go case insensitive on its own.  That is just begging for application breakage across the board.

I'd rather the filesystem be abstracted away entirely.  My documents should be found based on metadata and contextual information, and arranged based on my on-the-fly requirements.  I want a system where I don't need to know a file's name, and I don't need to give them one.

---

### Post by sicofante on 2006-09-30
> **Bloodfen Razormaw said:**
> I'd rather the filesystem be abstracted away entirely.  My documents should be found based on metadata and contextual information, and arranged based on my on-the-fly requirements.  I want a system where I don't need to know a file's name, and I don't need to give them one.
I totally agree.

=D>

---

### Post by IYY on 2006-09-30
> I'd rather the filesystem be abstracted away entirely. My documents should be found based on metadata and contextual information, and arranged based on my on-the-fly requirements. I want a system where I don't need to know a file's name, and I don't need to give them one.


I think this is where Windows and Apple are going, and I don't like it. It might be better for novices, but is horrible for experts. It feels like you need to trick the computer into doing what you want.

---

### Post by Bloodfen Razormaw on 2006-09-30
Why, pray tell, would an expert want to work more slowly and inefficiently?  Finding documents by filename using static file hierarchies is very slow.  The superiority of metadata based browing and dynamic organization is apparent in the popularity of software like Amarok.  If I have music videos and music, why do I have to choose whether to have a File Type/Artist/Album hierarchy or a Artist/Album hierarchy?  At different times I want my files related in different ways.  Why am I not allowed to work efficiently in one of those situations?

And no, Microsoft and Apple don't do anything close to this.  The closest thing is Tenor, which was scaled back so as to not meet its early promises of content/context browsing I believe.

---

### Post by xhaan on 2006-09-30
My case is always ignoring me and trivializing my feelings...
I need a case that is more sensitive to my needs. :cry:

---

### Post by cord on 2006-09-30
> **aysiu said:**
> I'm in favor of case sensitivity the way it's implemented now because one of the appeals of Ubuntu for me is the mix of advanced, intermediate, and beginner users.

If you get rid of case sensitivity in the terminal, advanced users will stop using Ubuntu, and many intermediate users will follow.

Right now, in the GUI, it's a non-issue. Both Nautilus and KDE sort by default regardless of case, and both have a GUI find that is also case-insensitive.

As I tried to point out earlier (and was handily ignored), it's a moot point:

1. If you're afraid of case sensitivity, you're also likely afraid of the terminal, and you're not likely to run into case sensitivity problems in the GUI.

2. If you're using the terminal, you're a slightly more advanced user, and you'd better get used to case sensitivity and stop whining.


Let me give you a common secnario. I dual boot with windows and I have over the years collected a large collection of comic books (some with more than 300 issues) in a directory so I can use a light weight image viewer to view them. The same thing goes with TV episodes.

Now, in nautilus and alot of gui applications for which I have found no option to disable case sensitivity, I have to make sure that everything is the same case. For example:

Comic1Issue1Page1 and comic1Issue1Page1 goes all out of whack. It is somewhat of an annoyance especially with larger sets of stuff.

In reailty my issue is that I wish there was an option in the guis to turn off case sensitivity for the purposes of sorting/ordering.

---

### Post by punkinside on 2006-09-30
i put everything in lowercase any way im too lazy to hit shift so :p

---

### Post by Shay Stephens on 2006-09-30
May we have a friendly debate :-)

> **aysiu said:**
> 2. If you're using the terminal, you're a slightly more advanced user, and you'd better get used to case sensitivity and stop whining.

That still is not a good reason to have case sensitivity now is it :-)  The only argument for it is that power users are used to it and without it they would leave?  Not really a feature benefit in my book, more like a legacy issue, but nothing more.

But I would also like to point out that whining is a cop out argument.  It's like a few hundred years ago saying:

> If you're reading the bible, you're a slightly more advanced user, and you'd better get used to reading latin and stop whining about having an english translation.

That argument doesn't serve the common good, it only serves the elite if you will.  So I still say, where is the benefit of having case sensitivity?

---

### Post by Virogenesis on 2006-09-30
No terrible ideal, you'll occur more breakages than anything.
This isn't a good thing for the user, nor is it any good for the community as the user will have a bad experience and blame it on linux rather than ubuntu.

Now what about about the server version, they either build two version or share the code, impentmenting such a change can affect things bad leaving holes where holes don't belong.

Linux isn't Mac os remember that, as Apple have total control this isn't the case on linux as its all made up of parts.

---

### Post by Iandefor on 2006-10-01
> **Shay Stephens said:**
> I don't see any personal benefit to case sensitivity.  It goes against how most people are taught.  And I believe it to be just an old technique used when resources were slim.  But come on, we have plenty of disk space and processing power now to deal with this right?!?! Do tell how using a quirk of the Roman alphabet to enable the use of 26 more characters in UNIX was predicated on a lack of processing power.
> **comomolo said:**
> I've heard OSX has got rid of UNIX case sensitivity. I believe that's a good thing. We humans use case to very different things than computers, and computers should work as close as we humans do. So my question is: do you guys know if there are any plans to free Ubuntu users from case sensitivity? I don't particularly see any good reasons for deliberately eliminating case-sensitivity and I haven't heard of any plans whatsoever for Ubuntu in terms of changing case-sensitivity in bash.

---

### Post by Shay Stephens on 2006-10-01
> **Iandefor said:**
> Do tell how using a quirk of the Roman alphabet to enable the use of 26 more characters in UNIX was predicated on a lack of processing power.
Well, like I was saying, it seems like it was originally done because it was easier to code to case sensitive rather than case insensitive operation.  But this is just me making guesses, since I still have yet to hear a real reason for **having** case sensitivity.  So I can only assume, I know that is dangerous ;-) ,what I did above.

> I don't particularly see any good reasons for deliberately eliminating case-sensitivity and I haven't heard of any plans whatsoever for Ubuntu in terms of changing case-sensitivity in bash.
I have not either, and don't think it will happen in the near term.  But I do find it very interesting that even the discussion meets with so much resistance and huffn' and puffn' ;-) hehehe

If you ask me, (and Eeyore would agree no one has) I think the discussion has hit a nerve, everyone knows case sensitivity is a pain, is old, and has nothing to recommend it other than historical use.  I think the real "reason" to keep it, is that it makes users feel elite in a small way.  And talk of removing it makes the formerly little club seem not so exclusive anymore.  Perhaps it is even an identity thing.  "We are linux, we have case sensitivty and no one else does, we are special." and talk of getting rid of that distinct "feature" is a personal affront.

But think about it, with continuing work on standardizing the desktops (e.g. Linux Standard Base and the work done to make packages work with that change), user friendly and intuitive apps (i.e. little upfront user skill required to be productive), and user interface polish and shine, I do think it is inevitable that the core will continue to be refined.  And eventually case sensitivity will be addressed the way it is being done in the gui, system wide, ideally I suppose in a backward compatible way.

---

### Post by aysiu on 2006-10-01
> **Shay Stephens said:**
> 
That still is not a good reason to have case sensitivity now is it :-)  The only argument for it is that power users are used to it and without it they would leave?  Not really a feature benefit in my book, more like a legacy issue, but nothing more.

But I would also like to point out that whining is a cop out argument.  It's like a few hundred years ago saying:

That argument doesn't serve the common good, it only serves the elite if you will.  So I still say, where is the benefit of having case sensitivity? You really quoted only half of my post, which was only half of my argument. The people who use the terminal *are* power users, and they *do* want case-sensitivity. The people who do not use the terminal aren't usually affected by case-sensitivity. So I don't see where getting rid of it is for the common good. It doesn't make a difference to one population, and it pisses the hell out of another population.

Keeping it as is keeps most people happy--terminal users can stay with what they're used to and what is generally the *nix standard, and GUI users don't know the difference anyhow.

This is very different from your example with the Bible, as plenty of people who read the Bible read it in English, but there are **not** plenty of terminal users who want to get rid of case sensitivity.

A far more appropriate example would be to say that all Bibles (even those printed for *seminarians*) would be printed in English because Aramaic, ancient Greek, and ancient Hebrew confuse laypeople. Laypeople wouldn't care because their Bibles are printed in English anyway, but seminarians would be quite upset about not being able to read the original languages. Does that make them "elite"? Is that just touching a "nerve"?

You say there's no benefit in keeping power users around (I would happen to disagree heavily with that--without power users, this community would disintegrate). Well, what's the benefit of getting rid of case sensitivity? Not really a whole lot.

As I said before (which you conveniently ignore), GUI users do not feel the effects of case sensitivity. They just point and click on files anyway, and both Nautilus and Konqueror default to sorting filenames without regard to case.

So who benefits?

---

### Post by henriquemaia on 2006-10-01
I jUsT lOvE cAsE sEnSiViTy.

I do. I really do.

---

### Post by beercz on 2006-10-01
> **henriquemaia said:**
> I jUsT lOvE cAsE sEnSiViTy.

I do. I really do.

So do I :-)   Keep it!!

---

### Post by grte on 2006-10-01
> **Shay Stephens said:**
> May we have a friendly debate :-)



That still is not a good reason to have case sensitivity now is it :-)  The only argument for it is that power users are used to it and without it they would leave?  Not really a feature benefit in my book, more like a legacy issue, but nothing more.

But I would also like to point out that whining is a cop out argument.  It's like a few hundred years ago saying:



That argument doesn't serve the common good, it only serves the elite if you will.  So I still say, where is the benefit of having case sensitivity?

So what's *your* argument?  That your idea of what's best actually has anything to do with the "common good"?  Forget that.  It's personal preference pure and simple, and you're angle is no better then the one you're arguing against.

Now, that being said, you can pry case-sensitivity from my cold, dead hands.

---

### Post by oedipuss on 2006-10-01
I think aysiu has a very valid point. The only time case sensitivity has been a *problem* for me, was with a very old windows UT cd, which had all its files in uppercase. Needless to say it wasn't er.. very official in the first place. 
On the other hand, it is rather easy to get used to it, since most if not all of the system files will be in lowercase, or in a way that makes much sense in mixed case (such as libGL). One exception would be the 'Desktop', which could be in lowercase just the same, for similarity with all the other directories.
As far as user created files go, I really can't see why someone would name his/her files with small weirdly similar names , dOG, Dog, dog etc, *and then need to access them from the terminal*, when the filename can be as descriptive as one likes. This would only be intentional, not by accident.
Finally, even in non-computer context, case isn't always equivalent. Acronyms and such can depend on case to be readable/distinguishable (hence 'DoG : D.. of G..' (or whatever) can be immediately recognized as an acronym and be differentiated from 'dog').

---

### Post by sicofante on 2006-10-01
> **IYY said:**
> It might be better for novices, but is horrible for experts.
I don't quite understand why, but I might as well add that the Linux model allows for home/office/casual (I prefer that over "novice") distros to live side by side with expert distros. The reason I'm watching Ubuntu and trying it is because it seems to be THE distro for the non-geeks and is somewhat taking the biggest effort in being easy. Experts have Slackware, Gentoo or Debian for its own fun. There's a bare need for a distro really focused in home/office/casual users and I hope Ubuntu takes that plunge seriously.

There's a great article/proposal about metadata based filesystems here:

[http://akaimbatman.blogspot.com/2005/06/linux-desktop-distribution-of-future_15.html](http://akaimbatman.blogspot.com/2005/06/linux-desktop-distribution-of-future_15.html)


> It feels like you need to trick the computer into doing what you want.That's all what programming is about... 


I must admit I've been a bit shortsighted when proposing this thread. Bloodfen Razormaw has really pointed to the right direction. Metadata based filesystems are the goal. I guess case insensitivity is just a little step in the right direction but probably too little.

---

### Post by Shay Stephens on 2006-10-01
Ok, since you want it, I will quote your entire message now instead of cutting it short for brevity ;) 

And remember, this is not an attack, I am just debating here to flesh out details that seem to be hard to come by.

> **aysiu said:**
> You really quoted only half of my post, which was only half of my argument. The people who use the terminal *are* power users, and they *do* want case-sensitivity.
But why?

> The people who do not use the terminal aren't usually affected by case-sensitivity. So I don't see where getting rid of it is for the common good. It doesn't make a difference to one population, and it pisses the hell out of another population.
Why, what does case sensitivty bring to the table?  Aside from just being used to using (which I am by the way) what other reason is there to recommend it.  What utility does it offer? How does it make ones life easier?

> Keeping it as is keeps most people happy--terminal users can stay with what they're used to and what is generally the *nix standard, and GUI users don't know the difference anyhow.
True enough I suppose, but by relying on that argument, one is really saying that there is no need to grow and evolve, and would likely be opposed to any changes regardless of it's benefits.  I have visions of grampa simpson shaking his fist at the whiper-snappers out there hehehe.

> This is very different from your example with the Bible, as plenty of people who read the Bible read it in English, but there are **not** plenty of terminal users who want to get rid of case sensitivity.

A far more appropriate example would be to say that all Bibles (even those printed for *seminarians*) would be printed in English because Aramaic, ancient Greek, and ancient Hebrew confuse laypeople. Laypeople wouldn't care because their Bibles are printed in English anyway, but seminarians would be quite upset about not being able to read the original languages. Does that make them "elite"? Is that just touching a "nerve"?
You're right, that is indeed a much better analogy.  So that leads me to ask then, is there a shell that allows for non-cases sensitive operation?  If not, it still seems like we need a "translation".

> You say there's no benefit in keeping power users around (I would happen to disagree heavily with that--without power users, this community would disintegrate). Well, what's the benefit of getting rid of case sensitivity? Not really a whole lot.
No, I never said that.  That would indeed be a bad and short sighted thing.  My point was that power users can be elitists and not want the unwashed masses into their club and resist tools that would make it easier for them to join.  That happens in any organziation and is not unique to linux.

> As I said before (which you conveniently ignore), GUI users do not feel the effects of case sensitivity. They just point and click on files anyway, and both Nautilus and Konqueror default to sorting filenames without regard to case.
I don't know if I would agree that I conveniently ignore it.  I do agree that the gui is largely free from case sensitivity, but not 100%.  But that is not my point really.  There are some out there that do use the command line and other tools in linux yet still do not enjoy or benefit from case sensitivity.  So I suppose I am speaking for them, much as you do for women when using "she" as a general third-person singular.

> So who benefits?
I am hoping to find a way all can benefit, but I suppose ultimately, I am hoping I will benefit ;)

---

### Post by punkinside on 2006-10-01
If anyone can give me ONE everyday use example of case sensivity ever being more of a slight annoyance when typing things at the terminal like:
```

 gedit /etc/x[tab]... [tab]... (OH right!) [backspace] /etc/X11/xorg.conf

```

ITS A NON ISSUE!!

Anyway, if it were to be rid of, you'd have to get EVERYONE in *at least* Debian & forks to go with it. otherwise you'll end up with a myriad of problems. Every single package out there would have to be case-sensivity proofed so as not to incurr in the libGL/libgl problems. I say, if it aint broke, why fix it?

---

### Post by Bloodfen Razormaw on 2006-10-01
> You're right, that is indeed a much better analogy. So that leads me to ask then, is there a shell that allows for non-cases sensitive operation? If not, it still seems like we need a "translation".
There can't really be a case-insensitive shell while there is a case-insensitive file system.  If the shell sacrifices case and the filesystem needs it, the shell would be practically useless.  You could try something like Scsh, since Lisp is traditionally not case sensitive, but that would only go for the shell command aspects, not the references to files.  Alternatively, ZSH's tab completion will handle case sensitivity issues IIRC, and even incorrect paths.  That is about as close as you can get.

---

### Post by Shay Stephens on 2006-10-01
I did some digging to see if I could find some reasons for case sensitivity that was a bit more understandable than the proffered "because" answers.

There seem to be a few main reasons:
1) Historical. Since linux began as an OS that the primary input was the keyboard, case sensitivity was relied on to speed up command entry.  Using switches like u and U mean different things.  So instead of having only 26 switches, with case sensitivity, you now have 52 switches to rely on without having to waste keystrokes.

This makes the most sense to me, and now that I think about it, I have used and relied on this utility myself.  Case insensitivity would make command lines more verbose and require more work to input.

(edit)But on thinking about this more, the app you are sending the commands to should be able to determine the differences between upper and lower case arguments without having to rely on the OS enforcing case sensitivity globally.

2) Performance.  Case insensitive operations (e.g. sorting) are slower.  The computer has to work harder to translate to "lazy" level.  But I would rather be lazy than to have the computer be lazy.  I mean come on, thats why I have a computer ;) hehehe

3) Historical again.  The C language is itself case sensitive.  So if allowed, as it is in linux, then case sensitivity propagates to the apps written in it. 

4) Technical. Linux is a byte-stream oriented OS.

This part I don't understand, but it sounds like another technical reason behind case sensitivity.  Apparently, in windows for example, file names have to be converted to upper case before they can be worked with by the OS, whereas linux takes the name as is and works on it.

---

### Post by Bloodfen Razormaw on 2006-10-01
Most likely the number one reason is that UNIX was more about making it simple rather than making it right.  When confronted with doing something the right way with a complex implementation or the wrong way with a simple implementation, UNIX goes with the later.  The end result is that the end users and application developers have to go through a lot of pain to deal with UNIX because the developers didn't put in the hard work themselves.

---

### Post by xtacocorex on 2006-10-01
I just tested the case-sensitivity on my MacBook and I'm now sort of pissed off that it's not there.  

Linux is a Unix clone, my thought is if you don't want case-sensitivity, hack the OS and get the functionability yourself.  I don't see case-sensitivity in Linux going away any time soon, if ever.

---

### Post by Shay Stephens on 2006-10-01
> **Bloodfen Razormaw said:**
> Most likely the number one reason is that UNIX was more about making it simple rather than making it right.  When confronted with doing something the right way with a complex implementation or the wrong way with a simple implementation, UNIX goes with the later.  The end result is that the end users and application developers have to go through a lot of pain to deal with UNIX because the developers didn't put in the hard work themselves.
I think you're right.  When I was talking about:
> And I believe it to be just an old technique used when resources were slim. But come on, we have plenty of disk space and processing power now to deal with this right?!?!
I should have been using your example, as this is what I meant by it.  You said it much more understandably :-)

---

### Post by sicofante on 2006-10-01
> **xtacocorex said:**
> if you don't want case-sensitivity, hack the OS and get the functionability yourself
Oh, no, not again, not at Ubuntu... ](*,)

---

### Post by sicofante on 2006-10-01
> **Bloodfen Razormaw said:**
> When confronted with doing something the right way with a complex implementation or the wrong way with a simple implementation, UNIX goes with the later.
But on the other side, that line of thought has made UNIX descendants like Linux or OSX more robust systems. Simplicity is a good thing at kernel level and other low levels. It just needs to stop there if the system is going to be used by ordinary people. At Apple they've managed to create a UNIX based system that cares for the end users (couldn't be otherwise if they wanted to keep their customers happy). That's just the last stage Linux is lacking still a bit. This very thread shows a clear line between geek and non-geek thinking, but I'm hopeful because I can see more and more computer savvy people thinking of the Regular User instead of just themselves.

---

### Post by grte on 2006-10-01
> **comomolo said:**
> This very thread shows a clear line between geek and non-geek thinking, but I'm hopeful because I can see more and more computer savvy people thinking of the Regular User instead of just themselves.

I'm sorry, but this line is unbelievably hypocritical.  Do you not see that you are guilty of exactly what you accuse "computer savvy people" of doing?

"Wha! Wha!  Regular users don't want it this way, change it!"

"Why should I?  I like it."

"Because I said so!"

---

### Post by sicofante on 2006-10-01
Wow, that's some very strong wording here... I just believe there's a need for a more user friendly Linux and I'm exposing my thoughts about it (other people exposing theirs). I can't see how that makes me hypocritical but I won't enter any argument based on these terms anyway. (BTW, I consider myself computer savvy...)

---

### Post by Bloodfen Razormaw on 2006-10-01
> **comomolo said:**
> But on the other side, that line of thought has made UNIX descendants like Linux or OSX more robust systems. Simplicity is a good thing at kernel level and other low levels. It just needs to stop there if the system is going to be used by ordinary people. At Apple they've managed to create a UNIX based system that cares for the end users (couldn't be otherwise if they wanted to keep their customers happy). That's just the last stage Linux is lacking still a bit. This very thread shows a clear line between geek and non-geek thinking, but I'm hopeful because I can see more and more computer savvy people thinking of the Regular User instead of just themselves.
I disagree with both of these claims.  Linux and UNIX have been extremely unstable systems because it takes so much insane work just to make something work right.  The kernel doesn't matter if the applications don't work.  Linux and UNIX still can't do things that people took for granted on LISP Machines.

As for OS X, it cares nothing for the end user.  It is like one giant middle finger to decades of usability studies.  I've seen Mac zealots brag that after a few months of using a Mac you will love it.  And yet a usability study on KDE in 2003 found that even longtime Windows users were able to use SuSE 8.x w/ KDE better than the Windows OS they were familiar with immediately upon first using it.  No months of training.  That is what usability means.

---

### Post by Fass on 2006-10-01
> **comomolo said:**
> Wow, that's some very strong wording here... I just believe there's a need for a more user friendly Linux

And since when is the command line - basically the only place where case sensitivity matters (and makes life a whole lot easier) - "user friendly?" You're complaining about an irrelevance.

---

### Post by grte on 2006-10-01
> **comomolo said:**
> Wow, that's some very strong wording here... I just believe there's a need for a more user friendly Linux and I'm exposing my thoughts about it (other people exposing theirs). I can't see how that makes me hypocritical but I won't enter any argument based on these terms anyway. (BTW, I consider myself computer savvy...)

Okay, we'll try a different tack:

Consider the effort.  Case sensitivity is a fundemental.  Changing it would be a truly herculean effort.  I mean, first, you'd have to get various different distros on board - Debian for sure, because that's who we get our packages from.  So we'd also have to get all the other distros who rely on debian on board.  You'd probably want to get non-debian distros on board too, to maintrain cross-platform compatibility.  So RedHat, et all.

Then the actual process of implementing it.  This isn't just some switch in the kernel.  I mean...It's the kernel, the file system, and who knows how many other apps would need to be updated.  I mean, I don't even want to know how many of the thoudsands of apps in the repos alone would need fixing.

And all that effort for a benefit that is debatable at best.

Would you rather have the linux community expend all that effort for such a minor change, or say, working wifi and more graphical conf editors?

---

### Post by sicofante on 2006-10-01
> **grte said:**
> And all that effort for a benefit that is debatable at best.
Exactly. That's what this thread is about. A debate on case sensitivity. I don't pretend to be absolutely right about that. As a matter of fact I already acknowledged that the issue was shortsighted on my side and the goal is further away in metadata based filesystems.

I can't really answer your question. It's the same I see posted everywhere on any other issue. You're asking about priorities and that's simply another whole debate.

---

### Post by grizzly on 2006-11-22
I am not sure if anyone has mentioned this , but if it hsn't been mentioned, then shame on you n00b$ :p

You can get case-insensitive completion in zsh(IMO better than bash)

Install zsh
> sudo apt-get install zsh

Add this in your ~/.zshrc >
> zstyle ':completion:*' matcher-list 'm:{a-zA-Z}={A-Za-z}'
open new shell , now you have case-insensitive completion!! i.e cd ~/docu<TAB> will complete with ~/Documents. :D

---

### Post by gorilla on 2006-11-22
no need to install zsh, bash also supports case-insensitive auto-completion!

just edit inputrc to your preference:

set completion-ignore-case on 


it makes best sense when used together with menu-complete. This means that hitting <TAB> will cycle through alternatives:
Tab: menu-complete


To still have the standard behaviour at your disposal, you can map *complete* to a different key, for example:
"\C-^": complete

---

### Post by Xzallion on 2006-11-23
First, I see computers like a language.  We have to learn the grammar rules for a language, well computer syntax is like written grammar, and case sensitivity has long been part of the rules.  The way I see it, this is like you suggesting that we get rid of caps in the english language just to make it easier to learn the rules.

Second, Linux was built as a Unix clone.  I would say if you don't like Unix, don't use Linux, but that wouldn't be nice, or fitting of the Ubuntu philosophy.  Instead I would suggest maybe finding a group of people with the programming knowledge to make what you want a reality, though I won't even pretend that that will be easy.

Third, what you are suggesting is so hard it nearly impossible.  It would entirely break Linux, ruining thousands of thousands of applications written with case sensitivity in mind.  It would be like having to write your own operating system.  If you can get a group willing that would be a neat project, but I don't see many getting behind it.

Mainly Shay Stephens made some good points that I agree with.

---

### Post by acheun on 2006-11-23
Allow me to put my humble opinion here.

I like case sensitive. I really find it user friendly, no matter using it in terminal or gui.

I create a folder 'music', it is used for general music file.  I use 'Music' as folder, it's for something name as 'Music'.  And 'MUSIC' folder for a subject which is an acronym.  (OK, I just make them up, I don't really have these 3 folders). It is just applied the same rule as English's proper noun or not.  

It's only frustrate when you need to use all the above 3 different folder to communicate to another box like Windoze which unable to differientate them.  To me, it's the Windoze incompetence.  Not Linux or Ubuntu's un-friendly.

I can't see why case sensitive is unhuman.  To me, case insensitive is unhuman, as it's not our nature way to use in our daily life.  If we found case insensitive more friendly, may be just because there are a lots more users using another sucky OS, and get use to it.

I hope I don't offense any one.

---

### Post by Circus-Killer on 2006-11-23
case sensitivity is very good. i should imagine the only people with a problem with case sensitivity are non-coding end-users.

this is just an opinion, but i would hate to see case sensitivity done away with. i dont see it as a problem, rather than something you just need to get used to.

---

### Post by argie on 2006-11-23
I don't think case sensitivity is a big deal. I actually like it. I don't know why, maybe it's because I'm used to it.

> **Bloodfen Razormaw]As for OS X, it cares nothing for the end user. It is like one giant middle finger to decades of usability studies. I've seen Mac zealots brag that after a few months of using a Mac you will love it. And yet a usability study on KDE in 2003 found that even longtime Windows users were able to use SuSE 8.x w/ KDE better than the Windows OS they were familiar with immediately upon first using it. No months of training. That is what usability means[/quote]
I love KDE, and I use it for my own personal non-admin account (I've heard of adept crashing), but that reference to the study certainly doesn't prove anything.

[QUOTE=gorilla said:**
> no need to install zsh, bash also supports case-insensitive auto-completion!

just edit inputrc to your preference:

set completion-ignore-case on 


it makes best sense when used together with menu-complete. This means that hitting <TAB> will cycle through alternatives:
Tab: menu-complete


To still have the standard behaviour at your disposal, you can map *complete* to a different key, for example:
"\C-^": complete
Wow thanks so much! I was looking for something like this.

---

