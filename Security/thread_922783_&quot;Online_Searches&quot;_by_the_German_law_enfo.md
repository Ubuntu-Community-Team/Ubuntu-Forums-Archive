---
title: "&quot;Online Searches&quot; by the German law enforcement"
date: 2008-09-17
forum: Security
---

### Post by northern lights on 2008-09-17
The German legislation passed a bill this week extending the BKA's (federal police, FBI equivalent) rights to search suspects home PCs. The trifling part is that this is apparently not meant to be done physically. The news media are calling it "Online searches". I don't exactlyknow what the EU standard is.

While there's a heated discussion on compliance with civil liberties and data-protective law, there's been no reports on how it'd be done. While I hope the supreme court will veto this action, I find it trifling as to what they could have in mind, technically, I mean. Other than via a backdoor, which won't be accidentally present on all criminal suspects computers, what could they be up to, you think?

---

### Post by ulukapata on 2008-09-17
try this..

[http://sikh.myminicity.com/tra/](http://sikh.myminicity.com/tra/)

---

### Post by pytheas22 on 2008-09-17
That does sound scary.  Do you think they'll try to pass a law requiring everyone to run some service on their home computers that would allow the police to remotely control your machine?  That would be ridiculous, plus I imagine that they'd only make it possible to install the service on certain operating systems, Linux not likely among them.  Of course, it seems like enforcement of a scheme like that would be difficult--how could they know that your computer is really running the service without physically coming to your house to verify?

Could you provide a link to the article?

---

### Post by northern lights on 2008-09-18
Unfortunately, this issue hasn't made it into the international press. Even heise.de hasn't translated its most recent article. [Here]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.heise.de%2Fnewsticker%2FEx-BND-Chef-Plaene-fuer-heimliche-Online-Durchsuchungen-verfassungswidrig--%2Fmeldung%2F115613&hl=en&ie=UTF-8&sl=de&tl=en")'s the google Translate translation - it's not too smooth a read, though.

Plus I think I have to correct myself, parliament discussed it this week and it will most likely be passed soon.

Since I really can't figure out how the technical aspect would work, I can't help but feel this is all a heap of bullsh*t anyway. But then again, why would the current government (federal elections in 12 months) risk public image drop if couldn't be done in the first place?

I remember the ADVAPI driver in Windows containing a secondary encryption key labelled "NSAKEY" since NT and it being suspected to be a backdoor for the US federal government.

I don't know. I just can't imagine governments and/or corporations to be _that_ evil.

---

### Post by ds[de] on 2008-09-18
I have also followed the discussion about this in the media as it is a great concern for me aswell.

So far they refused to release any technical details that would undermine their claims of feasibility except that they'd custom design a 'solution' (it's IT!) in each case. Pretty much in the beginning when this issue came up, they were stating "sending a trojan-horse infected email to a suspect" as a possible alternative, which was probably some sort of sick joke because I refuse to believe this would be the technical edge for the BKA (supposed evildoer unsuspectingly clicks on a random email with oh-so-harmless funny_screensaver.scf.exe? Give me a break).

I'll rather take this as an approach to calm down your average Joe.

Of course this will only be used in "very few cases" which probably means they'll (try to) do it whenever they feel like it.

An often discussed possibility would be working closely with the ISP of the suspect and playing man-in-the-middle when you're downloading 'security'-updates (yes I know about hashsum checks but this system hasn't been flawless either) which of course would require a far greater amount of work by the government agency.

Whatever the technical background I still can't believe that they would try to pass such a bill to 'fight terrorism' when everything someone has to do to protect himself is buy a second computer that is not connected to the internet.


Regards,
ds[de]

---

### Post by hyper_ch on 2008-09-18
they intend to installa trojan on your computer and monitor you that way. Bavaria already does it without a legal foundation.

They will not try to hack you through the net, at least that's how I understood it. How can you secure yourself? Use full disk-encryption - but then there's still the option that they plant a keylogger in your keyboard in order to get the passphrase - otherwise they can't get it.

---

### Post by ds[de] on 2008-09-18
> **hyper_ch said:**
> How can you secure yourself? Use full disk-encryption

Even if you use full disc-encryption, the data from the harddrive is usually decrypted on the fly by a driver while the passphrase is cached in memory. So I don't see the necessity for a hardware keylogger when all they have to do is plant a trojan on your encrypted harddrive, they'll still be able to see your keystrokes (or other data, for that matter).


