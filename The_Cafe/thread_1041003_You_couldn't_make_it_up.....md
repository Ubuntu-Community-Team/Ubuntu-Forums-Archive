---
title: "You couldn't make it up...."
date: 2009-01-16
forum: The Cafe
---

### Post by amauk on 2009-01-16
**16th Dec 2008**
[http://www.theregister.co.uk/2008/12/16/windows_for_submarines_rollout/](http://www.theregister.co.uk/2008/12/16/windows_for_submarines_rollout/)

**15th Jan 2009**
[http://www.theregister.co.uk/2009/01/15/royal_navy_email_virus_outage/](http://www.theregister.co.uk/2009/01/15/royal_navy_email_virus_outage/)

---

### Post by SunnyRabbiera on 2009-01-16
I just cant wait for the computer virus that makes one of them crash into a undersea mountain :p

---

### Post by jomiolto on 2009-01-16
> The entire command system of HMS Vigilant, a Trident nuclear-missile submarine, was apparently replaced with the SMCS-NG Windows LAN ...

> BAE Systems' work is proof that we can get commercial off the shelf technology to sea quickly and support it affordably.

Uh, I thought security was the number one feature on such systems, even if it costs a bit more? Not that Windows XP is such an awful system (at least from my experience), but I'd feel much comfortable if they used something like one of the BSDs, which have been proven to be extremely solid and stable.

---

### Post by aesis05401 on 2009-01-16
Unfortunately, the systems that were hit appear to actually be Unix variants.  

We will have to wait for more details, but this may be completely unrelated to the Windows implementations that were publicized in December.

---

### Post by amauk on 2009-01-16
> **aesis05401 said:**
> Unfortunately, the systems that were hit appear to actually be Unix variants.Have you got a source for that?

---

### Post by aesis05401 on 2009-01-16
Yes.  

_[Source in .pdf]("http://www.cesg.gov.uk/products_services/iacs/cc_and_itsec/media/certreps/CRP230.pdf")_

The systems that were hit are integrated into a Microsoft centric VPN known as DII, but are actually running on 'NonStop OS' by HP.  The messaging system that was brought down is known as OMEGA.

From the link on the software specs:
"The server component of OMEGA Version 7.20 Increment 70 runs on HP Integrity NonStop servers with the HP NonStop G06 Operating System."

As I mentioned, the tech integrates with a Windows VPN and the source mentions that there is client software that will, "run on PC workstations running DOS or Windows XP. Badge Encoder software can run under Windows 2000 or Windows XP.

Edit: I should mention that the piece you link to is not a good source for security information.The N* system that they are telling you is affected means nothing...My understanding is that N* is essentially just a hardened physical mounting system - and N* systems include whatever OS you want to pay to be supported.

The article refers to an N* outage.. that means nothing ;)  We are smarter than that.

---

### Post by scorp123 on 2009-01-16
> **aesis05401 said:**
> 'NonStop OS' by HP. ....  HP Integrity NonStop servers with the HP NonStop G06 Operating System. "NonStop" is **_NOT_** a Unix variant!

It's a proprietary OS originally developed by Tandem back in the 1970's. Via acquisition of Tandem Computers by Compaq and then the merger of Compaq and HP, it became a HP product. But it has nothing whatsoever to do with Unix. If anything you could probably compare it best with a MainFrame OS, e.g. such as from IBM.

Being a totally proprietary product "NonStop" has similar weaknesses such as Windows, e.g. nobody except a small group of programmers who work for the manufacturer is able to look at the source code; if weaknesses are spotted it might take quite a while until they are fixed (nobody but the manufacturer's programmers are able to supply a patch ...).

This just shows why one should avoid closed-source proprietary operating systems altogether; not just Windows.

---

### Post by shatteredmindofbob on 2009-01-16
I guess when you're stuck under water for months at a time, it's hard not to surf a few porn sites...

---

### Post by scorp123 on 2009-01-16
> **shatteredmindofbob said:**
> I guess when you're stuck under water for months at a time, it's hard not to surf a few porn sites... :lolflag:

---

### Post by aesis05401 on 2009-01-16
> **scorp123 said:**
> "NonStop" is **_NOT_** a Unix variant!

Tanks for the info.  I was told that NonStop was based on Unix, but after looking it up I stand corrected :)

Edit:  Wait a second!  They paid a fee and forked a Unix implementation back in '89 apparently to combat IBM System/88 - this somehow involved the Integrity line or its ancestor technologies...(I really don't know much about this).

