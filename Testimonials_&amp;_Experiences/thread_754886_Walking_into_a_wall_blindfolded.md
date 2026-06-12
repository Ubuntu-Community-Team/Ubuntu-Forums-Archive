---
title: "Walking into a wall blindfolded"
date: 2008-04-14
forum: Testimonials &amp; Experiences
---

### Post by pcjunkie on 2008-04-14
Hello all. 

I am glad to say I have stopped using windows and feel rather good about it. Its like walking outside into a forest and breathing crisp air. I am using it to code websites and perform graphic editing. I have a nice theme I patched from previous art  and I honestly enjoy working with Ubuntu. That aside, I have some points I would like people, the devs to consider. 

I recently tried to set up a server at work, a small importing business, to perform a few simple tasks. I wanted it to keep client information and accounts from an MYOB data file. Also it should mirror that data in a RAID array. I wanted this to in effect keep 3 copies on 3 disks at all times. The plan was to backup and serve MYOB data (as txt file) deployed over 5 PC's on the servers main drive then use keep to automatically back it up onto another drive (and partition) that was being mirrored. 

The problem of setting up the system started about the time I discovered RAID as in Nvidia Soft RAID via hardware was not supported. I had to revert to DMRaid and that was to say the least, like walking on glass. I followed to letter the Wiki and many posts but it never worked. In fact at one point Ubuntu stopped seeing the drive/s altogether. To add to that, it seems Gparted has big problems with Big drives and took 10 minutes a go just to find them. 

After spending half a day or more on this I gave that away in the hope I could work it out at a later time and deploy it properly. 

I then tried to use Samba (non Gui) to configure sharing but the instructions again did not work as to the letter, I then found posts on Gsambad and tried that too only to be confronted with information requests the average punter could not possibly understand. After spending some time researching samba and reading many posts, most negative, I gave up on using anything Linux as a network drive, file share, backup server and mail hub (thus backing up emails and their important information too).

To be honest, it was bloody awful and I felt totally useless. I am not a programmer or network guru though I do have a website, have made many more and can correctly format a properly rendering CSS dynamic website. So in that sense I am not unfamiliar with the way computers, servers, client side code and scripting goes. But this was honesty so hard to set up it dumbfounded me. 

The place is small, I am doing the best I can do to make sure the IT network performs soundly and provide, script and construct a working website with which 2000+ items of stock including data and images is compiled and sorted with a Hosted LAMP provider. Its not scary to me at all, In fact I enjoy it but I was hoping I could save them the needles expense of upgrading to Vista and being forced to purchase Office and yet again another year of AV, MYOB and so on. Its actually A big budget, over $12,000 dollars in fact I could save them just by using Ubuntu. I also could save the Hardware that actually is not that old, All of it uses DDR so its less than 5 years old and quite capable but Vista and the need for performance in a workplace will render these landfill. The sad truth is I could not get RAID, SAMBA, and a few other things to work correctly or at all though at home here I can take my time and try again in future.

I have put XP in place and it took about an hour to do all that. I am using Casper to provide a full Hard disk backup automatically and the Mother board is an ASUS nvidia with RAID 1 working soundly. 

I only had to set up the network share and the folders to share, Casper and partitions to supprt the framework I had in mind. Everything is doing exactly what I wanted. 3 copies of everything. Images, server backups, MYOB backups and client files. I was hoping linux could do that, but its tools are too advanced for a beginner to understand. I have commented on a few forums about this and the relies have been, well, Indignant. I stated I am not a programmer yet to be told I am ignorant, just for attempting this?

Well yes I am, but should I need to be a Linux guru just to set up samba? How hard should it need be?

IP = 192.168.0.1 (the hub)
share name is workgroup
no logins required please, this is software, not humans doing the file sharing. 

Is that so hard?

I have to state that small business would love to employ a full time IT guy, especially when you consider that the Website alone is massive, The great news for me is thaty their budgets could never handle a $70 an hour position. I am earning peanuts actually but its a learning thing for me and an excuse to go back to Uni - at 37....
I can see why in some respects small Buisiness has not picked up the ball and run with it considering the cost saving they can make and the performance gain plus productivity that goes with it. The sheer scope of Linux and some of its applications are beyond a novice like me at times and for the average punter, they will pay the dosh to save the hassle. Its only a few simple things preventing the massive and buldging SOHO situation from flooding over to Linux, set up configurations on common networked small offices and shares are problematic and bulky. For me at least, when I can I am still reading and experimenting, 6 weeks on.  

For the website I am using Joomla! and other Open Source products to fill the void of buggy, limiting expensive proprietary software and I have to say it exceeds and excels over anything a company with a handful of programmers can spit out. (Like bloat ware M$). Again its principals are modular and expandable and simple as ordering Pizza to set up and work with. and Joomla! does that to the letter. I can see why Open source will inspire more creativity and leave the others behind and will do so with ease. The internet is not that old in real terms, neither is open source but already it has surpassed anything else it competes with. 

I am glad I started Using Ubuntu. 

I love my PC now more than ever. 
Cheers

---

### Post by ukripper on 2008-04-14
I  used this guide to have my RAID 1 working perfectly.
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

may help.

---

### Post by bradwilliamson on 2008-04-14
Sorry your experience was so bad! And I won't bust your chops with the typical rants, that doesn't help anybody.

I will note one thing that is a common point of failure in things such as you describe:

Software RAID or Onboard RAID

Although your ship has already sailed, you would have been *much* better served spending part of the 12k on a 3Ware HARDWARE RAID controller. 

