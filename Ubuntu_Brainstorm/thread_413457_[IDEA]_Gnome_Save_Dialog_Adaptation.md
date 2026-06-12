---
title: "[IDEA] Gnome Save Dialog Adaptation"
date: 2007-04-19
forum: Ubuntu Brainstorm
---

### Post by Surkow on 2007-04-19
**Summary**

The GTK save dialog needs to be adapted or GTK needs to implement a function where the (simplified) file manager of your choice can be used instead of the standard save dialog.

**Rationale**

Comparing the save dialog to the dialogs from Windows, KDE and MacOSX it has the following restrictions:

- Renaming is not possible;
- Moving is not possible;
- Copying is not possible;
- Pasting is not possible;
- Removing is not possible;
- Save dialogs are not expanded by default (i.e. you can't browse directories immediately).

It doesn't behave like simplified version of a file manager and you aren't able to use a location bar instead of the so called "bread crums". Since the save dialog is a part of GTK there are two things that can be changed. The GTK save dialog needs to be adapted or GTK needs to implement a function where the (simplified) file manager of your choice can be used instead of the standard save dialog.

**Scope and Use Cases**

Gerard often saves images from the internet. After he creates a directory where he wants to save these images he makes a mistake with naming the directory. Instead of being able to rename the directory in the save dialog, he needs to use Nautilus (or any other file manager) to do it.

When he tried to save an image he stored it in the wrong directory. Instead of being able to move it in the save dialog to the correct directory he needs to use a file manager to do this.

**Implementation Plan**

A visual interpretation of what could be altered:

[img]http://img255.imageshack.us/img255/8369/savedialogxb0.png[/img]
Standard save dialog

[img]http://img408.imageshack.us/img408/441/savedialogwithlocationbmo3.png[/img]
Added (unfinished) menu and location bar

It should be clear that you are able to switch back to using the breadcrums instead of the location bar. This mockup does not show how any alternative file manager dialogs should look like.

**Related webpages/threads**
[http://ubuntuforums.org/showthread.php?t=403111](http://ubuntuforums.org/showthread.php?t=403111)
[http://www.mail-archive.com/gnome-devel-list@gnome.org/msg00769.html](http://www.mail-archive.com/gnome-devel-list@gnome.org/msg00769.html)

---

### Post by Surkow on 2007-04-19
I don't seem to be able to add the tag "**gutsy ideas**".

---

### Post by lolocaust on 2007-04-19
I was going to post something like this, the file dialogs in Gnome are pretty bad. Also I think when opening a file its not always possible to get a thumbnail for images, which would be useful when I need to upload an image in Firefox in a folder full of similar named images (from digicam so they all have cryptic names), and it's not possible to open files with the default application to have a quick look before uploading it.

I like the way things are in the 2nd screenshot, although the add and remove places buttons should be removed, they take up too much space, or at least reduced to + and - buttons.

---

### Post by TimJBart on 2007-04-19
Yeh I think this is a really good idea.  The save dialogues are one of my few annoyances with my ubuntu install.  Also, they seem to behave in a strange way for me.  When I try to scroll the wheel up to see all the file on the right hand panel, it is ultra slow, and only moves about 1pixel at a time.

I agree that it could do with a complete re-working.

---

### Post by oomingmak on 2007-04-19
100% support for this great idea from me too!

=D> 

And to whoever is responsible for GTK stuff, **PLEASE **show some respect for users click settings.  I do not appreciate being made to endlessly double-click my way around dialogs when I have specifically chosen the option to use **[COLOR="Red"]single[/COLOR]** click activation.

Switching back and forth between different numbers of clicks is irritating and inconsistent (not to mention troublesome for people who have motor difficulty).

---

### Post by Surkow on 2007-04-19
> **lolocaust said:**
> I was going to post something like this, the file dialogs in Gnome are pretty bad. Also I think when opening a file its not always possible to get a thumbnail for images, which would be useful when I need to upload an image in Firefox in a folder full of similar named images (from digicam so they all have cryptic names), and it's not possible to open files with the default application to have a quick look before uploading it.

I like the way things are in the 2nd screenshot, although the add and remove places buttons should be removed, they take up too much space, or at least reduced to + and - buttons.

I guess a preview function would be nice. But currently that's something that most file managers can easily do (i.e. why not use the capabilities of a normal file manager).

---

### Post by r3m0t on 2007-04-19
The Gnome team have something against the use of the file save dialog to do anything other than save files.

This one asks for delete and rename in save dialog:
[http://bugzilla.gnome.org/show_bug.cgi?id=325150](http://bugzilla.gnome.org/show_bug.cgi?id=325150)

This one asks for file management in open dialog:
[http://bugzilla.gnome.org/show_bug.cgi?id=301349](http://bugzilla.gnome.org/show_bug.cgi?id=301349)

The double/single click problem is here:
[http://bugzilla.gnome.org/show_bug.cgi?id=121113](http://bugzilla.gnome.org/show_bug.cgi?id=121113)

---

### Post by Bnonn on 2007-04-19
Then the Gnome team are silly. I suspect that there will be very, very few people who are not in favor of this idea. It would improve one of the most annoying little niggly aspects of Gnome.

+1.

---

### Post by Jhongy on 2007-04-19
I'm fully in suport of pressuring Gnome to make the dialog boxes a little more functional -- although I'm loathe to enter into comparisons with Windows or Mac. If this is too much for one iteration of changes, can I recommend cleaning up some of the most annoying bugs first?

For example, in the save  dialog, the suggested filename is lost if I change the save directory.

Say, for example, I'm saving a JPG from FireFox... the Save As dialog pops up, with a suggested directory and suggested filename. Usually, of course, I want to select a different subdirectory to save under... when I do, the filename text field becomes blank, so I have to type in a name instead. Grrrr.

Another bug: The width/height/position of the dialogs seem to be a law unto themselves. They should remember these settings.

---

### Post by CarpKing on 2007-04-19
The GTK file chooser dialog could definitely use some work.  The feature I desire most is support for showing thumbnails.  I know it can have a sidebar with a preview of the currently selected file, but this isn't quite as useful, and isn't available at all in Firefox or Epiphany, though it is in Galeon.  I was planning on posting a thread about this, and might still, seeing as this thread in title at least concentrates on the save dialog, where thumbnails aren't as important.

---

### Post by sque on 2007-04-20
Definatly very good idea! In general the common open/save dialog must be improved! It can save many of users time (and the current thumbnails of images... are far away of what is called usable!)

This is something that must be done in the near future. But.. this is ubuntu forum not gnome :S

---

### Post by muchmusic on 2007-04-20
I love this idea! That's all =p

---

### Post by MaX on 2007-04-20
> **CarpKing said:**
> The GTK file chooser dialog could definitely use some work.  The feature I desire most is support for showing thumbnails.  I know it can have a sidebar with a preview of the currently selected file, but this isn't quite as useful, and isn't available at all in Firefox or Epiphany, though it is in Galeon.  I was planning on posting a thread about this, and might still, seeing as this thread in title at least concentrates on the save dialog, where thumbnails aren't as important.


IIRC As an application developer you can plug-in the thumbnail thing. I belive Gimp does it.
I generally agree with the Gnome developers though, save shouldn't do anything else than just save.

If you want to change a filename or run another file. Open nautilus to that position.

---

### Post by Surkow on 2007-04-20
> **MaX said:**
> IIRC As an application developer you can plug-in the thumbnail thing. I belive Gimp does it.
I generally agree with the Gnome developers though, save shouldn't do anything else than just save.

If you want to change a filename or run another file. Open nautilus to that position.

There is a flaw in your reasoning. When you save a large number of files every day you'll see why you need to be able to do some file management with the save dialog. Think about opening Nautilus that often...

A solution for the gnome developers is to disable the context menu by default so that people who need it can enable it.

---

### Post by Spr0k3t on 2007-04-20
I truly hate the current load/save dialogs.  Granted they are not as heinous as their counterparts in Windows or Mac, but they could improve greatly.

I have a massive amount of visible space on most of my computer systems.  There's only one computer I have which is restricted to 800x600 (server).  What I would like to see is a dialog load/save open up to 90% of my vertical screen resolution and less than 45% of the width, or allow the option to set the sizes in a preference setting.  I would also love to see an option to center on screen, center on application, position absolute, or position relative to application.  There also needs to be setting to determine details, icon, or thumbt  These are features I miss the most from my days of using the Amiga.

---

### Post by oomingmak on 2007-04-20
> **Surkow said:**
> There is a flaw in your reasoning. When you save a large number of files every day you'll see why you need to be able to do some file management with the save dialog. Think about opening Nautilus that often.
Absolutely!

If save dialogs should only save, then Gnome should remove the places panel and breadcrumb path and just have one big save button in the middle. Choosing ***where** *to save a file is just as much a part of the act of saving as the actual write to disk.

If Gnome recognise that a user will want to save files into various different folders at different times (which is why Gnome provides a means by which to change directory) then they are already acknowledging that file management and organisation are part of the save process. If saved files did not need to be organised, then the save folder might as well be hard-coded to a single destination.

Users can't read the future, and so it is quite natural that things will occur to them only after they've got to the point of saving. Effectively punishing users for this lack of foresight (basically for being human - ironic given Ubuntu's name) is, at least in my opinion, bad design. Most GUI design guides will tell you that it is important to be forgiving of user mistakes and to make allowances for it. 

For those users that just want to constantly save without making any other changes, then their experience will not be compromised because they won't even see the context menu (as they have no reason to be right-clicking anyway). And even if they did right-click, all they'd see is what they saw if they right-clicked in Nautilus. 

It's nothing they haven't seen before.


> **MaX]If you want to change a filename or **run another file**. Open nautilus to that position.[/quote]
Where does it say anything about trying to *run *files from the save dialog? Look at the original Rationale below:


[QUOTE=Surkow said:**
> 
- Renaming is not possible;
- Moving is not possible;
- Copying is not possible;
- Pasting is not possible;
- Removing is not possible;
- Save dialogs are not expanded by default (i.e. you can't browse directories immediately).

All of the above actions are about preparing the ground for performing a file **save**. There is no mention whatsoever of using the save dialog as some kind of app launcher to '*run*' files.

---

### Post by r3m0t on 2007-04-20
> **MaX said:**
> I generally agree with the Gnome developers though, save shouldn't do anything else than just save.

If you want to change a filename or run another file. Open nautilus to that position.

I tried this with my invisible friend.

"OK, now to save this picture - whoops, why is this other picture here? This should be in 'originals', not 'altered'. I'll have to move it."
Me: "You have to go to the Places menu and open it from there."
"No no, the folder is right here on the screen... look, I'll just right-click it."
Me: "That isn't going to work. You should be saving now. Why are you doing something else?"
"OK, I'll just save the file and get on with my work."

Next time...
"Why is this other picture here?"

:(

---

### Post by junior aspirin on 2007-04-20
another anoying thing:
in nautilus ctrl+h shos hidden files. it doesn't in open/save. you have to rightliclick>show hidden files

grrr, it should just be a simplified nautilus, maybe without the menu bar.

---

### Post by Surkow on 2007-04-20
> **junior aspirin said:**
> another anoying thing:
in nautilus ctrl+h shos hidden files. it doesn't in open/save. you have to rightliclick>show hidden files

grrr, it should just be a simplified nautilus, maybe without the menu bar.

They keep saying the interface should be consistent. But the behavior of showing hidden files not consistent at all. Why can't people rename files...but can see hidden system files "normal' users shouldn't be able to see?

I like having a location bar instead of breadcrums because it's faster (you can type a part of the name of a directory and it will automatically complete the name).

---

### Post by H.E. Pennypacker on 2007-04-22
As much as I support changes to the Save As/Open dialog window, it seems this area is a lost cause for Gnome developers.  Something is stopping advancement here, when so many other operating systems actually make sense.  KDE has a sensible Save As/Open dialog as well. 

I wonder why Windows, Mac, and KDE are all using something that makes sense, and Gnome does not.  Besides, would it really hurt to have a normal and decent Save As/Open dialog?  The question is...would someone die as a result of this being changed?  It is not as if there is a compelling reason to keep the current dialog window.  There is no such reason.

We are preaching what appears to be a lost cause.

---

### Post by WiseElben on 2007-04-22
I agree, the weak Save As/Open dialogs in Gnome is annoying and must be improved. Obviously, this lack of features is a "feature" the Gnome dev team must get rid of.

---

### Post by afonic on 2007-04-22
+1000

Even if the Gnome dudes think this is fine, I find it unacceptable. There are thousands of times I want to do a simple operation (rename a folder, display hidden files) and I need to close the Save dialog first, make the change and then open the Save dialog again to actually save the file.

I love Gnome because its simple and clean but I think there is a thin line between simple GUI and a GUI that misses ways to do commonly used operations.

---

### Post by oomingmak on 2007-04-23
> **H.E. Pennypacker said:**
> We are preaching what appears to be a lost cause.
I am inclined to agree with you.

---

### Post by MaX on 2007-04-23
The Save dialogue is a part of GTK+ if you have been following the Gnome development you might know that there aren't that many GTK+ developers at all.

KDE has it all laied out since Trolltech makes Qt but no-one is actually interested in doing GTK+ work as long as it works.

This is a scenario from using windows:
[I]Browsing internet, choose to save a file.
Oops that other file should have been named in a different matter, select that, wait? what happened to the file name of the file I wanted to save? It's now the same as this one I'm trying to rename.
Ok, finish renaming the file, click cancel. Right-click and choose to save the file again, a finally I got the file name back.
[/I]
The whole Idea of the way we are saving is flawed. Take a look at Xfce, there should be a document icon that you just drag to the correct folder. The file should be constantly saved (preferably some sort of version system too).

If you save a lot of files each day, why would you want to move files around in the save dialogue?
If you use those folders that often I'd guess you'd have those places in your Favourites menu in Nautilus so getting there would be a one/two click affair.
By allowing deletion/move/copy etc. in a save dialogue you create an exponential number of (new)  possible user errors that can occur and that will cause the user to loose the data, and that's infinitely bad.

---

### Post by apoclypse on 2007-04-23
This is a great idea. I must say even Vista's save dialogue (which is uncannily similar to gtk's) is more functional at the moment. The way it works in Vista is as a mini file browser and to an extent the same goes for OSX. I think that's one thing they nailed in Vista. The save dialogue should retain as much functionality from the file manger as possible except with save specific features such as a save button.

---

### Post by Surkow on 2007-04-23
> **H.E. Pennypacker said:**
> We are preaching what appears to be a lost cause.

Indeed, it seems as if they think if it works for them it works for everyone.

> **MaX said:**
> The Save dialogue is a part of GTK+ if you have been following the Gnome development you might know that there aren't that many GTK+ developers at all.

KDE has it all laied out since Trolltech makes Qt but no-one is actually interested in doing GTK+ work as long as it works.

This is a scenario from using windows:
[I]Browsing internet, choose to save a file.
Oops that other file should have been named in a different matter, select that, wait? what happened to the file name of the file I wanted to save? It's now the same as this one I'm trying to rename.
Ok, finish renaming the file, click cancel. Right-click and choose to save the file again, a finally I got the file name back.
[/I]
The whole Idea of the way we are saving is flawed. Take a look at Xfce, there should be a document icon that you just drag to the correct folder. The file should be constantly saved (preferably some sort of version system too).

If you save a lot of files each day, why would you want to move files around in the save dialogue?
If you use those folders that often I'd guess you'd have those places in your Favourites menu in Nautilus so getting there would be a one/two click affair.
By allowing deletion/move/copy etc. in a save dialogue you create an exponential number of (new)  possible user errors that can occur and that will cause the user to loose the data, and that's infinitely bad.

Actually, I totally I agree with this. But what should be changed then? Even if the file dialog is flawed, why keep it handicapped? To drag and drop files like Xfce seems like an interesting approach. People from the Gnome mailing list have an interesting view about dragging a file into a file manager to save it:

```

On Thu, 2007-03-29 at 02:49 +0100, Alex Jones wrote:
> On Thu, 2007-03-29 at 01:55 +0100, Iain * wrote:
> > On 3/28/07, Alex Jones <[EMAIL PROTECTED]> wrote:
> > >
> > > We could do what RISC OS did, and have "save" just present you with an
> > > icon that you can drop into a file browser wherever you choose. That way
> > > we really can just use the file browser.
> > >
> > 
> > Now *that* is an original idea...I wonder why no-one has ever thought
> > of it before
> 
> I can't tell if you're being sarcastic, ironic or just funny... :P
> 
> In all seriousness, why not? The Tango Window Experiments[1] practically
> did this, and everybody loves that. [2]

I think this is a very good idea. It aligns well with the notion that
apps should always be creating and saving documents for the user
automatically. When the user is ready to "keep" the document, he moves
it to where he can remember it should be. But the act of naming is now
divorced from saving--wouldn't we be replacing the Save As dialog with a
Name dialog?

> [1] http://tango.freedesktop.org/Window_Experiments
> [2] http://wildassumptions.org/
```

But someone else seems to disagree with it because of the following reasons:

```
On 3/29/07, Alex Jones <[EMAIL PROTECTED]> wrote:

> I can't tell if you're being sarcastic, ironic or just funny... :P

I suggest you look up the meaning of these three words then...

> In all seriousness, why not? The Tango Window Experiments[1] practically
> did this, and everybody loves that. [2]

These are not "experiments". Nothing was tested.
Until there are tests these "experiments" are worthless.

reasons off the top of my head:
* Dragging is difficult for some
* The mental switching from documentation to application mode seems
distracting, at least to me.
* If we dream of a document based desktop, then why do I need to
think, "Hmm, where's my file manager gone" when I want to save the
document?

But none of these (bar the first) is backed by user testing. So user
test it (on the class of users that GNOME is targetting), then come
back to us.
```

So I wouldn't really say this is the solution either.

> **apoclypse said:**
> This is a great idea. I must say even Vista's save dialogue (which is uncannily similar to gtk's) is more functional at the moment. The way it works in Vista is as a mini file browser and to an extent the same goes for OSX. I think that's one thing they nailed in Vista. The save dialogue should retain as much functionality from the file manger as possible except with save specific features such as a save button.
So you suggest to design a file dialog that behaves like the normal file manager with some modifications to save files. Can you try to visualize it? Maybe I can create a mockup for the file dialog.

Edit: One thing I just remembered - what do you guys think about having these options when using other file dialogs like? For example...do you need to be able to rename something when you open a file?

---

### Post by Erunno on 2007-04-23
> **Surkow said:**
> ...on the class of users that GNOME is targetting...

[http://punjabsewa.gov.in/citizen-services/showServiceInfo.jsp?sid=8.8&cid=C8]("http://punjabsewa.gov.in/citizen-services/showServiceInfo.jsp?sid=8.8&cid=C8")

---

### Post by apoclypse on 2007-04-23
> **Surkow said:**
> Indeed, it seems as if they think if it works for them it works for everyone.



Actually, I totally I agree with this. But what should be changed then? Even if the file dialog is flawed, why keep is handicapped? To drag and drop files like Xfce seems like an interesting approach. People from the Gnome mailing list have an interesting view about dragging a file into a file manager to save it:

```

On Thu, 2007-03-29 at 02:49 +0100, Alex Jones wrote:
> On Thu, 2007-03-29 at 01:55 +0100, Iain * wrote:
> > On 3/28/07, Alex Jones <[EMAIL PROTECTED]> wrote:
> > >
> > > We could do what RISC OS did, and have "save" just present you with an
> > > icon that you can drop into a file browser wherever you choose. That way
> > > we really can just use the file browser.
> > >
> > 
> > Now *that* is an original idea...I wonder why no-one has ever thought
> > of it before
> 
> I can't tell if you're being sarcastic, ironic or just funny... :P
> 
> In all seriousness, why not? The Tango Window Experiments[1] practically
> did this, and everybody loves that. [2]

I think this is a very good idea. It aligns well with the notion that
apps should always be creating and saving documents for the user
automatically. When the user is ready to "keep" the document, he moves
it to where he can remember it should be. But the act of naming is now
divorced from saving--wouldn't we be replacing the Save As dialog with a
Name dialog?

> [1] http://tango.freedesktop.org/Window_Experiments
> [2] http://wildassumptions.org/
```

But someone else seems to disagree with it because of the following reasons:

```
On 3/29/07, Alex Jones <[EMAIL PROTECTED]> wrote:

> I can't tell if you're being sarcastic, ironic or just funny... :P

I suggest you look up the meaning of these three words then...

> In all seriousness, why not? The Tango Window Experiments[1] practically
> did this, and everybody loves that. [2]

These are not "experiments". Nothing was tested.
Until there are tests these "experiments" are worthless.

reasons off the top of my head:
* Dragging is difficult for some
* The mental switching from documentation to application mode seems
distracting, at least to me.
* If we dream of a document based desktop, then why do I need to
think, "Hmm, where's my file manager gone" when I want to save the
document?

But none of these (bar the first) is backed by user testing. So user
test it (on the class of users that GNOME is targetting), then come
back to us.
```

So I wouldn't really say this is the solution either.


So you suggest to design a file dialog that behaves like the normal file manager with some modifications to save files. Can you try to visualize it? Maybe I can create a mockup for the file dialog.

Edit: One thing I just remembered - what do you guys think about having these options when using other file dialogs like? For example...do you need to be able to rename something when you open a file?


What should really happen is that gtk+ becomes its own project with the enhancement of the widgeting system as its primary goal, not integration with gnome. Gnome should worry about integration gtk should just worry about the toolkit. Thats the way QT and KDE work and KDE is the better for it, often implementing things before Gnome does because the toolkit allows for it.

---

### Post by Surkow on 2007-04-23
> **apoclypse said:**
> What should really happen is that gtk+ becomes its own project with the enhancement of the widgeting system as its primary goal, not integration with gnome. Gnome should worry about integration gtk should just worry about the toolkit. Thats the way QT and KDE work and KDE is the better for it, often implementing things before Gnome does because the toolkit allows for it.

So just like with KDE the file dialogs should be a part of the toolkit? The only reason for me to dislike this is because there are very few developers that work on GTK. In other words...it will take ages before something really changes.

---

### Post by afonic on 2007-04-25
> **Erunno said:**
> [http://punjabsewa.gov.in/citizen-services/showServiceInfo.jsp?sid=8.8&cid=C8]("http://punjabsewa.gov.in/citizen-services/showServiceInfo.jsp?sid=8.8&cid=C8")

Very funny, you must be proud of yourself. :mad:

---

### Post by Naralas on 2007-04-25
Typing directories makes me happy!!

so many times I need to save to
~/pics
~/vids
~/torrents

and I don't wanna swtich back and forth the annoying Ubuntu way

---

### Post by Surkow on 2007-04-25
> **afonic said:**
> Very funny, you must be proud of yourself. :mad:

Don't worry too much about it. ;D

> **Naralas said:**
> Typing directories makes me happy!!

so many times I need to save to
~/pics
~/vids
~/torrents

and I don't wanna swtich back and forth the annoying Ubuntu way

I wonder what the best solution is to save a certain configuration of file dialogs. I assume some people still want to use the bread crums.

---

### Post by Surkow on 2007-04-27
I found a [website]("http://members.chello.nl/~h.lai/gtkenhancements/") where somebody enhanced the old version of the file selector ([old]("http://members.chello.nl/~h.lai/gtkenhancements/filesel-old.png") - [new]("http://members.chello.nl/~h.lai/gtkenhancements/filesel-new.png")). Maybe people are able to create this kind of patched for the newest GTK file dialogs.

---

### Post by oomingmak on 2007-04-27
> **Surkow said:**
> I found a [website]("http://members.chello.nl/~h.lai/gtkenhancements/") where somebody enhanced the old version of the file selector ([old]("http://members.chello.nl/~h.lai/gtkenhancements/filesel-old.png") - [new]("http://members.chello.nl/~h.lai/gtkenhancements/filesel-new.png")). Maybe people are able to create this kind of patched for the newest GTK file dialogs.
Interesting link.

It just goes to show what can be done (if the desire is there to do so).

---

### Post by CarpKing on 2007-04-28
> **Naralas said:**
> Typing directories makes me happy!!

so many times I need to save to
~/pics
~/vids
~/torrents

and I don't wanna swtich back and forth the annoying Ubuntu way

In the Open dialog there's a button next to the breadcrumbs that brings up a place to type a path.  Maybe they should put this in the Save dialog too.

---

### Post by Surkow on 2007-04-30
> **CarpKing said:**
> In the Open dialog there's a button next to the breadcrumbs that brings up a place to type a path.  Maybe they should put this in the Save dialog too.

That is something I didn't notice. Maybe this topic should be about all file dialogs? Because I guess when the Gnome guys will adapt the save dialog they will also have to adapt the open dialog.

---

### Post by CarpKing on 2007-05-01
> **Surkow said:**
> That is something I didn't notice. Maybe this topic should be about all file dialogs? Because I guess when the Gnome guys will adapt the save dialog they will also have to adapt the open dialog.

That does make sense, but if that's the case, the thread title should be changed accordingly.  Otherwise I may start a thread for the open dialog, or at least specific aspects of it.

---

### Post by pmj on 2007-05-01
I just found a hilarious bug in the save dialog. Hilarious, since it shows that nobody that works on this dialog is actually seriously using or testing their own creation. It took me this long to find it since I don't really use it much either.

Here's what you do: open the dialog and click the button to create a folder. Now move the window. The input will be taken from the folder-naming-field and the folder will be created and given the default name (or whatever you had typed in when you started moving the window). I had a fun time extracting a bunch of music albums via file-roller where the save dialog covered the whole file-roller window. I kept forgetting the name of the album I was extracting, information which I knew was in the names of the music files, files that were covered by the save dialog.. And yes, I kept forgetting myself and moved the window, creating folders named "Type name of new folder" over and over.

Hilarious.

I don't mind a basic save dialog, I just don't want it to be broken. And broken is what it is.

---

### Post by Surkow on 2007-05-01
> **CarpKing said:**
> That does make sense, but if that's the case, the thread title should be changed accordingly.  Otherwise I may start a thread for the open dialog, or at least specific aspects of it.

I think it's best to change the title to: "[IDEA] Gnome File Dialog Adaptation". I can't change it myself. I will probably edit the first post to include all file dialog problems.

> **pmj said:**
> I don't mind a basic save dialog, I just don't want it to be broken. And broken is what it is.
Agreed...but I don't think Gnome developers actually check this kind of topics. It's up to the Ubuntu guys to pick up the best ideas for the next Ubuntu release.

---

### Post by kadath on 2007-05-14
I'd just like to chime in and express my disgust with just how NON-functional GNOME's open/save dialog is.

I have a large image collection and frequently upload images to various sites via web forms. However, most of my images have numeric filenames (for example, 109475736.jpg), and since GNOME's dialog does NOT have a thumbnail view for files, I have to open Nautilus, find the appropriate file, and THEN locate the file using GNOME's open/save dialog.

Intuitive? Hardly. And the GNOME devs seem to just not give a damn.

I generally like GNOME, but it's things like this that are beginning to push me toward using KDE.

---

### Post by kevinlyfellow on 2007-05-15
> **H.E. Pennypacker said:**
> As much as I support changes to the Save As/Open dialog window, it seems this area is a lost cause for Gnome developers.  Something is stopping advancement here, when so many other operating systems actually make sense.  KDE has a sensible Save As/Open dialog as well. 

I wonder why Windows, Mac, and KDE are all using something that makes sense, and Gnome does not.  Besides, would it really hurt to have a normal and decent Save As/Open dialog?  The question is...would someone die as a result of this being changed?  It is not as if there is a compelling reason to keep the current dialog window.  There is no such reason.

We are preaching what appears to be a lost cause.

Thats the one thing I hate about gnome, they are so set in their 'great' ideas that parts of gnome become annoying.  Look what happened with gnome-screensaver...

BTW, I agree that the save dialog should have extra functionality.

---

### Post by nicky.7 on 2007-05-15
What can we do to change this?
It is possible to patch the file and propose it to gnome / ubuntu?
Does anybody know how to start?
We are the communitiy, we are the people using the software!

---

### Post by kadath on 2007-05-16
> **nicky.7 said:**
> What can we do to change this?
It is possible to patch the file and propose it to gnome / ubuntu?
Does anybody know how to start?
We are the communitiy, we are the people using the software!

The problem is this issue has already been brought up on the GNOME Bugzilla before, and the devs simply poo-poo'ed it. To quote:

> Sorry to disappoint you, but that was actually a design decision. It boils down
to how we expect our users to use the desktop, and using a "Load file" dialog to
manage your files is considered to be horribly wrong. I'm closing this bug
report as NOTABUG for now, if you strongly feel against it you can still try to
convince us to add this functionality, but it was really well thought-out :).

Maybe we can get them to change it. It's an issue that's been talked about for years, obviously.

---

### Post by Stu09 on 2007-05-16
I agree with this thread and would like to see more functionality in the Gnome Save/Open dialog.
On the other hand, It really bugs me when people here at work use the Microsoft Word Open dialog as their sole file manager! :mad:

---

### Post by oomingmak on 2007-05-16
> **Stu09 said:**
> On the other hand, It really bugs me when people here at work use the Microsoft Word Open dialog as their sole file manager! :mad:
Ewww!

#-o

---

### Post by Surkow on 2007-05-17
> **kadath said:**
> I'd just like to chime in and express my disgust with just how NON-functional GNOME's open/save dialog is.

I have a large image collection and frequently upload images to various sites via web forms. However, most of my images have numeric filenames (for example, 109475736.jpg), and since GNOME's dialog does NOT have a thumbnail view for files, I have to open Nautilus, find the appropriate file, and THEN locate the file using GNOME's open/save dialog.

Intuitive? Hardly. And the GNOME devs seem to just not give a damn.

I generally like GNOME, but it's things like this that are beginning to push me toward using KDE.

I have to agree with this. Because there is no other way to view images I have to use a file manager just to look at the contents of a file.

> **kadath said:**
> The problem is this issue has already been brought up on the GNOME Bugzilla before, and the devs simply poo-poo'ed it. To quote:



Maybe we can get them to change it. It's an issue that's been talked about for years, obviously.
I think we need to find developers who can explain us why they decided this to be a "feature". Currently I lack the knowledge to create an entry about this at [https://blueprints.launchpad.net/](https://blueprints.launchpad.net/). Because developers hardly visit these forums the chance that something would actually happen is very low.

---

### Post by Surkow on 2007-05-21
> Currently I lack the knowledge to create an entry about this at [https://blueprints.launchpad.net/](https://blueprints.launchpad.net/). Because developers hardly visit these forums the chance that something would actually happen is very low.Anyone is willing to do it or show me how to do it?

---

### Post by KLineD on 2007-06-30
In hopes that this thread is revived here's what I really hate about gnome's save dialog:

The preview thing is something I would like, it's very useful indeed, but not having it is not very annoying. At least not more than the freaking habit of the dialog to not remember the last directory, size and position used! I mean come on! I just HATE when for example in Abiword I need to open something and it defaults to /home/account when I have all my documents in /home/account/docs. Also the dialog just appears wherever it wants to, and the size...

The thing is I don't really like KDE, but I'm trying to get used to it because that issue has been going forever with gnome and there seems to be no way out. I wish I knew how to implement at least those features myself.

---

### Post by MaX on 2007-06-30
> **KLineD said:**
> In hopes that this thread is revived here's what I really hate about gnome's save dialog:

The preview thing is something I would like, it's very useful indeed, but not having it is not very annoying. At least not more than the freaking habit of the dialog to not remember the last directory, size and position used! I mean come on! I just HATE when for example in Abiword I need to open something and it defaults to /home/account when I have all my documents in /home/account/docs. Also the dialog just appears wherever it wants to, and the size...

The thing is I don't really like KDE, but I'm trying to get used to it because that issue has been going forever with gnome and there seems to be no way out. I wish I knew how to implement at least those features myself.

The Docs part will probably be fixed now that we get custom folders on the desktop.

I still think that if you save you save and if you load you load. KISS still applies.
Previewing would be very nice, but then I'd want previews of all document types.

I guess we use the computer quite differently, I use nautilus and when I want to open a file I click on it. If I want to open several documents I click on all of them from nautilus, I seldom use the open file dialogue from programs themselves. When I save I know where to save and then I do it. There's no need to see any other files during save because I'm not concerned about other files atm I just want to save the file I'm working on.

If I do get a duplicate name, I just alt-tab to Nautilus and fix it.

---

### Post by oomingmak on 2007-06-30
> **Surkow said:**
> I think we need to find developers who can explain to us why they decided this to be a "feature".
I don't see how that will make any difference. 

They have decided how users should be allowed to use their own desktops, and that's the end of it (as far as they are concerned).


Dev Quote:

"[I]Sorry to disappoint you, but that was actually a design decision. It boils down
to how **we **expect **our users** to use the desktop, and using a "Load file" dialog to
manage your files is considered to be horribly wrong. I'm closing this bug[/I]"

---

### Post by zekopeko on 2007-06-30
i would love the developers go to  flickr and upload a few pictures with non-descriptive names with their "great" save dialog which doesn't have thumbnail view!

---

### Post by ebichete on 2007-06-30
> **KLineD said:**
> In hopes that this thread is revived here's what I really hate about gnome's save dialog:

The preview thing is something I would like, it's very useful indeed, but not having it is not very annoying. At least not more than the freaking habit of the dialog to not remember the last directory, size and position used! I mean come on! I just HATE when for example in Abiword I need to open something and it defaults to /home/account when I have all my documents in /home/account/docs. Also the dialog just appears wherever it wants to, and the size...

The thing is I don't really like KDE, but I'm trying to get used to it because that issue has been going forever with gnome and there seems to be no way out. I wish I knew how to implement at least those features myself.
Don't blame the dialog. That is an application bug. The application is supposed to remember that info (it has a better idea of the context the user is operating in than GTK does) and pass it on to the dialog.

Whenever you encounter this, file a bug with the application.

---

### Post by KLineD on 2007-06-30
> **MaX said:**
> The Docs part will probably be fixed now that we get custom folders on the desktop.

I still think that if you save you save and if you load you load. KISS still applies.
Previewing would be very nice, but then I'd want previews of all document types.

I guess we use the computer quite differently, I use nautilus and when I want to open a file I click on it. If I want to open several documents I click on all of them from nautilus, I seldom use the open file dialogue from programs themselves. When I save I know where to save and then I do it. There's no need to see any other files during save because I'm not concerned about other files atm I just want to save the file I'm working on.

If I do get a duplicate name, I just alt-tab to Nautilus and fix it.

I get the whole KISS principle and actually I LIKE the way the gnome desktop is. However things like the dialogs not remembering your settings (directory, size, location) it's a mayor drawback (for me) and has nothing to do with the simplicity or atomicity of the save/load dialog.

For the preview, well I guess it's fair to say why should I want picture preview and not openoffice documents preview, pdf preview, or music preview, etc. But I still think that for pictures it's way easier for the user to get a glipmse of the picture and that, I think, has a lot to do with the way images are used nowdays (with digital cameras)

---

### Post by KLineD on 2007-06-30
> **ebichete said:**
> Don't blame the dialog. That is an application bug. The application is supposed to remember that info (it has a better idea of the context the user is operating in than GTK does) and pass it on to the dialog.

Whenever you encounter this, file a bug with the application.

That I didn't know. Thanks for the clarification.

---

### Post by CarpKing on 2007-07-01
> **MaX said:**
> Previewing would be very nice, but then I'd want previews of all document types....

I seldom use the open file dialogue from programs themselves. When I save I know where to save and then I do it. There's no need to see any other files during save because I'm not concerned about other files atm I just want to save the file I'm working on.

If I do get a duplicate name, I just alt-tab to Nautilus and fix it.

I too rarely use "open" dialogs, but when I do, I'm usually trying to upload pictures to the Internet.  This is where thumbnails come in.  Previews of non-image files could occasionally be handy, but a thumbnail of a document would have to be rather large to be discernible from one another.  Thumbnails of images, on the other hand, would be very useful.  The current previews (in a side panel) are better than nothing, but they are only used by a few programs.  

Resorting to Nautilus as part of your save/load process is a break in efficiency that should be avoided.

---

### Post by diggity on 2007-07-01
I think there needs to be a compromise. Users should be able to at least delete or re-name files during a save because there could be a naming collision the user is not aware of until the save process has begun. It is unproductive to cancel the save or switch windows to solve the issue and then perform the save again.

Previews of files should be handled the same as the file manager (configurable to on/off and based on filesize/type).

---

### Post by MaX on 2007-07-18
> **CarpKing said:**
> I too rarely use "open" dialogs, but when I do, I'm usually trying to upload pictures to the Internet.  This is where thumbnails come in.  Previews of non-image files could occasionally be handy, but a thumbnail of a document would have to be rather large to be discernible from one another.  Thumbnails of images, on the other hand, would be very useful.  The current previews (in a side panel) are better than nothing, but they are only used by a few programs.  

Resorting to Nautilus as part of your save/load process is a break in efficiency that should be avoided.

Yeah, uploading images to the web causes a problem. But now I use picasa instead :)
Maybe even f-spot supports uploading to flickr and picasa web albums?

---

### Post by zekopeko on 2007-07-18
> **MaX said:**
> Yeah, uploading images to the web causes a problem. But now I use picasa instead :)
Maybe even f-spot supports uploading to flickr and picasa web albums?

yes it does. just select the images you would like to upload, go to file>export>Picasa/Flickr

---

### Post by zsouthboy on 2007-07-18
I would settle for a simple button on the load/save dialog box that says "Open current location in nautlius" (hidden, if needed, to protect users from themselves, by default)

---

### Post by happy-and-lost on 2007-07-19
+1 here. The file management as a whole in Gnome needs a good sorting out. Just don't make it hideous like the KDE save dialog.

---

### Post by Surkow on 2007-07-24
Woah...suddenly lots of replies. I still think if the GTK people do not want to alter their dialogs they should implement a way to let file managers like Nautilus or thunar handle them as well. This way the dialogs can be altered a lot easier.

---

### Post by benx009 on 2007-09-28
it would be nice to be able to cut/paste/delete files while still in the "open" dialog like you can in windows because i've noticed that i do that a lot when i want to quickly reorganize the files in my folders when i'm opening something.  it sure beats have to go back to the desktop, click "home folder" and then browse to whatever folder i was opening from and then reorganize from there.  unfortunately, the only options the open dialog gives you are "add to bookmarks" and "show hidden files."  perhaps this isn't much an ubuntu fault as it is a gnome fault, but still.  i've honestly never understood why this was never present in "user-friendly" ubuntu.  i mean, i really don't think it would be that hard to implement (but what do i know, i'm no programmer...)

---

### Post by smartboyathome on 2007-09-28
You don't have to go back to the desktop. You can use the "Places" menu on the top bar. That way, you can just reorganize inside nautilus, You should talk to GNOME about this, too, and setup blueprints on Ubuntu and GNOME.

---

### Post by 23meg on 2007-09-28
Merged.

---

### Post by gaspard.leon on 2007-12-11
TITLE INCORRECT: should be "[IDEA] Open/Save dialog enhancements"

As seen in:
[http://ubuntuforums.org/showthread.php?t=413457]("http://ubuntuforums.org/showthread.php?t=413457")

GTK open/save dialogs:

[LIST]
[*]switching breadcrumbs off, and typing in a folder name, then pressing enter does not open that folder.

[*]The thumbnails seen in nautilus do not appear, so browsing for pictures is annoying.

[*]The right-click context menu is not the same as nautilus, so you can't just quickly rename, copy, paste, delete files, preview images, etc...

[*]You CAN create a folder from the save dialog, but be sure to type the name correctly... if not you will need to open nautilus and find the folder...

[*]The save dialog does not remember the file name if you switch folders... arrgh
[/LIST]

that's my list of problems/new features... either way you want to see it.

I mostly like the Ubuntu/GNOME interface, but the file open/save dialogs are irritating...

and a "Future" feature would be to remember the folder and window position per-application, I know applications can spawn the window in a folder, and I assume they can specify where the dialog appears on screen, but not all application developers can be bothered to add these conveniences, so it would be nice if the save/open dialog remembered stuff on it's own..

---

### Post by smartboyathome on 2007-12-12
I think this will be implimented along with GVFS in the upcoming Gnome release.

---

### Post by 23meg on 2007-12-12
I've merged this with the old thread from the Gutsy Gibbon Idea Pool on the same issue.

---

### Post by Joe_Bishop on 2007-12-12
That is bad idea. Your brains, guys, too deep in windows. If the file dialog would be a file manager, you can't do a great thing: drag some file, drop it on to the "Open File Dialog". The dialog focus is switched to directory which contains the file.

---

### Post by shafin on 2007-12-13
> **Jhongy said:**
> I'm fully in suport of pressuring Gnome to make the dialog boxes a little more functional -- although I'm loathe to enter into comparisons with Windows or Mac. If this is too much for one iteration of changes, can I recommend cleaning up some of the most annoying bugs first?

For example, in the save  dialog, the suggested filename is lost if I change the save directory.

Say, for example, I'm saving a JPG from FireFox... the Save As dialog pops up, with a suggested directory and suggested filename. Usually, of course, I want to select a different subdirectory to save under... when I do, the filename text field becomes blank, so I have to type in a name instead. Grrrr.

Another bug: The width/height/position of the dialogs seem to be a law unto themselves. They should remember these settings.
+1

---

### Post by CarpKing on 2007-12-15
> **smartboyathome said:**
> I think this will be implimented along with GVFS in the upcoming Gnome release.

Any source for that?  I don't see it in the [Gnome Roadmap]("http://live.gnome.org/RoadMap").  GVFS is on there, but they don't mention anything about the file chooser.  I did see [this](http://blogs.gnome.org/carlosg/2007/10/26/giving-the-last-kicks-in-libgnomeuis-butt/), but I've seen no confirmation that it is actually being used.

---

### Post by james.wong on 2008-04-02
Hi,

I have to agree.

I've just moved from KDE on FreeBSD to Gnome on Ubuntu, and I'm very impressed with most things.

But I'm really quite disappointed with the file open/save dialogues. In KDE, they have the functionality of a file manager, and I can access files on remote servers with ease.

Other things I miss are the file move/copy windows, which show much more information than the Gnome ones, and also in Dolphin or Konqueror, when you paste a file into a folder containing a file of the same name, it gives you the option of overwriting or specifying a new name, where Nautilus does not.

---

### Post by bruce89 on 2008-04-02
> **james.wong said:**
> Other things I miss are the file move/copy windows, which show much more information than the Gnome ones, and also in Dolphin or Konqueror, when you paste a file into a folder containing a file of the same name, it gives you the option of overwriting or specifying a new name, where Nautilus does not.

You'll like GNOME 2.22 then:

[IMG]http://media.arstechnica.com/reviews/os/gnome-2-22-review.media/GVFS.png[/IMG]

---

### Post by Dmole on 2008-04-05
I wonder if we can vote for the address bar some where. Maybe if they see that 90% of users want it...

[EDIT]
just found that you can use the name portion of the save dialog as an address bar
start with / and auto suggest will aid you
I just saved a file to "/media/NO NAME/PRIVATE/SmarTone-Vodafone/My Items/Other Documents/personal/working.txt"  this way

---

### Post by dimovnike on 2008-06-15
> **gaspard.leon said:**
> 

[LIST]
[*]switching breadcrumbs off, and typing in a folder name, then pressing enter does not open that folder.

[*]The thumbnails seen in nautilus do not appear, so browsing for pictures is annoying.

[*]The right-click context menu is not the same as nautilus, so you can't just quickly rename, copy, paste, delete files, preview images, etc...

[*]You CAN create a folder from the save dialog, but be sure to type the name correctly... if not you will need to open nautilus and find the folder...

[*]The save dialog does not remember the file name if you switch folders... arrgh
[/LIST]



I recently moved from windows to Ubuntu Gutsy (then Hardy). I like GNOME, and I really like the way copying files is handled and other things, but...  these dialogues are really annoying, they just make you waste time. I don't understand the developer's point of view, the fact is that an user wastes time because of lack of this features. 

I personaly need these features. And many people would use them if the would have them...

---

### Post by cszikszoy on 2008-06-15
They [gnome devs] have some pretty ridiculous rationale for not implementing this.  The impression that I got from reading the links to the bug reports (on the first page) was that they think there is something "fundamentally wrong" with wanting to do simple file operations from the save / load dialogs.

Support *for* this seems to be pretty unanimous, and I am definitely in favor of implementing this.  If this is what the vast majority of users would prefer then I don't see how that is "fundamentally wrong".

---

### Post by dsm iv tr on 2008-06-15
I wonder if there's a way to replace the stock Open/Save dialogs., with a GTK extension lib or something. I don't know a lot about gtk2 outside of python/glade.

---

### Post by dimovnike on 2008-06-16
I guess the best way is to make GTK configurable so it can use it's own dialogs or use default filemanager (nautilus/pcmanfm/etc...). The filemanager can keep the whole rightclick menu but the default item must be open or save. I guess the filemanagers then must support dialog mode, but as soon as the GTK will allow using them - the filemanagers will be added this feature. I wonder if gnome developers are reading this :)

---

### Post by Prometheus28 on 2009-03-30
> **Spr0k3t said:**
> I truly hate the current load/save dialogs.  Granted they are not as heinous as their counterparts in Windows or Mac, but they could improve greatly.

I have a massive amount of visible space on most of my computer systems.  There's only one computer I have which is restricted to 800x600 (server).  What I would like to see is a dialog load/save open up to 90% of my vertical screen resolution and less than 45% of the width, or allow the option to set the sizes in a preference setting.  I would also love to see an option to center on screen, center on application, position absolute, or position relative to application.  There also needs to be setting to determine details, icon, or thumbt  These are features I miss the most from my days of using the Amiga.

I agree 100%. The current method might work for a few limited users who cannot afford huge monitors or double desktops. But in the future, and for most people with enough money, there is no reason save/load dialog should look like a freaking dos terminal. I want huge thumbnails and easily customized(and saved config) load/save dialog for all of my programs.

---

