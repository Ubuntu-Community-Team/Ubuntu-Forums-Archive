---
title: "Worst Linux advice by gurus to give to a newb... don't use spaces in filenames"
date: 2010-05-12
forum: The Cafe
---

### Post by MechaMechanism on 2010-05-12
Really... Really!?  Don't use spaces in folder and filenames?  All I have to say is Oh Brother.  Newbs will be just fine putting spaces in folders and filenames.  It looks much cleaner and more readable too.  Besides on the command line I use "" and anybody worth their salt on the command line knows how to deal with spaces.  Please stop recommending new users to put in underscores or dashes.  It's very annoying and for the record when Rhythmbox rips CD's it rips with spaces.  We have long since passed the need for dashes and underscores.

The people need the right to do it their way.

---

### Post by betrunkenaffe on 2010-05-12
cd c:\Program Files\Betruken Affes Cool Program\I like poor naming schemes\

Command fails.

cd /home/betrunkenaffe/betrunkenaffescoolprogram/ilikepoornamingschemes

Command works but is fugly.


The suggestion is to avoid a command that doesn't work frustrating a new user. Beyond that, personal preference.

---

### Post by Shpongle on 2010-05-12
you can also use \ eg 

cd ~/Documents/college\ stuff/

---

### Post by fatality_uk on 2010-05-12
Hmmmmm,riightt!!!!!!

And would you care to share who gave you this advice or where you saw it?

---

### Post by RiceMonster on 2010-05-12
> **betrunkenaffe said:**
> cd c:\Program Files\Betruken Affes Cool Program\I like poor naming schemes\

Command fails.

cd /home/betrunkenaffe/betrunkenaffescoolprogram/ilikepoornamingschemes

Command works but is fugly.


The suggestion is to avoid a command that doesn't work frustrating a new user. Beyond that, personal preference.


Tell them how to use tab completion, and to escape spaces with a \. Problem solved.

---

### Post by antenna on 2010-05-12
What's the worst that can happen if you don't use spaces? I think you might be overstating this a a bit.  It's not a big deal.  

I use them in mp3 filenames but tend to avoid them (and capitals) otherwise, just makes things a bit easier on the command line.

---

### Post by MechaMechanism on 2010-05-12
> **fatality_uk said:**
> Hmmmmm,riightt!!!!!!

And would you care to share who gave you this advice or where you saw it?
[http://blogs.techrepublic.com.com/10things/?p=1507&tag=nl.e101](http://blogs.techrepublic.com.com/10things/?p=1507&tag=nl.e101)

EDIT: Look at number 8.

And I just get annoyed when users are told they can't do it their way.

---

### Post by MooPi on 2010-05-12
I would suggest that folders not have spaces, and file not so important. Things just work better if spaces are omitted.

---

### Post by aysiu on 2010-05-12
I wouldn't say new users should avoid spaces in filenames. I would say, though, that they should be aware that spaces have to be treated differently when working with them in the terminal and that Tab completion is their friend.

---

### Post by McRat on 2010-05-12
It makes sense to reduce usage of spaces in descriptors unless necessary:

1)  Possible errors  caused by multiple  spaces.
2)  Legacy systems and embedded computers might not like them.  Routers are one area I've seen problems today.
3)  Causes confusion when writing tech manuals. 
4)  Trailing and leading spaces can be invisible.


It just isn't a good habit to get into if you are going to use computers alot.

Some others:

Do not use I / l / 1 if possible.
Ditto for 0 / O 

AND GEEZ!  Could they agree on / or \ ??????  Or CR+LF or just LF or just CR?????

---

### Post by scouser73 on 2010-05-12
The only time I've had this problem was making a symlink and the file name had a space in it, apart from that I don't see a problem.

---

### Post by CharlesA on 2010-05-12
I use quotes around anything with a space in it.

---

### Post by koenn on 2010-05-12
In a GUI, file and directory names can be whatever you like
In an interactive shell, tab completion will will catch most problems

