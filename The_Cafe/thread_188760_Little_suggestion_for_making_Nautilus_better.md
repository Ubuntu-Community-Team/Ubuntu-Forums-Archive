---
title: "Little suggestion for making Nautilus better"
date: 2006-06-04
forum: The Cafe
---

### Post by el3ktro on 2006-06-04
Hi there,
well I really like Nautilus as a file manager, but I have a few little things which I'd like to see different.

One thing that really bugs me is that you can't eject a CD or USB stick in the "Places" sidebar or the places menu. I'd suggest something similar to Mac OS' Finder: Put a mall "eject button" behind all removable drives (see my screenshot).

Another thing would be: Make the icons a little bigger, and print the amount of free space available beneath the name of the drive. This is an always imporant information for me. Perhaps you have some other ideas of what information we could display here.

My third suggestion is about this "Places" thing. I think it makes no sense to have a "Desktop folder" and a "Desktop place" at the same time - it is confusing imho. Why not have a "Desktop" in the place menu/sidebar, and put all desktop files into a hidden directory ~/.desktop? (Again, look at my screenshot, there's no Desktop folder, only a Desktop "place".

For consistency, I'd also remove the "Personal folder" and "Computer" icon from the Nautilus toolbar, and put a Computer icon into the places sidebar - because there's also a Computer icon in the places panel menu. Why do I find everything in the places menu - but why do I find everything _except_ the Computer in the places sidebar?

The places sidebar should reflect the places menu, except it should show all mounted/available places and have no buttons to add new places, like the places menu has (e.g. Connect to server...)

The places siebar should look like this:

```

Personal folder
Desktop
-------------------
Computer
File system
<list of internal harddisks>
<list of internal CD/DVD, incl. burner device>
<list of remoavle USB/FW drives>
-------------------
Network
<available network mounts>

```

The places menu in the panel would have the same structure, except that in the "Network section" there's a button to connect to a server, and it sould have the search option and the "last viewed documents" button. The places menu in the panel also could have the "free space available" display and the eject buttons.

What do you think?

---

### Post by mscman on 2006-06-04
I think that adding a small eject button next to its selection on the places panel would be an excellent idea.  It could make ejecting devices just a little bit easier and faster (although not a huge groundbreaking amount... just for convenience)

---

### Post by henriquemaia on 2006-06-04
This is an excellent idea. Try posting this suggestion on lauchpad and contact nautilus developers.

---

### Post by el3ktro on 2006-06-04
[QUOTE=henriquemaia]This is an excellent idea. Try posting this suggestion on lauchpad and contact nautilus developers.[/QUOTE]

I'd surely do that :-) I made a little better mockup, also showing how I think that the places sidebar should be more reflecting the places menu in the panel - although that when I think of it this extra information (free space, "click here to burn etc." is a little too much. Perhaps instead of a "blablabla GB free" text there could be a small colored bar expressing the size of the disk and how much it is filled!?

Tom

---

### Post by henriquemaia on 2006-06-04
[quote=el3ktro]I'd surely do that :-) I made a little better mockup, also showing how I think that the places sidebar should be more reflecting the places menu in the panel - although that when I think of it this extra information (free space, "click here to burn etc." is a little too much. Perhaps instead of a "blablabla GB free" text there could be a small colored bar expressing the size of the disk and how much it is filled!?

Tom[/quote]

I like it even more now you redone the mockup. This should really be sent to developers, because this is a great idea (my opinion).

I prefer the text for the size, but maybe developers could use give the coloured bar option too, although gnome approach is simplicity. But maybe changeable on gconf. 

Nice idea and nice work to show it.

---

### Post by nalmeth on 2006-06-04
YOu can make the icons look bigger by holding CNTL and scrolling up or down.

---

### Post by el3ktro on 2006-06-04
[QUOTE=nalmeth]YOu can make the icons look bigger by holding CNTL and scrolling up or down.[/QUOTE]

I know about this, but it's only true for the actual directory view, it doesn't work in the sidebar. There's nothing wrong with the icon size in the sidebar right now, but _if_ there would be a second text line showing extra information, then I think the icons should be _a little_ bigger to match better.

Tom

---

### Post by el3ktro on 2006-06-04
[QUOTE=henriquemaia]I like it even more now you redone the mockup. This should really be sent to developers, because this is a great idea (my opinion).

I prefer the text for the size, but maybe developers could use give the coloured bar option too, although gnome approach is simplicity. But maybe changeable on gconf. 

Nice idea and nice work to show it.[/QUOTE]

Thanks :-) What do you think about the "consistency" between the places sidebar and the places menu? I think this is an issue, too.

