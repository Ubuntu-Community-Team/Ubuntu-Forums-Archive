---
title: "Why oh why virtual ?"
date: 2010-03-12
forum: The Cafe
---

### Post by MooPi on 2010-03-12
I've installed Virtualbox and successfully load XP pro. But why do this when this edition of a virtual system is handicaped. I can't play 3d games, skype doen't work and webcam . I did get StartCraft to function but not exactly a triumph. What does everyone use Virtualbox for ?

---

### Post by Post Monkeh on 2010-03-12
are you using the virtualbox from the repo or the one from their website?

the one from the repo is the open source edition which is pretty restricted.

3d functions, especially on directx games, are fairly limited i think.

you'd be better posting a help thread somewhere to get advice for setting it up.


i use it for nokia pc suite and not much else really  in terms of windows


i do use it to try various linux distros though

---

### Post by MooPi on 2010-03-12
Now that I can see as a viable situation and will try other distro's for testing. I must say though it was fun playing StarCraft last night :oops:
I'm using the Virtualbox from the Ubuntu repository with 3d enabled.

---

### Post by Bachstelze on 2010-03-12
I use VirtualBox for package building and development when the target system is different from the one I use at the moment, and as a TFTP/DHCP server for PXE booting because having it always on disturbs the network.

Hint: not everyone plays 3D games or uses Skype.

---

### Post by MooPi on 2010-03-12
> Hint: not everyone plays 3D games or uses Skype.Yes I know but for me it's PC, personal computer for fun and a little work. My job is mundane but pays very well so the computer and some golf are my entertainment and hobby.

---

### Post by gradinaruvasile on 2010-03-12
> **MooPi said:**
> I've installed Virtualbox and successfully load XP pro. But why do this when this edition of a virtual system is handicaped. I can't play 3d games, skype doen't work and webcam . I did get StartCraft to function but not exactly a triumph. What does everyone use Virtualbox for ?

There is Skype for Linux that works perfectly.

About the 3D:
It will not work right, it can be used by a handful of applications. At least in its current version. 
The reason is that most games use Directx (that is the Microsoft 3d API and exists only Windows). This API is only partway implemented and its in experimental state. So little chance to make newer games work for the time being. And i guess that there will be quite some time until it will work well. Im also curious also where VirtualBox will go with Oracle in charge...

OpenGL (that is a cross platform and open 3D API, its *the* Linux 3D base) is supported better because its an open standard and exists on every platform - hence games that can use OpenGL (mostly older ones, few recent games) are better supported - e.g. Half Life 1 works quite fast.

I use VirtualBox for applications that run only under Windows such as the e-banking app that works only with Internet Explorer and couldnt make it work with wine. 
PS. When i killed my Windows installation on my home desktop i said bye bye to hardcore gaming and never looked back. I use some FPS's (online) once in a while that exist under Linux too. And some Wine based stuff.

---

### Post by CharlesA on 2010-03-12
VMware would probably handle Graphics better, since I believe it has support for DirectX 9 (or 10).

---

### Post by sandyd on 2010-03-12
> **CharlesA said:**
> VMware would probably handle Graphics better, since I believe it has support for DirectX 9 (or 10).

it has support, but it runs like crap. which is why starcraft 2 doesnt work on there even though I set it to 800 x 600 resolution.....

---

### Post by themarker0 on 2010-03-12
I use virtual box to test anti viruses. So i'll set up various xp installs and install trial antui viruses and see which one is the most secure. For anyone wondering it is usually kaspersky.

---

### Post by samalex on 2010-03-12
> **MooPi said:**
> I've installed Virtualbox and successfully load XP pro. But why do this when this edition of a virtual system is handicaped. I can't play 3d games, skype doen't work and webcam . I did get StartCraft to function but not exactly a triumph. What does everyone use Virtualbox for ?

There's more to life then gaming :)  Being a Microsoft DBA I use Win XP Pro in VirtualBox so I can have SQL Server Management Studio 2008 and Visual Studio 2008 on my laptop.  Also though I use Skype on Linux (which works quite well) my webcam does work in VirtualBox, though you can't use the 'Open' version since it won't connect to any USB devices.

I also use it for iTunes, TomTom HOME to update my GPS, and some other apps that won't play well in Wine on Linux.  So I don't use it alot, but for the times I need it it's good to have it.  If I were a gamer though, I'd only run games native to Linux, which there are LOTS of them out there.

Take care...

Sam

---

### Post by MooPi on 2010-03-12
Well I just found a good use for it. Silverlight ! I missed so much of the olympic coverage because I didn't have silverlight. Hmm very good Thanks to everyone responding. Your giving me reason to continue with Virtualbox. The Tom tom ability alone should warrant usage.

---

### Post by Groucho Marxist on 2010-03-12
> **MooPi said:**
> I've installed Virtualbox and successfully load XP pro. But why do this when this edition of a virtual system is handicaped. I can't play 3d games, skype doen't work and webcam . I did get StartCraft to function but not exactly a triumph. What does everyone use Virtualbox for ?

I use it for Adobe Creative Suite 4 Design Premium, Sid Meier's Civilization III: Complete Edition and other programs. 

I agree with earlier posters in that it is best to use the versions offered on Virtualbox's website, as the OSE can be frustrating.

