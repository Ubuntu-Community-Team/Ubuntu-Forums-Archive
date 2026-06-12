---
title: "Can I RAID later?"
date: 2011-01-13
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-13
Hello everyone,
Let me start off by saying that I have absolutely no experience with servers of any kind... ever. I've actually only been using Ubuntu on my laptop for about 4 months, with no prior Linux experience. 

However, I recently ordered a server for my home! I've wanted to learn about computer networking/systems for a long time. I'm particularly interested in security. Therefore, I'm pretty excited about my new server. It is admittedly rather low-end. But... it will handle 3 computers, a printer and a PS3 just fine.

The server I ordered is a Dell PowerEdge t110. When I ordered it, I had the option of adding RAID. My preference would probably be RAID 1. However, I didn't add RAID because I didn't want to spring for an extra hard drive right away.

My question is twofold:

1. When I have the money to add another hard drive, can I add RAID at that time?
2. What will I need to do that? 

About question #2, I've heard about a RAID controller but I have no idea what that is. Is there any special software?

Thanks everyone. Please be patient with my lack of knowledge.

---

### Post by chrislynch8 on 2011-01-13
Hi,

Q1: You should have no problems adding RAID-1 Later using mdadm
q2: You'll be better off using software RAID, no need to splash out on a Controller Ubuntu will manage it all.


If I am wrong about Question one another person will correct me shortly:confused:

Rgds
Chris

---

### Post by Ranger_Joe on 2011-01-13
Ok... what is mdadm?

---

### Post by chrislynch8 on 2011-01-13
mdadm is what you will use to create a manage the Software RAID. see the man page here. 

[http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)

---

### Post by Ranger_Joe on 2011-01-13
Ok, so the way I understand it is this:

As far as RAID goes, my options are between software RAID and hardware RAID. Right? When Dell asked me if I wanted to "add RAID," that would have been the hardware option. By adding RAID with Ubuntu, that will be the software option. Am I getting this right?

Are there any differences in performance? Ease of use?

---

### Post by rubylaser on 2011-01-13
Dell might have used fakeraid, but probably was using a hardware controller.  In Ubuntu, you can use some fakeraid cards, as well as softraid (mdadm), or even hardware RAID controllers.  I would use either hardware or mdadm on Linux.

Hardware is a controller that handles the RAID and does the parity calculations on the card, and mdadm is software raid, and will do all of that in the Operating System.  A hardware RAID card can be pricey, as opposed to free with mdadm.  And a good hardware controller can be VERY fast, but so can mdadm :)

If you're not looking to spend a bunch of money on a hardware card, give mdadm a try.  It works great for me, and you can get a lot of help here on the forums if you need it.

---

### Post by Ranger_Joe on 2011-01-13
*DUPLICATE - PENDING DELETION*

Ok... here is the situation now... I think I want a hardware RAID controller. Don't ask me why... it just seems better.

I think there is still time to change my order but I will need input pretty quick.

Here are the options that Dell gave me:

-[FONT=arial][SIZE=1][COLOR=Red]Onboard SATA, 1-4 Hard Drives connected to onbaord SATA Controller -No RAID [/COLOR][COLOR=Red][Included in Price][/COLOR]
-[/SIZE][/FONT][FONT=arial][SIZE=1]PERC S100 (Embedded SATA Software RAID) supporting 2 Hard Drives &#8211; RAID 0 add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=1]PERC S100 (Embedded SATA Software RAID) supporting 3-4 Hard Drives &#8211; RAID 0 add $0.00[/SIZE][/FONT]
-[FONT=arial][SIZE=1]**PERC S100 (Embedded SATA Software RAID) supporting 2 Hard Drives &#8211; RAID 1 ****add $0.00**
-[/SIZE][/FONT][FONT=arial][SIZE=1]PERC S100 (Embedded SATA Software RAID) supporting 4 Hard Drives &#8211; RAID 10 add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=1]PERC S100 (Embedded SATA Software RAID) supporting 3-4 Hard Drives &#8211; RAID 5 add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=1]No RAID - Add-in SAS6iR (SAS/SATA Controller), 1-4 Hard Drives add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=1]RAID 0 - Add-in SAS6iR or H200 (SAS/SATA Controller), 2-4 Hard Drives add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=1]**RAID 1 - Add-in SAS6iR or H200 (SAS/SATA Controller), 2 Hard Drives ****add $0.00**
-[/SIZE][/FONT][FONT=arial][SIZE=1]Add-in PERC S300 (SAS/SATA Controller) supporting 3-4 Hard Drives &#8211; RAID 5 add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=1]Add-in PERC S300 (SAS/SATA Controller) supporting 4 Hard Drives &#8211; RAID 10 add $0.00[/SIZE][/FONT]
[FONT=arial][SIZE=1]
The one in [COLOR=Red]red[/COLOR] is the one I went with. Again... because I didn't want to pay an extra $99 for another hard drive. The ones in **bold **are the ones that will work with RAID 1 (which is what I want).

So... here are the new questions:

1. Should I change my order? 
2. Which one should I get?

Thanks for your help! Much appreciated. 
[/SIZE][/FONT]

---

### Post by Ranger_Joe on 2011-01-13
[SIZE=2]Ok... here is the situation now... I think I want a hardware RAID controller. Don't ask me why... it just seems better.

I think there is still time to change my order but I will need input pretty quick.[/SIZE] [SIZE=2]

Here are the options that Dell gave me:[/SIZE] [SIZE=2]

