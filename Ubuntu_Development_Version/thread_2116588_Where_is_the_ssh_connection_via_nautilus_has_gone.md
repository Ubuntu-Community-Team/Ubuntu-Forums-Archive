---
title: "Where is the ssh connection via nautilus has gone?"
date: 2013-02-16
forum: Ubuntu Development Version
---

### Post by Joao Lacerda on 2013-02-16
Hi friends.

how to connect to ssh server with 13.04 via nautilus?

please see image.

thank you for your time.

---

### Post by Budovi on 2013-02-16
```
protocol://hostname:port
```
should work. You need to specify port only if it is not default one.

I just tried it with SSH and works flawlessly.

---

### Post by Morbius1 on 2013-02-16
You have got to be kidding me. Gnome has changed "Connect to Server"? Because the old way was too intuitive? 

The unrelenting desire to reduce function by Gnome is making Gnome irrelevant. They didn't take it away in Xubuntu 13.04 did they?

---

### Post by Morbius1 on 2013-02-16
Just out of curiosity and only if you have the time does Gigolo exhibit the same lack  of options? When you run gigolo and use the Actions > Connect you should get the attached dialog box.

---

### Post by VinDSL on 2013-02-16
Works fine here, too...

I need to connect to remote (web) servers often.

There are a couple of ways of doing it:
[LIST]
[*]Connect to Server
[*]Enter Location
[/LIST]

I prefer "Enter Location", e.g. via command line.

To make life easier, once you successfully mount the server:
[LIST]
[*]Right-click the server name
[*]Add Bookmark
[/LIST]

That way, in the future, it becomes a single-click (bookmark) & auth (enter credentials) affair...  ;)

---

### Post by VinDSL on 2013-02-16
> **Morbius1 said:**
> You have got to be kidding me. Gnome has changed "Connect to Server"? Because the old way was too intuitive?
Depends on how you look at it...

I didn't care for Gnome's "less_is_more" paradigmatic shift, at first blush.  

I actually quit using Nautilus, for several months, because of all of the functionality they stripped out of it, but finally reneged.  After all, we're supposed to be testing this stuff, warts and all.

Now that I'm starting to get used to the changes, I find them more palatable.

That said, Nautilus is at least usable now, and getting better every day.

Stay tuned...  ;)

---

### Post by cariboo on 2013-02-16
I just enter the url manually, in the location bar, the first time, then bookmark the connection in Nautilus, then use the bookmark from then on.

The process I use the first time is:

[LIST=1]
[*]Open Nautilus
[*]Press Ctrl-t to open a second tab
[*]Press Ctrl-l to open the location bar
[*]type sftp://servername
[*]do what i have to.
[*]Profit :)
[/LIST]

---

### Post by EgoGratis on 2013-02-16
Yes the new dialog does look like it's made for more experienced users except added Browse button if i understand correctly what it's for does simplify network shares discovery if less experienced user finds this dialog in Nautilus/Files. But for "command line" example at least it should be added how you define port number in the example or better yet as it was suggested use protocol://hostname: port as more general example.

But basically new dialog is just one more "command line" GUI tool? Good or bad i don't know but i guess if you want to make nice and simple GUI tool to connect to variety of server (protocols) and you end up with just another "command line" embedded in GUI dialog it kinda beats the purpose indeed!

---

### Post by Budovi on 2013-02-16
I agree, that now it is for "more experienced users", and previous version was "just more GUI" with a ton of boxes and lists,

but look at that this way:
I really doubt, that some person, which is able to use ftp/ssh/sftp/whatever, never saw or is not able to "learn" basic URL format, and then it is nicely in one place  :D . With provided example is not that hard to guess. And once it is saved... :popcorn:

---

### Post by EgoGratis on 2013-02-16
> I agree, that now it is for "more experienced users", and previous version was "just more GUI" with a ton of boxes and lists,

I don't know if i agree it had a ton of boxes and lists. What it had was at least list of protocols it supports. The new tool doesn't indicate what protocols are supported.

It had port box and new tool doesn't try to show how the port should be set. It just expects you are experienced in "command line".

> I really doubt, that some person, which is able to use  ftp/ssh/sftp/whatever, never saw or is not able to "learn" basic URL  format, and then it is nicely in one place  :grin: . With provided example is not that hard to guess. And once it is saved... :popcorn:

Yes once you learn something then it isn't a problem anymore. But for example few random users were confronted with Unity and didn't understand "Dodge Windows" behavior and it was removed. Let's say this was true for the sake of argument and now imagine the same users are confronted with this dialog and they have to use one of the supported protocols to connect to the server. I imagine this would be mission impossible and old dialog at least gave the possibility to click on those 3 boxes multiple times  and make it work somehow.

Now you have to know exactly what you are doing with no feedback and if you don't manage to do exactly what it want you to do in command line then it won't work and the odds to guess what it wants from you are basically null.

---

### Post by EgoGratis on 2013-02-16
But hay i am not complaining i am just expressing my opinion and in this particular case i don't see the point in having such tool because it only opens up another dialog with embedded "command line" and this is something "ctrl+l" already does. 

