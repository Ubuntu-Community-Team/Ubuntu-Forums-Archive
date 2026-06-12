---
title: "World of Warcraft? Other Sys76 Computer Probs?"
date: 2008-04-24
forum: System76 Support
---

### Post by iheartubuntu on 2008-04-24
My sister bought a Serval Performance, model number is either FL92 or SERP4.

She (we) cant get World of Warcraft to install on this system. She doesnt know anything about linux, I dont know a whole lot, but I have Ubuntu installed on several computers at my work and also at home and can usually get any problems resolved with help from the forums here.

That said, I have installed WoW for my sister on two other ubuntu linux computers without a problem. They work great. No problems. I dont play WoW, but have installed it to prove it works on linux. the WoW community here in the forums are great with any help, but I feel this might be a System76 problem so I thought I would post it here.

If anyone has gotten WoW to work on their Serval Performance, please post here how you did so :) Thanks.

I have followed the 'WoW on Ubuntu' guidelines [here]("https://help.ubuntu.com/community/WorldofWarcraft"), and the normal procedure is to install Wine, then copy the files from the WoW discs to a folder on the Ubuntu desktop, then run the install file in the folder and the game will install. Not on this new computer. While installing, we get an error message saying it is either a media problem or a drive problem (error code 38 ).

I have also installed the DLL files listed in the troubleshooting guide [here]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting"), but that didnt help any.

As one of the last resorts, I downloaded the 3GB game from the internet (via the WoW Ubuntu forum link above) and the computer froze at about 2/3s of the way through. Any opportunity to restart the download crashes the whole computer.

As a last resort, I decided to put in my Ubuntu 7.10 official Canonical OS disc and reinstall the OS on this computer and poof. It wont install on this System76 computer. Ive tried to reinstall the OS in regular mode, safe mode, and OEM mode all with no luck (the LiveCD crashes). This is the first time Ive come across these types of bugs both with a LiveCD and with trying to install WoW.

My sister has high hopes with this computer especially having 4GB of mem and 512mb nVidia video card on a laptop. Any help would be appreciated to get WoW working on this system.

I have yet to try a 7.10 alt disc install. I will wait to hear from anyone from System76 before proceeding any further.

Thanks for any help!

---

### Post by iheartubuntu on 2008-04-24
The WoW installer keeps fouling up in the same place, when trying to unpack "terrain.MPQ" file. A simple Google search on "terrain.MPQ" brings up the discussion on the WoW forums and Blizzard Entertainment has linked this error while installing to a memory problem. From [here]("http://forums.worldofwarcraft.com/thread.html?topicId=101821095&sid=1") I quote:
> 
One of the main causes for installation and patching failures is mismatched or faulty RAM.

The solution is to take out some of the RAM and see if the installation works fine. Gee, that doesnt sound too good regarding the memory on this brand new computer. I'll try the work around and see what I come up with.

---

### Post by newsun on 2008-04-25
a simple solution if you have a removeable harddrive is to just copy a working install to the location you wish to run it from. Then just play away. World of Warcraft does not have any need to register with the os and as such can be played as a portable app ;)

I personally am hoping I can get my x3100 vid card to work with wow in 8.04 as it did not in 7.10.

---

### Post by iheartubuntu on 2008-04-26
> **newsun said:**
> a simple solution if you have a removeable harddrive is to just copy a working install to the location you wish to run it from. Then just play away. World of Warcraft does not have any need to register with the os and as such can be played as a portable app ;)

I personally am hoping I can get my x3100 vid card to work with wow in 8.04 as it did not in 7.10.

I actually got it working using that method. I copied the game over from a working system, installed it on this new one and it works fine. The only prob is with the RAM chips now.

On a side note, I did get WoW to work with an x3100 vide card. Read about it here...

[http://ubuntuforums.org/showthread.php?p=4685770#post4685770](http://ubuntuforums.org/showthread.php?p=4685770#post4685770)

The problem was after finally getting the game to work, the slowness and lag was horrible. Unplayable really. That was on a brand new DELL laptop with 4GB ram too. My sister ended up sending that DELL back for a refund and she went with this System76. It is an AWESOME computer. Everything works great on it (sans the ram issue which I feel will get resolved).

Tech support with Sys76 is awesome as well. Im sure they will do great business in the future.

---

### Post by Trance56k on 2008-04-30
Try installing WOW with either Crossover or Cedega. I believe they both have free trials.

---

### Post by glacialfury on 2008-05-07
I also had problems installing WoW on the brand new serval performance.  I did not have any problems installing it in the same way on my desktop.  I'll try reinstalling again in the next few days and post the actual errors.

---