I think another improvement would be to integrate Beagle search into Nautilus. When the "personal folder" and the "computer" icon in the toolbar are gone, there would be more space for a search bar. It could look like this:

Search for [Documents] ____________________

While [Documents] is actually a drop down list like Beagle has it, where you can choose between All, Documents, Media files, E-Mails, Contacts etc. etc. and the underline would be a input field. If you enter something there, Beagle is asked to search for matching files, and Nautilus would present the search result.

Tom

---

### Post by disturbed1 on 2006-06-04
> One thing that really bugs me is that you can't eject a CD or USB stick in the "Places" sidebar or the places menu. I'd suggest something similar to Mac OS' Finder: Put a mall "eject button" behind all removable drives (see my screenshot).

Never knew that. I always use tree view, and right-click eject works that way.

---

### Post by henriquemaia on 2006-06-04
[quote=el3ktro]Thanks :-) What do you think about the "consistency" between the places sidebar and the places menu? I think this is an issue, too.

I think another improvement would be to integrate Beagle search into Nautilus. When the "personal folder" and the "computer" icon in the toolbar are gone, there would be more space for a search bar. It could look like this:

Search for [Documents] ____________________

While [Documents] is actually a drop down list like Beagle has it, where you can choose between All, Documents, Media files, E-Mails, Contacts etc. etc. and the underline would be a input field. If you enter something there, Beagle is asked to search for matching files, and Nautilus would present the search result.

Tom[/quote]

Sorry, I forgot to address that too. The consistency between places and side bar is apparently good, but I don't nkow if that is practical in the long run (like having lots of bookmarks, lots of network connections, etc). Maybe other can say their opinions to have a general idea.

On the Beagle intregation, that's also good, but Beagle must be stable enough for nautilus developers think about it (I guess). You really must share your ideas with them to get the proper scenario. Maybe someone around here knows what is the best approach for this.

---

### Post by el3ktro on 2006-06-04
[QUOTE=disturbed1]Never knew that. I always use tree view, and right-click eject works that way.[/QUOTE]

Yeah thats what I mean: It works in the sidebar tree view, but _not_ in the sidebar places view - which is inconsistent imho.

Tom

---

### Post by el3ktro on 2006-06-04
[QUOTE=henriquemaia]Sorry, I forgot to address that too. The consistency between places and side bar is apparently good, but I don't nkow if that is practical in the long run (like having lots of bookmarks, lots of network connections, etc). Maybe other can say their opinions to have a general idea.

On the Beagle intregation, that's also good, but Beagle must be stable enough for nautilus developers think about it (I guess). You really must share your ideas with them to get the proper scenario. Maybe someone around here knows what is the best approach for this.[/QUOTE]

Wow, I never knew about this bookmark feature - just figured that out. Yeah if you have a lot of them then of course it can become a mess - but it would also become a mess as it is today, I didn't change so much, I just suggested to re-order the places sidebar a little to match the places menu.

Perhaps Nautilus could just optionally integrate Beagle. Put my suggestion into the toolbar, but use the old-fashioned Nautilus search. If Beagle is installed, then automatically use it (or enable it via preferences or gconf.

---