-[/SIZE] [FONT=arial][SIZE=2][COLOR=Red]Onboard SATA, 1-4 Hard Drives connected to onbaord SATA Controller -No RAID [/COLOR][COLOR=Red][Included in Price][/COLOR]
-[/SIZE][/FONT][FONT=arial][SIZE=2]PERC S100 (Embedded SATA Software RAID) supporting 2 Hard Drives – RAID 0 add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=2]PERC S100 (Embedded SATA Software RAID) supporting 3-4 Hard Drives – RAID 0 add $0.00[/SIZE][/FONT][SIZE=2]
-[/SIZE][FONT=arial][SIZE=2]**PERC S100 (Embedded SATA Software RAID) supporting 2 Hard Drives – RAID 1 ****add $0.00**
-[/SIZE][/FONT][FONT=arial][SIZE=2]PERC S100 (Embedded SATA Software RAID) supporting 4 Hard Drives – RAID 10 add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=2]PERC S100 (Embedded SATA Software RAID) supporting 3-4 Hard Drives – RAID 5 add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=2]No RAID - Add-in SAS6iR (SAS/SATA Controller), 1-4 Hard Drives add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=2]RAID 0 - Add-in SAS6iR or H200 (SAS/SATA Controller), 2-4 Hard Drives add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=2]**RAID 1 - Add-in SAS6iR or H200 (SAS/SATA Controller), 2 Hard Drives ****add $0.00**
-[/SIZE][/FONT][FONT=arial][SIZE=2]Add-in PERC S300 (SAS/SATA Controller) supporting 3-4 Hard Drives – RAID 5 add $0.00
-[/SIZE][/FONT][FONT=arial][SIZE=2]Add-in PERC S300 (SAS/SATA Controller) supporting 4 Hard Drives – RAID 10 add $0.00[/SIZE][/FONT][SIZE=2]
[/SIZE] [FONT=arial][SIZE=1][SIZE=2]
The one in [/SIZE][SIZE=2][COLOR=Red]red[/COLOR][/SIZE][SIZE=2] is the one I went with. Again... because I didn't want to pay an extra $99 for another hard drive. The ones in **bold **are the ones that will work with RAID 1 (which is what I want).

So... here are the new questions:

1. Should I change my order? 
2. Which one should I get?

Thanks for your help! Much appreciated. [/SIZE]   
[/SIZE][/FONT]

---

### Post by rubylaser on 2011-01-13
The PERC controller is a fakeraid card (I wouldn't bother with this one).  The SAS6iR is a hardware controller capable of RAID 0 or 1.  That's the one I'd go with if you want hardware RAID, although that's pretty limited card it should work fine for RAID1.

---

### Post by Ranger_Joe on 2011-01-13
Boom. SAS6iR it is. Thanks!

---

### Post by chrislynch8 on 2011-01-14
Hi before you make your choice, consider the following.

1: 
You can manage/Monitor/rebuild the RAID on Ubuntu with mdadm. If you use a Hardware Controller, you will have to find other Software to manage this, I know dell have a Open Manage application that may work.
2: 
Those cards that come with Dell a Fake(Hardware) RAID. Even the better SAS6iR cards are cheap, as you can see that there is no extra cost for them.
3: 
DO a bit more research re: Hardware vs Fake RAID1 - I think alot of people would find Software to be the better option, speed, etc. Google is your friend [here.]("http://www.google.ie/search?hl=en&client=firefox-a&hs=XN3&rls=org.mozilla:en-GB:official&channel=s&biw=1024&bih=620&&sa=X&ei=hjQwTZOoHIfOhAfFyPH3Cw&ved=0CBcQBSgA&q=Hardware+vs+Software+RAID+1&spell=1") you will find alot will use Software for RAID0-1 and then look at buying expensive Controllers for other types

Rgds
Chris

---

### Post by Ranger_Joe on 2011-01-14
Chris, thanks for your help man. It looks like that will end up being my only option. Even though the website says SAS6iR is free... when you add it to the cart, it tacks on $200. When I called about this, they confirmed that it's not really free, just a small mistake on the website.

Also, I would have had to spend another $100 on a small wired hard drive, making my $300 starter server twice as expensive. No thanks.

I think I will get an additional hard drive soon and go with some sort of fakeraid option. Thanks everyone!

---

### Post by chrislynch8 on 2011-01-14
They prob supply the controller free and charge for setup + I think when you select a controller you must select a second HHD also. That could be the extra cost two. IT all adds up, as they say nothing is free

---

### Post by Ranger_Joe on 2011-01-14
Well if RAID 1 via software works then... who cares right?

---

### Post by Ranger_Joe on 2011-01-14
Well if RAID 1 via software works then... who cares right?

---

### Post by Ranger_Joe on 2011-01-14
Well if RAID 1 via software works then... who cares right?

---

### Post by Ranger_Joe on 2011-01-14
Well, if RAID 1 via software works... who cares right?

---

### Post by Ranger_Joe on 2011-01-14
Well, if RAID 1 via software works... who cares right?

---

### Post by rubylaser on 2011-01-14
I works great, and is a great learning experience as well.

---

### Post by rubylaser on 2011-01-14
It works great, and is a great learning experience as well.

---

### Post by elico on 2011-01-14
well it depends on the purpose of your envierment and for most of the systems software raid can be very good.

---

### Post by elico on 2011-01-14
well it depends on the purpose of your envierment and for most of the systems software raid can be very good.

---

