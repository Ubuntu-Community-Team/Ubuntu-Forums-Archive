---
title: "Is this TRUE?? Running VIRTUAL Windows is illegal?"
date: 2007-02-27
forum: Windows
---

### Post by PaulFXH on 2007-02-27
I'm using vmplayer in Ubuntu as host to guest OS Windows XP.
I used this guide ([http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)) to access my existing physical Windows XP through vmplayer.
This works very well and is so much more convenient than going through the reboot necessary in a dual boot situation.
However, if I boot to WinXP through the virtual route after previously having accessed it through the dual boot scheme, I am asked to re-activate my Windows. Indeed, apparently I can no longer use my original CoA product key because I have activated my copy of Windows XP too many times (the limit seems to be around ten or possibly less).
Now, to activate it I have to call Microsoft and go through a 10 minute rigmarole before I get to use Windows.
My concern is how long will Microsoft permit me to re-activate WinXP over the telephone?
I asked this question on the Microsoft Windows XP General forum and was told that I cannot legally run WinXP through a virtual machine without a separate licence.
Surely this cannot be true?
Any opinions?

---

### Post by Kateikyoushi on 2007-02-27
I do not know about XP but I read about Vista that the EULA does not permit it to be run from virtual machine.

EDIT:

Some people pointed it out it just effects vista starter and basic home, the other versions can be run in virtual machine.

---

### Post by william_hunter on 2007-02-27
Did you know you can't run the two lower level Vista releases on a Mac using Boot Camp according to the EULA? How they get away with this one escapes me. My $200 should allow me to put their bloated monster of an OS anywhere I want. So, I won't buy it. What now Microsoft?

---

### Post by PaulFXH on 2007-02-27
Hmm, so it looks like it IS true.
But this would mean that very many people, including myself, are illegally running virtual copies of their legally purchased Windows software on the very same computer for which it was licensed. WTF!

---

### Post by Ramses de Norre on 2007-02-27
Not that they'll ever notice...

---

### Post by PaulFXH on 2007-02-27
Well, they will notice if you need to re-activate your Windows XP every time you switch from booting the virtual machine to booting the physical version.
As I mentioned in my first post, I now can no longer use the original CoA key and have to phone Microsoft to get a new key to complete the activation.
My concern is are they going to cancel my license because I have activated my legally purchased copy of Windows XP too many times?

---

### Post by Toet on 2007-02-27
Due to the same action I had to reactivate my xp once by phone and kept my original key (they re-activated it).

One more reason to never install it again. I'm now keeping a backup of the vmware directory containing xp.

---

### Post by NotPhil on 2007-02-27
> **PaulFXH said:**
> However, if I boot to WinXP through the virtual route after previously having accessed it through the dual boot scheme, I am asked to re-activate my Windows. Indeed, apparently I can no longer use my original CoA product key because I have activated my copy of Windows XP too many times (the limit seems to be around ten or possibly less).

Now, to activate it I have to call Microsoft and go through a 10 minute rigmarole before I get to use Windows.
You've gotta love the way that company treats its customers. 

> **PaulFXH said:**
> I ... was told that I cannot legally run WinXP through a virtual machine without a separate licence.

Surely this cannot be true?

Any opinions?Well, in my opinion, Microsoft has a very limited understanding of both the law and ethics. And their track record in court prevents me from assuming that everything they stick in their licenses and EULAs is legal anyhow. I'm not even sure EULAs (or click-through licenses) are legally binding in the first place. 

Of course, legal or not, there's not much that can prevent Microsoft from suing you, and they've demonstrated that they're more than happy to sue their customers.

---

### Post by Fitzy_oz on 2007-02-27
> **NotPhil said:**
> You've gotta love the way that company treats its customers. 

Well, in my opinion, Microsoft has a very limited understanding of both the law and ethics. And their track record in court prevents me from assuming that everything they stick in their licenses and EULAs is legal anyhow. I'm not even sure EULAs (or click-through licenses) are legally binding in the first place. 

Of course, legal or not, there's not much that can prevent Microsoft from suing you, and they've demonstrated that they're more than happy to sue their customers.

And they wonder why there are cracks all over the internet for their software to disable these intrusive and dubiously legal features of their software.  I don't personally use windows at home anymore, I think I've finally managed to find some sort of balance between the open source alternatives and using wine effectively.  Is there any software in particular that you absolutely must have XP for?

---

### Post by russell.h on 2007-02-27
My understanding is that its completely legal to run XP in a VM.

Your problem is a technical issue (and potentially a legal one too, not sure) that arises from using the same installation of windows in the virtual environment and normally.

