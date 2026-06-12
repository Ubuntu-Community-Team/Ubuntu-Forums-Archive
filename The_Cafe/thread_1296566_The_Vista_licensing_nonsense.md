---
title: "The Vista licensing nonsense"
date: 2009-10-20
forum: The Cafe
---

### Post by cnbiz850 on 2009-10-20
I posted a note on [http://ubuntuforums.org/showthread.php?t=1291644]("http://ubuntuforums.org/showthread.php?t=1291644") on a similar topic mainly to seek some technical help.  Here I would like to seek some more discussion on the legal aspect.  

I am not a lawyer, but would like to initiate some discussions (if it has not been initiated) and see if we can get more support on this topic, and possibly have some actions together in the future following the advice of some more capable persons.

The issue (as mentioned in the above link) is this: I just bought a Dell laptop that comes with a Vista Home Premium license.  What I would like to do is to wipe out the Vista (pre-installed by Dell but not activated by me yet) and install Ubuntu on it, then install Vista on a virtual machine on top of Ubuntu and activate Vista there.

According to a response of that thread, the Vista license says that > You may not use the software installed on the licensed device within a virtual (or otherwise emulated) hardware system.  Accordingly, that is extracted from [http://download.microsoft.com/documents/useterms/Windows%20Vista_Ultimate_English_36d0fe99-75e4-4875-8153-889cf5105718.pdf]("http://download.microsoft.com/documents/useterms/Windows%20Vista_Ultimate_English_36d0fe99-75e4-4875-8153-889cf5105718.pdf")

I think this kind of term is really out of the lines with the reasonable aspects of the associated laws.  Again, I am not a lawyer, but I believe the laws are at least reasonable, and so are the copyright law and whatever laws that govern in this situation.  Lawyers please comment and help.  

Forbidding someone from having multiple copies when he only bought the license for one copy is reasonable and understandable.  However restricting someone on HOW to use a tool is totally unacceptable.  For instance in the hardware world, the manufacturer can not say that the car is not allowed to be driven on red carpets or above ground in a building.  It is not their business!  Vista is a tool and it is up to the user -- NOT Microsoft -- to decide on how to use it -- as long as he paid for the copy.

Why does MS require that Vista can not be run on a virtual machine?  It is abusing its monopoly power to bully the end users.  Should they require that other software can not be installed on Vista?  Or should they require that other OS (like Ubuntu) can not be installed on the hardware where Vista is installed?  Looks like they going that direction.

MS may argue that Vista only runs directly on top of hardware.  Well unfortunately, 1) it does not really run directly on top of hardware and 2) it also runs indirectly on top of hardware.  For case 2) I don't need to say more because it runs on VM's.  For case 1), it does not really function much if put directly on a piece of HW because it badly needs various and many appropriate hardware drivers.  What is a driver?  It is a piece of software that sits between the OS and the hardware.  In other words, it is an emulating layer under the OS.  So according to MS's license terms, Vista is not allowed to run on any computer because there are software emulation underneath.

Well, MS, if the emulating drivers are OK for Vista, why not a VM?  What is the difference?

Come on guys!  What is really in the laws?  Can we stand up and fight?!

---

### Post by jwbrase on 2009-10-20
I can imagine a number of things they might be attempting with such licensing terms:

1): They may be trying to stop people from installing their copy of Vista on multiple VM's running on the same host machine, and claiming they haven't violated the licensing terms because they only installed it on one machine.

