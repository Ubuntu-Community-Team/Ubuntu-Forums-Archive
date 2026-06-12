---
title: "An article about Windows Vista."
date: 2006-03-14
forum: The Cafe
---

### Post by YourSurrogateGod on 2006-03-14
I found this article online and I've decided to share it with you. There are many good points in it that are worth to sit and ponder. If the goodies that are described in this work are delivered succesfully by Microsoft, then it will be a big bonus and not just Windows users.

The below is my favorite part.
> -snip-

Well, that's sort of what Microsoft is doing with Vista. Rewriting the kernel completely would break too many applications, so that's not really an option. While the kernel in Vista is still primarily the same one as in Windows 2000 and XP, there have been some significant changes to tighten up security. _Fewer parts of the OS as a whole run in Kernel mode - most drivers run in User mode, for instance._ Things that run in Kernel mode are prevented from installing without verified security certificates, and even then they require administrator-level user permission. In Vista, it should be much more difficult for unauthorized programs (like Viruses and Trojans) to affect the core of the OS and secretly harm your system. In theory, you practically have to invite one in. Of course, the security of the kernel is unproven and will remain so until the OS ships and is out "in the wild," but it's encouraging that Microsoft has done everything they can to enhance stability and security while maintaining backward compatibility, which is no easy task. 

-snip-

[http://www.extremetech.com/article2/0,1697,1931914,00.asp](http://www.extremetech.com/article2/0,1697,1931914,00.asp)

I think separating the kernel from the drivers is a great idea. If a bad driver implodes, your entire system won't go down with it.

---

### Post by Bandit on 2006-03-14
[QUOTE=YourSurrogateGod]I think separating the kernel from the drivers is a great idea. If a bad driver implodes, your entire system won't go down with it.[/QUOTE]
I agree there.

But, about the virus threat. It isnt the kernel that has to be attacked. A System32 DLL can be deleted and if the right one can bring the system down :)

---

### Post by YourSurrogateGod on 2006-03-14
[QUOTE=Bandit]But, about the virus threat. It isnt the kernel that has to be attacked. A System32 DLL can be deleted and if the right one can bring the system down :)[/QUOTE]
Well, aparently they'll tighten things up there as well. Plus, since only portions of the OS will run in kernel mode, it will be more difficult to get access the necessary priviliges in order to do some real mayhem. That and IE will **finally** run in non-priviliged mode, making it difficult, at best, for a virus to install itself once it downloaded itself on a computer.

---

### Post by Kernel Sanders on 2006-03-14
Vista has enhanced *native* security, but as far as I can see, that wasnt really the problem?

I always found that the problem was stopping the crap coming in to start with. A good firewall, antivirus, antispyware has solved that problem, so any improvement in Vista securty is a matter of perspective IMHO......

---

### Post by YourSurrogateGod on 2006-03-14
[QUOTE=*John*]Vista has enhanced *native* security, but as far as I can see, that wasnt really the problem?

I always found that the problem was stopping the crap coming in to start with. A good firewall, antivirus, antispyware has solved that problem, so any improvement in Vista securty is a matter of perspective IMHO......[/QUOTE]
Not really. Read the article in its entirety.

---

### Post by Kernel Sanders on 2006-03-14
[QUOTE=YourSurrogateGod]Not really. Read the article in its entirety.[/QUOTE]

I was always of the opinion that the main problem with security of Windows XP was stopping threats getting in, not what they did once they were there.

With firefox, a good firewall, a good antivirus, and a good antispyware have solved that problem. My computer is like fort knox, and running all the online security tests ranked my computer as **SUPERB**

Vista has done a lot of work on stopping threats getting in, but it has championed its security in restricting what files can do once they get there.

There are 2 problems with this as far as I can see. 

With what I mentioned above, (needing a good firewall etc..) threats cant get in, so restricting what they can do when they get in is kind of a moot point. 

Also, with almost every application, there is a security/functionality trade off. At the moment, due to their much championed work with restricting what threats can do once they get inside your system, Microsoft have tipped this balance too heavily on the security side. Have you tried the latest beta? I have, and I wasnt the only one complaining about Vista bullying you with constant security warnings. I actually said that if microsoft dont find a way to tone that down a bit, or allow you to raise your privilages, the I may quite possibly end up LESS functional in Vista than I was in XP.

My 2 cents...... :D

---

### Post by YourSurrogateGod on 2006-03-14
[QUOTE=*John*]With what I mentioned above, (needing a good firewall etc..) threats cant get in, so restricting what they can do when they get in is kind of a moot point.[/quote]
Not really. Security isn't just your moat and wall, it's also making sure that once you breach those outer defenses, you'll be faced with hardened bunkers, not easy to destroy farm houses.
[quote=*John*]Also, with almost every application, there is a security/functionality trade off. At the moment, due to their much championed work with restricting what threats can do once they get inside your system, Microsoft have tipped this balance too heavily on the security side. Have you tried the latest beta? I have, and I wasnt the only one complaining about Vista bullying you with constant security warnings. I actually said that if microsoft dont find a way to tone that down a bit, or allow you to raise your privilages, the I may quite possibly end up LESS functional in Vista than I was in XP.[/QUOTE]
At the moment, this doesn't seem too bad. They have still months of programming to do, so this doesn't seem like too serious. That and it wouldn't surprise me if they tried to have a function that decides how much security/restrictions you need/want. From the looks of it, this doesn't seem like a terribly serious problem, if left unaddressed, it could be, but I would be very surprised if Microsoft let it slide.

---

### Post by Bandit on 2006-03-14
[QUOTE=YourSurrogateGod]Not really. Security isn't just your moat and wall, it's also making sure that once you breach those outer defenses, you'll be faced with hardened bunkers, not easy to destroy farm houses.[/QUOTE]
I liked that comment. Never thought of windows files as farm houses..

---

### Post by rfruth on 2006-03-14
Is the firewall thats ships with Vista the same half baked one that XP uses ?

---

### Post by YourSurrogateGod on 2006-03-14
[QUOTE=Bandit]I liked that comment. Never thought of windows files as farm houses..[/QUOTE]
Not files, but its systems. It's easy to cause a buffer overwrite in just about any OS once you get a piece of malicious code into it. I don't know of a single OS that's invulnerable to this attack. I believe that AMD has said once that it has a feature in its CPUs that prevent such an attack, but I'm skeptical.

Vista probably will undoubtedly have its holes too, but the question this time around that I'd like to have answered is how big are those holes?

The goal would be to make the vulnarabilities as small as possible. You want to make the hacker's job difficult, so difficult that it would cause him/her to think that it's not worth hacking your system.

---

### Post by YourSurrogateGod on 2006-03-14
[QUOTE=rfruth]Is the firewall thats ships with Vista the same half baked one that XP uses ?[/QUOTE]
Supposedly it's going to be much more robust. XP's firewall is indeed lacking... to say the least.

---

### Post by YourSurrogateGod on 2006-03-14
[QUOTE=Bandit]I liked that comment. Never thought of windows files as farm houses..[/QUOTE]
In some ways, I view Linux in a very much similar manner.

---

### Post by rfruth on 2006-03-14
You hit the nail on the head when you said

"The goal would be to make the vulnarabilities as small as possible. You want to make the hacker's job difficult, so difficult that it would cause him/her to think that it's not worth hacking your system" 

Thats a tall order considering Windows (all versions) have 90 + percent of the market and ease of use is assumed, Vista will be interesting to say the least.

---

