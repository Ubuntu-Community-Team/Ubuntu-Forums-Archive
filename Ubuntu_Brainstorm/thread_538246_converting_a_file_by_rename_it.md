---
title: "converting a file by rename it"
date: 2007-08-29
forum: Ubuntu Brainstorm
---

### Post by Mr.mouse on 2007-08-29
the user click on a file then click on the right button of the mouse
then >rename

if the user change the  "family" name, a window will pop up "do you want  to convert this file" click  OK

abcd.mp3 ->abcd.ogg
abcf.doc ->abcf.pdf


if the user  click  ctrl a then rename - all the files on that directory will be converted


if the user adding a "family" name to a folder like abcd.vcd all the files will be as one vcd file
avi, sub (in one folder)-> folder.vcd
avi,doc,mp3 (in one folder)-> folder.zip ->folder.rar
1jpg, 2.jpg, 3.jpg (in one folder)->folder.odp ->folder.vcd
 folder.zip ->folder.rar->avi,doc,mp3 (delete the "family" name convert it to a folder)

---

### Post by rsambuca on 2007-08-29
What happens when...   OOOPS, I just accidentally converted my config files into pdf's?  :)

---

### Post by smartboyathome on 2007-08-29
> **Mr.mouse said:**
> the user click on a file then click on the right button of the mouse
then >rename

if the user change the  "family" name, a window will pop up "do you want  to convert this file" click  OK

abcd.mp3 ->abcd.ogg
abcf.doc ->abcf.pdf


if the user  click  ctrl a then rename - all the files on that directory will be converted


if the user adding a "family" name to a folder like abcd.vcd all the files will be as one vcd file

-1 from me. It isn't needed (you can use OpenOffice or KOffice for converting PDFs, and there are some converters around for converting sound files). Also, what happens to "Unsupported Filetypes" (ie: abcd.txt -> abcd.xyz (where xyz is a random extention)), and "Unsupported conversions" (ie: abcd.mp3 -> abcd.doc)? Basically, this is one feature that is just for show (to me) and isn't really needed.

---

### Post by Mr.mouse on 2007-08-29
there are a lot of tool but not one that can do it all
this is the right thing on the right place 

about the Unsupported 
the ui of the pop up window will tell the user that and give him options

---

### Post by smartboyathome on 2007-08-29
and what would you use as the converter? If it is the individual apps, it would take just as long to open it up and go through the procedure.

---

### Post by Mr.mouse on 2007-08-29
after the user select a format and click OK 

the tool will search for the right library 
if it's not installed the tool  will install it (like mp3 support)

---

### Post by Greenwizard88 on 2007-08-29
This is an amazing idea for **SOME** file types.

---

### Post by smartboyathome on 2007-08-29
> **Mr.mouse said:**
> after the user select a format and click OK 

the tool will search for the right library 
if it's not installed the tool  will install it (like mp3 support)

