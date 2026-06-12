---
title: "Parallels violating the Wine LGPL"
date: 2007-06-30
forum: The Cafe
---

### Post by Andrewie on 2007-06-30
> 
 According to this page on the Wine Wiki, Parallels may be violating the GPL by using Wine created code and not properly releasing changes, as per the license.

    Parallels Desktop for Mac([www.parallels.com](www.parallels.com)) contains Wine’s Direct3D code according to [http://www.parallels.com/en/licensing/](http://www.parallels.com/en/licensing/). So far(June 29th, 2007) attempts to ask them for the modified source code failed. This page is meant for keeping track of this, without starting legal action or a publicity campaign. 

If this is true, what effect might this have on the thousands upon thousands of users who’ve paid for Parallels, or for the future of the software itself? 


Just say this on Digg

Another user posted this:

[quote=nitehawk]
They modified it:

"In current implementation Parallels uses modified Wine code under LGPL license."
[http://forum.parallels.com/showthread.php?t=12648](http://forum.parallels.com/showthread.php?t=12648)
[/quote]

source: 
[http://babygotmac.com/a/is-parallels-violating-the-wine-gpl/](http://babygotmac.com/a/is-parallels-violating-the-wine-gpl/)
[http://www.digg.com/apple/Is_Parallels_violating_the_Wine_GPL](http://www.digg.com/apple/Is_Parallels_violating_the_Wine_GPL)

---

### Post by starcraft.man on 2007-07-01
Hehe, oh the ironies of using a Linux Implementation like WINE to satisfy the 3d needs of Mac users who want Windows working right. Oh what a twisted web we weave :p.

I doubt their violating the LGPL, its very lenient isn't it compared to the GPL? And here I thought Parallels had actually gone to all that work and effort to make 3d work, rather they picked up WINE and modified it. That just seems so damn cheap and easy, and they tout it like their major innovation. Bleh.

---

### Post by deanlinkous on 2007-07-01
Amazing isn't it......

---

### Post by DoctorMO on 2007-07-01
Foolish mortals, the fsf will come take their souls away *haha*

---

### Post by deanlinkous on 2007-07-01
what souls....

---

### Post by machoo02 on 2007-07-01
> **starcraft.man said:**
> I doubt their violating the LGPL, its very lenient isn't it compared to the GPL? 
Only if they made no changes to the Wine DLL files that they are using.  If they did modify them, and are not submitting their changes back to the Wine Project or releasing the source for those DLLs, then they are in violation of the LGPL.

---

### Post by BoyOfDestiny on 2007-07-01
> **deanlinkous said:**
> Amazing isn't it......

Indeed, seems they want a free lunch. I'm curious to see if what they've changed/added is useful (assuming they did change something, and are in violation.)

EDIT:
Maybe it's just a lack of communication?

[http://forum.parallels.com/showthread.php?t=12648](http://forum.parallels.com/showthread.php?t=12648)

From that post it seems they are willing to give the source... Although why the delay when the WINE team asked...

---

### Post by deanlinkous on 2007-07-01
Yep, take and not give.... he even stated they used modified WINE code and they werent providing source so they WERE in violation and if they still aren't providing source they still are in violation. 

It isn't enough to be willing to give if asked after a long delay and approval - so either way they suck....now they are just adding more suckage! :D

---

### Post by forrestcupp on 2007-07-01
They must have mistaken it for the BSD license, just like the operating system they took over.

---

### Post by deanlinkous on 2007-07-01
They must of obviously felt that numerous companies are ripping off GPL software so it makes it alright to do it.....glad to see v3 get some teeth to deal with these matters.

---

### Post by Enverex on 2007-07-01
I just spoke to Stefand (one of the few doing the majority of D3D work) and he says he's requested it multiple times from that page and still not heard anything (which is what the annoyance all came from).

Nice to see companies dragging their heels as long as they can make money from it.

---

### Post by starcraft.man on 2007-07-01
> **Enverex said:**
> I just spoke to Stefand (one of the few doing the majority of D3D work) and he says he's requested it multiple times from that page and still not heard anything (which is what the annoyance all came from).

Nice to see companies dragging their heels as long as they can make money from it.

It is typical. I just find it sad that, they advertise it like _they_ did something revolutionary. In the end, I guess all they did was combine the WINE implementation (other people's hard work) and the commands from the program, then link the VM to run directly off the hardware through the translation (Just a guess from my limited knowledge). It just seems like misrepresentation to me, they don't state much anywhere (I looked on their site, its tucked away) in the open that it was free software that allowed em to do it.

I hope more of the Mac people realize how they got their benefit, and I'll be sticking to Vbox and VMware (64 bit needs). I don't like Parallels style at all.

---

### Post by hanzomon4 on 2007-07-01
Are the wine dlls the reason why Parallels 3.0 can run games in virtual windows? Could the changes made to the wine code by parallels be used to give 3d acceleration to open Virtualbox?

---

### Post by starcraft.man on 2007-07-01
> **hanzomon4 said:**
> Are the wine dlls the reason why Parallels 3.0 can run games in virtual windows? Could the changes made to the wine code by parallels be used to give 3d acceleration to open Virtualbox?

Well, from my limited understanding (please correct if I'm wrong), the way it works is as follows. The Virtual Machine operates the OS.  You open program A requires rendering, Parallels intercepts the request for rendering and uses the WINE API/DLL/whatever else to translate (through whatever means) the request for direct rendering, to openGL commands (Mac's of course don't have DirectX, they can have OpneGL like Linux). The translated commands are then directly funnelled to the hardware (This part, IMO, is insecure. To do this, I am pretty sure Parallels had to compromise the security of the VM (isolation from the host) to create a situation in which commands from inside can go directly to your hardware, if coders get wary of this they can and might write viruses to target this avenue, overloading your card might not be too hard). Then, with the passage active and open program runs.

I believe its limited to DirectX 8, maybe 9 was too much to make perfectly stable and 10 (thats light years away I suppose, WINE is just trying 9).

Thats it. I suppose yes, if Parallels released all the modifications they made VBox and others could do this. The key is the modifications (I suppose) they made were to their product not under the LGPL, they only have to release WINE modifications, and I don't think they made that many. Any VM that wants to implement this will have to do all the hard work themselves, VMware made a Fusion product that does this also on the Mac.

Now, I will tell you why you won't see it.
Mac = 5-10 sets of hardware (i.e. mobos, graphics card) to code this for
Windows/Linux = 1000's of combinations.

I believe that it involves coding directly for the platform in use, thus you won't see it ever likely, unless they have a way of writing it for everyone.

---

### Post by Extreme Coder on 2007-07-01
I hope when (if? ) Parallels releases the code, it would improve 3d support in Wine and VirtualBox :)

---

### Post by starcraft.man on 2007-07-01
> **Extreme Coder said:**
> I hope when (if? ) Parallels releases the code, it would improve 3d support in Wine and VirtualBox :)

My scepticism dictates that this does not compute!

Really though, I know WINE will improve of course (its already pretty darn good for free) Vbox and VMs on PC hardware, that I will believe when I see if ever. Besides, like I noted above, I don't know how secure I'd feel about allowing the VM to directly interact with hardware on my machine (I like VMs for their isolation from host). Since it is Windows after all, nothings perfectly protected and I run XP in it. Even Vista has proven its not exploit free.

---