2): They may be trying to prevent people from using a VM to disguise a bootleg copy of Vista as valid (for instance, I think some of their validation procedures involve hardware checks, which would lead to multiple VM's looking like the same machine), or from running Vista in a VM and using various imaginable methods to reverse engineer Vista.

The best way to fight this is not to buy Vista. (Or 7, or any other MS product).

---

### Post by Frak on 2009-10-20
If you're running it in a VM, it's a different device. You're using a competitor or duplicate product. Go buy a full version of Vista, and it won't affect you. The version you have was made specifically for your laptop, nothing else.

What are the laws? Microsoft tells you what you can run it on, and if you don't agree with it, don't use it.

@jwbrase
You're correct. It's possible to fool versions of Vista with a special VM.

---

### Post by Jackelope on 2009-10-20
Why would you want to run Vista in a VM when you could use Server 2008 R2 (stripped Win7 basically) for free by getting the trial and extending it every 60 days? Annoying for a primary OS, sure. But for a VM? I'd be ok with it. Just an idea for ya.....

BTW, I'm impressed that you read the EULA. I thought I was the only one.

---

### Post by Shibblet on 2009-10-20
Can't you run the original installation in a VBox?

---

### Post by dj-toonz on 2009-10-20
> **Shibblet said:**
> Can't you run the original installation in a VBox?


If it's a retail copy of windows yes u can , but not a OEM version I believe but don't quote me on that

---

### Post by earthpigg on 2009-10-20
terms and conditions that limit your fundamental freedoms are a fundamental component of non-free software.

period.

---

### Post by cnbiz850 on 2009-10-21
> **Shibblet said:**
> Can't you run the original installation in a VBox?

Do you mean using VBox's "raw host hard disk" feature?  Even if it was activated, when you run it in VBox, would it think that you are running on a different device and ask you to activate it again?

---

### Post by FLMKane on 2009-10-21
You guys should remember that you can never buy Windows. The EULA is a lease agreement. Those terms are absolutely fine for a lease agreement.

---

### Post by t0p on 2009-10-21
If you want to use Microsoft's product, you have to agree to abide with the EULA.

Of course, you don't necessarily have to abide by the agreement.  It may be possible to install Vista in a virtual machine.  I've never tried it.  But I've broken EULAs with impunity in the past.  Despite Microsoft's best efforts, they can't (always) see what you're up to with their software.

---

### Post by cnbiz850 on 2009-10-21
Guys,

Thanks very much for all the responses.

But I must say that I don't really agree with those of you so easy on the EULA.  Some said that if you agree with what it says, you use it, otherwise, don't.  Well it is not that simple.  If MS were one of that smaller company, that would work out fine.  Nowadays, it is in a monopoly stage and the end user is not free to walk away.  Although I am a heavy Ubuntu user, I am really sorry that this is how things work now.  Maybe it is better in US or EU, but I am in China.  Every bank (including some of world's largest banks in some aspects) requires that you use Windows and IE in order to do online banking.  China Mobile requires that you use IE to access your online account.  I do securities trading.  Basically every security analysis and trading software runs on Windows.  I managed to get most I need to run on Wine, but there are still some that don't.

Even facing a monopoly like MS, the world shouldn't so easily accept what is demanded to them.  Think about an extreme case: if the EULA has a clause saying that you the end user must knee before the computer everytime before you want to use it and pray "Bill, the Lord, please let me use the computer now and I will do anything you ask for".  Will there be anyone accepting the term?  In the short term, still many!  The world is basically abducted by MS.  But I think we all agree that many would stand up and fight it because it is too unreasonable and absurd.  The thing is that being unreasonable and being reasonable is not a black and white switch.  Is the current EULA reasonable?  You heard me on that.  So we can't just sit back and accept it.  It definitely appears that I or a few of us can not fight MS alone, but I am sure there are more potent powers in the world who can beat the unreasonable MS.

---

### Post by lukjad on 2009-10-21
Eh, well. I don't care.

---

### Post by jwbrase on 2009-10-21
> **FLMKane said:**
> You guys should remember that you can never buy Windows. The EULA is a lease agreement. Those terms are absolutely fine for a lease agreement.

Well, actually, if enough Linux users got together, maybe we could buy Windows... :) Anyone for a corporate takeover bid? :p

---

### Post by blur xc on 2009-10-21
> **earthpigg said:**
> terms and conditions that limit your fundamental freedoms are a fundamental component of non-free software.

Period.

bingo!

Bm

---

### Post by PhilGil on 2009-10-21
I agree that some EULA's are heinous, that's one of the many reasons I use Linux.  

A great organization that fights for privacy rights and against overreaching intellectual property laws is the [Electronic Frontier Foundation]("http://www.eff.org/").

---

### Post by juancarlospaco on 2009-10-21
*Who cares?*
You cant run MS Vista on MS Virtual PC, LOL

---

### Post by blur xc on 2009-10-21
> **juancarlospaco said:**
> *Who cares?*
You cant run MS Vista on MS Virtual PC, LOL

:confused:

am I missing something?  I run vista in a VM all the time... 

BM

---

### Post by Frak on 2009-10-21
> **jwbrase said:**
> Well, actually, if enough Linux users got together, maybe we could buy Windows... :) Anyone for a corporate takeover bid? :p
You'd still be lacking $19,999,999,999.