It isn't until you start using scripts to manipulate file and directory names that spaces (and some other special characters) become problematic - 
eg you'll end up having to insert all sorts of extra quotes all over the place because you can't manually  escape a space in a filename caught inside a variable by some procedure in the script.

That alone is reason enough for me to avoid spaces in directory and file names.

---

### Post by alexfish on 2010-05-12
> **MechaMechanism said:**
> Really... Really!?  Don't use spaces in folder and filenames?  All I have to say is Oh Brother.  Newbs will be just fine putting spaces in folders and filenames.  It looks much cleaner and more readable too.  Besides on the command line I use "" and anybody worth their salt on the command line knows how to deal with spaces.  Please stop recommending new users to put in underscores or dashes.  It's very annoying and for the record when Rhythmbox rips CD's it rips with spaces.  We have long since passed the need for dashes and underscores.

The people need the right to do it their way.

/etc/You are correct/to farther of Gurus/We don't care

---

### Post by CharlesA on 2010-05-12
> **koenn said:**
> 
It isn't until you start using scripts to manipulate file and directory names that spaces (and some other special characters) become problematic - 
eg you'll end up having to insert all sorts of extra quotes all over the place because you can't manually  escape a space in a filename caught inside a variable by some procedure in the script.

Been there. Hated it. Extra work for me. :(

---

### Post by 98cwitr on 2010-05-12
proper progamming syntax is as follows:

/youNeedToSeparateWordsWithCapitalLetters/likeThis/

The PROPER way to do it is without spaces, underscores, or special characters.

Readable and PROPER. That's the way it should be done. /thread.

There is a reason your root directory doesn't spell out the entire paths...:roll:

---

### Post by RiceMonster on 2010-05-12
> **98cwitr said:**
> proper progamming sntax is as follows

/youNeedToSeparateWordsWithCapitalLetters/likeThis/

Readable and PROPER. That's the way it should be done. /thread.

Creating files and directories is not programming, so there's no need to be "proper" and use cammel casing.

---

### Post by 98cwitr on 2010-05-12
whats next? It's ok to have the entire first paragraph of your word doc in the file name?

---

### Post by johnb820 on 2010-05-12
Personally I put underscores in for spaces as I am not in the habit of using quotations when working in a terminal. I wouldn't say it's bad advice. It couldn't hurt to try and eliminate whitespace as much as possible.

I have more of a problem with abbreviations.

---

### Post by koenn on 2010-05-12
> **98cwitr said:**
> whats next? It's ok to have the entire first paragraph of your word doc in the file name?

some people actually do that. Or rather, they click OK when MS Word suggests it.
Then they show up as errors in the backup logs

---

### Post by renkinjutsu on 2010-05-12
There are more problems with just using the commandline.

say you want to add an fstab entry that mounts some device to the folder "My Device" .. how do you put that into mtab? there's a whole different syntax for different configuration files and it becomes problematic and learning one isn't enough. I had this problem when i wanted my rtorrent to watch a folder with a space in it.. i had no idea how to express it in the .rtorrent.rc i used the \ to escape the spaces, i also tried putting it in quotes. in the end, i just renamed the folder.

spaces work most of the time, but "no-spaces" works all the time. And people like giving foolproof advice.

---

### Post by MasterNetra on 2010-05-12
My Advice use short naming conventions, not that long ones are bad but do you really want to have to type a file name later that is this long?:

~/documents/** I\wanna\get\down\get\funky\and\party\all\night\long.mp3 **

*Edit: If you see a space between n & g in long I dunno how that got there I didn't put one there or anything between n&g for that matter.*

---

### Post by juancarlospaco on 2010-05-12
How do you know if spaces or tab is being used on a name/text, this is the problem,
and some systems get problems with lèttèrs lìkè thìs, 
or longer paths like 256 character path limit on Windows Systems,
or problems with "Ñ ñ" because theres no Ñ on english. 

:)

---

### Post by nothingspecial on 2010-05-12
This thread is funny.

Using spaces in file names is for users who understand that spaces need to be escaped.

Not for new users, who don`t.

It will only lead to problems later.

Not using spaces is good advice.

---

### Post by mister_playboy on 2010-05-12
> **nothingspecial said:**
> This thread is funny.

Using spaces in file names is for users who understand that spaces need to be escaped.

Not for new users, who don`t.

It will only lead to problems later.

Not using spaces is good advice.

Haha, I found myself going through my files and replacing all my underscores with spaces.  I still occasionally get tripped up with them in the command line, but I can resolve the issue painlessly nowadays, rather than wondering what the heck is going on. :)

---

### Post by 98cwitr on 2010-05-12
> **RiceMonster said:**
> Creating files and directories is not programming, so there's no need to be "proper" and use cammel casing.

dont care...it's the proper naming convention and should be used....especially for new users.

---

### Post by chriswyatt on 2010-05-12
Depends on the use case I reckon, seeing as modern filesystems support spaces no problem I don't see it as much of an issue.  If I was making a website though I'd probably go for all lowercase and underscores.

I work for a small company making Facebook games, and for our game we used special characters and spaces in our filenames, wasn't my idea of course :).  It caused us loads of issues later on, mainly FTP which doesn't really support special characters all that well.

---

### Post by juancarlospaco on 2010-05-12
The World is UTF-8.
The legacy Windows not.

---

### Post by nothingspecial on 2010-05-12
I have plenty of files with spaces, &s, $s etc.

The original post was about bad advice to give new users.

I understand that you have to escape special characters.

New users may not.

Advising that spaces are not a good idea is not bad.

---

### Post by snova on 2010-05-12
> **betrunkenaffe said:**
> cd c:\Program Files\Betruken Affes Cool Program\I like poor naming schemes\

Command fails.

As I recall that works perfectly fine under Windows. I think command line parsing is done by applications rather than the shell (not sure how it works).

> **McRat said:**
> It makes sense to reduce usage of spaces in descriptors unless necessary:

1)  Possible errors  caused by multiple  spaces.
2)  Legacy systems and embedded computers might not like them.  Routers are one area I've seen problems today.
3)  Causes confusion when writing tech manuals. 
4)  Trailing and leading spaces can be invisible.

It just isn't a good habit to get into if you are going to use computers alot.


I don't think shells have ever had particularly sane rules for spaces and quoting. Fortunately it's only a problem with: *shells*. I do not otherwise care.

> AND GEEZ!  Could they agree on / or \ ??????  Or CR+LF or just LF or just CR?????

I've yet to see a system that used something other than / and LF (please not CR) except Windows. (Not that I've seen many systems, just that it's more or less normal.) Well, CRLF is somewhat common on the internet...

> **juancarlospaco said:**
> The World is UTF-8.
The legacy Windows not.

NTFS is (more or less) UTF-16.

---

### Post by 98cwitr on 2010-05-12
> **chriswyatt said:**
> Depends on the use case I reckon, seeing as modern filesystems support spaces no problem I don't see it as much of an issue.  If I was making a website though I'd probably go for all lowercase and underscores.

I work for a small company making Facebook games, and for our game we used special characters and spaces in our filenames, wasn't my idea of course :).  It caused us loads of issues later on, mainly FTP which doesn't really support special characters all that well.

it's not about the system...it's about the user.

---

### Post by Crunchy the Headcrab on 2010-05-12
> **98cwitr said:**
> t's the proper naming convention and should be used....especially for new users.
Um.  No.

Camel case is hardly easy to read as you suggest.  I think it looks like a bloody nightmare and yes I use it often.

> **98cwitr said:**
> dont care...

What a coincidence neither do we.

---

### Post by emarkay on 2010-05-12
"In space, mo one can hear you scream..."
Good operating practice to avoid spaces as a rule anyway - underscore suffices.  Blame ASCII...

---

### Post by K.Mandla on 2010-05-12
> **MechaMechanism said:**
> Really... Really!?  Don't use spaces in folder and filenames?  All I have to say is Oh Brother.  ...
To be honest that's the first time I'd ever heard of that advice, and it makes me a bit skeptical of a writer's expertise if they say something like that. Perhaps Mr. Wallen is not the Linux expert he appears to be.

Personally I like to throw a lot of unnecessary slashes and backslashes into my file names.

---

### Post by MechaMechanism on 2010-05-12
When directly working with directories and files manually, meaning using terminal, I use underscores or dashes.  However when I interact with files and directories through a program interface that create spaces by default, then I never have a problem with it.  Say I touch a file then I use underscore.  Now take Rhythmbox for example, spaces never matter for my music since I access it exclusively through Rhythmbox.  But terminal for sure I always use dashes and underscores.

---

### Post by chucky chuckaluck on 2010-05-12
> **MechaMechanism said:**
> Really... Really!?  Don't use spaces in folder and filenames?  All I have to say is Oh Brother.  Newbs will be just fine putting spaces in folders and filenames.  It looks much cleaner and more readable too.  Besides on the command line I use "" and anybody worth their salt on the command line knows how to deal with spaces.  Please stop recommending new users to put in underscores or dashes.  It's very annoying and for the record when Rhythmbox rips CD's it rips with spaces.  We have long since passed the need for dashes and underscores.

The people need the right to do it their way.

it would take at least a six vehicle car accident to get me that excited.

---

### Post by chillicampari on 2010-05-12
Oh my. I just figured everyone used my preferred naming convention of 

inordinately_long_file_names_with_too_many_underscores_and_rAnDoM_cASe.ftw

---

### Post by CharlesA on 2010-05-12
> Edit- what's up with that gap?

Security feature.

---

### Post by MasterNetra on 2010-05-12
> **CharlesA said:**
> Security feature.

So that's what it is, I thought it was glitching.

---

### Post by chillicampari on 2010-05-12
> **CharlesA said:**
> Security feature.

Neat.

---

### Post by CharlesA on 2010-05-12
> **MasterNetra said:**
> So that's what it is, I thought it was glitching.
It does it with certain URLS and javascript/whatnot as well.

---

### Post by Giant Speck on 2010-05-12
We need to hold new users' hands more.  They might get lost and not figure out things for themselves.

---

### Post by betrunkenaffe on 2010-05-13
For those that pointed out \ escape... did you notice that I was showing off a Windows cd command and not a Linux one?

BTW, found a nice reason to not have spaces in folders, had a space in a folder and make ended up erroring out that it couldn't find a directory. Removed space and solved it.. easier than finding the glitch in the makefile :)

---

### Post by 3rdalbum on 2010-05-13
Better advice would be to avoid putting special characters in filenames. If you decide to rip an album full of Swedish music and then transfer it to a Windows machine, no Windows program will be able to access the music due to all the special characters.

This has actually happened to me; albeit not with a Swedish album but a regular album that had some special characters :-)

---

### Post by spupy on 2010-05-13
> **chillicampari said:**
> Oh my. I just figured everyone used my preferred naming convention of 

inordinately_long_file_names_with_too_many_underscores_and_rAnDoM_cASe.ftw

That is what I use as well. Shift+_ is easier to type than AltGr+\. (German kezboard)

---

### Post by szymon_g on 2010-05-13
> **mister_playboy said:**
> Haha, I found myself going through my files and replacing all my underscores with spaces.

I do similar thing, but i replace all spaces with underscores ( _ ) :)

---

### Post by Meep3D on 2010-05-13
> **betrunkenaffe said:**
> For those that pointed out \ escape... did you notice that I was showing off a Windows cd command and not a Linux one?

BTW, found a nice reason to not have spaces in folders, had a space in a folder and make ended up erroring out that it couldn't find a directory. Removed space and solved it.. easier than finding the glitch in the makefile :)

As someone else pointed out on Windows you can put a path with a space in quotes, such as:  cd "c:\program files\" which if you think about it is how it should be done - any sensible programming language demands literal strings by placed in quotes, in fact in a shell which lets you use * as a filename it should be mandatory.

---