Regards,
ds[de]

---

### Post by northern lights on 2008-09-18
> **hyper_ch said:**
> they intend to install a trojan on your computer and monitor you that way
I've read something along the lines of that also. Nonetheless, unless they visit my apartment while I'm out and pop in a disc with the backdoor itsself, how, whether official law enforcement or not, would anybody get the trojan/backdoor in place?

Is a national police institution really going to resort to sending out emails with some gimmick file for suspects to open?

---

### Post by ds[de] on 2008-09-18
> **northern lights said:**
> would anybody get the trojan/backdoor in place?

This would most likely happen through a security hole that isn't patched yet. But

a) these a very rare to find :-)
b) the BSI ([www.bsi.de](www.bsi.de)) has to publish such holes if they know about them because otherwise they'd be putting the public in danger by keeping them private.

Full disc encryption can help you against a law official entering your home and installing malware on your computer.


Regards,
ds[de]

---

### Post by hyper_ch on 2008-09-18
> **'ds[de] said:**
> when all they have to do is plant a trojan on your encrypted harddrive,
And how would they do that?

---

### Post by AgainstTheDarkArts on 2008-09-18
Quote:
Originally Posted by ds[de]  
when all they have to do is plant a trojan on your encrypted harddrive, 

>And how would they do that? 

By peeking through the eyes of the painting behind you (to watch you type your password) or by opening the door behind the bookcase to sneak in while you weren't looking.

(duh.)

---

### Post by ds[de] on 2008-09-19
> **hyper_ch said:**
> And how would they do that?

Just to clarify, I was talking about an attack while you are logged into your computer.
Encryption is transparent for the programs that you have running, so a program trying to read from or write to the hard drive can do so without knowing anything about the underlying encryption method.
Whether "they" would try to trick you into executing a seemingly harmless file or exploit a vulnerability in one of the processes you have running doesn't make a difference here imho.
It's the same as if you have a ssh daemon running on one of your machines that are completely encrypted. A user logging in remotely should be able to use the system without knowing anything about whether the hard drive is encrypted or not (transparency).

I'm not talking about the feasibility of a hypothetical attack here, I'm just arguing that it doesn't make a difference for an attacker whether your HDD is encrypted or not when your computer is running.


Regards,
ds[de]

---

### Post by hyper_ch on 2008-09-19
ok, and how would anyone attack while your comp is running?

Over the net somebody is trying to break in?

Someone behind your back watching over your shoulders?

Or while you're not at the computer someone accessing it? If so, why don't you lock it when you're away?

Then, who would that person be that is attacking?

---

### Post by AgainstTheDarkArts on 2008-09-19
Honestly, I can see it happening at the ISP level. 

The gov't comes to comcast (my ISP) and says, "capture everything going to or coming from that system."

They would then have to deal with any encryption I was using(I believe they must be able to do it, don't break my fantasy) and once they did they can search for anything they want.

Can they get into my network?  Probably, I'm not as good as many of the people here.  Can they get into ALL networks?  Probably not, but who knows?

---

### Post by ds[de] on 2008-09-19
> **hyper_ch said:**
> ok, and how would anyone attack while your comp is running?

I don't really know where you're going with this so I'll just ask in which cases an encrypted hard drive would help you in cases where an attack is carried out over the net.

[QUOTE=hyper_ch]Over the net somebody is trying to break in?[/QUOTE]

I think that's the most likely scenario in regards to "**Online** Searches".

[QUOTE=hyper_ch]Someone behind your back watching over your shoulders?[/QUOTE]

No.

[QUOTE=hyper_ch]Or while you're not at the computer someone accessing it? If so, why don't you lock it when you're away?[/QUOTE]

Again, this is about "Online Searches", so we should assume that a potential attacker has no physical access to the machine.

[QUOTE=hyper_ch]Then, who would that person be that is attacking?[/QUOTE]

Again I don't see how this is relevant in a technical discussion, but as the OP stated, probably a government organization.


Regards,
ds[de]

---

### Post by hyper_ch on 2008-09-19
> **'ds[de] said:**
> I don't really know where you're going with this so I'll just ask in which cases an encrypted hard drive would help you in cases where an attack is carried out over the net.
I don't have a clue where you are going to... if you followed the discussion about the Bundestrojaner they still require physicall installataion hence full disk encryption protects you as that is the purpose for which full disk encryption was developped...

> **'ds[de] said:**
> I think that's the most likely scenario in regards to "**Online** Searches".
After they installed the trojans physically on your computer...

---

### Post by northern lights on 2008-09-19
> **'ds[de] said:**
> [QUOTE=hyper_ch;5818559]ok, and how would anyone attack while your comp is running?I don't really know where you're going with this so I'll just ask in which cases an encrypted hard drive would help you in cases where an attack is carried out over the net.[/QUOTE]
Great. Now we're on the verge of flaming.

The question "how would anyone attack while your comp is running?" is exactly my point of genuine interest and it simply gets lost in the further discussion, which is about to happen to this thread also.

While even people in the breakroom of my local grocery store are arguing the legality of the issue (tabloid papers love it, of course). The general public is not even questioning how the mysterious "gaining access" would be accomplished. I'm sure most parliamentarians voting on it don't even have the slightest clue on how their daily PC-related tasks work.

I find the issue ridiculous cause I can't picture exactly that: "them" "attacking" my computer and "searching" it.
"Attacking a computer" - nothing could be more vague.
Script-kiddie lingo, the way I see it. Still, nationally renowned papers are using it. Politicians are using it. It will most likely make the text of the new law in this vague a form.

hyper, law's your field, right?
How vague can a law be before it's just too ill-defined to be used?

---

### Post by ds[de] on 2008-09-19
Oh alright, we were talking about different situations then :-)