If I had to venture a guess you are likely using an OEM version of Windows, although this might happen with retail too. When you first activate your windows installation it collects serial numbers and other individually specific information from your hardware, and saves it for future reference.

Now every time you boot up windows it gathers your hardware information again, and checks it against the numbers it has recorded. If you have an OEM copy of windows it won't let you change out the motherboard, or certain other hardware.

But when you boot in the virtual environment the VM is probably not passing along information about your actual hardware, rather it is probably just making stuff up or something. So windows sees that you have different hardware than you did before, and requires you to reactivate windows.

I'm a little bit vague on how all of that works, but I'm fairly certain that your problems have to do with the virtualized hardware, vs the real hardware.

As for the legal issues, those would arise from the fact that you aren't allowed to install windows on more than one computer, and in the case of OEM windows it may only ever run on the hardware it was originally installed on (you are allowed to install new hard drives and whatnot, but you can't switch out your motherboard for example). Does running Windows on a virtual machine constitute running it on a different computer? Dunno, ask a lawyer.

---

### Post by Quillz on 2007-02-27
> **Kateikyoushi said:**
> I do not know about XP but I read about Vista that the EULA does not permit it to be run from virtual machine.
This is not entirely true. You cannot run Windows Vista Starter or Home Basic editions on virtual machines, but you are permitted to run Business, Home Premium, Enterprise and Ultimate editions.

---

### Post by NotPhil on 2007-02-27
> **Fitzy_oz said:**
> I don't personally use windows at home anymore, I think I've finally managed to find some sort of balance between the open source alternatives and using wine effectively.  Is there any software in particular that you absolutely must have XP for?Not me. But honestly, I wish there were some better financial applications for Linux. It looks like I'm going to end up using Quicken under WINE because I can't find a better alternative. 

And not having any encyclopedias for Linux bugs me too. I'm still one of Microsoft's customers, though I'd rather not be, because I'm running MS Encarta through WINE. (I wonder what they think of that.)

---

### Post by Jott on 2007-02-27
I was actually in the same situation a few months ago - I was dual booting, and set up a virtual machine to run xp off the existing windows partition.  When I booted back into windows on the physical machine, I had to re-activate my software, and the key didn't work any more.  I called the activate by phone number, and they gave me a new key with no hassles.  I got the feeling the tech support droid had no idea what I was talking about when I told him what happened - I think I lost him at the word 'partition'.  Anyway, I was fairly surprised at how little hassle I got - though I only did it once (never got the vm to work quite right and gave up on it).

It would certainly be nice if there were better financial apps...I've used gnucash and KMyMoney, but none of it replaces Quickbooks for small bussiness accounting...I recently installed xp in a vm on my machine just so that my wife can use Quickbooks.  Actually works ok - I set it to suspend on close, and put a little windows button on the desktop for her - it taked less time to resume the windows session with quickbooks active than it takes to open quickbooks from scratch on windows.

I also saw somewhere recently an article on software that lets you just open an app from your virtual machine in it's own window, without getting the whole virtualised os.  Gives the appearance of seamless virtualisation.  Can't remember what it's called...

...anyway, that's my rambling $.02.

---

### Post by Fitzy_oz on 2007-02-27
> **NotPhil said:**
> Not me. But honestly, I wish there were some better financial applications for Linux. It looks like I'm going to end up using Quicken under WINE because I can't find a better alternative. 

And not having any encyclopedias for Linux bugs me too. I'm still one of Microsoft's customers, though I'd rather not be, because I'm running MS Encarta through WINE. (I wonder what they think of that.)

I don't imagine it's what they had planned for Encarta when they designed it :)

I don't run one but I did have a look at appdb.wine.org and did see that there are quite a few that work and quite a few that haven't really been tested in a long time like myob.  Might be worth rolling up the sleeves and having a look.

---

### Post by srt4play on 2007-02-27
> **Jott said:**
> I also saw somewhere recently an article on software that lets you just open an app from your virtual machine in it's own window, without getting the whole virtualised os.  Gives the appearance of seamless virtualisation.  Can't remember what it's called....

That sounds really cool, if you remember the name of it let us know.

---

### Post by Kateikyoushi on 2007-02-27
> **Quillz said:**
> This is not entirely true. You cannot run Windows Vista Starter or Home Basic editions on virtual machines, but you are permitted to run Business, Home Premium, Enterprise and Ultimate editions.

Thanks for correcting me, I will add it to that post not to scare someone away from vista. ;)

