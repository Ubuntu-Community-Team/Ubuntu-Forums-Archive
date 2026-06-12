---
title: "Microsoft Released MechCommander 2 Source Code"
date: 2006-03-22
forum: The Cafe
---

### Post by Carmack78 on 2006-03-22
Although, it is not directly related to Ubuntu and/or Dapper Drake, I want to
 let you know that Microsoft has relased MechCommander 2 Source Code, which is available at [here]("http://www.microsoft.com/downloads/details.aspx?FamilyID=6d790cde-c3e5-46be-b3a5-729581269a9c&DisplayLang=en").

As far as I know it is a FIRST from Microsoft, releasing a complete source.

The download is over 1GB and 4GB is needed to install it.

Mech Commander is actually an old game, but you need the latest tools 
(Visual Studio 2005, XNA (what the hell is XNA, anyway? :-k )) in order to build the game.

I haven't check the license, but time will show if we are going to see a native
 OpenGL build running on Linux. :confused:

---

### Post by stubby on 2006-03-22
funny, i just installed the game on windows.

it's ok, nothing revolutionary

---

### Post by earobinson on 2006-03-22
thats pretty cool that they released some source code.

Also this should have been in the programing or the community chat sections, no problem It will get moved.

---

### Post by hentaidan on 2006-03-22
Cool! I love mech games :)

[QUOTE=Carmack78]As far as I know it is a FIRST from Microsoft, releasing a complete source.[/QUOTE]

What about Allegiance?
[URL="http://research.microsoft.com/allegiance/"]
http://research.microsoft.com/allegiance/[/URL]

---

### Post by mostwanted on 2006-03-22
[QUOTE=Carmack78]
I haven't check the license, but time will show if we are going to see a native
 OpenGL build running on Linux. :confused:[/QUOTE]

From the site you linked to: *"This is the Shared Source release for MechCommander 2."*

[http://en.wikipedia.org/wiki/Shared_Source](http://en.wikipedia.org/wiki/Shared_Source)

---

### Post by Carmack78 on 2006-03-22
Geez, you're right. Altough I have the client setup for my Allegiance on my disk, I have completely forgotten about it.

[http://en.wikipedia.org/wiki/Allegiance_(computer_game](http://en.wikipedia.org/wiki/Allegiance_(computer_game)) gives every detail about the game and [http://www.freeallegiance.org/](http://www.freeallegiance.org/) is the official site.

[http://en.wikipedia.org/wiki/Shared_Source](http://en.wikipedia.org/wiki/Shared_Source) license description (thanks mostwanted) gives the nuts&bolts.

Anyway, reverse engineering (!) for educational purposes without being commercial is always possible. :)

---

### Post by Heretic09 on 2006-03-22
Under what license was it released?

---

### Post by ComplexNumber on 2006-03-22
[quote=Heretic09]Under what license was it released?[/quote] microsofts shared source licence. [click]("http://en.wikipedia.org/wiki/Shared_source")

---

### Post by imagine on 2006-03-22
Micros~1 already released complete source codes to the public a couple of times, so it isn't the first time. However you need to be aware that the Shared Source Licence is no free/copyleft licence : )

---

### Post by Kvark on 2006-03-22
Wow, thats great news. Looks like Microsoft is experimenting with being less evil. Perhaps they will eventually make a habit out of doing this with legacy products like ID does. :-D

The game is better then the average RTS, or at least was when it was new. I would play it again and maybe even try to figure out how it's built up if I still had Windows installed.

It will probably not be ported to Linux anytime soon since it uses DirectX and other Windows only stuff. :(

I wonder which shared source licence it's released under, wikipedia says there are several. [One shared source licence]("http://http://msdn.microsoft.com/msdn-files/027/001/901/ShSourceCLIbetaLicense.htm") I found allows modification and is viral just like the GPL. But is different from GPL in that it is anti commercial(so it's not real open source) and anti software patents, on the other hand it doesn't force you to include the source code. Funny to see something like that from Microsoft that gets a couple thousand patents per year.

---

### Post by ComplexNumber on 2006-03-22
> Looks like Microsoft is experimenting with being less evil. no it isn't. its just learning how to *disguise* its evilness better by being a wolf in sheeps clothing.

---

### Post by joflow on 2006-03-22
XNA is MS's new framework.  I'm not too sure about the technical side but it has shared libraries that will make developing games for Xbox 360 and PC easier.

To me it seems like a extension of their original strategy with the first xbox which was to port/move as many PC games/franchises to their console as possible.  This should make it even easier for PC developers to port their games to,jointly develop for, or completely switch to Xbox.

---

### Post by Carmack78 on 2006-03-22
Here are the exact terms of MechCommander 2 Shared Source release. The EULA is included as part of the product installation.

```
Shared Source Limited Permissive License for use of MechCommander® 2

This license governs use of the accompanying software. If you use the 
software, you accept this license. If you do not accept the license, do not 
use the software.

1. Definitions
The terms “reproduce,” “reproduction” and “distribution” have the same 
meaning here as under U.S. copyright law.
“You” means the licensee of the software.
“Licensed patents” means any Microsoft patent claims which read directly on 
the software as distributed by Microsoft under this license.  

2. Grant of Rights
(A) Copyright Grant- Subject to the terms of this license, including the 
license conditions and limitations in section 3, Microsoft grants you a non-
exclusive, worldwide, royalty-free copyright license to reproduce the 
software, prepare derivative works of the software and distribute the 
software or any derivative works that you create.

(B) Patent Grant- Subject to the terms of this license, including the license 
conditions and limitations in section 3, Microsoft grants you a non-exclusive, 
worldwide, royalty-free patent license under licensed patents to make, have 
made, use, practice, sell, and offer for sale, and/or otherwise dispose of the 
software or derivative works of the software.

3. Conditions and Limitations
(A) Limitation on Commercial Distribution- Notwithstanding the rights granted 
in section 2(A) above, you are not granted any rights to commercially 
distribute any artwork from the software (“Art Assets”) in any derivative 
work or otherwise.  Microsoft grants you a limited, non-exclusive, worldwide, 
royalty-free copyright license to use, reproduce and distribute the Art Assets 
on a non-commercial basis only.

(B) No Trademark License- This license does not grant you any rights to use 
Microsoft’s name, logo, or trademarks.

(C) If you begin patent litigation against Microsoft over patents that you 
think may apply to the software (including a cross-claim or counterclaim in a 
lawsuit), your license to the software ends automatically.

(D) If you distribute copies of the software or derivative works, you must 
retain all copyright, patent, trademark, and attribution notices that are 
present in the software. 

(E) If you distribute the software or derivative works in source code form you 
may do so only under this license (i.e., you must include a complete copy of 
this license with your distribution), and if you distribute the software or 
derivative works in compiled or object code form you may only do so under a 
license that complies with this license.

(F) The software is licensed “as-is.” You bear the risk of using it. Microsoft 
gives no express warranties, guarantees or conditions. You may have 
additional consumer rights under your local laws which this license cannot 
change. To the extent permitted under your local laws, Microsoft excludes 
the implied warranties of merchantability, fitness for a particular purpose and 
non-infringement.
```

I'm not a lawyer, but it is seems like staying non-commercial, you can do 
whatever you like with this code. And if you are going to be commercial, you 
CANNOT distribute artwork and if not I'm mistaken you can even sale 
original/modified code holding the patents/trademarks etc.. instact.

---

