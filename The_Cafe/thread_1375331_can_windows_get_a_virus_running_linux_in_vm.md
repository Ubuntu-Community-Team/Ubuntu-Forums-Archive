---
title: "can windows get a virus running linux in vm?"
date: 2010-01-07
forum: The Cafe
---

### Post by mamamia88 on 2010-01-07
just wondering if my windows install is safe if i run ubuntu in virtualbox?  got tired of booting my computer over and over again so decided to use ubuntu in virtualbox instead of a separate partition and just love how well seamless mode works

---

### Post by NoaHall on 2010-01-07
Yes. But not from the GNU/Linux guest. The Windows host can still get a virus.

---

### Post by mamamia88 on 2010-01-07
ah good to know then think this setup will work great for me.  dedicated ubuntu 512mb ram and it doesn't even seem to slow down my windows partition.  so i can get the best of both worlds without ever rebooting great

---

### Post by speedwell68 on 2010-01-07
I have been known to install malware and all sorts of other nasties on Windows in VirtualBox, normally when a friend has got something and wants to know how to get shot of it.  I have W7 in Virtualbox and I installed a whole host of nasties on it.  Just to prove a friend wrong, as a store muppet in PC World had told him that W7 was immune to all existing malicious software.:lol:

---

### Post by NoaHall on 2010-01-07
> **speedwell68 said:**
> I have been known to install malware and all sorts of other nasties on Windows in VirtualBox, normally when a friend has got something and wants to know how to get shot of it.  I have W7 in Virtualbox and I installed a whole host of nasties on it.  Just to prove a friend wrong, as a store muppet in PC World had told him that W7 was immune to all existing malicious software.:lol:

People who work in PC World clearly have no knowledge of anything to do with PC's whatso ever.

---

### Post by pwnst*r on 2010-01-07
> **speedwell68 said:**
> I have been known to install malware and all sorts of other nasties on Windows in VirtualBox, normally when a friend has got something and wants to know how to get shot of it.  I have W7 in Virtualbox and I installed a whole host of nasties on it.  Just to prove a friend wrong, as a store muppet in PC World had told him that W7 was immune to all existing malicious software.:lol:

I'm glad I don't have this "PC World" near me.

---

### Post by NoaHall on 2010-01-07
> **pwnst*r said:**
> I'm glad I don't have this "PC World" near me.

Think of it of a UK-type Best Buy, but they have PC World's in the USA too, I think.

---

### Post by tacantara on 2010-01-07
> **pwnst*r said:**
> I'm glad I don't have this "PC World" near me.

That's right....instead, there's Best Buy ;)

---

### Post by staf0048 on 2010-01-07
> **mamamia88 said:**
> ah good to know then think this setup will work great for me. dedicated ubuntu 512mb ram and it doesn't even seem to slow down my windows partition. so i can get the best of both worlds without ever rebooting great


Just to be sure you understand.  If Ubuntu is run in a VM, it will not protect Windows from Windows viruses.

---

### Post by manosx on 2010-01-07
Yes.. Ubuntu is like any other software in the world in this point..

---

### Post by speedwell68 on 2010-01-08
> **pwnst*r said:**
> I'm glad I don't have this "PC World" near me.

Oh no they are mucho fun.:D  Over the recent festive period I bought myself an Archos player for which I needed a case.  I went into PC World to look at their MP3 cases, I found one I liked, but it had no price displayed.  So I took it over to the cash desk and asked how much it was, they guy scanned it and told me.  I then asked if it was compatible with Linux, he said he didn't know but he could find out.  They employ the people that aren't bright enough to work at McDonalds.

---

### Post by BFG on 2010-01-08
> **staf0048 said:**
> Just to be sure you understand.  If Ubuntu is run in a VM, it will not protect Windows from Windows viruses.

Perhaps an obvious point to mention too, is that if the windows OS gets a virus in the VM, it does not place Ubuntu at any risk. I.e. Ubuntu cannot become infected as a result.

---