---

### Post by Firestem4 on 2010-03-12
Virtualbox is great at many things. Gaming is not one of them however. There are a few reasons for it. Performance is an issue because you're already sharing resources with your host computer. The other issue is that VirtualBox emulates hardware resources for the virtual enviroment. Driver support is lacking in some areas (mainly graphics).

I have a desktop system with an ATI X1950 graphics card. My Host machine sees this only. To VirtualBox I haven an InnoTek VGA Adapter. (InnoTek is the company that initially developed VBox before Sun acquired them).

Drivers are king when it comes to graphics. There are no ati drivers or nvidia drivers available for your card in a virtual machine.

As to answer one of your questions OP. Virtual Machines are damn useful for so many things. Graphics not being one of them but instead they're useful for letting alternative OS users run Windows programs that they need (Quickbooks, Photoshop, MS Office, etc). In a professional enviroment too. They're also great for testing and development and evne security and forensics work.

---

### Post by juancarlospaco on 2010-03-12
*To test legacy OS, like XP or 7*

---

### Post by samh785 on 2010-03-12
> **gradinaruvasile said:**
> There is Skype for Linux that works perfectly.
Yup. When I installed the latest version, I didn't have to tweak *anything* to get it working. :D Large improvement over the last year or so.

---

### Post by swoll1980 on 2010-03-12
Virtual Machines are not for 3d gaming. The 3d capabilities are for  3d compositing desktops like Compiz, and Aero. Not that you can't play games on it, but don't expect a good experience. If you use the OSE version from the repo, you wont have USB support.

---

### Post by MooPi on 2010-03-12
My computer is a first generation quad from AMD and it handles the virtual environment well. I just installed anti-virus, as I was holding off because I wanted to make sure it wouldn't bog it down. Everything fine and some so far. I may bump the ram to 4 gig if I really want to stretch the envelope a bit.

---

### Post by pricetech on 2010-03-12
I use Virtual Box from the repos with XP installed for the few things I can't do, for whatever reason, under Ubuntu.

By the way, your new avatar looks like a hippy longhorn.  (or longhorn hippy as the case may be)

---

### Post by MooPi on 2010-03-12
I plan on changing my avatar to fit my mood. I've got a couple to mix in for special moods. ;)

---

### Post by pricetech on 2010-03-12
> **themarker0 said:**
> I use virtual box to test anti viruses.
<snip>
For anyone wondering it is usually kaspersky.

Thanks.  I'll make a note of that.

---

### Post by Post Monkeh on 2010-03-12
the one in the repos doesn't support usb passthrough (ie if you connect a usb device to your machine you can't use it in virtualbox) that's the main reason i use the proprietary version

---

### Post by doas777 on 2010-03-12
> **MooPi said:**
> I've installed Virtualbox and successfully load XP pro. But why do this when this edition of a virtual system is handicaped. I can't play 3d games, skype doen't work and webcam . I did get StartCraft to function but not exactly a triumph. What does everyone use Virtualbox for ?

I use a virtual XP instance to config my router. the interface software provided by the manufacturer requires java 1.4.2 or earlier (1.3 - 1.4 only), and since I write some java code in 1.5, i can't have 1.4 only apps on any box I would do dev on. 

I dual boot for games though. your right, they don;t play right. I did have some luck playing light or medium games via vmWare player, but it only worked with teh player version included in the trial of workstation full. the player keeps working after the workstation trial license expires though.

---

### Post by Firestem4 on 2010-03-12
> **MooPi said:**
> My computer is a first generation quad from AMD and it handles the virtual environment well. I just installed anti-virus, as I was holding off because I wanted to make sure it wouldn't bog it down. Everything fine and some so far. I may bump the ram to 4 gig if I really want to stretch the envelope a bit.

Just remember you're sharing resources with your host system. If you have only 4gb of RAM total and you allow the VM to access 4GB you can potentially have a lot of competition for your memory, especially if you start using memory intensive programs inside of the VM.

---

### Post by blueshiftoverwatch on 2010-03-12
According to VirtualBox's [website]("http://www.virtualbox.org/wiki/Editions") the only things that are not included in the OSE are: remote desktoping, USB support, and USB over remote desktop. None of those have anything to do with 3D graphics.

As far as I know, no VM is particularly good at handing 3D games. They're not really designed for that anyway. That's where projects like WINE come into play.

---

### Post by twisted_steel on 2010-03-12
VMware Workstation is supposed to be able to do some 3D graphics.  There is HalfLife 2 running in the screenshot on this page: [http://www.vmware.com/products/workstation/new.html](http://www.vmware.com/products/workstation/new.html).  It is not free.

---

### Post by wgarider on 2010-03-13
*What does everyone use Virtualbox for ?*
I have a replica of the data center infrastructure (from where I work) setup - three Windows servers (DNS, Active Directory, etc), a couple of Windows clients, 2 Linux servers, 3 or 4 Ubuntu VM"s of various flavors and one running a NetApp filer simulator.....

---

### Post by chriswyatt on 2010-03-13
VirtualBox is great and it's a lot better than I expected it to be.  When I first tried it I thought it was gonna run like a slug but it's actually reasonably snappy.

---

