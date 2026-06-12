---
title: "So, what makes Ubuntu Ubuntu?"
date: 2006-03-22
forum: Testimonials &amp; Experiences
---

### Post by harisund on 2006-03-22
Distrowatch lists tons and tons of Linux variations. Ubuntu proudly stands on the top. 

So my question, what makes Ubuntu recognize more hardware than, say Fedora Core or any other distro that comes on multiple CDs? I mean, come on, Ubuntu is merely a single CD, while there are heavy distros with 4-5 CDs / a DVD. Wouldn't it be right to assume they have better hardware support? 

Or does size of a distro not necessarily imply hardware support? 

If not hardware support, what makes people flock to ubuntu? Please don't give an answer like ease of software installation. If anybody is knowledgable to type apt-get install <something> on the command line they can just as well use yum, emerge or whatever. So also with Synaptic. 

In other words, I am just keen on knowing what exactly the ubuntu developers changed in Debian to suddenly rise Ubuntu up the charts? 

Anyhow, all hail Ubuntu !!

---

### Post by mvaniersel on 2006-03-22
I'm always told that Knoppix has the best hardware support.

For me the process of choosing a distro went like this:

- does it work on my box without too many tweaks - check
- does it have a friendly and active community - check

That's it. I think the community is a big part of the reasons why Ubuntu is so popular.

---

### Post by harisund on 2006-03-22
Hmmm...community .. Somehow, I always thought each distro would have a dedicated community. Still, it is the Ubuntu forums that has attracted me the most (you can observe I have more than 240 posts,) more than any other forums. Perhaps that does indeed play a big role (though I have never looked into mailing lists and IRC)

Also, regarding hardware detection, hmm.. Knoppix is supposed to detect more hardware. That's true, but then again, Knoppix is not meant to be installed on to your hard disk, right? So let's say you boot with Knoppix and you realize your <insert piece of hardware here> works so you go with the assumption that Linux recognizes it, and install another distro, only to realize the hardware is not supported directly, and you have to install drivers for it. 

Also, why can't Ubuntu Live CD have an inbuilt installer, like Mepis does? As in you put the live CD, if you like it, you can install it right there without having to quit. Is this feasible? Do you think this could increase the adoption rate of Ubuntu?

---

### Post by Zeroangel on 2006-03-22
Yes. A problem with small communities is that there tends to be few posts, but a high ratio of interesting ones to 'drivel' ones, as well as a greater sense of intimacy and knowing others in the community. Mid-sized communities tend to have entrenched power structures, elitism and a moderately high rate of drivel posts. And large communities tend to be too dumbed down and anonymous, it is easy to get lost in a crowd.

The ubuntu community has almost none of these problems, I am happy to say! Save for the getting lost thing, however it is easy to ignore topics one is uninterested in since they are usually named straightforwardly. People are friendly for a large community, and almost all of the topics on here are useful in some way.
[quote="harisund"]Also, why can't Ubuntu Live CD have an inbuilt installer, like Mepis does? As in you put the live CD, if you like it, you can install it right there without having to quit. Is this feasible? Do you think this could increase the adoption rate of Ubuntu?[/quote] Actually, the Dapper Drake version of Ubuntu will have the ability to install the distro straight out of the Live CD. As I recall, it was mentioned as something that should be done for Breezy, but it couldn't because the installation files alone took up too much space. I don't know what kinds of black magic the dev team is using to pull that one off. But it is good to see that concept being made a reality.

---

### Post by alamba on 2006-03-22
There's an interesting question that's been brought up here, would appreciate if someone could throw some light on the point below:

"What makes Ubuntu recognize more hardware than, say Fedora Core or any other distro that comes on multiple CDs? I mean, come on, Ubuntu is merely a single CD, while there are heavy distros with 4-5 CDs / a DVD. Wouldn't it be right to assume they have better hardware support? "

A

---

### Post by harisund on 2006-03-22
Hello zeroangel

Is Dapper really going to have that functionality? Wow ! Neat stuff that.. 

And alamba, on my question earlier.. maybe they all do have more or less similar hardware support and perhaps what makes Ubuntu popular is that it is a single CD, comes with Live and Install in one package (from ShipIt !) and people can test with Live, and immediately go with the install? 

Still, most of my question remains unanswered. If the content is merely a CD as opposed to a DVD, what are the sacrifices made? If the developers have put in more drivers so that the number of machines that work out of the box is high, shouldn't they have cut down on something?

---

### Post by kadymae on 2006-03-22
I think the posters who have mentioned the Ubuntu Community have really hit on a big part of what makes Ubuntu Ubuntu.

I mean, if I were making up official slogans to describe these forums they'd be things like:

"Ubuntu Community -- Jerks shot on sight."

"Ubuntu Community -- n00bs welcome. No, really."

"Ubuntu Community -- We ETFM."  (Explain The F'ing Manual.)

"Ubuntu Community -- We're as sweet as our favorite distro."

---

### Post by anaconda on 2006-03-27
> Or does size of a distro not necessarily imply hardware support? 

That is true. The size of a distro depends mostly about how much extra programs are included to the install CD:s. This is nuts. Who wants to install a linux that has tons of programs that the user doesn't even want? ](*,)   

Ubuntu is reasonbly sized 1CD. But even ubuntu comes with (big) programs that I would rather get using apt-get IF I need them. For example OpenOffice ~100MB is so big that it shouldn't be on the install CD, or there should be a different (stripped) install CD for faster download-times.

One example of a small distro with exellent hardware support and detection is "Damn Small Linux" which is just 50MB, which proves that size does not tell how well linux supports hardware.

---

### Post by engla on 2006-03-27
[QUOTE=alamba]There's an interesting question that's been brought up here, would appreciate if someone could throw some light on the point below:

"What makes Ubuntu recognize more hardware than, say Fedora Core or any other distro that comes on multiple CDs? I mean, come on, Ubuntu is merely a single CD, while there are heavy distros with 4-5 CDs / a DVD. Wouldn't it be right to assume they have better hardware support? "

A[/QUOTE]

Let me hazard a guess... the hardware detection probably depends on** I.** The amount of included driver modules in the default kernel and **II.** on the detection logic  of the installer and configuration scripts. That would mean that this is really not space critical (modules consume disk space, but not really that much.. a normal collection of them is around 30M uncompressed)..

The extra files on the Fedora CDs come from the **diversity of applications** they include, applications that many times over overlap in their niche; a simple example is that both KDE and GNOME are included for Fedora (Ubuntu has two separate CDs for that). Ubuntu's philosophy is to bundle one application for each task [OOo for office, gedit for text, evolution for mail etc]

---

### Post by harisund on 2006-03-27
Hmm.. I think that makes a lot more sense.. After all, though Linux is all about choice, when a new user is confronted with a ton of choices for doing something, he tends to get confused.  

nice philosophy of Ubuntu though !

---