---

### Post by Shibblet on 2009-10-21
> **cnbiz850 said:**
> But I must say that I don't really agree with those of you so easy on the EULA.  Some said that if you agree with what it says, you use it, otherwise, don't.  Well it is not that simple.

You want a flat panel TV. I sell Flat-Panel TV's at my store.  However, the requirement of purchasing one is that the customer could only have Dish Network, no Comcast, or Local Cable Service, or DirecTV even.  That "could" be enough restriction to sway a customer to shop elsewhere.  Somewhere there are less restrictions.

So you are faced with the choice:  Either Buy the TV and the Dish Network Package (EULA), or go elsewhere to buy a different brand of TV (Ubuntu) and use whatever television service you prefer.  However, you CAN'T use Dish Network, because they aren't providing service to people who didn't buy from me.  

Is that stupid?  Yes.
Is it restrictive?  Yes.
Will that change your opinion of my store?  Yes.

Is it legal?  Yes.

---

### Post by Shibblet on 2009-10-22
> **Frak said:**
> You'd still be lacking $19,999,999,999.

Dear Mr. Ballmer,

On behalf of the Linux Users Group of Cherry River, South Dakota.  We would like to send a check for the amount of $125.76, a 20 count pre-paid coffee card from the shop we meet at, and a picture of Dyllan's 23 year old sister, cuz she's hot.

In exchange, we would like you to purchase the majority share of your company Microsoft.  If this is a situation you would be interested in, please call me at (418) 555-1234.  If I do not answer, leave a message with my mom.

Thanks,

Norman (N-Dog) Rasmussen
President Linux Users Group
Cherry River, South Dakota

---

### Post by jwbrase on 2009-10-22
> **Shibblet said:**
> Dear Mr. Ballmer,

On behalf of the Linux Users Group of Cherry River, South Dakota.  We would like to send a check for the amount of $125.76, a 20 count pre-paid coffee card from the shop we meet at, and a picture of Dyllan's 23 year old sister, cuz she's hot.

In exchange, we would like you to purchase the majority share of your company Microsoft.  If this is a situation you would be interested in, please call me at (418) 555-1234.  If I do not answer, leave a message with my mom.

Thanks,

Norman (N-Dog) Rasmussen
President Linux Users Group
Cherry River, South Dakota

I was thinking something more along the lines of "Linux Users of the World, UNITE!"

---

### Post by Gwasanaethau on 2009-10-22
> **Shibblet said:**
> Dear Mr. Ballmer,

On behalf of the Linux Users Group of Cherry River, South Dakota.  We would like to send a check for the amount of $125.76, a 20 count pre-paid coffee card from the shop we meet at, and a picture of Dyllan's 23 year old sister, cuz she's hot.

In exchange, we would like you to purchase the majority share of your company Microsoft.  If this is a situation you would be interested in, please call me at (418) 555-1234.  If I do not answer, leave a message with my mom.

Thanks,

Norman (N-Dog) Rasmussen
President Linux Users Group
Cherry River, South Dakota
You forgot to get him to sign a EULA! ;)

---

