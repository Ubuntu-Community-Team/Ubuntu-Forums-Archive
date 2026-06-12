---
title: "DVDs and CSS"
date: 2013-05-23
forum: Ubuntu, Linux and OS Chat
---

### Post by newb85 on 2013-05-23
So the other day my wife and I sat downto watch a movie on my laptop, recently graced with a fresh installof Raring.  I had installed my favorite browser, email client, biblesoftware, restricted extras, etc., but I’d neglected to run theinstall-css.sh script.  I’d done it a dozen times in the past, andcould almost do it from memory.  But this time I had to do it whilemy wife (only recently introduced to Ubuntu) watched.  To be honest,I was a little embarrassed that my OS requires me to run a scriptburied five layers into the system files just to watch a DVD.

Then it hit me.  Why?  I’d never eventhought about what the script did in the past.  I just ran it, andthen DVD play started working.  I was a little surprised to realizethat all the script does is download the libdvdcss2 package from theMaverick release of the Medibuntu repository and install it.  Sothen, why isn’t libdvdcss2 included in the Multiverse repository? For that matter, why isn’t it included in  the restricted extrasmetapackage?

---

### Post by MadmanRB on 2013-05-23
Simply put its a mostly illegal workaround so even the restricted repos are not immune to possible lawsuits.
At least MP3 playback in linux is MOSTLY legal as are some other codecs.
But the matter of libdvdcss is more complicated.
Heck even windows cant play DVD by default in terms of the law, a non OEM copy of windows wont have DVD playback

---

### Post by lalaaa on 2013-05-24
what is css???

---

### Post by newb85 on 2013-05-25
Content Scramble System.  [http://en.wikipedia.org/wiki/Content_Scramble_System](http://en.wikipedia.org/wiki/Content_Scramble_System)

---

### Post by MadmanRB on 2013-05-25
> **newb85 said:**
> Content Scramble System.  [http://en.wikipedia.org/wiki/Content_Scramble_System](http://en.wikipedia.org/wiki/Content_Scramble_System)

this is the main controversy here, as I said at least something like MP3 playback is semi legal while DVD playback is far more of a gray area.

---

### Post by newb85 on 2013-05-25
I'm not trying to make legal or political arguments here.  (I'm not qualified for the first, and the second is against CoC.)  I just want to understand better.  The difference between "semi legal" and "grey area" evades me.

Here's how I understand it.  Please feel free to correct...

As I understand it, laws and rulings against distribution of CSS decryption are for the protection of the DVD content, not the format itself.

Codecs are different, however, in that any lawsuits that could/would take place would be for the protection of the patented encoding format itself.

So then, distribution of the unpatented CSS decryption tools is illegal because we could use it to copy copyrighted material, but distribution of patented codecs is not?

---

### Post by MadmanRB on 2013-05-25
Yes, as those patented codecs are so common anyhow so distributing them on the side is a non issue for the most part.
The only time codecs become an issue is when they come pre packaged with the OS like on linux mint, but since it is not as public as Ubuntu it can slip in the cracks a little.
Ubuntu however is owned by a major company as opposed to a independent distro so it cant come with codecs out of the box.
And windows is no different, again get a box copy of windows and it will have no codecs on it.
The main reason why windows seems "easier" with multimedia is because companies like dell/HP/Toshiba and the like hand you the codecs but install windows on your own and its your job to install codecs.

---

### Post by josephmills on 2013-05-25
Read this and you will see why 
[http://en.wikipedia.org/wiki/Digital_rights_management](http://en.wikipedia.org/wiki/Digital_rights_management)

---

### Post by monkeybrain2012 on 2013-05-25
I think libdvdcss is only potentially illegal in the U.S because of DMCA, but there has been no definitive words as far as I know, it seems not important enough for the copyright thugs  to bother, possibly because of desktop Linux's small user base in the U.S. But then it is also illegal in the U.S. to unlock your cell phone. Distros are only playing it safe for not bundling it. Since I don't live in the U.S. it is never my concern. 

I am wondering what goodies are bundled in Kylin (Ubuntu Chinese edition) :)

---

### Post by monkeybrain2012 on 2013-05-25
Codecs are different. It is illegal to distribute codecs without permission, but it is not illegal to use them for personal purposes (you need to pay for license to play mp3 if you run a radio station, but not if you listen to music at home) But libdvdcss is different in that under DCMA any technology with the purpose of circumventing copyright protection is illegal and it is exactly what libdvdcss does, so if libdvdcss is indeed illegal (likely though there has not been any official word) it will still be illegal if you download it from Videolan yourself (VLC). But again this is only in the U.S. Videolan is in France so it can host libdvdcss publicly with impunity. I suppose medibuntu's server is also somewhere in Europe.

---

### Post by grahammechanical on 2013-05-25
We are missing something. Ubuntu policy. Ubuntu is a Free and Open Source Linux distribution that allows users to decide to install codecs that might be illegal in some jurisdictions and also non-free proprietary software. We tick to install third party software during installation or install it afterward. It is our choice just as it is the choice or decision of Canonical not to include this stuff as default software.

Fundamentally, the desire of the Ubuntu owners and developers is to have Ubuntu as Free and Open Source as possible. That is not practically possible, when you also want a distribution that ordinary people can use without needing a university degree in Linux. But it is the aim. 

So, it is easy to install proprietary video drivers. It also means that certain code will never be part of the default installation or be put in the repositories. And its no good moaning about it.

Now, for something completely different.

> **Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).**