I just think that would be too much hassle. Especially since sometimes synaptic will be open (or update-manager will be updating). I would say stick with current techniques, they are adequate for now (I don't know of many major OSes with this feature by default).

---

### Post by Steveway on 2007-08-29
And what is if someone doesn't use fileextensions?
You know on Linux we don't need fileextensions.
There is a command called file wich analyses the file and tells you what it is.
> steveway@steveway-laptop:~$ file rand.png
rand.png: PNG image data, 160 x 446, 8-bit/color RGBA, non-interlaced

And I don't think that it is really usefull.

---

### Post by Mr.mouse on 2007-08-29
you can say the same on mp3 support

1 answer for a 1000 questions
[http://ubuntuforums.org/search.php?searchid=26267533](http://ubuntuforums.org/search.php?searchid=26267533)

---

### Post by smartboyathome on 2007-08-29
Yes, people ask how to convert things, but you should use SOFTWARE that does it, not impliment a complicated system which does it by renaming something (and will be flawed because there could be many complications like mentioned above).

---

### Post by gnomeuser on 2007-08-29
See that would be difficult to make work, you'd have to actively stop the user from converting say an mp3 file into a presentation file. 

To make that work you'd have to do an awful lot of work behind the users back, detecting mime types and which mime type conversions are valid, warn the user when he is trying to do something naughty, check that we have conversion filters for the desired action. So many pitfalls.

What we could do that would be easier and safer would be to develop a nautilus action script that would convert files for you, they already exist for things like FLAC to OGG/MP3/etc. Naturally this would not be entirely non trivial either and it has the potential to be very nasty looking code but it would be discoverable (action submenu in the context menu is probably more discoverable than noticing that you convert files by renaming them).

You can also use media-convert.com - it detects the input format, you select the output format you desire, I use it all the time for presentation files (I don't have OpenOffice installed and GNOME Office which I like better has no presentation app currently)-

---

### Post by Mr.mouse on 2007-08-30
this is a navigation tool 
understand what the  use is trying to do
understand what pack the user need 
understand if the pack is in installed or not
and by clicking OK the tool run the code

this tool help people to work with files and folders only by rename the file name

---

### Post by rsambuca on 2007-08-30
I can see why this could be a decent idea in very limited circumstances, but I think you are asking the computer to do too much mind reading here.  There are just too many variables.

---

### Post by Mr.mouse on 2007-08-30
this is not as hard as it look like
80% of the format already in the os


1 find the libraries that you need

FFmpeg to convert video and photos
[http://biggmatt.com/winff](http://biggmatt.com/winff)
p7zip to work with zip, rar...
oo library to convert documents

2 create one ui and  integrated with the files system 

3 add feature if the library is not installed, install it

---

### Post by talz13 on 2007-08-30
I think it would be a great *extension* to ubuntu, and maybe after it has had a while to prove itself, would make a splendid addition to the OS.  It would be a very inventive idea to include with an OS, and if OS X did it, you know people would be crowing about how innovative it was!

I just don't think it would be a simple thing to integrate into a distribution copy, but would rather make a nice plugin of some kind for the time being.

---

### Post by Wolki on 2007-08-30
1) You need to be *extremely* careful, as the way you describe it is a potentially destructive operation - it may not be undoable completely or entirely.  Think of the following two examples:
[LIST]
[*] Andrew borrowed a CD from his friend and ripped it to FLAC. (legal in many countries). He returns the cd back, listens to the music, and really likes it. In fact, he likes it so much he wants it on his portable mp3 player. He knows that he can change filetypes by renaming on his computer, so he renames them to .mp3. After listening to these mp3s, h notices that they don't sound exactly the same anymore (maybe Andrew's an audiophile with a good hi-fi system and the music was experimental music where the compression techniques of mp3 are suboptimal). He tries to change them back, but it's too late - the sound stays the same, and the cd is gone.
[*] Bridget is working on a document she needs to send to Corey for approval. She's using OpenOffice.org and, after completing it, she send the .odt to him. Corey has some trouble displaying it correctly, though (he guesses he's missing some fonts) and asks for a pdf. Bridget renames the file to .pdf, and Corey is very happy with it, but finds a typo and asks her to fix it. She renames the file back to .odt, but the conversion doesn't work, so she has to spend a lot of time recreating the original work.
[/LIST]

2) While renaming for format conversion kind of makes sense (especially to people who don't really understand what file formats are), most people coming to ubuntu right now have at least intermediate experience with computers, many are power-users. They know they can't change formats just by renaming (since you need programs for that!), so they'd never try it. But easy conversion would be a cool feature, why hide it from the people who would want it the most? (I agree with gnomeuser here)

3) You would have to greatly change how the rename functionality works - the way it is right now does not make sense for selecting multiple items. There's only one entry field for many files. Sure, you could add more entry fields, but that would mean that to convert 100 mp3s to oggs, you'd have to replace .mp3 with .ogg a hundred times; or add more and more buttons that are only useful for format changing to the rename dialog. You could also just leave one entry field and use changes to its extension to change all fields, but then what would happen if the user actually changes the non-extension part of the file name?

As for resolving these problems, I mostly agree with gnomeuser. I think a general-purpose conversion extension in nautilus would be even better than lots of small actions/scripts dealing with single types, though. We have a good mime-type database and some nice infrastructure from freedesktop.org, if someone were willing to work on it I'm sure it would be possible. HAving it would be cool, at least.