### Post by xpod on 2010-01-08
> **mamamia88 said:**
> just wondering if my windows install is safe if i run ubuntu in virtualbox?  got tired of booting my computer over and over again so decided to use ubuntu in virtualbox instead of a separate partition and just love how well seamless mode works

If your forever wondering whether your Windows install is "safe" or not then it might be a better idea to install Ubuntu to your drive and stick Windows in the vm.
If anything does go wrong with your Windows vm then it`s quicker to replace an infected vm snapshot than it is to replace an infected drive installation.

---

### Post by Lord Stig on 2010-01-08
> **speedwell68 said:**
> Oh no they are mucho fun.:D  Over the recent festive period I bought myself an Archos player for which I needed a case.  I went into PC World to look at their MP3 cases, I found one I liked, but it had no price displayed.  So I took it over to the cash desk and asked how much it was, they guy scanned it and told me.  I then asked if it was compatible with Linux, he said he didn't know but he could find out.  They employ the people that aren't bright enough to work at McDonalds.
I'd like to say I'm deeply offended by your remarks about people who work at PC World...
Unfortunately, although I'd like to I can't, as I know it to be for the most part true - I used to work there (not as a sales bod).

The money is poor and technical knowledge isn't really important. Achieving margin targets was, though.

---

### Post by Nerd King on 2010-01-08
Never met anyone with a brain at PC World. They're special.

---

### Post by Techsnap on 2010-01-08
> I then asked if it was compatible with Linux, he said he didn't know but he could find out. They employ the people that aren't bright enough to work at McDonalds.

At least they're working! Seriously I wouldn't expect someone at the till to know what they're talking about anyway as it's not really in their job description to do so. Just like asking someone on the till in a supermarket how to cook the food that you purchase. I don't expect the people in PC World to know much about Linux either re: Linux Marketshare. 

> PC World had told him that W7 was immune to all existing malicious software.

Of course they would have, they're trying to sell a product. People make stuff up about Linux too you know when they try to "convert" people who really aren't interested about it.

---

### Post by RabbitWho on 2010-01-08
> **speedwell68 said:**
>   Just to prove a friend wrong, as a store muppet in PC World had told him that W7 was immune to all existing malicious software.:lol:

Jesus, that person is either silly or evil, the worrying thing is that if he's silly someone evil must have told him that at some point, do you think PC world are instructing their staff to do that? I wouldn't put it past them considering the problems members of my family have had with them in the past. 

I've also found they can be very rude to their customers (A friend of mine went in asking for something she didn't know the name of, trying to describe it,  and the woman bluntly told her no such thing existed and basically called her an idiot while I stood there trying to jump in on the conversation and explain what she was looking for once again.. instead of asking questions to figure out what the customer was looking for she just said ! "No! no! there's no such thing!" rolling her eyes )  and when I wrote to complain I didn't receive a response in any way shape or form. Sometimes people that know things about computers are worse... arrogant .. urrrgh

---

### Post by llawwehttam on 2010-01-08
> **NoaHall said:**
> People who work in PC World clearly have no knowledge of anything to do with PC's whatso ever.

For my own amusement I asked a PC world employee if they sold any computers with linux or without an OS. I was sharply informed by him that it is ILLEGAL to buy a computer without windows.

I almost laughed myself to death.

An apple employee also told me that Macs cannot get malicious software. I asked him why you can buy a mac antivirus then. He went to ask his manager.lol

---

### Post by staf0048 on 2010-01-08
> **llawwehttam said:**
> For my own amusement I asked a PC world employee if they sold any computers with linux or without an OS. I was sharply informed by him that it is ILLEGAL to buy a computer without windows.

I almost laughed myself to death.

An apple employee also told me that Macs cannot get malicious software. I asked him why you can buy a mac antivirus then. He went to ask his manager.lol

:lolflag:  That is just too funny!!

---

### Post by pwnst*r on 2010-01-08
> **RabbitWho said:**
> Jesus, that person is either silly or evil,

..or the story was slightly exaggerated. That happens around here.  A lot.

---

### Post by Marisa H on 2010-01-08
> **llawwehttam said:**
> For my own amusement I asked a PC world employee if they sold any computers with linux or without an OS. I was sharply informed by him that it is ILLEGAL to buy a computer without windows.

I almost laughed myself to death.

An apple employee also told me that Macs cannot get malicious software. I asked him why you can buy a mac antivirus then. He went to ask his manager.lol


[SIZE=5]lol[/SIZE] :lolflag:

---

### Post by MasterNetra on 2010-01-08
Install Ubuntu as Host OS and run Windows in VM.

---

### Post by marco123 on 2010-01-08
> **speedwell68 said:**
> I have been known to install malware and all sorts of other nasties on Windows in VirtualBox, normally when a friend has got something and wants to know how to get shot of it.  I have W7 in Virtualbox and I installed a whole host of nasties on it.  Just to prove a friend wrong, as a store muppet in PC World had told him that W7 was immune to all existing malicious software.:lol:

I had fun doing this a few months ago in the Security forum. [http://ubuntuforums.org/showthread.php?t=1100531](http://ubuntuforums.org/showthread.php?t=1100531)

It was actually pretty hard to do: I had to purposely seek out dodgey sites, click on popups and install/give permission to everything, and this was on XP!  It makes me wonder how some people even get these damn viruses in the first place??

Marco.

---

### Post by marco123 on 2010-01-08
> **MasterNetra said:**
> Install Ubuntu as Host OS and run Windows in VM.

I used to do that, but the only Windows program I like nowadays (Spotify) runs perfectly in Wine.

---

### Post by Icehuck on 2010-01-08
> **mamamia88 said:**
> just wondering if my windows install is safe if i run ubuntu in virtualbox?  got tired of booting my computer over and over again so decided to use ubuntu in virtualbox instead of a separate partition and just love how well seamless mode works


No, it is not safe run Ubuntu in a virtual machine. Once doing so you will find that Ubuntu will infest your Windows machine. Your wallpaper will turn red and slowly display messages talking about Soviet Russia. Your machine may also start to hold conversations with you about why capitalist pig dogs are bad.  If it ever says, "One day, I will rule Candyland with an iron fist." Then run away as fast as you can.

---

### Post by darco on 2010-01-08
> **MasterNetra said:**
> Install Ubuntu as Host OS and run Windows in VM.

In this scenario, can Windows pick up a virus in a virtual state?

---

### Post by NoaHall on 2010-01-08
> **darco said:**
> In this scenario, can Windows pick up a virus in a virtual state?

Yes, of course. It's a real Windows OS you're running.

---

### Post by forrestcupp on 2010-01-08
> **NoaHall said:**
> Yes, of course. It's a real Windows OS you're running.

> **NoaHall said:**
> Yes. But not from the GNU/Linux guest. The Windows host can still get a virus.

Your two posts kind of contradict each other.

If you're running Ubuntu as the host and Windows as a guest in a virtual machine, it's still possible to get a virus in your virtual Windows.  Windows in a vm has a straight shot to your network just like a regular install of Windows does.  The good thing is that it will be confined to your virtual machine and it won't affect Ubuntu or anything else at all.

There have been people who have even gotten a virus by installing something malicious with Wine.  But it is confined to Wine and very easily fixed.

---

### Post by NoaHall on 2010-01-08
> **forrestcupp said:**
> Your two posts kind of contradict each other.

If you're running Ubuntu as the host and Windows as a guest in a virtual machine, it's still possible to get a virus in your virtual Windows.  Windows in a vm has a straight shot to your network just like a regular install of Windows does.  The good thing is that it will be confined to your virtual machine and it won't affect Ubuntu or anything else at all.

There have been people who have even gotten a virus by installing something malicious with Wine.  But it is confined to Wine and very easily fixed.

That's what I said. A virtual Windows is still windows.

---

### Post by forrestcupp on 2010-01-08
> **NoaHall said:**
> That's what I said. A virtual Windows is still windows.

Sorry.  I was reading your first post too fast and I misread it.  I thought you originally were saying not if Ubuntu is the host, but you said not from an Ubuntu guest.

---

