---
title: "Why so much Mono in latest updates?"
date: 2007-12-05
forum: The Cafe
---

### Post by lancest on 2007-12-05
Latest (OO?) updates have alot of Mono. Is Mono that important?

---

### Post by hanzomon4 on 2007-12-05
Wow just updated... A lot of mono, to my knowledge the only mono apps installed by default are tomboy and fspot. I must say however that mono apps rock hard. I love banshee, beagle, fspot, and tomboy.

---

### Post by DoctorMO on 2007-12-05
these new updates prompted me to remove the entire mono library; I've been meaning to do it for some time as I just don't see the point in having them installed at all. As a programmer I'd rather play it safe and not waste my time in a dangerous framework. Python, Java or C++ for me thanks.

---

### Post by pcjoe on 2007-12-05
I don't get the hostility towards mono - .NET is a great development platform as far as I'm concerned. Whenever I'm at home working on my personal projects in C++, I can't stop thinking to myself "Man.. This would have been so much easier if I could program it in C# like at work." I can do things in .NET that would take me well over double the time in C++. Yeaahhh, it's by Microsoft, but that's like saying you refuse to use a free calculator because it's made by a company you dislike. Instead, you'll do ALL of the arithmetic by hand.

Either way, It's not like everyone is forced to use it... The choice is there for developers that feel more comfortable with .NET. AFAIK, wasn't the entire Linux thing ABOUT choice? If a developer wants to use .NET, that's great; it'll probably get a lot of the .NET guys who traditionally only develop for windows to make linux apps too.

---

### Post by DoctorMO on 2007-12-05
> I don't get the hostility towards mono - .NET is a great development platform as far as I'm concerned.

It's credibility is not undermined for want of trying on technicalities (although the size of the damn thing is pretty bad anyway) it's actually dangerous because of patents. Go destroy the software patent trigger happy industry and you may get me to move from python for easy, although I can't see how to be honest, I can even write usb drivers in python.

The Cil and Mono stuff isn't Microsoft btw, although some may say the problem is not the implementation but the reliance on something that has question marks;

I have no idea why we shun liblame (mp3 support) because of a couple of software patents yet are quite happy to include mono in the default install. It's just a gnome/ubuntu double standard which hits my nerves too. It's aright when it's dev tools to ignore potential patent problems, but as soon as it's user space it should be avoided. bah!

---

### Post by macogw on 2007-12-05
> **pcjoe said:**
> "Man.. This would have been so much easier if I could program it in C# like at work." 
C#?  So, like Martin said, Java.

---

### Post by gnomeuser on 2007-12-05
> **DoctorMO said:**
> It's credibility is not undermined for want of trying on technicalities (although the size of the damn thing is pretty bad anyway) it's actually dangerous because of patents. Go destroy the software patent trigger happy industry and you may get me to move from python for easy, although I can't see how to be honest, I can even write usb drivers in python.

The Cil and Mono stuff isn't Microsoft btw, although some may say the problem is not the implementation but the reliance on something that has question marks;

I have no idea why we shun liblame (mp3 support) because of a couple of software patents yet are quite happy to include mono in the default install. It's just a gnome/ubuntu double standard which hits my nerves too. It's aright when it's dev tools to ignore potential patent problems, but as soon as it's user space it should be avoided. bah!

I will repeat what I've asked everytime someone makes this statement.

Give me just one patent that Mono infringes upon, the stated goal of the Mono project is that if such a situation should ever arise they will combat, invalidate or workaround the patent. Yet nobody who makes this claim has EVER been able to show one patent Mono infringes upon.. till that happens such claims are nothing but FUD.

---

### Post by Bannor on 2007-12-05
For those of us that are in sales 

could someone explain what mono is?

---

### Post by tenjin1 on 2007-12-05
Yes I too have like 40 updates related to Mono. Since I'm just a ubuntu user and not a programmer, I assume I do not need to install all these updates?

---

### Post by p_quarles on 2007-12-05
> **Bannor said:**
> For those of us that are in sales 

could someone explain what mono is?
It's an open source implementation of the MS .NET programming framework. The idea behind the project is interoperability with Windows -- i.e., writing high-level language apps that will work on several platforms with minimal modifications.

As I understand it, there are a couple of libraries in mono that have patent *questions*, but there's nothing definitive. I understand the nervousness entirely, though: If I were a developer, I would certainly avoid using a framework that could potentially be shut down and break my work. I also know there's a wide range of opinions on how likely this is to happen.

---

### Post by andrewsomething on 2007-12-05
> **tenjin1 said:**
> Yes I too have like 40 updates related to Mono. Since I'm just a ubuntu user and not a programmer, I assume I do not need to install all these updates?

No, you should go ahead and update. If you have them installed already you must have programs that depend on the Mono libraries.

---

### Post by igknighted on 2007-12-05
How is mono vs .NET any different than Java and gcj?  Sure java is going open-source now, but we all accepted having gcj (an open-source implementation of a proprietary platform) installed before.  Just because Microsoft created .NET should it be held to a different standard?

Personally (and I don't actually program C#, I'm a java/python/C guy as well) I think that having more options is great.  Having a platform familiar to the many C# programmers can only help getting quality new apps for linux, and besides, it seems to be a pretty decent language to code in.

---

### Post by Hairy_Palms on 2007-12-05
mono winforms libraries, asp.net and the gdiplus implementation infringe microsoft patents, and unlike the C# language itself microsoft has not said it wont sue anyone who implements them and has not released them as standards. its so obvious its funny, its the old embrace and extend, get many programmers invested in C# and .net then pull the plug on the crossplatform part of winforms, asp serverside stuff and gdiplus and leave linux/mono looking like a poormans alternative to windows.

---

### Post by macogw on 2007-12-05
The trouble I see with Mono is that because it's trying to be .NET, it is subject to Microsoft's whim.  So, if they make a crappy design decision, the Mono guys can't be like "well that's dumb.  Let's do this instead."

---

### Post by DoctorMO on 2007-12-05
> till that happens such claims are nothing but FUD.

You're quite right, it is fear, it is uncertainly and I am quite doubtful; Although at least it isn't baseless. We know that Microsoft have certain parts of the .Net framework which are not standardised and yet mono is implementing them. We also know that Microsoft has a bad track record for being moral, fair or balanced; they have a history of setting rather complex and long game traps and killing competition will some quite ingenious plans. Just a shame it'll be all for naught.

---