Onboard desktop RAID's are *horrible*, ranking just slightly above WinModems in terms of compatibility. Usually they are software based anyway, and implement the bare minimum in hardware. If they work, good for you, if they don't, well, you've seen what happens when it doesn't.

Software RAID works "better" but it's still a huge pain to recover. I would rather sync things to other computers than do software RAID on one computer.

A 3Ware hardware RAID controller would have removed nearly all your setup woes (for disks anyway).

As far as Samba goes, yes it's a little odd to set up sometimes, but for simple systems like yours, I would recommend that you install Webmin and use that for setting everything up. It puts a nice Web interface on nearly everything.

Please be careful sharing things with an XP box, the 10 user limit will bite you one day and you will have nowhere to go. XP is *not* a great file server in any way.

Don't give up on Linux! You have a great attitude towards this failure, and you'll be much better served in the long run by switching over, but do it at your own pace. It does all work, or there wouldn't be this many people switching over. 

Side note: I wish the HARDWARE VENDORS would pick up the clue phone! Everybody dances around that issue like the hardware comes from Mars and there's nothing we can do about it. Hardware comes from hardware vendors. Hardware vendors who do not support Linux should be voted against with our wallets AND told that we are not buying their specific product XYZ BECAUSE it does not support Linux and/or they do not provide Linux drivers (open or closed source, matters not to *me*, but provide the darn drivers!). They need to learn, and bite Bill Gates' hand once in a while. Others can feed them too if they play nice.

---

### Post by pcjunkie on 2008-04-15
The 3ware raid controller would be nice but I think my boss/s would turn white if I even looked like I was going to ask for money. :)

I managed to secure a PC to experiment with so I will gladly continue with Ubuntu and configuring it. I am in no rush as I need to get the website running before anything else. Xp will hold the fort for now until the operator knows what he is doing. After that, all things told these guys have 2 to 3 years to figure out if they want to become people of the world or Microsoft pawns...

Thankyou for your suggestions I took at look at the Debian RAID version. I will try it soon.

---

### Post by hyper_ch on 2008-04-15
well, samba is used for sharing with windows computers... if you have none, use NSF (or even sshfs)

---

### Post by pcjunkie on 2008-04-15
Currently the network is XP with 1 NT 4 (yeah!) working as a server. Not the best and mostly its used for CRM accounting Office and Email. That's the main function. I was hoping Ubuntu could quickly fill that position with ease and it still could, I have to network Windows before Ubuntu will be accepted. 

They are not young people and PC skills are lacking. (eg you can copy using CTl + C, You can?) and even getting them to use Mozilla mail and web has been a series of complaints. So changing to any OS Vista or Ubuntu will be horrendous but, in my mind they are better off with Ubuntu. If I can back this network up soundly (hot swapping disks and shadow copy keeping 3 copies at all times) and keep the documentation under 20 pages (currently that's not going to happen) then I can do it. I have to be aware that I might not be here after I finish the Job so everything must be complete with full instructions. 

Care for a challenge? That's what I have to work with.

---

### Post by rustybronco on 2008-04-15
> **pcjunkie said:**
> 
After spending half a day or more on this I gave that away in the hope I could work it out at a later time and deploy it properly. 

> **pcjunkie said:**
> Its actually A big budget, over $12,000 dollars in fact I could save them just by using Ubuntu. I also could save the Hardware that actually is not that old, All of it uses DDR so its less than 5 years old and quite capable but Vista and the need for performance in a workplace will render these landfill. 
I can see why in some respects small Buisiness has not picked up the ball and run with it considering the cost saving they can make and the performance gain plus productivity that goes with it. 

> **bradwilliamson said:**
> I will note one thing that is a common point of failure in things such as you describe:

Software RAID or Onboard RAID

Although your ship has already sailed, you would have been *much* better served spending part of the 12k on a 3Ware HARDWARE RAID controller. 

Onboard desktop RAID's are *horrible*, ranking just slightly above WinModems in terms of compatibility. Usually they are software based anyway, and implement the bare minimum in hardware. If they work, good for you, if they don't, well, you've seen what happens when it doesn't.

Software RAID works "better" but it's still a huge pain to recover. I would rather sync things to other computers than do software RAID on one computer.



> **pcjunkie said:**
> The 3ware raid controller would be nice but I think my boss/s would turn white if I even looked like I was going to ask for money. :)

Thank you for your suggestions I took at look at the Debian RAID version. I will try it soon.The company has a potential of saving thousands of dollars and won't get a proper raid card? penny wise-pound foolish. 
save the time/headaches and get one, [http://ubuntuforums.org/showpost.php?p=4248386&postcount=31](http://ubuntuforums.org/showpost.php?p=4248386&postcount=31) > or just say ***** it and get a smart array controller ...
plus it will go a long way keeping the documentation pages low.

---

### Post by pcjunkie on 2008-04-25
Thnx for the reply


lol These (bastards, excuse me) are so tight they were not willing to provide me with a suitable computer to produce multimedia on. (So I bought my own) They are sloppy with priorities and fail to see my reasoning at all. I can't even get them to go halfway. 

That's the life of a webcoder. Pain in the rear people who want everything but refuse to pay for it. 

If I am to get a reasonable reference from them, I have to be a network admin, and IT expert and a webdesigner that can pop out anything they can dream up in php, java and CSS. When Xp had its hard drive wiped (an attachment was opened in Outlook 2000.) I was the reason it happened. yup....

Honestly, driving a truck is easier and in my case. Pays better.

---

