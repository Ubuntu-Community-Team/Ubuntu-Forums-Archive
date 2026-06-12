---
title: "Problems running DDO"
date: 2009-04-28
forum: Wine
---

### Post by horgabob on 2009-04-28
So I posted this a few days ago and for some reason the thread was closed before I got any response....

Please help!

Whenever I launch DDO I get this error:

"System.NotImplementedException: Not implemented.
at System.Drawing.Graphics.GetNearestColor(Color color)
at System.Windows.Forms.Label.OnPaint(PaintEventArgs e)
at
System.Windows.Forms.Control.PaintWithErrorHandlin g(PaintEventArgs e, Int16 layer, Boolean disposeEventArgs)
at System.Windows.Forms.Control.WmPaint(Message&m)
at System.Windows.Forms.Control.WndProc(message&m)
at System.Windows.Forms.Label.WndProc(Message&m)
at
System.Windows.Forms.ControlNativeWindow.OnMessage (Message&m)"

There's more to it but I dont' feel like typing the mumbo-jumbo

any ideas?

Ubuntu 8.10
2.8 GHz Single Core CPU
1 GB RAM
ATI X1300/1550 Video Card

---

### Post by ajackson on 2009-04-28
> **horgabob said:**
> There's more to it but I dont' feel like typing the mumbo-jumbo

Do you feel like reading the [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2910") page for DDO?

The "mumbo-jumbo" can often contain some very useful information, sometimes googling some of that "mumbo-jumbo" (or maybe even DDO wine or DDO linux) can get a wealth of information. Maybe you didn't feel like searching either or reading stickies hey?

---

### Post by horgabob on 2009-04-28
Actually, I did a lot of searching and reading of stickies before posting, so please don't assume that I post questions simply because I am lazy. I came here looking for help and I don't really think the sarcastic response was necessary. 

The rest of the "mumbo-jumbo" I was referring to was the exact same type of thing I had already posted, and to be honest the game would freeze and distort, which would make most of it unreadble anyway, so I don't think I'd be able to copy it.

As far as the AppDB, I'm kinda new to Wine, so I'm still unsure what it means, but I'll look into it and see if it helps.

---

### Post by ajackson on 2009-04-28
> **horgabob said:**
> Actually, I did a lot of searching and reading of stickies before posting
Ah so the sticky called [Before asking for help with Wine << READ BEFORE POSTING ** I'M SERIOUS READ IT **]("http://ubuntuforums.org/showthread.php?t=885111") doesn't exist or contain the information:

> Things you should try before asking for help:

   1. Check AppDB - Wine's Application Database is one of the best sources for help with running apps in Wine. First and foremost, it will tell you when an application is not worth trying at all. Secondly, but almost as important, an application's AppDB entry may include how-to information on the proper way to install and run your application.
   2. Search for an existing how-to - Many popular applications have excellent how-tos already written for them that aren't necessarily part of AppDB. Google is your friend. Be wary that many of the published howtos might be very out of date - check AppDB first.
   5. Search the forums - There are many, many, many, many, many, many posts on running specific applications in Wine already. Chances are really good that someone has already asked the same question you have.

Things to include when asking for help:

   1. Wine version - Wine is updated roughly every two weeks. Each update includes numerous changes and fixes. Knowing which version you are using can often lead to very specific fixes for whatever problem you may be having
   2. Terminal output - Run your application from the terminal and include the output in your post (make sure you use the forum CODE tags). The informational and error messages provided in the terminal can be very helpful in pinpointing where the problem is occurring
   3. Wine configuration - How you have Wine configured changes how Wine behaves greatly and may be the cause of whatever issue you may be having. Configuration items to consider including are :
          * OS version
          * Library overrides
          * Sound settings, all options
          * Graphics settings, all options
          * Registry edits
   4. Hardware specs/drivers - This is especially important if the application you are having issues with is a 3D game.
   5. Other Wine applications - Include any other apps you may have installed in your Wine directory. Be sure to mention if you've used third party tools like winetricks, PlayOnLinux, or wine-doors.


> **horgabob said:**
> As far as the AppDB, I'm kinda new to Wine, so I'm still unsure what it means, but I'll look into it and see if it helps.
Umm the stickies, which you claim to have read, tells you what it's purpose is.

> **horgabob said:**
> I don't really think the sarcastic response was necessary.
You are correct, ignoring would have been a better option.

---

### Post by hikaricore on 2009-04-28
pwned!

---

