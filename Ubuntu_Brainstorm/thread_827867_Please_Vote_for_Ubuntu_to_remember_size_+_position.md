---
title: "Please Vote for Ubuntu to remember size + position of all windows"
date: 2008-06-13
forum: Ubuntu Brainstorm
---

### Post by erlguta on 2008-06-13
Hi.

It is incredible that Ubuntu (gnome) does not remember windows posittions.
I am bored of constantly resizing / maximizing / repositioning my windows every time i power on my PC.

Please read this idea in Ubuntu Brainstrom:
[http://brainstorm.ubuntu.com/idea/1442/](http://brainstorm.ubuntu.com/idea/1442/)

I am surprised that so few people show interest in this improvement. For me it is essential, is BASIC in one modern OS.

If you think the same, vote for this needed option...

Thank you for your time.

---

### Post by housam on 2008-06-13
I agree to add this necessary feature to the next versions of Ubuntu applications.

---

### Post by ibutho on 2008-06-13
Should this not be addressed to the GNOME developers? I can't see how the Ubuntu devs can resolve this because its a problem with GNOME thats not restricted to Ubuntu.

---

### Post by frodon on 2008-06-13
This is strange as for me size and window position are saved without any problem, are you sure you checked the box which tells to save your session each time you log out (it's in the session configuration window) ?

If you want to do this manually once type "gnome-session-save" in a terminal.

And if you want to control all, what you're looking for is devilspie.

---

### Post by forestpixie on 2008-06-13
Never quite got my head round that current session thing and didn't want to try tbh :)

So - if I for instance have a bunch of apps which I have starting in sessions open where I want them and then use the Automatically remember option I don't have to have them all starting in Sessions startup programmes and they will also stay where I put them.

Is that right?

---

### Post by frodon on 2008-06-13
Yes it's supposed to do that, pratically there's some apps that can't be handled by the session-save tool like amule for instance but most common apps are 100% supported.

Also i don't really get the OP suggestion in brainstorm as on my computer size and position are perfectly saved for each apps, i mean if i resize rythmbox close it then the change is saved and next time i'll open it it will have the new saved size.

---

### Post by forestpixie on 2008-06-13
Cool I'll try that then - I only start amarok and thunderbird - thanks for that. Never thought it was worth starting athread for so to get the answer like this is great :D

Edit - save state doesn't like tbird and alltray

Edit edit - got it right eventually - two instances of amarok, a bash terminal, oepra telling me it couldn't find the plugin directory and opening nautilus, thunderbird desperately trying to start even though it an alltray weren't supported ... phew :)

Finally worked out that I had to make sure that they were not in the current session list - even after they'd been closed :)

---

### Post by bruce89 on 2008-06-13
You can hardly expect non-GNOME programs to save states properly.

---

### Post by forestpixie on 2008-06-13
Personally I don't expect anything - never get disappointed either.

---

### Post by olskar on 2008-06-13
I have been told that this is an issue that is difficult to fix because they do not know who should fix it. Whos responsibility it is or something. So until that is made clear, voting won't get us very far..please correct me if I'm wrong.

---

### Post by dennymeta on 2008-09-30
Yeah, GNOME and Metacity people say it is the application's business to save its position.  Application developers (and users!) all see quite clearly that this is something the window manager should handle (the clue's in the name, people - manage the damn windows!)

So basically, nobody is going to fix it.  Meanwhile KDE, MacOS and Windows all do this correctly, so people coming from any of those to GNOME are going to be very disappointed by the sheer stupidity of having to re-size and re-position your windows every single time you restart your machine or your X session.

---

### Post by gnomeuser on 2008-09-30
There is a a valid case to be made for applications to manage this kind of state information. Often an application will have more rich state information already such as which tab is active, what documents were loaded e.g. Adding the coordinates to this set would not be hard and as such you would get more than just positional data when saving your session which is likely what people really want - namely restore my desktop to the state I left it in.

Another reason would be replacing the window manager, all the complicated code would need to be ported each time we have a new window manager instead of being present once in the application layer (with hooks to the session and window manager).

Ultimately you'd probably want this to be a fdo standard with a reference library to handle the distribution of information, then each application would have to save it's own additional state information seperately because only your wordprocessor e.g. knows which document was open, how far down you were scrolled, where the cursor was and so on. 

However if all you want is the relatively dumb task of remembering window placement then sure you could do that in.. every single window manager known to mankind and if we are really lucky they might even agree on what format to save this information in. This however is not really a nice solution as is shown above, it would only need to take hints from the application and session manager then play it's part in the larger scheme.

---

