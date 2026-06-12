---
title: "Would anyone like free hardware to use in testing?"
date: 2015-01-06
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2015-01-06
I cannot believe my eyes. 

[http://mhall119.com/2015/01/community-donations-report-q2-2014/](http://mhall119.com/2015/01/community-donations-report-q2-2014/)

> [COLOR=#333333][FONT=Georgia]If you want to travel to an event, would like us to sponsor an event, _need hardware for development or testing_, or anything else that you feel will make Ubuntu the project and the community better, please go and [/FONT][/COLOR][fill out the request form]("http://community.ubuntu.com/help-information/funding/")[COLOR=#333333][FONT=Georgia].[/FONT][/COLOR]

Now don't all rush at once! I saw it first.

Regards.

---

### Post by ventrical on 2015-01-06
:) 

 I filled out a request for a ver3 SATA 3TB hdd for testing UEFI and to replace older storage devices.

 Who knows eh ?

Thanks Graham.

;)

---

### Post by QIII on 2015-01-06
I think I need one of these to test on ...

[ATTACH=CONFIG]259063[/ATTACH]

---

### Post by sammiev on 2015-01-06
> **QIII said:**
> I think I need one of these to test on ...

[ATTACH=CONFIG]259063[/ATTACH]

Thought you would of asked for New Teeth! :lolflag:

---

### Post by kansasnoob on 2015-01-07
I'd kind of like a refurb UEFI box or laptop with Win 8 or higher to perform iso-testing on but I'm reluctant to ask because my health is on the decline so I might no more than get it and drop dead :lolflag:

---

### Post by grahammechanical on 2015-01-07
Perhaps we could use this thread to come up with a list of special testing needs and the hardware that is required to run those tests. Then, maybe some of us could offer to request these items and do the testing.

The issue I see with UEFI and Windows 8 is the way manufacturers seem to be deviating from the specifications with every model they release. It is important to remember that this money is not set aside for Canonical engineers to spend on equipment for development or testing but for the Ubuntu community. And some of us here are good candidates for applying for this under the testing category.

Regards.

---

### Post by ventrical on 2015-01-07
Good point graham.

---

### Post by kansasnoob on 2015-01-07
The latest and greatest new hardware can be quite expensive but I think there is a true need for individual testers to be trying Ubuntu or it's flavors on newer equipment. I think most development is actually performed on virtual machines, at least that has frequently popped up during various bug discussions on Launchpad, etc.

A perfect example of need for newer hardware to test with is that ubiquity on UEFI with Windows 8 data eraser bug. I gladly would have done the verification for the bug-fix but I lacked the hardware - thankfully ventrical came to the rescue \\:D/

Another scenario that comes to mind is Tim Lunn's unanswered request for testing Ubuntu GNOME with Optimus graphics due to some upstream gdm bug. No testing = no fix :(

That said I really am kind of serious about not being in a good position to put such equipment to good use myself. I've already scaled back my iso-testing and reporting on the QA Tracker. I used to use two test boxes at the same time to perform various tests but I just can't handle multi-tasking at all anymore. Sometimes I get confused even just performing one set of tests on one machine - that's where notepads and sticky notes come in handy ;)

If I still had the umph to pull it off I would put in a request for a refurb UEFI puter - much cheaper than even building from scratch and usually you'll know within the 90 day warranty period if you have a dud or not + by the time refurbs start rolling out you can Google search the "make & model + Ubuntu" and find out if it's compatible at all.

---

### Post by MAFoElffen on 2015-01-07
I traced down the guideleines... and a few points stuck out (edited below to summarize). I think the key points are:
> 
Any Ubuntu Member is welcome to apply for funding from this donations budget (Ubuntu Membership is required).
...
Here are some examples of common areas we will likely fund:


Equipment (e.g. if a community member wants to add support for the equipment to Ubuntu).
...
<From the Donation Report>
...need hardware for development or testing, or anything else that you feel will make Ubuntu the project and the community better, ...

That's what is of interest to here?

I think it is also of interest to a certain mdadm-GUI project... on live storage space to test on.

---

### Post by ventrical on 2015-01-13
Ok .. I need your help or some simple suggestions. I received a reply for my request of a SATA ver3 3TB hdd worth about $150 Canadian.

  One of the persons has asked me;

