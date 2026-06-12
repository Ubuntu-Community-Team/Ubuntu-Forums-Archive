---
title: "Verizon FiOS w/Ubuntu?"
date: 2006-04-16
forum: The Cafe
---

### Post by Aviatrixie on 2006-04-16
Hi fellow Ubuntuites,

   I received a call from Verizon a couple of days ago informing me that FiOS was now available to me and I could upgrade at no additional charge. As I'm over 14,000' from the nearest CO (COVAD) I'm limited to 1.5 M down and about 340 k up on regular DSL. This would move me to 5 Meg down and I forget the up-put. For an additional $10/mo. I can get 15 Meg down and 2 meg up.  As it sounded too good to pass up I signed up and to my surprise the tech will be here on the 19th to hook me up.

 Anyway... I was sitting around tonight and got to thinking... will my Breezy even work with this? I'm building up to a bit of a rant... which is why I posted here. When I decided to finally go from dial-up to DSL it was because I was fed up with Windows and wanted to explore Linux. I've used computers since the very early 80's and have owned TI-99's, CPM's, C-64's Atari 8 bits, Mac's,
and every permutation of Windows. 

  When I first called Verizon to do my upgrade install I asked them if their DSL would work with Linux. They told me "no, I need Windows or Mac OS to install". I asked them if there was a work-around, and she told me "yes".

  That's about as far as the conversation went. I loaded an old copy of 98se and got online, set up my DSL, yanked my 98se HD and installed a new drive and have only used Breezy since.

I did learn that Linux doesn't care so much about the modem used but does like HTCP or something like that. (Damn Small Linux, Puppy, Slax, Mepis, literally every distro I've used finds my connection with NO fiddling!)

   So... next Wednesday the install person will arrive. I will have my old 98se HD ready to install his windows code and will tell him when he leaves that I will pull the windows drive and reinstall my beloved Ubuntu drive. My big question is... will my wonderful Breezy Badger work with my new Fiber Optics?

:::Rant over:::

So... Will my plan work, or will my home network crash into Bill Gate's greedy little lap? 

Erika

---

### Post by bjweeks on 2006-04-16
> will my wonderful Breezy Badger

Yes, it is just a router you have to connect to...

---

### Post by banadushi on 2006-04-16
It will work, my parents have a breezy workstation and FIOS service.

I have them setup through a linksys router, that is the easiest, but it will work directly connected to the FIOS terminater thing as well.

They use PPPoE with the FIOS just like their DSL, so you should just be able to plug in and go.

The johnnie that came out to install it gave my mother a yarn "Oh this won't work with FIOS", and "You should run windows, hackers use Linux".

So I got on the horn with him and he was clueless.  I told him to hook it up, and test it, as long as there was service on the ethernet cable, I could talk my mother through the rest.  They had a router and laptop that they used to setup everything, ranting the entire time "its not going to work", but alas it did and still does.

When he left, I had my mother plug the cable into the Linksys router and configured PPPoE via the web gui.

If you can stand their ignorance about the technology, then you shouldn't need to have the win98 install.

Have fun!

Jason

---

### Post by Aviatrixie on 2006-04-30
just an update...

   I'm using my FiOS now. It was just like my initial DSL install, except this time they needed to do my end in person. (plain-jane DSL uses the old copper wire, but FiOS needs converters, battery back-up, and fiber-optics brought into the house.) It took most of the day! The install guy showed up around 9 am and I showed him my Ubuntu. He thought it was cool, but said he needed Windows to do the install. I told him I had that available and he went outside to do his thing. A couple of hours later he came back inside to set things up. I now had him booted into Winders. He foosed around with it for about 2 hours and couldn't get it to work, so he called a coworker to help him. His coworker showed up and they both foosed with it for another 2 hours. Still no good. Finally, the second guy decided to call a guru friend. His guru friend told him to reboot.

   Bingo... he was in, they installed my FiOS, and we all laughed at Winders.

   As they were cleaning up their mess and packing up their stuff I got to have a good convo with them. I told them as soon as they were gone I'd be pulling the win drive. I've absolutely had it with Windows and the resultant virii, spyware, browser hijacks, and everything else that comes with microsoft products. The first guy that showed up was really sort of clueless, but the second guy was hip and told me that he didn't even install the Verizon FiOS software... that he could see I didn't need it, as it was only a Verizon frontend. I told him it was spyware anyway, and he just nodded.

   They ended up leaving around 5 pm.

   So... things I've learned...

   1) You don't need Winders to use DSL... or FiOS
   2) They Need Winders to initially set it up
   3) Once it's set up any ole OS will do
   4) the only reason the have it set up this way is so they can install their frontend       and spy on you
   5) I really do wish that companies like Verizon and Comcast would let their customers do the install with the OS of their choice!

I know... my update was a bit of a rant. But... it's all about choice!  LOL

Erika

---

### Post by Jason_25 on 2006-04-30
Let us know what sort of download/upload speeds you get.  Regarding the verizon-installed spyware, they're known as a company that uses heavy anti-consumer tactics.  For instance, the motorola razr phone they market has bluetooth file transfer disabled.  They want to be in control for sure.  Anyway, I hope it lives up to the hype.

---

### Post by Aviatrixie on 2006-04-30
I'm getting just under 4.9 down and about 1.8 up. :)

For $30/mo I'm happy. I told the install guys I was thinking of springing for the extra $10/mo for 15 meg down and they told me to sit tight... soon Verizon will offer 10 meg down for the same price I'm paying for 5 meg down.

Seems Verizon is hot to sell FiOS!

Erika

---

### Post by Buffalo Soldier on 2006-04-30
Glad things work out:) Hope someday (dreaming) my country will have this blazing broadband connection too.

Just my personal opinion here. I think you need to get the word out that FiOS works with Ubuntu/Linux:[list=1]
[*] Email Verizon/FiOS helpdesk, PR dept, anyone from that company that you can reach. Inform them that their product works in other platfrorm and that it was a good step to use protocol/hardware that is standard. Not sure how much this will help, but hopefully if other people called verizon after this asking whether FiOS will work with Linux or not... they will remember your email saying it does work.

[*] If you have a blog or personal website, it would be good to put this good news there too. First it will inform other Linux users. Second, let other ISP/hardware vendor know that their competitor is doing something right and users appreciate this.[/list]

---

### Post by 3rdalbum on 2006-04-30
[QUOTE=Buffalo Soldier]
Email Verizon/FiOS helpdesk, PR dept, anyone from that company that you can reach. Inform them that their product works in other platfrorm and that it was a good step to use protocol/hardware that is standard. Not sure how much this will help, but hopefully if other people called verizon after this asking whether FiOS will work with Linux or not... they will remember your email saying it does work.[/QUOTE]

Yes, do that, but just don't expect anyone to reply to your e-mails.

I've e-mailed an ISP telling them how I got ADSL working on Ubuntu, and an MP3 Player manufacturer telling them that their product works with Ubuntu, and both times I've not even had a form-letter in response.

---

### Post by Aviatrixie on 2006-05-01
I'm really starting to get back into my rebel frame of mind... went to college in the late 60's/early 70's... protested the Viet Nam war... married and raised two great kids. Now I see peers like Dubbya totally embarrassing me in world forums. :::shakes head:::
What in the world is WRONG with people now?!!!

Erika

---