It was originally called NonStopUX.  I have no idea if they have stuck with that model, but I thought that was what they were based on.

Anyhow, you are correct about being about as proprietary as Windows, most Unix flavors are.  I worked with IBM variants for a while, and that was closed as you come at the time.

EDIT: The muddy waters around UNIX IP was what let SCO tie up the courts with their lawsuits for so long.  Whether or not it still exists the original NonStopUX line would have been as closed as they come.

---

### Post by aesis05401 on 2009-01-16
> **scorp123 said:**
> "NonStop" is **_NOT_** a Unix variant!

It's a proprietary OS originally developed by Tandem back in the 1970's. Via acquisition of Tandem Computers by Compaq and then the merger of Compaq and HP, it became a HP product. But it has nothing whatsoever to do with Unix. If anything you could probably compare it best with a MainFrame OS, e.g. such as from IBM.

Being a totally proprietary product "NonStop" has similar weaknesses such as Windows, e.g. nobody except a small group of programmers who work for the manufacturer is able to look at the source code; if weaknesses are spotted it might take quite a while until they are fixed (nobody but the manufacturer's programmers are able to supply a patch ...).

This just shows why one should avoid closed-source proprietary operating systems altogether; not just Windows.

I just reread your post and want to clear something up.  UNIX is a mainframe OS, and the AIX line from IBM, now renamed iSeries or something is UNIX.

UNIX on the desktop really still consists of using a VT100 terminal, though graphical layers are certainly available, they are typically not implemented in a traditional UNIX environment.  It is a mainframe based time sharing system with all sorts of proprietary hardware fault tolerance extensions available.

And UNIX implementations are heavily defended by IP hawks.  Many like the one we are discussing target military customers and their secrecy is generally considered an asset.

Your comment would make sense if we were talking about Linux.

---

### Post by Sealbhach on 2009-01-16
Similar chain of events here:

[http://goban.weebly.com/](http://goban.weebly.com/)



.

---

### Post by scorp123 on 2009-01-16
> **aesis05401 said:**
> UNIX is a mainframe OS ... With "mainframe OS" I meant something along the lines of IBM S/390 (zSeries). With the focus on being as fail-safe as possible and given the fact that the OS is pretty much tied to the hardware I thought that this comparison was quite fitting.

---

### Post by scorp123 on 2009-01-16
> **Sealbhach said:**
> Similar chain of events here:
[http://goban.weebly.com/](http://goban.weebly.com/)  Well, sometimes people get exactly what they pay for. And they paid for Windows ... so by all means they deserve the problems they have now :lolflag:

---

### Post by |eafhound on 2009-01-16
amazing

---

### Post by bruce89 on 2009-01-16
The snag is the UK (sort of) nukes are just a few miles from me. Hopefully they have a fail-safe.

---

### Post by MaxIBoy on 2009-01-16
> **scorp123 said:**
> "NonStop" is **_NOT_** a Unix variant!

It's a proprietary OS originally developed by Tandem back in the 1970's. Via acquisition of Tandem Computers by Compaq and then the merger of Compaq and HP, it became a HP product. But it has nothing whatsoever to do with Unix. If anything you could probably compare it best with a MainFrame OS, e.g. such as from IBM.

Being a totally proprietary product "NonStop" has similar weaknesses such as Windows, e.g. nobody except a small group of programmers who work for the manufacturer is able to look at the source code; if weaknesses are spotted it might take quite a while until they are fixed (nobody but the manufacturer's programmers are able to supply a patch ...).

This just shows why one should avoid closed-source proprietary operating systems altogether; not just Windows.
Interesting that it's an OS I'd never heard of until now. Chances are, these military systems were actually targeted for attack. Unless I've simply been under a rock, I doubt there would be many  NonStop installations out there; thus, there wouldn't be any NonStop viruses "in the wild." This seems deliberate.

---

### Post by Firestem4 on 2009-01-16
lmao..i didnt even finish reading the first arcticle after it had said it implimented Windows LAN ethernet (blah blah) systems. I'm thinking.....Its the end of the world.

If i wasn't as preoccupied i wouldve died in my seat laughing from the title of the second article....you really CAN"T make that crap up

---

### Post by aesis05401 on 2009-01-16
> **Firestem4 said:**
> lmao..i didnt even finish reading the first arcticle after it had said it implimented Windows LAN ethernet (blah blah) systems. I'm thinking.....Its the end of the world.

If i wasn't as preoccupied i wouldve died in my seat laughing from the title of the second article....you really CAN"T make that crap up

Read up on DII in general.  Scary stuff.

---

### Post by scorp123 on 2009-01-16
> **MaxIBoy said:**
> Interesting that it's an OS I'd never heard of until now. I worked seven years for HP (2000-2007) and only _ONCE_ even caught a glimpse of it :D

It's not that "NonStop" is super-secret or something ... it's just the same as with other certain OS'es, e.g. IBM OS/390, OS/400, hp MPE/x .... Outside of certain circles you're simply unlikely to ever hear about them, let alone even see or touch them. The fact that those OS'es are tightly tied to sometimes very expensive and special hardware too makes sure that average geeks never ever get into contact with this stuff.

> **MaxIBoy said:**
>  I doubt there would be many  NonStop installations out there Actually "NonStop" is quite popular in certain sectors, e.g. banks, government, insurance companies ....

What I doubt here is that this virus really infected NonStop ... Maybe NonStop is used as some sort of file server? So it may have transported the virus and/or trojan or whatever it is to the Windows systems, but NonStop itself didn't get infected; it just served as the means of transport.

It's a similar scenario with Linux file servers: there could be viruses on a Samba share, yes. Linux won't be infected but any Windows client accessing the virus probably will.

It might have been something similar here?

---

### Post by MaxIBoy on 2009-01-16
You know, I hadn't thought of that. If some kind of worm got into the system and infected the Windows machines, it could bring a LAN to its knees by trying to spread itself, without ever infecting the servers.

---

### Post by MikeTheC on 2009-01-16
Why didn't they pick Linux? I mean, the source is open, the platform robust and solid, no NDAs would have had to be signed on their part, and they'd have the benefit of a widely peer-reviewed OS.

Sounds like just another Microsoft sales job.

Bet you one thing, though. Something happens and a person, place or city gets damaged and it's traceable back to Windows, Microsoft's name is gonna be mud faster than light takes getting from Sol to the Earth.

---

### Post by scorp123 on 2009-01-17
> **MikeTheC said:**
> Why didn't they pick Linux? I mean, the source is open, the platform robust and solid, no NDAs would have had to be signed on their part, and they'd have the benefit of a widely peer-reviewed OS Even if the GPL stopped them (the GPL might force them to publish any changes they did to the kernel or other component under the GPL) ... They could have used any of the BSD's. The BSD license lets you do pretty much what you want (just look at Apple and Mac OS X which is based on BSD to a very large part ...) without being forced to give anything back if you don't want to ....

---

### Post by amauk on 2009-01-17
> **scorp123 said:**
> the GPL might force them to publish any changes they did to the kernel or other component under the GPLonly applies if you distribute binaries to third parties
using modified GPL software internally within an organisation is perfectly fine

---

### Post by scorp123 on 2009-01-17
> **amauk said:**
> only applies if you distribute binaries to third parties But that's the point exactly: I'd assume that a commercial vendor or other third party would implement the system for them, e.g. in a "pilot" environment first, and then on a prototype, and then when everything is fine, they'd go into serial production .... to my understanding this would constitute "distributing binaries" then and therefore disclosure of the modified source code would become a "must".

---