Ditch it then completely if those 2 boxes are too much. I would because in current state it's bloated (just another command line more in Files to use) or maybe better term would be same feature implemented two times and that is confusing and redundant.

---

### Post by Morbius1 on 2013-02-17
I think I understand the the nature of the problem. The attachment is a screenshot of "Connect to Server" in OSX. Someone must have sent the Gnome developer a memo with a similar screeshot that said: "make this happen".

---

### Post by EgoGratis on 2013-02-17
Yes this is silly and there in no better word for it sorry. Anyway we have "CTRL+l" that gets the job done and at least GNOME be consistent and remove this new useless dialogue because it's  "CTRL+l" duplicate and therefore bloat at least by GNOME standards.

Experienced users in this topic expressed they don't use the tool anyway and for less experienced users is useless too and i don't see the reason why "CTRL+l" couldn't be used instead and why have two GUI command lines instead of one.

---

### Post by EgoGratis on 2013-02-17
And yes it looks like somebody bought Apple computer and just can't get enough of it but i don't know what exactly should that have to do with GNOME. But for the GnomeShell no there we must not directly copy Apple.

It would be insane to give the users standard desktop experience.

---

### Post by Morbius1 on 2013-02-17
Don't get me wrong, if you are going to copy the UX of another operating system better it be OSX than something like this: [http://plan9.bell-labs.com/plan9/screenshot.html](http://plan9.bell-labs.com/plan9/screenshot.html)

---

### Post by EgoGratis on 2013-02-17
I personally don't mind if this is direct copy from Apple UX but the mindset lately sucks. It happened with Nautilus too for example (direct Apple UX copy and because of that some  features had to go and more...) just to look like Apple UX? And what will happen when Apple changes it's UX GNOME becomes depreciated and old Apple UX project?

In this latest addition small and efficient GUI tool to connect to servers was striped down to GUI command line input duplicating "CTRL+l" capabilities. I would not be surprised if Apple upgrades it's tool and adds one drop down list of supported protocols just to mock GNOME.

And again i am not complaining because i am use to this and it would not help to complain anyway it's just amateurish and silly in the end.

And yes if GNOME has become Apple wannabee then i guess i do have a problem with this because then i would rather use the real thing. And again there is nothing fundamentally wrong if GNOME does copy UX from Apple where it does make sense but striping down small and efficient GUI tool suitable for experienced and novice users to bare GUI command line tool JUST TO LOOK LIKE Apple is...

---

### Post by Budovi on 2013-02-17
Ok, in my previous answer I really thought there must be reason for such a change and I took it as "Ok, if it has to be this way, I could live with that, it is not that bad". But if this is true - because of Apple's UI, this is so silly that it cannot be described politely.

I just cannot understand people blindly approaching everything about Apple, for no good reason (and no, I have nothing against "normal Apple users" and also see some advantages of their devices/UI).

I could understand this change, as a copy of Apple's layout, if their UI was better. But this is not that case. More stupid reason is only "we needed to remove 100 lines of code because Raring still cannot fit on regular CD".

---

### Post by Morbius1 on 2013-02-18
>  I could understand this change, as a copy of Apple's layout, if their UI  was better. But this is not that case. More stupid reason is only "we  needed to remove 100 lines of code because Raring still cannot fit on  regular CD".Although I agree generally with the rest of your post let us not forget that the culprit here is not Ubuntu but Gnome.

Look, Nautilus used to show up as "File Manager" but the Gnome developers reasoned that they really didn't want it to "Manage" anything so it was changed to "Files". Soon more function will be removed and it will be listed as "F" and eventually just dropped altogether.

[COLOR=Blue]*The ironic thing about copying OSX's "Connect to Server" utility is that it is a very uncharacteristic thing for Apple to do. I don't mean this as derogatory as it will sound but Apple really doesn't want their users to think. They abhor presenting their users with error messages if they or it does something silly. Most of them don't even know that they have a Terminal emulator installed. Yet they are expected to know the syntax when connecting to a samba or ssh server? It's a curious thing.*[/COLOR]

---

### Post by Budovi on 2013-02-18
Wait, this means that right-click folder context menu was reduced because of Nautilus is no more "File Manager"? I want to manage my files! Sure it is manager, and "Files" is just stupid name for "file explorer / manager".... Open files... Sounds really stupid and it obviously means something else.

This is so bad change, I really hate it already, why would they do that?!

New trends == removing features?? Ouch...

---

### Post by EgoGratis on 2013-02-18
Yes i remember when this trend started and GUI tool for creating launchers had to go but launchers stayed and didn't go anywhere.

But don't feel bad about it you will get use to it. Looks like this is a phase (removing stuff) and we can't do much about it ATM and once this trend to remove everything because "i decided nobody uses it anyway" and "Apple Phase" is over then i guess the situation will calm down. There are some nice features/improvements coming out of GNOME camp and that is why i am still modestly optimistic about the GNOME future.

---

### Post by alphacrucis2 on 2013-02-18
My theory is that gnome 4 will remove all features and the Gnome devs will then be able to retire. Command line only for us plebs.

---

### Post by cariboo on 2013-02-18
This thread has veered way off topic, and I think the op's original question was answered, so it's time to close this thread.

---

