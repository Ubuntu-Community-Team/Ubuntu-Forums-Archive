---
title: "Question about a concept and whether any virtualization does that - Xen??"
date: 2011-06-27
forum: Virtualisation
---

### Post by ClientAlive on 2011-06-27
Hi,

I have a question about a concept that occurred to me. I'm inclined to think that some type of virtualization does this - that it's just the way it works already, but I'd like someone with more knowledge/ exper to tell me if I'm on the right track. I'm trying to learn about virtualizaion - especially Xen and am reading books and watching vids but not sure about this one.

The best way I know how to explain my question is to use logic to describe, and try to integrate some explanation as I go. I'm going to try and keep it simple but I think I have to add some differences in order to really show what I"m wondering about.

Lets say you have operating systems A, B, and C. Each of these operating systems has the components a, b, and c that make them up but only a is identical between A, B, and C (all the o/ses). In addition, b is identical between A and C but not B :and: c is identical between A and B but not C. So then let's say Ab and Cb=b1 but Bb=b2 :and: Ac and Bc=c1 but Cc=c2.

Rather than store A=abc, B=abc, and C=abc on the server's drive why not just store only the least required components and combine them in the correct order for the o/s that's being requested when it is requested?? Following the example above that would be the components a, b1, b2, c1 and c2 being stored on the server's drive (much less this way).

Now, when someone requests o/s A the VMM combines the components a, b1, c1. When someone requests o/s B they are combined and served up as a, b2, c1. And when requesting o/s C they are combined and served up as a, b1, c2.

Does this make sense? I hope I haven't made any typo or otherwise an error in my logic statement above. Just trying to figure out how things could be combined, duplication eliminated, and resources economized. Sorry I don't have a simpler way to describe this without it taking 5 million words and probably becoming so convoluted that it's worthless in the end anyway. At least with this method it is succinct and precise.

[B]So, my real question is - does any VMM already work this way? More specifically, does Xen work this way, or can it? I've seen the word "granulation" used in some of the materials talking about virtualization. Could that be what they are talking about when they use that word?
[/B]

Any guidance would really be appreciated. I'm finding it difficult to get some of the concepts they talk about straight in my head.

---

### Post by ClientAlive on 2011-07-08
Ok. Maybe I chose a bad way/ overly complicated way to ask my question. I can't really see a more succinct and clear way to state the question though. Unfortunately, since it it's a question about the existence of a particular technology or not, I don't know the correct term/ terms to use. All I can possibly do is take a stab at describing what's on my mind. If anyone knows anything about this I'd sure appreciate a little help.


Thanks
Jake

---

### Post by haqking on 2011-07-08
Could you write it in Russian so i could understand it better ? LOL

When you say component what do you mean ? a virtualised hardware component ?

and what server do you refer to ?

---

### Post by ClientAlive on 2011-07-08
> **haqking said:**
> Could you write it in Russian so i could understand it better ? LOL

When you say component what do you mean ? a virtualised hardware component ?

and what server do you refer to ?



Hi,

I guess I'm thinking of the guests one might have in a virtualization software. I know there are many choices available with virtualization software so I guess my question is kind of two part (1) is there some particular virutualization software that's already designed that way or that has a some feature for that, and (2) examining the possiblity of modifying some existing virtualization software (if one doesn't exist already) so that you do end up with that.

So what is "that?"

What I'm talking about is a situation where a person has many VMs in some virutalation software. If that guy is, for one example, running all debian based Linux distros for his VMs - then they will have a lot of commonalities between them. One example might be the kernel itself. With, say, 10 different Linux distros - it's possible that every one of them is running the same kernel, same release of it, same configuration, everything. Why have 10 kernels taking up space on your hard drive when you could just have one. Have every different distro use the same kernel just combine all the rest of what makes it uniqe together with what they all have in common. Serve it up on the fly right when you need it.

Now that was just for a simple example to try and explain what I'm getting at. Now if you think about it though, you can see very quickly how there's (1) a more general concept at stake here and it (2) applies to much much more than just a kernal (or whatever other single item we might choose just for an example).

If you follow the idea out to it's logical end they you would have to say it means to identify every single commonality and group them in some meaningful way. To differentiate between the commonalities and the unique items. To record and categorize the commonalities vs the unique parts.

In a total group of just 10 VMs, for instance, this could get very complicated. Taking into consideration all the things that make up an o/s, it won't always be the case that all 10 share some of the various 'components'in equal measure. For example, it might be that case that 10 use the same component A but their other components are unique to only it and 4 share component B but some of their other components are unique only to them, 2 share this other thing, but only on has that, and so on and so on and so on . . . The end result is very possibly worth it though. You store a single instance of every single (software/ code package/ whatever) thing that is needed to make up any given VM. When that particular VM is called on to lauch/ run, the system pulls together all the neccessary parts and peices that make that, particular VM what it uniquely is - all carried out behind the scenes.

Now you have the best of both worlds. Rather than storing 10 times the amount of data on your disk than you actually need to (referring to the kernel example again, but again it's much bigger than that). you just store the min amount required and what you get is the same as if you bloated out your drive by doing things in the traditional way (untold duplicates of packeges and code and  . . . . uggg!).

Now take that thought and apply it to 50 VMs. to 100, to however many you want or need. Apply it to a huge server farm somewhere running a billion dollars worth of equipment. Apply it, not only to a particular brand of o/s but to all kinds (Microsoft, Macintosh, and all the little unheard of ones too). Apply it to, not just a certain strain of Linux distro but to all of them (to RPM based ones and to unique systems like Gentoo and *BSD, etc, etc). Now you get the idea . . .

Hope that makes a little more sense. I can see it in my head, it's just really hard to try and explain. I'm not talking about compiling the thing anew every time ether though or even reinstalling over and over. The closest term I know to use might be "multiplexing." You would be multiplexing all the peices that make that one VM what it is/ what it should be and serving it up for use right there on the fly. The system might be using some sort of database or something to catalogue all the parts and manage them. Perhaps there are services running as daemons that tap that database whenever you click the button to launch a certain VM and it uses that info to find an bring together all the right parts and sever the end result up to you. I don't know. Seems like it would be awfully cool though.

Honestly . . .  A person could realize so much space savings that way that it would be possible to take a disk that would normally only allow you to have 10 VMs (space limitation) and now be able to have 100 VMs in the same space. To take a disk that is perhaps larger but that you only want to use a portion of it for that use and put 10 VMs in the space it would take for 1 VM.

Shoot! Maybe the concept of "compression" would be useful here. Just not compression in the traditional sense. Not on a level of bits and bytes but on a level of software packages.

---

### Post by ClientAlive on 2011-07-08
> **haqking said:**
> Could you write it in Russian so i could understand it better ? LOL

When you say component what do you mean ? a virtualised hardware component ?

and what server do you refer to ?


I'm sorry. I don't think I really addressed that question properly. It's just that I don't know what else to call it. I guess I'm referring to several different things, such as: libraries, apps, daemons, configuration utilites . . .  anything you can think of that makes up a Linux operating system (or any brand o/s for that matter). But not the thing as a whole, as the user sees it after it's installed, and also not at the code level or the binary level or bit or byte level - but as in breaking it down into its basic functional parts - "components." So I'm talking about all the individual things that go into making an complete operating system.

The "server" I refer to is really just saying the virtualization software. Whether that be Xen or Virutal Box or VMWare, whatever. What I'm getting at is, either it exists or a person (possibly such as myself) brings it into existence. Right?

---