> 
Can you please tell us how having that equipment will benefit the
Ubuntu project or community?
 


  I am not sure how to answer. I had stated already that I would use it to test UEFI hardware with 
Windows OSes and the Ubuntu <install alongside> option in Ubiquity. UEFI is needed to test storage space greater than 2TBs.  But the other benefit would be personal as I would be able to free up an existing 1.5TB and 500GB hdd so that I can return them for my personal use.

  From an purely economic standpoint , how would I , personally being the recipient of the 
aforesaid benevolence, be able to benefit the Ubuntu community as a whole?  All I can think 
of is that my experience and testing efforts may provide some data to developers when testing 
larger hardware form factors.

Any input would be gratefully appreciated.

Regards..

---

### Post by ventrical on 2015-01-13
Ok.. here is how I answered:

> "Hi Michael,
 
   I would use the equipment to test certain aspects of the Ubiquity  installer in development version (which is currently 15.04 vivid  vervet). There has been many problems with UEFI mode that already have a  Windows 8 operating system on it and the Ubiquity 'Install Alongside" option. Although some of those bugs are being fixed fast it  is important to keep up to speed on how larger hard drive equipment is  being used along with UEFI and Windows 8 with hard drives larger than 2  TBs (where the UEFI boot process is  required to read and configure those larger drives).
 
   My testing efforts and results may benefit Ubuntu Development Version and the contributors and developers who visit there.
 
 Sincerely , (real name here) Ventrical



---

### Post by grahammechanical on 2015-01-13
@ventrical

You are a Ubuntu Member. Can a person be accepted as a Ubuntu Member if they have not already in some way served the Ubuntu Community? I do not think so. You set aside much personal time to test the development release and have been doing this for several years.

You have purchased equipment at your own expense to use as test beds. You could have been content to limit your testing of the development release to motherboards that you already owned but they were ones with BIOS boot systems. But technology has moved on the UEFI boot systems, so you have purchased motherboards with UEFI boot systems.

Ventrical, you get my vote as a useful member of the Ubuntu Community who is giving back to the community. If community testers are not recognised as being of benefit to the Ubuntu community, then this invitation should not have included "testing" as a valid reason for applying for sponsorship from Community donated funds.

Regards.

---

### Post by ventrical on 2015-01-13
@graham..

  Thank you. I am going to frame that and hang it on my wall.  :)

Regards..

---

### Post by sammiev on 2015-01-13
> **grahammechanical said:**
> @ventrical

You are a Ubuntu Member. Can a person be accepted as a Ubuntu Member if they have not already in some way served the Ubuntu Community? I do not think so. You set aside much personal time to test the development release and have been doing this for several years.

You have purchased equipment at your own expense to use as test beds. You could have been content to limit your testing of the development release to motherboards that you already owned but they were ones with BIOS boot systems. But technology has moved on the UEFI boot systems, so you have purchased motherboards with UEFI boot systems.

Ventrical, you get my vote as a useful member of the Ubuntu Community who is giving back to the community. If community testers are not recognised as being of benefit to the Ubuntu community, then this invitation should not have included "testing" as a valid reason for applying for sponsorship from Community donated funds.

Regards.

+1

---

### Post by ventrical on 2015-01-23
Haven't received any further word as of yet.

@kansasnoob.

 I might be able to get a cheap Intel UEFI board and send it.  Either that or if I do not get approval of what I requested then I will write M. Hall and ask him to second  my request to you so you can get a UEIF MoBo. You have done a lot of work on qatracker. Why don't you apply for membership?

Regards..

---

### Post by kansasnoob on 2015-01-23
> **ventrical said:**
> Haven't received any further word as of yet.

@kansasnoob.

 I might be able to get a cheap Intel UEFI board and send it.  Either that or if I do not get approval of what I requested then I will write M. Hall and ask him to second  my request to you so you can get a UEIF MoBo. You have done a lot of work on qatracker. Why don't you apply for membership?

Regards..

I'm old and tired. I was hospitalized three times last year - twice with cardiac problems and once with a mild stroke. So I wish I had UEFI hardware just because I like to fool around, but I probably won't be that much of a contributing member long enough to justify someone else paying for hardware to provide me.