Their EULAs are really strange I heard they had some packages "By opening this package you accept the EULA" printed on them, which was inside the package so you can hardly read it to decide wether you accept it or not.

Not that law always works in the first place, so EULAs are just like that made for the majority, they just want to milk another few hundred $ from thos who can't use the Vista which came with their pc on virtual machine.

---

### Post by AusIV4 on 2007-02-27
I don't know where everyone is getting their information. Any version of Windows Vista can be run from a virtual machine. The EULA of some versions of vista prohibits using the **same license** on a physical machine and virtual machine. 

It states:
> USE WITH VIRTUALIZATION TECHNOLOGIES. You may not use the software installed on the licensed device within a virtual (or otherwise emulated) hardware system.You would be fine to install it on a virtual machine, you just can't install it on your computer, then run it from a virtual machine.

---

### Post by PaulFXH on 2007-02-28
This is most distressing!:( 
So apparently, the fact that virtualisation has afforded me a "shortcut" to WindowsXP from Ubuntu (compared to the dual boot situation) is deemed a criminal offense?
For crying out loud!!!!](*,) 

russell.h said
> you are likely using an OEM version of Windows
Yes, I am.
> But when you boot in the virtual environment the VM is probably not passing along information about your actual hardware, rather it is probably just making stuff up or something. So windows sees that you have different hardware than you did before, and requires you to reactivate windows.
OK, to run the VM WinXP, I had to create a different hardware profile simply by copying the profile that was already there and gave it a different name. Now, whatever about the software getting the impression that the hardware has changed or not, the fact is that both the virtual and the real/physical Windows are using the EXACT same hardware.
However, I would guess that Microsoft's attitude is like ly to be "Don't bother me with the facts".[-X 
> Does running Windows on a virtual machine constitute running it on a different computer? Dunno, ask a lawyer.

Hmmm, problem is, what I'd have to pay the lawyer would be enough to buy not just several copies of Vista Ultimate but a few brand new computers as well :lol: 

Fitzy_oz said:
> Is there any software in particular that you absolutely must have XP for?
Yes, Skype. This just does not work well in Ubuntu in my experience.

---

### Post by CompShrink on 2007-03-02
Skype through WINE or native linux skype? What problems exactly are you having? If that's really the only thing holding you to Windows, it seems a little troubleshoooting will let you be free...

---

### Post by PaulFXH on 2007-03-04
Note that I'm taking about SkypeOut or pc-to-phone. I have no problem using Skype for pc-2-pc calls even in Ubuntu.
If you have any thoughts on how I can more reliably make SkypeOut calls from Linux I'd love to hear them.
However, although Ubuntu is my preferred OS, I have no particular desire to shut myself off completely from Windows. There's an awful lot of good stuff in there. Additionally, I use VMware which allows me to have a running version of WinXP right there in my Ubuntu tray (at the cost of 5-15% cpu usage) and this sure beats dual booting.

---

### Post by bravemosquito on 2007-03-04
> **PaulFXH said:**
> Additionally, I use VMware which allows me to have a running version of WinXP right there in my Ubuntu tray (at the cost of 5-15% cpu usage) and this sure beats dual booting.

/semi-offtopic
And the computer configuration is... ? Whether this scenario works sufficiently fast on Sempron 2600+/3000+ cpus ?

---

### Post by PaulFXH on 2007-03-04
> And the computer configuration is... ?

