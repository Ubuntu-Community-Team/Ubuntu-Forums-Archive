---
title: "Understanding what Open-Source means"
date: 2007-12-10
forum: The Cafe
---

### Post by Wazeem on 2007-12-10
Hello im fairly new to linux and to open source software in general.

Now I have used open source and have a broad understanding of what open source software is. It is that you can view and edit the code and are allowed to distribute as long as no money or personal gain is involved.

That much I "kinda" understand. But being a beginner programmer myself I dont really understand how it works.

Now say I went and edited the code to an Open Source application how can I gain credit for my contribution (like say I wanted to show an employer) and what overall gain would I have? Now I know Open Source is not about personal gain but it makes it difficult to justify putting time and effort into it.

Maybe if some devs (not necessarily ubuntu) would explain why they work on open source stuff that would help me better.

How would open source be able to tell if someone is stealing the code? Like I wouldn't want to make an open source app and then have some guy come in and release something similar but is closed source. I dont see how Open Source deals with this and as there is nobody that owns the code who would press charges (would charges be involved? if not what happens?).

Likewise what if I wanted to program an app but wanted the control over it and created a closed source alternative (say I use the Open source code as a reference NOT COPY, is this aloud?). How can I assure that my app can not be charged or proved to be a copy (obviously keeping the code different is one thing but say I used the app as a reference).

Also Lastly whats the deal with UNIX? my friend says they are open source but I say many closed source unix variants that make you pay for it.

Sorry I know its many questions but I been thinking bout it lots.

---

### Post by Lostincyberspace on 2007-12-10
> **Wazeem said:**
> 
Now say I went and edited the code to an Open Source application how can I gain credit for my contribution (like say I wanted to show an employer) and what overall gain would I have? Now I know Open Source is not about personal gain but it makes it difficult to justify putting time and effort into it.
If you showed it to your boss it could show how well you work with others code, or how well you work in a group environment.
> **Wazeem said:**
> 
Maybe if some devs (not necessarily ubuntu) would explain why they work on open source stuff that would help me better.
Most do it because they believe in the project and want to help make it better.
> **Wazeem said:**
> 
How would open source be able to tell if someone is stealing the code? Like I wouldn't want to make an open source app and then have some guy come in and release something similar but is closed source. I dont see how Open Source deals with this and as there is nobody that owns the code who would press charges (would charges be involved? if not what happens?).
It still has a liscense and therefore can be sued for not providing the code but you cant sue for the use itself if it is under GPL.
> **Wazeem said:**
> 
Likewise what if I wanted to program an app but wanted the control over it and created a closed source alternative (say I use the Open source code as a reference NOT COPY, is this aloud?). How can I assure that my app can not be charged or proved to be a copy (obviously keeping the code different is one thing but say I used the app as a reference).
As long as you are not copying or very similar to the original code that is fine. Say you want to make a music player but cant get the nav bar to display right then you could go look at the code for another program to see how they tackled it.
> **Wazeem said:**
> 
Also Lastly whats the deal with UNIX? my friend says they are open source but I say many closed source unix variants that make you pay for it.

Unix is closed source itself.  Linux is an opens ource clone of it. and being open source doesn't mean it free. You can sell it but you have to provide the source code to be able to do so.

I hoped this has helped a little. It was a lot to answer all in one sitting

---

### Post by perce on 2007-12-10
> **Wazeem said:**
> 
Now I have used open source and have a broad understanding of what open source software is. It is that you can view and edit the code and are allowed to distribute as long as no money or personal gain is involved.


It is not correct: you can sell free software, and personal gain is often involved. The point is allowing others to use and modify what you wrote.

---

### Post by IYY on 2007-12-10
> **Wazeem said:**
> 
How would open source be able to tell if someone is stealing the code? Like I wouldn't want to make an open source app and then have some guy come in and release something similar but is closed source. I dont see how Open Source deals with this and as there is nobody that owns the code who would press charges (would charges be involved? if not what happens?).


This is where the GPL comes in. You see, there are two kinds of open-source licenses: viral (sharealike) and nonviral. The BSD license, for example, gives you no protection from your code being "stolen" and BSD developers don't consider it to even be stealing. In fact, Mac OS X is a modification of FreeBSD.