Like I have two bugs to do follow up testing on right now, stuff that should take a few hours but it'll likely take me a few days. That's just life - we eventually grow old and feeble.

So I'd much rather the money be spent on someone that's more likely to be able to continue contributing.

---

### Post by sudodus on 2015-01-23
But you have ***time***. And you have ***experience***. Many younger people are busy with so many other things. I think it is a good idea that you get an UEFI laptop or an UEFI motherboard :-)

---

### Post by ventrical on 2015-01-23
+1 :)

---

### Post by ventrical on 2015-01-23
> **kansasnoob said:**
> I'm old and tired. I was hospitalized three times last year - twice with cardiac problems and once with a mild stroke. So I wish I had UEFI hardware just because I like to fool around, but I probably won't be that much of a contributing member long enough to justify someone else paying for hardware to provide me.

Like I have two bugs to do follow up testing on right now, stuff that should take a few hours but it'll likely take me a few days. That's just life - we eventually grow old and feeble.

So I'd much rather the money be spent on someone that's more likely to be able to continue contributing.

But you always have better days and are diligent in your bug testing. I may be able to send a used MoBo for cheap. I have a friend in Texas and we often correspond. It would be Intel Core2Duo MoBo requiring 2GBs of 800MHz DDR2 RAM and you would need an old 80GB SATA and a 20 pin ATX 400W PSU. Do you have any of these other parts excluding the MoBo?

btw :) I am not entrepenure either :) but have contacts on parts.:)

Regards..

---

### Post by ventrical on 2015-01-23
@elfy,cariboo

Clarification needed.

Since this topic is open and transparent about aquiring assistance from the Ubuntu Community is it off topic to discuss about members and end_users sending computer surplus parts to other destinations?

Regards..

---

### Post by sammiev on 2015-01-23
> **sudodus said:**
> But you have ***time***. And you have ***experience***. Many younger people are busy with so many other things. I think it is a good idea that you get an UEFI laptop or an UEFI motherboard :-)

+1

---

### Post by pfeiffep on 2015-01-23
I see the focus is naturally on newer hardware. Is there a way to donate fully functional hardware?
Dell Inspiron 6000, Intel celeron 1.5 Ghz, 2 GB memory, 40 GB hdd; wifi + ethernet, 4 USB ports. 
Runs Ubuntu 14.04 perfectly.
Shipping NOT included

---

### Post by Elfy on 2015-01-24
> **ventrical said:**
> @elfy,cariboo

Clarification needed.

Since this topic is open and transparent about aquiring assistance from the Ubuntu Community is it off topic to discuss about members and end_users sending computer surplus parts to other destinations?

Regards..
I've certainly not go any issue at all with any of us sending anything to anyone else.

I've got no issue, as a member of the Forum Council, with saying that's nothing to do with the forum itself - if *you* and *they* decide between yourself to trust - that is good and proper.

In addtition to that as a member of the Community Council I would applaud that here on the forum we have people willing to trust each other.

I hope that makes the position clear.

If it doesn't - then the right place to ask the question for further clarification will be the Resolution Centre, not only for the rare one's wandering about in here, but for all.

regards.


(however, I add that any requests to the Community Team are not anything to do with the forum in itself, and any *trolling* about the subject will be treated as such in accordance with the forum CoC )

Edit - the last comment in parantheses being SPECIFICALLY about thread topic at this point and not recent posts.

---

### Post by Elfy on 2015-01-24
> **ventrical said:**
> @elfy,cariboo

Clarification needed.

Since this topic is open and transparent about aquiring assistance from the Ubuntu Community is it off topic to discuss about members and end_users sending computer surplus parts to other destinations?

Regards..

> **Elfy said:**
> I've certainly not go any issue at all with any of us sending anything to anyone else.

I've got no issue, as a member of the Forum Council, with saying that's nothing to do with the forum itself - if *you* and *they* decide between yourself to trust - that is good and proper.

In addtition to that as a member of the Community Council I would applaud that here on the forum we have people willing to trust each other.

I hope that makes the position clear.

If it doesn't - then the right place to ask the question for further clarification will be the Resolution Centre, not only for the rare one's wandering about in here, but for all.

regards.