> [COLOR=#333333][FONT=sans-serif]It is your legal responsibility to make sure that the software you are installing can be legally used in your country and for your intended purpose.[/FONT][/COLOR]

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Regards

---

### Post by newb85 on 2013-05-25
Well, in starting this thread, it wasn't my intent to start a long discussion on legality or distribution philosophy.  Philosophy played a central role in the development of Ubuntu, and I imagine it won't change.  If one doesn't like the philosophy of Ubuntu, it's much more effective to simply switch to a distro you do like.

I guess the main reason for my question was the fact that I didn't understand the purpose of the Universe and Multiverse repos.  They're still hosted by Ubuntu, and so they still need to fall within legal bounds.

---

### Post by MadmanRB on 2013-05-25
Well the hosting of the codecs is a non issue, you can host the codecs just not distribute them on the distro by default via the install disc.
Hosting the codecs is not the issue, its using them is where that legal gray area comes in
Again that all has to do with that legal gray area that even windows isnt immune to.
The codecs you install at your own risk, ubuntu or canonical can host the codecs yes but its up to to you if you wish to ignore the laws of your respective nation.

---

### Post by LordDelta on 2013-05-25
> **MadmanRB said:**
> 
Again that all has to do with that legal gray area that even windows isnt immune to.
The codecs you install at your own risk, ubuntu or canonical can host the codecs yes but its up to to you if you wish to ignore the laws of your respective nation.

What does Windows do about it?

I don't think the issue is about the legality; Medibuntu exists because its practical. Windows users watch films because it is practical.

What can be done to make this more practical without making it an issue?

Its not as if Medibuntu is more legal than normal Ubuntu. E.g., there are always it seems these knockoff distros such as Zorin OS and such which DO come with all the bases installed, and they sometimes even charge for their stuff. Why are they getting away with this, when Ubuntu can't?

Does Ubuntu need to offer a 5$ version of their OS that has these codecs installed, so they can pay some licensing fee? Its not like people are averse to paying for software, and those people who are embarassed to use a script in front of their significant other will have no problem just forking out a couple of bucks I imagine...while those that don't care continue to just use Medibuntu.

As for legality, things that are practical and widely accepted by society have a habit of becoming law anyways (in free societies at least). Should #FSF be harping more on the rights of users to watch the films they purchase?

---

### Post by MadmanRB on 2013-05-26
> **LordDelta said:**
> What does Windows do about it?

Nothing, Windows by default does not ship codecs by default.
What it does however is usually come with windows media player what when installed does install the codecs you need.

> I don't think the issue is about the legality; Medibuntu exists because its practical. Windows users watch films because it is practical.
No it has everything to do with legality.
Medibuntu is a unofficial repository so it stays off the radar
As for the official repos there is nothing really there to get ubuntu into trouble, again it is the end user who is at hand here.

> What can be done to make this more practical without making it an issue?
End software patents

> Its not as if Medibuntu is more legal than normal Ubuntu. E.g., there are always it seems these knockoff distros such as Zorin OS and such which DO come with all the bases installed, and they sometimes even charge for their stuff. Why are they getting away with this, when Ubuntu can't?

No medibuntu is an unofficial repo as I said
As for spin  offs again it all goes down to what they are willing to prepackage that is at stake here, by default Ubuntu cant as its owned by a publicly known company.
The other distros like Zorin and mint are not owned by a major company, they are made by smaller entities.
As for zorin by all means what it is doing is illegal and i am surprised it hasnt been killed off but because its still small I guess thats why it avoids scrutiny.

> Does Ubuntu need to offer a 5$ version of their OS that has these codecs installed, so they can pay some licensing fee? Its not like people are averse to paying for software, and those people who are embarassed to use a script in front of their significant other will have no problem just forking out a couple of bucks I imagine...while those that don't care continue to just use Medibuntu.

No as the cost of the codecs is much higher then just a fiver.

> As for legality, things that are practical and widely accepted by society have a habit of becoming law anyways (in free societies at least). Should #FSF be harping more on the rights of users to watch the films they purchase?

There is little the FSF can do, its not that powerful.

---

### Post by LordDelta on 2013-05-26
> **MadmanRB said:**
> Nothing, Windows by default does not ship codecs by default.
What it does however is usually come with windows media player what when installed does install the codecs you need.


No it has everything to do with legality.
Medibuntu is a unofficial repository so it stays off the radar
As for the official repos there is nothing really there to get ubuntu into trouble, again it is the end user who is at hand here.


Ok, so how is that legal for Windows?

Windows Media Player is very well known, and anything but unofficial or off of the radar.

How about just obfuscating the hell out the binary? If they're going to treat legitimate users like felons, perhaps the legitimate users should act more like felons and take a couple pages from the virus community. >_<

I don't usually wish bad things on people, I but I hope everyone at the RIAA/MPAA/Patent Troll loses their job, is locked up for twenty years, and is financially ruined forever, for their greed, gluttony, idiocy, and general tyrany.

---

### Post by MadmanRB on 2013-05-26
The thing is that windows media player gets its codecs via the internet (normally) it wont work otherwise.
As for software patents yes they need to end but as long as the corrupt are in power it wont cease any time soon.
But that is more of a political issue so I wont say more

---

### Post by newb85 on 2013-05-26
> **LordDelta said:**
> Its not like people are averse to paying for software, and those people who are embarassed to use a script in front of their significant other will have no problem just forking out a couple of bucks I imagine...while those that don't care continue to just use Medibuntu.

Perhaps you misunderstand what I said.  I'm not embarrassed to use a script.  They're quite useful.  I'm embarrased that my OS doesn't have a more user-friendly way of doing something so common as watching a DVD.

And for the record, yes, some people are averse to paying for software.  At least, I can attest to the existence of one who is.  And the party in question is one to which the current poster is in the habit of referring by means of the perpendicular pronoun...

---