Viral licenses, like the GPL, ensure that your code is safe using copyright law. When you license your program under the GPL, you basically declare that anyone can modify and redistribute your code only as long as they release their modifications under the GPL as well. Anyone breaking this rule will be breaking copyright law, and can be sued using a very standard manner (it's the same as him literally stealing your code, or pirating your program).

> **Wazeem said:**
> 
Likewise what if I wanted to program an app but wanted the control over it and created a closed source alternative (say I use the Open source code as a reference NOT COPY, is this aloud?). How can I assure that my app can not be charged or proved to be a copy (obviously keeping the code different is one thing but say I used the app as a reference).


You are allowed to make an open source version and a closed source version of your own app, like you said. If you used the open-source code as a "reference", it's quite possible that you would be breaching copyright law, depending on how close your version is to the open source version. This, of course, greatly depends on what you call "reference". Generally speaking, this is not a good idea.

> **Wazeem said:**
> 
Also Lastly whats the deal with UNIX? my friend says they are open source but I say many closed source unix variants that make you pay for it.


The deal with UNIX is this: when it was first created at AT&T, it was illegal for AT&T to commercially participate the computer industry due to an earlier lawsuit. This meant that UNIX source-code was released basically without a license. During those early years, many versions of UNIX based on that code appeared -- some commercial (like Sun's Solaris) and some BSD-style open source (like FreeBSD).

---

### Post by Darkhack on 2007-12-10
> **Wazeem said:**
> ...you can view and edit the code and are allowed to distribute as long as no money or personal gain is involved.

Incorrect.  You can sell open source software all you want, for as much as you want.  It's just that when you give/sell the software to someone else, you have to respect their freedoms.  Read the Open Source Definition and Free Software Definition below.  They lists the freedoms that users should have.

[http://en.wikipedia.org/wiki/Open_Source_Definition](http://en.wikipedia.org/wiki/Open_Source_Definition)
[http://en.wikipedia.org/wiki/Free_software#Definition](http://en.wikipedia.org/wiki/Free_software#Definition)

> **Wazeem said:**
> Now say I went and edited the code to an Open Source application how can I gain credit for my contribution (like say I wanted to show an employer) and what overall gain would I have? Now I know Open Source is not about personal gain but it makes it difficult to justify putting time and effort into it.

Maybe if some devs (not necessarily ubuntu) would explain why they work on open source stuff that would help me better.

FOSS is about respecting the user's freedom.  People work on FOSS because they believe in the moral/social reasons or the practical advantages to an open development model.  Many do it as a hobby and some sell support or hardware.  Red Hat makes money by offering to support (provide patches and fix problems if your server goes down) even though their software is free,   Sun makes money by selling hardware.  They support FOSS because while everyone is shipping buggy Windows Server machines, they can ship quality machines with FOSS and people will buy them just for having those things pre-installed.  Some Adobe products like AIR are open source because it can help build a better quality product than if it was closed source (superior development model) and leads to sales by having developers use proprietary Adobe software to help create AIR applications.

> **Wazeem said:**
> How would open source be able to tell if someone is stealing the code? Like I wouldn't want to make an open source app and then have some guy come in and release something similar but is closed source. I dont see how Open Source deals with this and as there is nobody that owns the code who would press charges (would charges be involved? if not what happens?).

Somebody does own the code.  The copyright holder.  You are confusing a less restrictive license with the public domain.  Linus Torvalds could sue if somebody is violating the GPL for Linux.  The Free Software Foundation (FSF) is currently in the process of suing Verizon for a GPL violation.

> **Wazeem said:**
> Likewise what if I wanted to program an app but wanted the control over it and created a closed source alternative (say I use the Open source code as a reference NOT COPY, is this aloud?).

Depends.  You are walking on thin ice.  For somebody like Microsoft, just looking at a competitors product even once makes you considered "contaminated" and less likely to work on their bigger stuff for fear that you might use an idea you remember seeing once.  Most open source project aren't that strict.  Read up on the history of Linux and BSD and you'll see that both of these project used other people's code as a reference (AT&T UNIX was used by BSD and Minix by Linus Torvalds) and did so legally by having different enough code that it didn't infringe upon the originally creators work.

> **Wazeem said:**
> How can I assure that my app can not be charged or proved to be a copy (obviously keeping the code different is one thing but say I used the app as a reference).

Change the code layout and flow.  Changing variable names isn't enough and if a patch for one program, works in yours, it's too similar.

> **Wazeem said:**
> Also Lastly whats the deal with UNIX? my friend says they are open source but I say many closed source unix variants that make you pay for it.

UNIX is closed source.  Linux and BSD are "UNIX-like" which means they resemble UNIX while still having all original code and not infringing on any copyrights.  Also, companies like Red Hat or Novell sell services like maintaining and back-porting patches.  Thus the reference to "software as a service" in the FOSS world.

---