(however, I add that any requests to the Community Team are not anything to do with the forum in itself, and any *trolling* about the subject will be treated as such in accordance with the forum CoC )

Edit - the last comment in parantheses being SPECIFICALLY about thread topic at this point and not recent posts.

On a purely personal note as elfy, piskie or hobgoblin - whether you know me from here or IRC - if I had hardware that I could pass on to good standing members of the forum for little cost (I am poorer in fact than the proverbial church mouse) I would do so - the proper place for *that* would really be the [Market]("http://ubuntuforums.org/forumdisplay.php?f=38")

hope that both those posts from me make some sense :)

---

### Post by ventrical on 2015-01-24
> **Elfy said:**
>  (I am poorer in fact than the proverbial church mouse) 

hope that both those posts from me make some sense :)


 Hey ... that's my line :) jk..

 Thanks for clarification. 

  I have access to a lot of surplus. Other buyers go to these swap meets for charity. 
[http://www.cfkcanada.org/](http://www.cfkcanada.org/)

  There are a lot of Intel MoBos with UEFI that are in good working order and very cheap. I'll get back at this on Monday.

  Of course my own personal request for 3TB ver 3 SATA hdd still stands as they do not sell new or refurbished equipment at the swap meets. They do have refurbished 2 and 3TB hdds at Factory Direct and if my request gets approved I would likely purchase the hdd from Factory Direct.   [http://www.factorydirect.ca/Canada-Ontario-/Computer_Add-Ons/Hard_Drive/Sata/HA4035/_Hard_Drive_4Tb_3_5__Sata__Rb_/0](http://www.factorydirect.ca/Canada-Ontario-/Computer_Add-Ons/Hard_Drive/Sata/HA4035/_Hard_Drive_4Tb_3_5__Sata__Rb_/0)

Edit: The above hdds are sold out :(

 Kansasnoob does not live very far from me. We get the tail end of all his tornados :)

Regards..

---

### Post by ventrical on 2015-01-24
> **Elfy said:**
> I've certainly not go any issue at all with any of us sending anything to anyone else.

I've got no issue, as a member of the Forum Council, with saying that's nothing to do with the forum itself - if *you* and *they* decide between yourself to trust - that is good and proper.

In addtition to that as a member of the Community Council I would applaud that here on the forum we have people willing to trust each other.

I hope that makes the position clear.


 I took it to private mail now at this stage.

Thanks for your help.

Regards..

---

### Post by kansasnoob on 2015-01-24
> **sudodus said:**
> But you have ***time***. And you have ***experience***. Many younger people are busy with so many other things. I think it is a good idea that you get an UEFI laptop or an UEFI motherboard :-)

Time in that context is sort of a subjective thing - I mean it now takes me 10 times longer to do things than it should.

I'm glad we now have less respins of the iso images for the opt-in alphas and beta 1. I just can't keep up anymore.

---

### Post by sudodus on 2015-01-25
*kansasnoob*, do the things you like and and let it take the time necessary. You have made and are still making an important contribution to our community :-)

---

### Post by kansasnoob on 2015-01-25
> **ventrical said:**
> I took it to private mail now at this stage.

Thanks for your help.

Regards..

I think my last reply via PM didn't work, I've tried twice and it never shows up in my sent box, so I thought I'd reply here regarding versions of UEFI. Since I know almost nothing about UEFI I had to do some studying and [according to Wikipedia]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#History") Version 2.1 of the UEFI (Unified Extensible Firmware Interface) specification was released on 7 January 2007, and it looks like there were no major changes until 2013.

I then used the links provided in [the mobo specs]("http://downloadmirror.intel.com/15033/eng/DQ965GF_ProductGuide03_English.pdf") you provided and found the UEFI settings on page 32 of [the BIOS settings PDF]("http://download.intel.com/support/motherboards/desktop/sb/biosglossarybymenu_v13.pdf") but I found no mention of what the version of UEFI is. Does that really matter? I assume that I just need to be sure UEFI is turned on in the BIOS and start with a GPT drive.

---

### Post by ventrical on 2015-01-25
> **kansasnoob said:**
> I think my last reply via PM didn't work, I've tried twice and it never shows up in my sent box, so I thought I'd reply here regarding versions of UEFI. Since I know almost nothing about UEFI I had to do some studying and [according to Wikipedia]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#History") Version 2.1 of the UEFI (Unified Extensible Firmware Interface) specification was released on 7 January 2007, and it looks like there were no major changes until 2013.

