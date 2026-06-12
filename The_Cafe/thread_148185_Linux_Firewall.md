---
title: "Linux Firewall"
date: 2006-03-21
forum: The Cafe
---

### Post by 4dz0 on 2006-03-21
This thread has been reposted from programming talk to gain feedback from a wider range of users:

I am currently planning my final year project at university and I'd like some opinions on my initial idea. I do have to stress that this idea is extremely primitive and I have barely begun, what I'd really like is to have some comments from you guys that I can use to decide whether to proceed.

I'm looking to create an interactive firewall, the exact nature of the firewall is yet to be determined but my main aim is to create a user friendly application that can help new users to Linux configure network access with maximum ease. By interactive I mean a firewall that is restrictive by default, allowing only those applications and services network access through interactively granting permissions.

What I'd really like at this initial stage is some opinions, on whether Linux actually needs another firewall, and some features that you'd like to see. I'd also like some advice on what is currently available, what firewall you use, and the things you like/dislike about it.

I'd really like people to be honest in there opinion, I'm not tied down to this application and I have pleanty of time, if the idea isn't required amongst Linux users then there is little point in proceeding.

I've asked a lot of questions here so comments on any would be great.

Thanks.

---

### Post by htinn on 2006-03-21
At this point I'm just looking for some nice Ethereal filters. With that, I'm pretty much set for security.

---

### Post by jamesford on 2006-03-21
if u have the opportunity, study agnitum outpost firewall for windows. its such a wonderful application. something like that for linux is something ive been missing

---

### Post by 4dz0 on 2006-03-21
thanks, I'll take a look. Any more comments appreciated.

---

### Post by schnappy on 2006-03-21
Though I tend to be a little sceptical concerning these kind of firewalls (I think they easily tend to give users a false sense of security), I think it's safe to say that there are certainly a lot of people looking for this kind of functionality on linux. Just take a look around these forums, this comes up again and again.

I think this alone would make this a very worthwhile endeavor, so I'm really looking forward to your software and can only encourage you.

---

### Post by 4dz0 on 2006-03-22
bump

---

### Post by stoeptegel on 2006-03-22
Another ex outpost pro lover here. I think the way outpost pro interacts with the user is the best way i've seen on all firewalls. (and i've used a lot)

You can judge about GUI firewalls giving a wrong feeling about the level of security, but one way or another i think you have to make it easy/usefull for novice people to configure it. 
But i do feel that all win32 firewalls are way to much "with our firewall you are not in danger, granted". But that is probably because they are commercialized.

---

### Post by public_void on 2006-03-22
I don't trust most firewalls, especially on Windows, thats why I'm going to set up a box with IPCop on.

But for novice users it has to do the job, require little user interaction and simple to step up. If settings need changing then it should be simple to find and change.

---

### Post by woedend on 2006-03-22
firestarter is good, but i guess it depends on how much time and talent you have.  Firestarter lacks a lot of features.  One nice lacking feature(for the future more than now I suppose) is the ability to allow certain programs access and others block.  Also the ability to block certain IP addresses either in or out(specify both).  This is useful for tinkering, blocking sites, blocking users, etc.  I take it though you will be using iptables base right?

---

### Post by 4dz0 on 2006-03-22
> I take it though you will be using iptables base right?

This is something I'm going to need to discuss with my professor, i realise that to attempt to create something anywhere near comparable with iptables would be foolish, that would be reinventing the wheel. However, I need to ensure I undertake a project that is challenging enough to gain me a first class degree.

---

### Post by woedend on 2006-03-22
ah, but you see, there is no full featured gtk based iptables frontend that I know of.  Firestarter is easy but primitive.  Iptables is extremely easy to use, definetely all of your work would be in interfacing only.  I personally would LOVE a full featured gtk frontend, typing is laborious :p.

---

### Post by gabruo on 2006-03-22
I tries firestarter, Kmyfirewall, and a GTK based gui having been used to windows easy firewalls.  After much tinkering I was unhappy with all of them and finally settled on Firehol which is terminal based but fairly easy to use as well as fairly secure.  I also tried many win firewall and I believe my favorite was symantec personal firewall, because it was less about being pretty and easy to use and didn't treat me like a complete idiot.

---

### Post by 4dz0 on 2006-03-23
thanks for your comments, much appreciated.

---

### Post by frodon on 2006-03-23
[QUOTE=4dz0]This is something I'm going to need to discuss with my professor, i realise that to attempt to create something anywhere near comparable with iptables would be foolish, that would be reinventing the wheel. However, I need to ensure I undertake a project that is challenging enough to gain me a first class degree.[/QUOTE]iptables is not a firewall, it's just a language to configure the firewall embedded in the kernel which is Netfilter.
[http://www.netfilter.org/](http://www.netfilter.org/)
So your purpose is more to create a frontend for iptables in order to configure interactively Netfilter, i think. Netfilter is one of strongest firewall ever seen and it's embedded to the kernel (really more reliable than windows firewalls because it acts at the start of the chain), you can filter by packet and also forward connections or configuring it as a proxy, i'm really impressed by what netfilter is able to do.
So since i learnt how use iptables i don't use nothing else than own iptables rules for my firewall and it's not really hard to use.

4dz0, you should have a look to the mandriva's firewall because it works the interactive way and is really near to your goal i think, therefore you will gain some times trying to learn more about how the mandiriva's interactive firewall works.

Good luck guy ;)

---

### Post by 4dz0 on 2006-03-23
[QUOTE=frodon]So your purpose is more to create a frontend for iptables in order to configure interactively Netfilter[/QUOTE]

Do you think this is the best way to tackle the problem, or would interfacing directly with netfilter, bipassing iptables, be a more powerful and flexible approach?

---

### Post by frodon on 2006-03-23
> Do you think this is the best way to tackle the problemIt's an easier way, interfacing directly with netfilter is good idea but i would ask myself if it's interesting to spend time to do something that iptables already do really well, execpt if you are mainly in a learning spirit.
However there are a lot of interesting things to do with interactivity. For example a friend asked me today if it's possible to define a firewall which open the port when you open the apps and close it when you close the apps, this idea require something to handle in real time iptable rules and could be a plus for a firewall frontend.
So there a lot of things to do to create a good front end for iptables and for the moment there's no perfect iptables frontend (my opinion).

So i would spend more time to find good idea's to make a reliable front end, of course easy to use, and add some new features like the one my friend asked for than spending times in re-creating iptables like feature (which is not needed i think). It mainly depends on what is your purpose.

---