My computer really is no great shakes (nearly 5-y-o, 2.58GHz CPU, 1024 MB RAM) but the virtual machine (I use VMPlayer which is available in Synaptic) works well.
The downside is that the VM only "sees" a maximum of two usb ports, can handle less than the maximum memory, uses only one of my two optical drives and has a default graphics card memory of 16 MB. (Oh yeah, and it can't handle usb2.0; only usb 1.1)
But, you can call up Windows (or any of a whole range of other OSes) in microseconds rather than the 3-4 minutes need for a reboot. For run of the mill stuff, I don't see any major speed problems.
More details on what to do are [here]("http://www.ubuntuforums.org/showthread.php?t=342631&highlight=vmware-player+howto").

---

### Post by t94xr on 2007-03-04
Windows XP is legal to run within a virtualistation software like vmware and such

Due to the popularity of it, Micrsoft have decided they would prefer users their operating system as a main OS and not under any virtualisation software..
They sneaked it into the EULA of Vista RC2 commenting that you agree not to run vista under any virtualisation system or method or something. But what do ya know, VMare.com are still running?

So who gonna listen to it.
Most of wat people do already with modding and customising XP is techwnicially considered illegal under the EULA anyway and its not like its a hugely enforced thing.
there is alot of "illegal" things you can do with vista and M$ wont sue you mainy due to the cause of cost. Why sue for doing this, if they do they'll have to sue everyone else = $$$ and its not like they'll win alot.

---

### Post by PaulFXH on 2007-03-04
Not sure exactly what is your message here but I posted my concerns about the legality of running WinXP as a VM guest in Ubuntu host in the VMTN (VMware Technology Network) forum. Their position is that a genuine licensed copy of WinXP can be used legally either as a physical OS or as a VM on one computer but not both at the same time.
As a result, I have stopped using the physical OS although I must admit that having to re-activate the OS every time I moved from the VM to the physical OS was another motivator.

OTOH, it's a little more difficult to side with Microsoft's position from a moral standpoint.  I use my home computer solely for fun, nothing else. Nobody and nothing are going to be harmed if I use a Windows product as a virtual machine on my home computer. Neither are Microsoft going to suffer a loss in earnings because of this.
Indeed, it could be argued that they may actually gain something. Since I got involved in Linux about one year ago, I had almost stopped using Windows. A major reason for this was the inconvenience of rebooting to switch OS. However, now that I have the VM WinXP just a few mouse-clicks away, I am much more inclined to switch over to WinXP now and again.
So is it likely that the world would be a better place if MS were to sue home users running their OSes as VMs?

---

### Post by Kratos on 2007-03-04
The key to the whole Microsoft Activation gauntlet is to simply BS your way through. There have been countless times that I've had to reinstall Windows due to a partition mistake, or simply because it didn't work. I even used my OEM copy to reinstall a friend's PC, but used their COA to activate it. Every time I've had to call Microsoft, I dare to venture as far as to say that it's a surprise as to how easy it is sometimes. I even managed to get a new COA for Halo: Combat Evolved, after my younger brother lost the original envelope it came in. (After reading off a product number.)

Don't be scared by over-the-phone activation, most tines they'll only venture as far as to ask if the OS has been installed on any other machines. Just answer 'no', and you're safe.

---

### Post by PaulFXH on 2007-03-04
My fear is more to do with the actual NUMBER of times that MS are prepared to contiue to activate my OS by phone.
As things stand, every single time now that I want to boot to the physical OS, I need to call MS to activate which take sabout 10 minutes.
Are they really likely to unconcernedly continue to re-activate my OS on what could be a daily basis for the foreseeable future?

---

### Post by jesus5511 on 2007-03-04
The only people that should be buying Vista are 40-50 year old mothers who don't know any better, I mean why? Am I missing something? Is their some reason to spend 100+ dollars on a new operating system when one you already have works completely fine?

---

### Post by jamyskis on 2007-03-05
It would only take one refusal from Microsoft to activate a perfectly legit copy of WinXP or Vista before a class action lawsuit is brought against them and their entire legally dubious licensing scheme is brought to its knees. That's why the system seems rather harsh on the outside, but when you actually deal with it, it's a pain in the ***, but they'll never turn you down.

If they do, they know they're only encouraging lawsuits and legitimising activation cracks.

---

### Post by igknighted on 2007-03-05
> **jesus5511 said:**
> The only people that should be buying Vista are 40-50 year old mothers who don't know any better, I mean why? Am I missing something? Is their some reason to spend 100+ dollars on a new operating system when one you already have works completely fine?

I just built a PC last week, if I was going to use windows I certainly would have used Vista.  For roughly the same price I can get an OEM Vista Home Premium or an OEM XP Pro disk... and I hate XP, so Vista it would be.  However, I have no plans of running window on my new box, so sorry bill.  Even Ultimate is under $200 for OEM versions on newegg.  This enormous price jump from XP has certainly turned out to be quite mythical.

---

### Post by vinboy on 2007-03-05
I don't see any problem though.
It's not like you're going to get caught doing it.

Remember, you're not killing people/selling drugs here.
the police won't go after you.

if you ever get caught, just tell the judge that you do not understand what the EULA is saying/the EULA is too long to read, u'll get short sighted if you manage to read the whole thing.

---

### Post by PaulFXH on 2007-03-05
While I am quite unconcerned about the possibility of life imprisonment together with confiscation of all goods for this heinous crime, I really do have a hard time accepting the Microsoft argument.
So, while I paid more than &#8364;2000 for my computer together with a fully licensed version of Windows XP, it seems they take exception to people like me using the same OS on the virtual computer I downloaded for free.
This really does seem like hogwash to me.
Is there anybody who is not a Microsoft employee who can accept this stance of theirs?
If so, can you please explain this to me in layman's terms?

---