I then used the links provided in [the mobo specs]("http://downloadmirror.intel.com/15033/eng/DQ965GF_ProductGuide03_English.pdf") you provided and found the UEFI settings on page 32 of [the BIOS settings PDF]("http://download.intel.com/support/motherboards/desktop/sb/biosglossarybymenu_v13.pdf") but I found no mention of what the version of UEFI is. Does that really matter? I assume that I just need to be sure UEFI is turned on in the BIOS and start with a GPT drive.

The one I was going to send I think had 2.0. I am going to wait until Monday and see one of my suppliers. I left you a msg that there were some new Zenix Desktops in so I  I have to wait and see whats in them, most likely some Intel quads with UEFI 2.1 .. so I'll get back. The other one from 2006/last quarter has the EFi .. Not sure if there is much of a diff bwtween them.

 I'll get back.

happy sunday , day of  rest :)

Regards.

---

### Post by kansasnoob on 2015-01-25
> **ventrical said:**
> The one I was going to send I think had 2.0. I am going to wait until Monday and see one of my suppliers. I left you a msg that there were some new Zenix Desktops in so I  I have to wait and see whats in them, most likely some Intel quads with UEFI 2.1 .. so I'll get back. The other one from 2006/last quarter has the EFi .. Not sure if there is much of a diff bwtween them.

 I'll get back.

happy sunday , day of  rest :)

Regards.

No rush - it's just going to be a toy for testing :D

---

### Post by ventrical on 2015-01-26
I had 2 failed MoBos. Tried everything. The other 2 (that work and the manuals say they are EFI capable) will not present a UEFI option. I went to one of my places of contact and they still haven't found the MoBo that I am looking for. So I'll have to  wait. A newer board with DDR3 SATA 3.ect plus memory+processor is over my budget atm.

edit:

Ok... I have 3 working UEFI systems. I can send you the Intel DB43LD MoBo . with fan and 2 1GB sticks of DDR2

Regards..

Please met me know right away so I can send it today.

Thanks..

---

### Post by QIII on 2015-01-26
I asked for something, but since it won't leave much money left I think I'll get rejected.

---

### Post by ventrical on 2015-01-26
> **QIII said:**
> I asked for something, but since it won't leave much money left I think I'll get rejected.


It's been a while since I have heard anything on my submission.

Regards..

---

### Post by kansasnoob on 2015-01-26
> **ventrical said:**
> I had 2 failed MoBos. Tried everything. The other 2 (that work and the manuals say they are EFI capable) will not present a UEFI option. I went to one of my places of contact and they still haven't found the MoBo that I am looking for. So I'll have to  wait. A newer board with DDR3 SATA 3.ect plus memory+processor is over my budget atm.

edit:

Ok... I have 3 working UEFI systems. I can send you the Intel DB43LD MoBo . with fan and 2 1GB sticks of DDR2

Regards..

Please met me know right away so I can send it today.

Thanks..

Sounds awesome. Many, many thanks.

---

### Post by ventrical on 2015-01-26
> **kansasnoob said:**
> Sounds awesome. Many, many thanks.

You'll never believe this ...:) .. but in the rush I forgot to send the IO shield along with the rest of the pkg  :(

I'll have to send it in an envelope :)

Regards..

Edit:

You will have to check this link out [http://ubuntuforums.org/showthread.php?t=2259219&p=13200176#post13200176](http://ubuntuforums.org/showthread.php?t=2259219&p=13200176#post13200176) and clean out the old [ubuntu] and [windows bootloader] entries.

---

### Post by kansasnoob on 2015-01-26
> **ventrical said:**
> You'll never believe this ...:) .. but in the rush I forgot to send the IO shield along with the rest of the pkg  :(

I'll have to send it in an envelope :)

Regards..

Edit:

You will have to check this link out [http://ubuntuforums.org/showthread.php?t=2259219&p=13200176#post13200176](http://ubuntuforums.org/showthread.php?t=2259219&p=13200176#post13200176) and clean out the old [ubuntu] and [windows bootloader] entries.

Sounds like something I would do :lolflag:

Is that UEFI partition advice meant for someone else? Because I'll be starting with a blank drive and just creating a GPT partition table, then installing Windows enterprise. I'm debating whether to go for Win 8 or Win 10???????? I suppose it doesn't really matter because I only care how Ubuntu treats things in dual/multi-boot installations.

---

### Post by ventrical on 2015-01-26
> **kansasnoob said:**
> Sounds like something I would do :lolflag:

Is that UEFI partition advice meant for someone else? Because I'll be starting with a blank drive and just creating a GPT partition table, then installing Windows enterprise. I'm debating whether to go for Win 8 or Win 10???????? I suppose it doesn't really matter because I only care how Ubuntu treats things in dual/multi-boot installations.

  It does not matter because  they both use the same installer. There is nothing new in the (windows8) installer that I can see.

As far as the link I sent you ... I am not really sure it matters but just in case I usually clear out the old entries. That was Old Freds' advice because I was having probs because Windows would not fully shut down (That is a windows Bug). As you start out it is best to use the F10 boot option before you try and install it  set to boot from Grub as the start-up choice because it will blow out Windows 8 and you will have to use Grub Rescue to restore your windows 8 install.
also .. when the PC is shut off there will be a blinkng red LED. That just means that the Intel AMT is out of band.
 btw .. @grahammechanical too , I heard that windows 10 is going to be offered as a sort of free -opensource wannabe ??

  Ok.. I am way off topic on this thread. :)

Regards..

---

### Post by ventrical on 2015-01-27
@kansasnoob

Ok.. I sent the I/O shield via snail mail :)

Regards..

---

### Post by ventrical on 2015-01-29
@grahammechanical and all

 I received e-mail today of approval for my request ! :)  So *WE* are all the proud owners of new SATA 3 3TB hdd  soon:)

 Thanks to everybody for help and support.

 Regards..

---

### Post by kansasnoob on 2015-01-29
> **ventrical said:**
> @grahammechanical and all

 I received e-mail today of approval for my request ! :)  So *WE* are all the proud owners of new SATA 3 3TB hdd  soon:)

 Thanks to everybody for help and support.

 Regards..

Cool ................. and you've already "paid it forward" by sending me a UEFI board to test on :guitar:

---

### Post by ventrical on 2015-01-29
> **kansasnoob said:**
> Cool ................. and you've already "paid it forward" by sending me a UEFI board to test on :guitar:

:) .. It should be there by tomorrow. I have tracking no. for it in case it gets lost.

Thanks :)

---

### Post by Elfy on 2015-01-29
Nice :)

---

### Post by ventrical on 2015-01-29
> **Elfy said:**
> Nice :)

Perhaps by next week I'll have it in hand so if anyone has any  scenarios they would like me to try  then please let me know.

Of course .. part of the approval goes hand in hand that I report back to the community in general any relevant data pertaining to experiments using UEFI in alongsides with other OSes.. etc..

Thanks again.

---

### Post by QIII on 2015-01-29
So, ventrical...

Did they offer to purchase and send it to you, or wire the money to your account?

I got an email from Michelle Surtees-Myers (and looked her up on LinkedIn) saying they would wire the money.  Usually uncomfortable with that, but I see her all over the place as a Canonical employee.

---

### Post by ventrical on 2015-01-29
> **QIII said:**
> So, ventrical...

Did they offer to purchase and send it to you, or wire the money to your account?

I got an email from Michelle Surtees-Myers (and looked her up on LinkedIn) saying they would wire the money.  Usually uncomfortable with that, but I see her all over the place as a Canonical employee.

Wire money to account. I  received notice from the same as you mentioned. I am just going through the process in a spirit of trustworthiness. The next step was to get my supplier to send an order receipt and then I will send receipt next week. I can understand the process of due diligence.

Regards..

---

### Post by QIII on 2015-01-29
Check the email header.

The Message-ID on mine was <...random...@mail.gmail.com>

I would have expected a Canonical domain.

Also, the first MSA bounce was a Google server.  I would have expected that to be a Canonical domain, too.

I left an inquiry for an explanation.  She may have sent it from her cell phone using gmail using her @canonical.com address as an alias.  But can't be too careful.