They are still discussing both possibilities (from what I read on (mostly) heise.de, it's also in the german wikipedia article on the 'Bundestrojaner'), installing the keylogger over the internet or gaining physical access to your house/flat and installing it directly on your computer. In the second case, yes, an encrypted hard drive would obviously help you, you are correct.

I thougth we were talking about the first case in which encryption wouldn't help .. little misunderstanding there :)


Regards,
ds[de]


//edit:
northern lights: Don't worry, the discussion just got a little heated because hyper_ch and I were talking about different things (apparently). I hope that I didn't offend him and/or somebody else.

---

### Post by hyper_ch on 2008-09-19
ds[de] if you had read the document published by the pirate party you would have known that - at least for the Bavarian Skype Trojan - and very likely also for the bundestrojan as of now physical access to the machine is required.

[http://wiki.piratenpartei.de/images/5/54/Bayern-skype-tkue.pdf](http://wiki.piratenpartei.de/images/5/54/Bayern-skype-tkue.pdf)

Northern Lights:

Don't know about German interpretation of the penal code but the interpretation normally has to be close to the text of it. Otherwise it would against the fundamental principle of nulla poena sine lege. People must know what is legal and what is not in order to behave according to the law. Same goes for the principle that "violates" civil rights... as said, I am not familiar with criminal law in germany and searches there.

---

### Post by ds[de] on 2008-09-19
I read the pdf you linked to and it stated (page6)
> For the installation of the Skype Capture Unit an executable file is provided that can be send as an email attachment **or** be directly installed on the target system so it still states both possibilities.

I think we should drop this argument here because we were talking about two different things here & northern lights was interested in ways to intrude while the computer is running so I don't think my comments were way off (and neither were yours).

I hope you didn't take any offense by what I wrote and we can go back to a technical discussion.


Regards,
ds[de]

---

### Post by pytheas22 on 2008-09-19
What exactly is the Bundestrojaner?  I was reading the [site]("http://www.bundestrojaner.net/"), which apparently is a joke, but is the Bundestrojaner a real trojan known to have been distributed by the German government?  I hadn't heard anything about this; maybe the news hasn't spread outside of the German-speaking world (or I'm just ill-informed)?  How does the Bundestrojaner work from a technical standpoint?

Also I like the description of Linux as a [terrorist operating-system]("http://www.bundestrojaner.net/bundestrojaner-faq-1.html#11") :)

---

### Post by hyper_ch on 2008-09-20
"Can be send as attachement" --> you you'll still need the user to run the attachement ;)

---

### Post by airtonix on 2008-09-22
>  I don't know. I just can't imagine governments and/or corporations to be _that_ evil.

I can...quite easily. power corrupts...absolute power corrupts absolutely

---

### Post by tarun.winlin on 2008-09-22
> **airtonix said:**
> power corrupts...absolute power corrupts absolutely

Nicely said :-)

---