---

### Post by Mr.mouse on 2007-08-30
so...you can add note "be aware, you can't convert this file back to___"

Andrew and Bridget can do the same mistake after searching in google and asking in Forums 



look at that way 
Andrew want to play his odp in his dvd, he rename the file to vcd/dvd  and burn it

today he need to
1 search and asking in Forums how he can do it
2 install a plug to oo 
3 know how to use the plug

---

### Post by smartboyathome on 2007-08-30
> **Mr.mouse said:**
> so...you can add note "be aware, you can't convert this file back to___"

Andrew and Bridget can do the same mistake after searching in google and asking in Forums 



look at that way 
Andrew want to play his odp in his dvd, he rename the file to vcd/dvd  and burn it

today he need to
1 search and asking in Forums how he can do it
2 install a plug to oo 
3 know how to use the plug

It can only be useful in situations where there is not a very practical way to do it. This would also break other files (file.png.bk "change to .bk file"). It will just be too complicated for something as simple as renaming a file. Maybe a separate tool could be developed to do this?

---

### Post by Wolki on 2007-08-30
> **Mr.mouse said:**
> so...you can add note "be aware, you can't convert this file back to___"

Andrew and Bridget can do the same mistake after searching in google and asking in Forums 

Yeah, but you see, your simple idea is becoming rather complex. That's bacause you'Re fighting against two principles in user interface design:
1) Don't destroy your users work (in your case, by making a needlessly destructive operation)
2) Make things discoverable (easy to find)

There's absolutely no need that conversion needs to be destroy the original, only when it's coupled with renaming (if you want to have at least some semblance to renaming). And there's no need that it needs to be hidden under renaming when it could be its own menu entry - it should definitely be cool and useful enough.



> 
look at that way 
Andrew want to play his odp in his dvd, he rename the file to vcd/dvd  and burn it

today he need to
1 search and asking in Forums how he can do it
2 install a plug to oo 
3 know how to use the plug

You forgot that Andrew will need to find out that he can just rename the things - there's nothing in the interface that tells him too. Plus, he needs to find out what extension is expected for something like that, so more asking / searching.

With a separate "Convert to ..." context / dropdown menu entry, not only can he find it easily by browsing the menus, it can also offer him the conversions  available for that document type.

---

### Post by Mr.mouse on 2007-08-30
not every thing needs to be in version 1

---

### Post by rsambuca on 2007-08-30
I also see problems arising just from careless typing errors.  I often don't have any extensions on my files.  What if I am renaming a file and accidentally hit the . key followed by whatever while I am renaming it?  Poof!

Or I am tired after a long day and rename my homemovie.mpeg as video.mp3.  Poof!  video gone?

Silly and extreme examples, but I see this as too potentially damaging.

---

### Post by Wolki on 2007-08-30
> **rsambuca said:**
> Silly and extreme examples, but I see this as too potentially damaging.

Mr.mouse did say it should prompt the user for confirmation in the first post... but I had to re-check that too.

---

### Post by Mr.mouse on 2007-08-30
rsambuca
after a long day you can click delete 


Andrew know about it because it is the right thing on the right place 
and if he convert a file before it mast be there

add a note does not make it difficult, not knowing (like now) is a problem

you can add a link in the menu "converting by rename"-select a file

---

### Post by rsambuca on 2007-08-30
> **Mr.mouse said:**
> rsambuca
after a long day you can click delete 
LOL, yeah, that can definitely happen too!  But at least it goes to the trash!

---

### Post by Mr.mouse on 2007-08-30
rsambuca 
the user click on a file then click on the right button of the mouse
then >rename then change the file type then click OK

this is more then enough



imagine  how much questions you can answer with one answer

---

### Post by smartboyathome on 2007-08-30
> **Mr.mouse said:**
> rsambuca 
the user click on a file then click on the right button of the mouse
then >rename then change the file type then click OK

this is more then enough



imagine  how much questions you can answer with one answer

This convo is going in circles and getting no where. i would say +1 if it were a different tool (change filetype sounds appropriate); -1 if it is part of the rename tool.

---