There is definitely a person by that name that works at Canonical.  I've seen the name on some Ubuntu blogs.

---

### Post by ventrical on 2015-01-30
I got  [email]real_name@canonical.com[/email] in the header.

As for other info .. if she is using android device and/or chrome then google will of course be the first bounce.

I got pretty well the same random Message ID that you did .

Now you got me paranoid :)

---

### Post by ventrical on 2015-01-30
> **QIII said:**
> Check the email header.

The Message-ID on mine was <...random...@mail.gmail.com>

I would have expected a Canonical domain.

Also, the first MSA bounce was a Google server.  I would have expected that to be a Canonical domain, too.

I left an inquiry for an explanation.  She may have sent it from her cell phone using gmail using her @canonical.com address as an alias.  But can't be too careful.

There is definitely a person by that name that works at Canonical.  I've seen the name on some Ubuntu blogs.

Also she sent me reciprocated information that only M. Hall would have.

Regards..

---

### Post by QIII on 2015-01-30
I'm sure it's her, but one can never be too careful.  Maybe I just need to add an extra layer of tinfoil to my hat...

---

### Post by ventrical on 2015-01-30
> **QIII said:**
> I'm sure it's her, but one can never be too careful.  Maybe I just need to add an extra layer of tinfoil to my hat...

 Can unicorns fly ?..

:)

---

### Post by kansasnoob on 2015-01-30
> **ventrical said:**
> :) .. It should be there by tomorrow. I have tracking no. for it in case it gets lost.

Thanks :)

Still in transit, no worries:

[ATTACH=CONFIG]259615[/ATTACH]

I think our mail goes from Kansas City to Emporia and then finally here, so probably Tuesday.

---

### Post by ventrical on 2015-01-30
> **kansasnoob said:**
> Still in transit, no worries:

[ATTACH=CONFIG]259615[/ATTACH]

I think our mail goes from Kansas City to Emporia and then finally here, so probably Tuesday.


You remind me of that guy in that movie .. 'A Beautiful Mind'..  :)

Regards..

---

### Post by kansasnoob on 2015-02-02
> **ventrical said:**
> You remind me of that guy in that movie .. 'A Beautiful Mind'..  :)

Regards..

Beautiful Mind = awesome puter:

```
ubuntu@ubuntu:~$ cat /proc/cpuinfo | head -10 && lspci | grep VGA && lspci | grep Audio && lspci | grep Ethernet
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 1200.000
cache size	: 2048 KB
physical id	: 0
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1944       1332        612        101        158        686
-/+ buffers/cache:        487       1456
Swap:            0          0          0
```

So far I've only run a Trusty live DVD long enough to be sure I had everything properly connected and to format that new 250GB drive to GPT. That small case made things slightly challenging but it's all crammed in there ;)

BTW I haven't looked at the spec-sheet yet but you mentioned something about a blinking red light and I see that right between the RAM modules, do you know what that is?

EDIT: figured out the red blinking light = Intel AMT. Not sure but I may want to disable that. 

I'll have time tonight to play with the BIOS just to familiarize myself with the new hardware. Many, many thanks again.

---

### Post by sudodus on 2015-02-03
Have a good time with your new mobo *kansasnoob* :-)

---

### Post by ventrical on 2015-02-03
> **kansasnoob said:**
> Beautiful Mind = awesome puter:

```
ubuntu@ubuntu:~$ cat /proc/cpuinfo | head -10 && lspci | grep VGA && lspci | grep Audio && lspci | grep Ethernet
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 1200.000
cache size    : 2048 KB
physical id    : 0
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1944       1332        612        101        158        686
-/+ buffers/cache:        487       1456
Swap:            0          0          0
```

So far I've only run a Trusty live DVD long enough to be sure I had everything properly connected and to format that new 250GB drive to GPT. That small case made things slightly challenging but it's all crammed in there ;)

BTW I haven't looked at the spec-sheet yet but you mentioned something about a blinking red light and I see that right between the RAM modules, do you know what that is?

EDIT: figured out the red blinking light = Intel AMT. Not sure but I may want to disable that. 

I'll have time tonight to play with the BIOS just to familiarize myself with the new hardware. Many, many thanks again.


  I mentioned before ... the AMT light blinks when the PC is off to indicate that  it is 'out of band'   (which it should be doing when it is active).  It is not an error code.Oh yes ..a \nd do not worry about the FAN errors.. just keep an eye on the main processor fan that no wires get in there and slow it down.

:) 
Regards..


F10 to boot into UEFI shell.

---

### Post by kansasnoob on 2015-02-03
> **ventrical said:**
> I mentioned before ... the AMT light blinks when the PC is off to indicate that  it is 'out of band'   (which it should be doing when it is active).  It is not an error code.Oh yes ..a \nd do not worry about the FAN errors.. just keep an eye on the main processor fan that no wires get in there and slow it down.

:) 
Regards..


F10 to boot into UEFI shell.

It's all working just as it should, I just had to take a little while familiarizing myself with the BIOS settings and wrapping my mind around the whole Intel AMT thing which was new to me. No fan errors - I suppose because I have both front and rear fans as well as the CPU fan. I installed the Ubuntu GNOME Trusty amd64 daily build last night just using the entire disc option and things worked fine.

---

### Post by ventrical on 2015-02-03
Thats great news.  Sometimes during the winter ESD  has a way of bricking hardware.

Regards..

---

### Post by kansasnoob on 2015-02-03
> **ventrical said:**
> Thats great news.  Sometimes during the winter ESD  has a way of bricking hardware.

Regards..

I always wear an anti-static wrist strap and play things super safe. I had to laugh once when I went to a guys house to check out a box he'd built that wouldn't post. When I got there he was still dinking with it and had everything laying on a shag carpet :oops:

---

### Post by ventrical on 2015-02-04
We just had a blizzard of the century here on the great lakes. Record.  I haven't been checking in.  Doing snow around here. Sorry for off topic.

---

### Post by sudodus on 2015-02-04
We haven't had as much snow as we have now since 1966. The snow machines at the near-by slalom pists can rest for a while :-D

I took the attached picture a few days ago after a windy and snowy day, when we received 37 cm of snow (average thickness increase of snow, not water content :-P )

---

### Post by grahammechanical on 2015-02-04
@ventrical

You should change your stated location on your forum profile from Beta testing in Canada, to snow clearing in Canada. :) You must have done a lot of that this past year.

---

### Post by ventrical on 2015-02-04
> **grahammechanical said:**
> @ventrical

You should change your stated location on your forum profile from Beta testing in Canada, to snow clearing in Canada. :) You must have done a lot of that this past year.

Oy me back ! :)

It's like a war zone up here. People keep clearing their snow and the city trucks keep humping it back up.

[http://blogs.windsorstar.com/news/sidewalk-enforcers-expected-to-pounce-wednesday](http://blogs.windsorstar.com/news/sidewalk-enforcers-expected-to-pounce-wednesday)

Beta Testing from the New North Pole :)

---

### Post by ventrical on 2015-02-04
> **sudodus said:**
> We haven't had as much snow as we have now since 1966. The snow machines at the near-by slalom pists can rest for a while :-D

I took the attached picture a few days ago after a windy and snowy day, when we received 37 cm of snow (average thickness increase of snow, not water content :-P )

Ohhhh .. Geee !!   That reminds me of that song by Led Zepplin ... The Immigrant Song.. :)

---

### Post by xc3RnbFO8P on 2015-02-04
> **ventrical said:**
> Ohhhh .. Geee !!   That reminds me of that song by Led Zepplin ... The Immigrant Song.. :)
Ok, 
Next stop Iceland...:p

---

### Post by sudodus on 2015-02-04
> **Ringi said:**
> Ok, 
Next stop Iceland...:p

Impressive ice, who beats it with a picture from Greenland or Antarctica?

Anyway, this time of the year (near the north pole) we have no problems to cool our computers :-P

---

### Post by QIII on 2015-02-05
Got the AMD R9 290X today courtesy of Canonical.  We'll see what Vivid thinks of it this weekend.

---

### Post by ventrical on 2015-02-06
3TB hdd

[http://www.storagereview.com/seagate_barracuda_3tb_review_1tb_platters_st3000dm001](http://www.storagereview.com/seagate_barracuda_3tb_review_1tb_platters_st3000dm001)

---

