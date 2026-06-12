---
title: "The Future of Ubuntu CE and a little explanation..."
date: 2008-02-02
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2008-02-02
**Update: **I am going to reimbursed for my laptop!! It may take a little while to see the money, but at least I will get reimbursed. I apologize for my absence from the forums. I have been very busy doing tons of freelance work and also developing my site, [TheJesusTV.com]("http://www.thejesustv.com"). I am going to suspend work on the Ubuntu CE project temporarily, but indefinitely. I have struggled with this decision for quite a while. The project is **not dead**, but I need some time to work on some other projects. I hope you all will understand this decision. Please keep me in your prayers.

God Bless, Jereme

-------------------------------------------------------------------------------------------------------------------------------

Hi all,
I know that many of you are chomping at the bit to find out about the next release of Ubuntu CE. First let me say thank you for all of your enthusiasm. I never expected Ubuntu CE gain such a community. 

I know things have been very slow with Ubuntu CE and I do apologize for that. I wanted to post a little explanation of why things are moving so slow and to layout the plan for the next release.

Ok, so here is what has slowed things down. Ubuntu CE has many contributors without which Ubuntu CE could not exist. However, at the core Ubuntu CE is a one person "operation". I do not mean to diminish the efforts and contributions of the many Team members and forum members who have contributed. I just want people to understand the the website, distro, and all of the custom packages (dansguardian gui, esword installer, etc) are all built on my laptop. Which brings me to a bizarre situationi that started back in September.

Back in September I was taking out the trash. Our building has a room on the first floor for disposing of our trash. Occasionally people will throw away old computers. In fact a few years ago I found one their and installed Ubuntu on it and gave it to a friend who was in need of a laptop. It was truly a "trash to treasure" moment. So when I spotted a broken laptop I was stoked. The only thing that I was able to salvage was the 30gb hard drive from the wreckage. So, I put the hard drive into an extra enclosure that I had and plugged it in to my laptop to see if it was functioning. It worked perfectly. My plan was to format it and use it for extra storage. Before I formatted it I decided to see what was on the hard drive. That is where I made a mistake.

Well, I guess it wasn't a mistake because I am glad that I was able to help in the upcoming investigation. My bad I am getting ahead of myself. So, the hard drive had some teenage kids homework and such. I ran across some "adult" material. The only problem is that I started noticing that there were some odd things like tons of info on school shootings and terrorism. Then I found the worst thing that I have ever seen. It was a cache of child pornography. I immediately pulled the usb cord out of my laptop and tried to figure out what to do.

Now, I have two young boys of my own. I sat up almost all night worrying about my kids, the kids in the pictures and just completely disgusted at the whole thing. I decided that I had to inform the authorities. The next day I called and several detectives came to investigate. I was glad to be helpful, but I did not know that I was going to end up losing my laptop over it. 

The detectives asked me tons of questions and took my statement. Then they dropped the bombshell. Since my laptop had been connected to the hard drive via usb cable they had to confiscate my laptop so they could verify that the images and such originated from the hard drive and not my laptop. I assumed they were just going to take my hard drive, but they took my whole laptop. They said that I would get it back in a matter of a few weeks. Boy were they wrong! They did allow me to make a full backup of the hard drive, so I would not lose all of my data.

So, now I am working off a much older/slower laptop that simply will not run Vmware or Virtualbox at a speed suitable for testing. It locks up before it ever gets started. The detective in charge of the investigation recently called to let me know that I should have my laptop back by the end of March.

I apologize for not explaining this sooner, but I was hoping that I would get my laptop back sooner and I could move on with things. I wished I had the resources to just go out and buy a new laptop, but that simply is not an option right now. 

So, the plan for the next release of Ubuntu CE is this. I will focus on building on Hardy. There will not be a Gutsy release. At this point it only makes sense to skip Gutsy. I will also be focusing on the Dansguardian GUI. I will probably discontinue work on the esword installer and ies4linux installer as these complicate the build process quite a bit and I believe that the Parental Controls is the most important area to focus on at this point. I also may switch over to a DVD release instead of keeping things down to a 700mb disc. This would also make the build time faster.

Please let me know what you think.

God Bless, Jereme

---

### Post by david_kt on 2008-02-02
> **mhancoc7 said:**
>  I will probably discontinue work on the esword installer and ies4linux installer as these complicate the build process quite a bit

I will make sure the generic "how to" to install esword will work on Hardy:

[http://ubuntuforums.org/showthread.php?t=404042]("http://ubuntuforums.org/showthread.php?t=404042")

 As for ies4linux, I thought below script is easy enough:
[http://http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu]("http://http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu")

DK

---

### Post by jonathonblake on 2008-02-02
> **david_kt said:**
> I will make sure the generic "how to" to install esword will work on Hardy:

Thanks.

I'm looking at the options for the resource installer. Specifically, integrating *The e-Sword Module Database* into it.

xan

jonathon

---

### Post by waspinator on 2008-02-02
Well I hope you get your laptop back soon. If police want people to come forward with information they should treat people with respect. Just goes to show you that no good deed goes unpunished. You may be more forgiving then I am, but after hearing that I would never help the police again. I say, let them mind thier own business and I'll mind mine.

---

### Post by Jim Shunamon on 2008-02-02
Dear Jereme,
As the father of a 10 year old I can understand how mortified you must have been when you saw what was on that drive. I wish that I had a laptop that I could send you, but I am disabled and don't even own one myself  (All of my computing is done on an old, and I mean old Compaq Pentium 3 tower) lol!
I think it is the wise thing to do to just do the build on Hardy, and I can't wait to see the finished product. I also think that the DVD release is a great idea.
One request if I may: Please do not eliminate E-Sword:)  I depend on it daily and I don't have the knowledge to deal with Wine and trying to tackle something like that myself.
At any rate I hope that you get your laptop back soon, and know that you and your family are in our thoughts and prayers.
God Bless.
><>  Jim Shunamon  <><

---

### Post by mhancoc7 on 2008-02-02
> **david_kt said:**
> I will make sure the generic "how to" to install esword will work on Hardy:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

 As for ies4linux, I thought below script is easy enough:
[http://http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

DK

Thanks, if the generic "how to" is maintained then it may be fairly easy for me to keep the esword installer in the next release.

Yes the script that you mentioned is basically all that is used in Ubuntu CE. When I first put it together the ies4linux script did not have the nice GUI that it has now. The other issue is that the installed IE can be used to circumvent the parental controls. 

> **jonathonblake said:**
> Thanks.

I'm looking at the options for the resource installer. Specifically, integrating *The e-Sword Module Database* into it.

xan

jonathon

Thanks, keep me updated!

> **waspinator said:**
> Well I hope you get your laptop back soon. If police want people to come forward with information they should treat people with respect. Just goes to show you that no good deed goes unpunished. You may be more forgiving then I am, but after hearing that I would never help the police again. I say, let them mind thier own business and I'll mind mine.

I would feel that way if kids weren't involved. It is a small price for me to pay if it will help to get one of those kids some help.


> **Jim Shunamon said:**
> Dear Jereme,
As the father of a 10 year old I can understand how mortified you must have been when you saw what was on that drive. I wish that I had a laptop that I could send you, but I am disabled and don't even own one myself  (All of my computing is done on an old, and I mean old Compaq Pentium 3 tower) lol!
I think it is the wise thing to do to just do the build on Hardy, and I can't wait to see the finished product. I also think that the DVD release is a great idea.
One request if I may: Please do not eliminate E-Sword:)  I depend on it daily and I don't have the knowledge to deal with Wine and trying to tackle something like that myself.
At any rate I hope that you get your laptop back soon, and know that you and your family are in our thoughts and prayers.
God Bless.
><>  Jim Shunamon  <><

Thanks Jim. I really appreciate your kind words and input. I really do not want to leave out esword either. Thanks for showing your support for keeping it. That will help me decide to keep it or leave it out.

God Bless, Jereme

---

### Post by david_kt on 2008-02-02
[QUOTE=mhancoc7;4257484]Thanks, if the generic "how to" is maintained then it may be fairly easy for me to keep the esword installer in the next release./QUOTE]

If you just teach me how to make the script and subsequently the deb package, I would be happy to help you to maintain esword deb package.

DK

---

### Post by mhancoc7 on 2008-02-03
> **david_kt said:**
> [quote=mhancoc7;4257484]Thanks, if the generic "how to" is maintained then it may be fairly easy for me to keep the esword installer in the next release./QUOTE]

If you just teach me how to make the script and subsequently the deb package, I would be happy to help you to maintain esword deb package.

DK

Thanks for that. The script is fairly basic. I use gambas to build the GUI. I am not sure how good of a teacher I would be though. I am still learning myself. :)
God Bless, Jereme

---

### Post by cjm5229 on 2008-02-03
Jereme,
I just wanted to vote for the eSword installer, eSword is the best Bible study program available at any price. Since Bible Study is the most important aspect of Christianity, I think it is the most important app we have. The installer did work when Gutsy first came out, but it broke shortly after. I have been trying to get it installed with the generic "How To" every since. I can get eSword to install but the Modules give me fits. I agree with Jim Shunamon, that it is beyond the technical ability of most Ubuntu Users. 

I also want to say God Bless you for standing up and doing "the right thing". I am sure that a lot of us would be happy to through an offering into the collection plate to help you get a new Computer, if you would accept it.

May God Bless You and Yours, as well as your efforts to help spread the word.
Carl

---

### Post by ke4ke on 2008-02-03
Yes, I want to put in my vote for e-Sword as well.

Sorry about your troubles Jereme. Feels like you are being punished by them keeping your laptop. It is not evidence. I am glad to see that Hardy is the focus now.

To be honest I do not use CE. I just put e-Sword on regular Ubuntu. Having e-Sword is the only reason I so quickly switched over to Ubuntu from XP. I can't go back now, but not having a Bible program that allows me to click on a word and see the Hebrew or Greek definition is all important. (I had to switch to another computer and thus a new install.) Multiple Bible versions are nice, but what is really important is what the original language actually says. (There are instances where the English is not only misleading, but the opposite in meaning.) If you use Strong's Concordance read his instructions for use!

Here is a simple one. Romans 14:14 I know, and am persuaded by the Lord Jesus, that there is nothing common of itself: but to him that esteemeth any thing to be common, to him it is common.

Makes a big difference if you understand the difference between common and unclean.

Tim

---

### Post by waspinator on 2008-02-03
Would you consider working with others to realize a more complete parental control suite for U:CE in the future? Is it that you prefere to work alone, or are there just no others willing to help?

I would really like to see you perental contorls expand in capabilities (including setting them up for different accounts, as well as activity logging) and maybe even having them included as an integrated part of standard ubuntu. I know it would detract some people from using U:CE, but maybe you could think of the greater good.

---

### Post by twin_57103 on 2008-02-03
Sorry to hear about everything that's happened.  You did the right thing, and I pray blessing on you for standing up for it, even though you've been treated poorly.  I don't use CE myself (regular Ubuntu), but it is a great project, especially to those with families.  I will pray for your situation and that your laptop will be returned soon.  Thanks for your ministry.  God bless!

---

### Post by jonathonblake on 2008-02-03
> **cjm5229 said:**
> 
I just wanted to vote for the eSword installer,

One major issue with the e-Sword installer, is that e-sword.net has pretty much been redesigned to drop all connections from bots.  

*e-Sword* can not be included in *Ubuntu Christian Edition* for licensing reasons.  (The* e-Sword EULA* prohibits both Internet distribution of the executable file and commercial distribution.)

I expect to release the documentation for installing *e-Sword* in a WINE bottle within a fortnight. (More specifically, Sections 1 - 10, and 65 - 67 of *The e-Sword Utility program FAQ*, in English.  Esperanto, toki pona,  and Afrikaans translations will follow.)

xan

jonathon

---

### Post by ke4ke on 2008-02-03
Thanks for the explanation. That is unfortunate.

I have emailed a bit with Rick Meyers. His current interest is for a Live version online, but that is not really helpful for real study considering the internet connections most have available. Because of that he has no plans for a Linux or Mac version.

Tim

---

### Post by waspinator on 2008-02-03
I've never used e-sword. Is it that good and are there no alternatives? If he doesn't charge for it maybe he could release the source someday.

---

### Post by jonathonblake on 2008-02-04
> **waspinator said:**
> I've never used e-sword. Is it that good 

What makes e-Sword so good are:
* A very extensive range of resources.  (5,000 by my last count);
* Very easy for users to create their own resources;
* The functionality of the various components;

> are there no alternatives?

There are four commercial Bible study programs that garner attention:
* Logos;
* BibleWorks;
* Quickverse;
* PC Study Bible;  

My guess is that there are more users of e-Sword, than there are of those four programs combined. ( Total downloads of e-Sword exceed the combined sales of those four programs since they first went on the market.)

As far as Bible study programs for Linux goes, *The Sword Project* is the only organization that has created any.

e-Sword has both more resources, and more functionality than the Sword Project programs.

>  If he doesn't charge for it maybe he could release the source someday.

For e-Sword to be ported to Linux, or any other platform, the following are needed:
* A cross platform database engine;
* A cross platform display rendering engine;

These will either have to be written from scratch, or use source code that has either a BSD or public domain license.

xan

jonathon

---

### Post by mhancoc7 on 2008-02-04
> **cjm5229 said:**
>  I also want to say God Bless you for standing up and doing "the right thing". I am sure that a lot of us would be happy to through an offering into the collection plate to help you get a new Computer, if you would accept it.

May God Bless You and Yours, as well as your efforts to help spread the word.
Carl

Thanks, for you kind words. I really do appreciate it. I am going to do everything I can to keep esword in the next release.

Thanks for considering "passing the hat". It is awesome to think that anyone would consider it. The Ubuntu CE site does accept donations but I do not want to actively solicit for donations.

> **waspinator said:**
> Would you consider working with others to realize a more complete parental control suite for U:CE in the future? Is it that you prefere to work alone, or are there just no others willing to help?

I would really like to see you perental contorls expand in capabilities (including setting them up for different accounts, as well as activity logging) and maybe even having them included as an integrated part of standard ubuntu. I know it would detract some people from using U:CE, but maybe you could think of the greater good.

Well, it is not that I don't want to work with others on it. The main reason that I have kept the distro so "close" is to ensure that I had control over its future. I have seen lots of projects that had many people behind it and they seemed to lose their focus. Now, I would love to see a community develop that would begin to work on packages such as a new dansguardian GUI and present it for inclusion. This way I could keep the distro itself centralized, but also allow for community developed areas. I would just love that. I have mentioned this to some in the past, but nothing ever came of it. So, if you want to be the one to start up a group to build a new more powerful dansguardian GUI that would be AWESOME!

Thanks to everyone that has posted their kind words. It is really nice to have such a great community.

God Bless, Jereme

---

### Post by cjm5229 on 2008-02-04
> **jonathonblake said:**
> One major issue with the e-Sword installer, is that e-sword.net has pretty much been redesigned to drop all connections from bots.  

*e-Sword* can not be included in *Ubuntu Christian Edition* for licensing reasons.  (The* e-Sword EULA* prohibits both Internet distribution of the executable file and commercial distribution.)

I expect to release the documentation for installing *e-Sword* in a WINE bottle within a fortnight. (More specifically, Sections 1 - 10, and 65 - 67 of *The e-Sword Utility program FAQ*, in English.  Esperanto, toki pona,  and Afrikaans translations will follow.)

xan

jonathon

jonathon,
What about working with Wine itself to get it set up for eSword to install simply? If Wine came with support for eSword, it would make it a lot easier on the less "techy" Christians among us. it would make it easier for those running other Distro's as well.

---

### Post by jonathonblake on 2008-02-04
> **cjm5229 said:**
> 
What about working with Wine itself to get it set up for eSword to install simply?

After I finish writing how to install e-Sword in a WINE bottle, and the rest of the documentation for e-Sword, I might do that. 

xan

jonathon

---

### Post by Faud on 2008-02-05
As far as the installer for "The Word" does it make it run in WINE or does it run on linux w/o using WINE.
Thanks,
Faud

---

### Post by david_kt on 2008-02-05
> **jonathonblake said:**
> I expect to release the documentation for installing *e-Sword* in a WINE bottle within a fortnight. (More specifically, Sections 1 - 10, and 65 - 67 of *The e-Sword Utility program FAQ*, in English.  Esperanto, toki pona,  and Afrikaans translations will follow.)

xan

jonathon

Jonathon,
Is this "how to" similar to the one I make? There is one problem with the how to I make is downloading dll from internet. Sometimes the dll is corrupted or somtimes the files are changed.

If we could host the said dlls, may be it is a better solution. One problem though is the legality of hosting such dlls.

But I think the most critical dll is the riched20, and I have been thinking of a permanent solution i.e. by installing wordviewer, which provide riched20 legally.

DK

---

### Post by jonathonblake on 2008-02-06
> **david_kt said:**
> 
Is this "how to" similar to the one I make? 

a) I include screen shots;
b) It is part of the document on installing the various components required by the e-Sword Utility programs; (The document is roughly 150 pages in length.)

> There is one problem with the how to I make is downloading dll from internet. Sometimes the dll is corrupted or sometimes the files are changed.

I'll add MD5 hash sums for the required components in my documentation.

> One problem though is the legality of hosting such dlls.

Needed: One North Korean resident with access to *The Pirate Bay*.

More seriously, I don't grok Microsoft's policy regarding redistribution of DLLs and OCX files. The relevant EULAs appear to simultaneously permit, prohibit,and require it for third party applications.

> thinking of a permanent solution i.e. by installing wordviewer, which provide riched20 legally.

I'll be lazy, so I'll do a cut and paste from the FAQ.

The Required components

Every utility program wants something else to be installed, prior to it working correctly.  I call those things “Required Components”.   

* DAO365.DLL:
** Bible Module Editor;
** Biblos;
** Commentary Editor

* DAOCheck;
** e-Sword;
** Tag Scanner;
** Text2DAO;
** Topical File Editor;

* Java
** Study Notes Tool;

* MDAC 2.8
** e-Sword;
** Bible Import Tool;
** Text2DAO;

* MSDATGRD.OCX:
** Text2DAO;
** e-Sword;

* MSINET.OCX:
** Bible Import Tool;
** Text2DAO;

* .NET Framework 1.1:
** Ben's e-Sword Tool;
** Ben's Pocket e-Sword Tool;
** Unicode2RTF;
** Utmost Import Tool;

* .NET Framework 2.0:
** Ben's e-Sword Tool;
** Ben's Pocket e-Sword Tool;

* Python
** Python e-Sword Scripts;

* RichEdit.OCX:
** Bible Comparison Tool;
** e-Sword;

*  RichEd20.dll:
** e-Sword;
** Text2DAO;

* Visual Studio Express
** John Mark's Tools;

That is my current list of what is required by each of the utility programs,and e-Sword, It is not complete,and I think that some of the listings are incorrect.   

One thing I haven't looked into, is if a specific version is required.  e-Sword uses the version of the RTF that was released with either Word 97, or Word 2000.  (At any rate, it is a version of RTF that is incompatible with the version of RTF that was released with MSO 2007.)

I'd like to get at least the core e-Sword utility programs running on Linux. ( BeST, MFC Creator, Text2DAO, Bible Compare Tool, Scripture Tooltip Generator, TheWORDpad Editor.)

I think I've seen an executable that includes all of the DLL and OCX files, but I don't know where. :(

xan

jonathon

---

### Post by Z_Cee on 2008-02-06
Thanks for all you do Jereme! I think you made the right call about the child porn you found on the hard drive. I skipped through several post, but I would remind the police about "returning" your laptop and not to put it out for a "police auction."  Which is what they do with a large amount of items they recover.

---

### Post by mhancoc7 on 2008-02-06
> **Faud said:**
> As far as the installer for "The Word" does it make it run in WINE or does it run on linux w/o using WINE.
Thanks,
Faud

It uses WINE.

> **Z_Cee said:**
> Thanks for all you do Jereme! I think you made the right call about the child porn you found on the hard drive. I skipped through several post, but I would remind the police about "returning" your laptop and not to put it out for a "police auction."  Which is what they do with a large amount of items they recover.

Thanks. I am in direct contact with the authorities about the matter. I am supposed to get it back mid March! :)

Thanks, Jereme

---

### Post by Teasdale on 2008-02-08
> **mhancoc7 said:**
> 
So, the plan for the next release of Ubuntu CE is this. I will focus on building on Hardy. There will not be a Gutsy release. At this point it only makes sense to skip Gutsy. I will also be focusing on the Dansguardian GUI. I will probably discontinue work on the esword installer and ies4linux installer as these complicate the build process quite a bit and I believe that the Parental Controls is the most important area to focus on at this point. 

I'm brand new to Linux (a week) and this is the first I've heard of Ubuntu CE. The Hardy edition sounds like it might be just what I'm looking for - I'm very interested in Dansguardian GUI, especially if it's preinstalled. I'm not so interested in anything that relies on WINE to run.

---

### Post by caricc on 2008-02-08
You did the right thing by calling the authorities. Sorry to see that they took your laptop and everything else. But you at least can sleep at night knowing you DID DO RIGHT by your kids and everyone elses kids.

---

### Post by xilix on 2008-02-09
Thank you for explaining this. When I saw the title of this thread "The Future of Ubuntu CE and a little explanation..." I already feared this would be the end of this project!

I think it is the right decision to continue with a Hardy release. What would also be great if an accountability software (-> mssever is developing it) will find it's way into Ubuntu CE.

I don't want to criticize you for maintaining Ubuntu CE as a "single-person-project". But I wonder if there are one or two persons (persons you know very well) who can help you with this. (Just have to think of Moses and Jitro.) This is just a question...

God bless you
xilix

---

### Post by mhancoc7 on 2008-02-11
> **caricc said:**
> You did the right thing by calling the authorities. Sorry to see that they took your laptop and everything else. But you at least can sleep at night knowing you DID DO RIGHT by your kids and everyone elses kids.

Thanks!

> **xilix said:**
> Thank you for explaining this. When I saw the title of this thread "The Future of Ubuntu CE and a little explanation..." I already feared this would be the end of this project!

I think it is the right decision to continue with a Hardy release. What would also be great if an accountability software (-> mssever is developing it) will find it's way into Ubuntu CE.

I don't want to criticize you for maintaining Ubuntu CE as a "single-person-project". But I wonder if there are one or two persons (persons you know very well) who can help you with this. (Just have to think of Moses and Jitro.) This is just a question...

God bless you
xilix

I agree that an accountability software package would be awesome!

As far as making this less of a "one person" project, I understand your thoughts. I would love to see groups startup to build specific packages for Ubuntu CE. What I mean is that I would love to have a group that maintained and developed an accountability package, etc.

Anyway, I am still deciding exactly what will be in the next release and what will not.

God Bless, Jereme

---

### Post by thibeaz on 2008-02-26
Hey Jereme, Zach here. That was a tough call but a good one, God will Bless you for doing the right thing. Great to see you still around. Miss you at churchforge (now Geekbrownbag.com) anyways. God Bless

---

### Post by mhancoc7 on 2008-02-26
> **thibeaz said:**
> Hey Jereme, Zach here. That was a tough call but a good one, God will Bless you for doing the right thing. Great to see you still around. Miss you at churchforge (now Geekbrownbag.com) anyways. God Bless

Hey Zach,
Thanks for your support. I miss churchforge as well. I keep meaning to post to Geekbrownbag.com but just have not had the time. Maybe I can try to get back over there with you guys soon.
God Bless, Jereme

---

### Post by beta.tester on 2008-02-27
Blessings Jereme

Please be assured you are also in our prayers, my health not been too good lately hence no messages. You did the right thing and I believe God will both bless and honour you. I am at a healing Mass tonight so will ask for your intentions also.

Pax et bonum

john

"Evil triumphs when good men (and women) stand by and do nothing!".

---

### Post by mhancoc7 on 2008-02-28
> **beta.tester said:**
> Blessings Jereme

Please be assured you are also in our prayers, my health not been too good lately hence no messages. You did the right thing and I believe God will both bless and honour you. I am at a healing Mass tonight so will ask for your intentions also.

Pax et bonum

john

"Evil triumphs when good men (and women) stand by and do nothing!".

Thanks you very much for that. I hope your health has gotten better. I will keep you in my thoughts and prayers as well.

God Bless, Jereme

---

### Post by Phlinux on 2008-03-01
Gidday Jim

May I add something so far off the beaten track it aint funny?! The 1Cross + 3Nails = 4given... I don't why, but just reading that brought God's peace into my heart - I have been going through various struggles as everyone does in life, but I wasn't reacting in the right way to them. A few simple words and I have His peace again... thank you and may God bless you Jim!!

Phil

---

### Post by Paul H on 2008-03-02
God bless you Jereme!
As a father of two children I support you on your decision.  One of the reasons I enjoy UCE is the "parental" controls.  I can work beside my children without having to worry while they search the internet for homework resources.
I wish that I understood programing and could help out....hmmm there are quite a few "geeks" at our church.  Would you mind if I approached them to take a little of the burden from you?  I think that a "project" like this would be an incredible outreach experience for those involved.
I am thankful that you are updating the package.

Paul H

---

### Post by mhancoc7 on 2008-03-05
> **Paul H said:**
> God bless you Jereme!
As a father of two children I support you on your decision.  One of the reasons I enjoy UCE is the "parental" controls.  I can work beside my children without having to worry while they search the internet for homework resources.
I wish that I understood programing and could help out....hmmm there are quite a few "geeks" at our church.  Would you mind if I approached them to take a little of the burden from you?  I think that a "project" like this would be an incredible outreach experience for those involved.
I am thankful that you are updating the package.

Paul H

Hi Paul,
Thanks so much. Yes, I would welcome the help.

I am still working out how I am going to approach future releases. I am going to be focusing on stability and making things a bit easier to keep updated. This may mean that some packages will have to be excluded, but I want to be sure this project can continue.

God Bless, Jereme

---

### Post by incen on 2008-03-06
> **mhancoc7 said:**
> 
I will focus on building on Hardy. There will not be a Gutsy release. At this point it only makes sense to skip Gutsy. I will also be focusing on the Dansguardian GUI. I will probably discontinue work on the esword installer and ies4linux installer as these complicate the build process quite a bit and I believe that the Parental Controls is the most important area to focus on at this point. I also may switch over to a DVD release instead of keeping things down to a 700mb disc. This would also make the build time faster.

That will be really cool to have CE on Hardy! I myself don't have a CE yet. I plan to take one more old laptop from home and install latest CE ontop of it.
I think esword is important. It's a big featuer of CE. A little late will be fine for almost everybody, I think, in order to get a complete CE! :)
For me, probably the sizing-down is not as important as others features. However, I'm not even sure if the disk drive of that old laptop can read DVD... ><
HAHA~
Anyway, thank you very much, Jereme. May God bless all your work and your family! ^^

Best,
Cissi

---

### Post by Eutaw on 2008-03-07
> **mhancoc7 said:**
> Hi Paul,
Thanks so much. Yes, I would welcome the help.

I am still working out how I am going to approach future releases. I am going to be focusing on stability and making things a bit easier to keep updated. This may mean that some packages will have to be excluded, but I want to be sure this project can continue.

God Bless, Jereme
My first time here, glad I got to read both your courage and faith. I am confident the Lord will reward you in due season. 
At this time, I'm just working off liveCD. My wife isn't ready to give up Vista yet:confused:, but she'll come around. Or we'll keep both on. Just wanted to affirm you, and let you know I'll be around.
Rick Williams
Eutaw, Alabama

---

### Post by sloggerkhan on 2008-03-08
I would bill the cops for your lost productivity.

---

### Post by Eutaw on 2008-03-08
, > **sloggerkhan said:**
> I would bill the cops for your lost productivity.
Tempting thought, but a better way would be to trust the Lord:
"Beloved do not avenge yourselves, but rather give place to wrath; for it is written, 'Vengeance is mine, I will repay,' says the Lord...Do not be overcome by evil, but overcome evil with good." Romans 12:19,21 NKJV
See also Psalm 1.

---

### Post by Guiness on 2008-03-15
> **incen said:**
> I think esword is important. It's a big featuer of CE. A little late will be fine for almost everybody, I think, in order to get a complete CE! :)

Me too would rather wait for E-sword as I followed all different instructions from all over the net and couldn't get it work properly.
Also Ubuntu 8.1 will be out on the 24th April or May, if CE could be delayed till that release comes out maybe?

---

### Post by david_kt on 2008-03-15
> **Guiness said:**
> Me too would rather wait for E-sword as I followed all different instructions from all over the net and couldn't get it work properly.
Also Ubuntu 8.1 will be out on the 24th April or May, if CE could be delayed till that release comes out maybe?

Have you ever tried below instruction:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

If untii now you still could not get e-sword running, I will try to guide you to run it. It has been reported that it could run on Hardy Alpha as well.

DK

---

### Post by rcdeacon on 2008-03-20
I have been away a long time. Used CE a couple of releases ago and did like it but my infatuation with KDE got the best of me. Linux Mint has definitely changed my perspective on the GUI and I am primarily using Mint but have recently installed Hardy Alpha 6 and am anxiously awaiting beta 1 then final. I was very much enthused about the possibility of a Hardy CE. Looking forward to it. I currently have esword working well on Hardy Alpha 6 and I also vote for its inclusion along with dansguardian. I have been unsuccessful in getting Logos to work and since i have sunk a fair sum of money into Logos it would be nice for it to work in Wine but I think my efforts along those lines are futile at least according to their tech support people. At any rate, looking forward to the next CE release, keep up the good work and may God bless you.

---

### Post by waspinator on 2008-03-26
How is development coming along? Have the police returned your laptop yet? Otherwise I will assume that they charged you for possession of child pornography and that you will never be seen again.

---

### Post by JFonseka88 on 2008-03-28
Jeremy...your efforts and the result is brilliant. This distro is something that many people should have, especially in this day and age where unacceptable material lures kids at an early age and has them trapped in perpetual cyber tomfoolery.

I pray that your future efforts are not in vain and that God grants you all the resources you need to be as productive as possible.

God Bless

---

### Post by mhancoc7 on 2008-04-10
> **waspinator said:**
> How is development coming along? Have the police returned your laptop yet? Otherwise I will assume that they charged you for possession of child pornography and that you will never be seen again.

No, I have not got my laptop back. I am working on getting reimbursed. Also, I have never been a suspect in this case. The reason for they took my laptop was to rule my laptop out as the origin of the materials, which it was not.

I think you were trying to be funny, but IT IS NOT FUNNY!

Jereme

---

### Post by david_kt on 2008-04-10
> **mhancoc7 said:**
> No, I have not got my laptop back. I am working on getting reimbursed. Also, I have never been a suspect in this case. The reason for they took my laptop was to rule my laptop out as the origin of the materials, which it was not.

I think you were trying to be funny, but IT IS NOT FUNNY!

Jereme

I deeply concern about your situation. Please let us know what we could do to help you to be cleared from this issue. 

DK

---

### Post by mhancoc7 on 2008-04-10
a> **david_kt said:**
> I deeply concern about your situation. Please let us know what we could do to help you to be cleared from this issue. 

DK

Thank you very much for your concern. Things are actually looking good for now. My laptop has returned from being examined and was found to NOT contain any questionable materials. I have never been a suspect. I have simply gotten caught up in a bad situation. The case against the owner of the harddrive that I found is growing and I expect to be called as a witness. Anyway, thanks again for your concerns.

God Bless, Jereme

---

### Post by david_kt on 2008-04-10
> **mhancoc7 said:**
> a

Thank you very much for your concern. Things are actually looking good for now. My laptop has returned from being examined and was found to NOT contain any questionable materials. I have never been a suspect. I have simply gotten caught up in a bad situation. The case against the owner of the harddrive that I found is growing and I expect to be called as a witness. Anyway, thanks again for your concerns.

God Bless, Jereme

Wow,what a relief. Reading your last post, I thought you are about to be a suspect, that what make me worry.

DK

---

### Post by mhancoc7 on 2008-04-10
> **david_kt said:**
> Wow,what a relief. Reading your last post, I thought you are about to be a suspect, that what make me worry.

DK

Thanks man. Yeah, that has never been a worry. It is amazing how the guy who is trying to do the right thing is the one who has to be inconvenienced. I mean the guy who harddrive I found is still living in our building. The authorities assure me that he is being watched, but it still gives me a weird feeling.
God Bless, Jereme

---

### Post by kmf on 2008-04-11
So when will "Operations resume" ?

Thanks
Karl

---

### Post by Coords on 2008-04-11
[COLOR=Green][SIZE=3][FONT=Comic Sans MS]I am also looking forward to the eventual release of 8.04 CE, hopefully with the almost completed new version of The Word. Thanks Jereme.:)[/FONT][/SIZE][/COLOR]
[COLOR=Green][SIZE=3][FONT=Comic Sans MS]
Lets not forget to pray for the person involved in this porno. He is loved by and needs the salvation only Jesus Christ can bring!
[/FONT][/SIZE][/COLOR]

---

### Post by waspinator on 2008-04-12
> **mhancoc7 said:**
> No, I have not got my laptop back. I am working on getting reimbursed. Also, I have never been a suspect in this case. The reason for they took my laptop was to rule my laptop out as the origin of the materials, which it was not.

I think you were trying to be funny, but IT IS NOT FUNNY!

Jereme

I'm sorry for my insensitive comment. I just wanted to point out the absurdity of what the police have done to you for trying to help, the power they have over you, and how much worse it could be for you if they decided they couldn't find the real guy and just wanted to pin it on someone. I hope that guy just possessed it and didn't actually make it. Otherwise letting him roam free without help is dangerous. 

I hope work on 8.04CE will resume.

Waspinator

btw you kind of contradicted yourself by saying that you have "never been a suspect in this case" but that they took your laptop to "rule [your] laptop out as the origin of the materials". If they didn't suspect you then they wouldn't have taken it, although I believe your innocence.

---

### Post by rhenrick on 2008-04-14
Will you at least be updating DansGuardian GUI to work with 8.04? That is more important to me than another CE release.

---

### Post by Kaaiman on 2008-04-16
^^ Indeed. I will only upgrade to 8.04 when the DG-script has been made compatible with it. For my own protection.

---

### Post by waspinator on 2008-04-23
Any news? Hardy is just around the corner and I hope that the Dansguardian script will be updated for it soon.

---

### Post by rhenrick on 2008-04-23
> **Kaaiman said:**
> ^^ Indeed. I will only upgrade to 8.04 when the DG-script has been made compatible with it. For my own protection.

AMEN! Same for me too.

---

### Post by thane777 on 2008-04-24
Have you ever considered adding a keylogger to the distro?  Do any of  you know how to get LKL startup during boot?


Jereme, I am sorry to hear that you were given so much grief when you were doing the right thing.  God is our Judge.  He will provide justice.

Keep serving Him!


Thane

---

### Post by tnl2k7 on 2008-04-26
Hi,

Crikey dude you've had a rough time. I can't believe what's happened to you and certainly hope I never hear of it happening to anyone again, that's vile.

You did the right thing reporting it to the police though, let's just hope they catch the original owner of that laptop, eh?

Good luck in the future,
-Luke.

---

### Post by StandUp&amp;BeCounted on 2008-04-26
This is actually a great opportunity to find out about the average Ubuntu CE user.  Is he (or she) more like the typical cheap*** linux user or more like the tithing Christian who sees Ubuntu CE as another form of ministry.  IF the latter, then why can't WE the community raise enough money to buy Jereme another laptop and get the project out of suspension.  At government auctions an Ubuntu worthy laptop goes for as little as $150.
    Any ideas on how to get this done?

---

### Post by waspinator on 2008-04-27
Just donate to the project. If we all (50 people) give $20 I'm sure he can find a worthy laptop to work on. I've done my bit. O:)

---

### Post by Marc Higgins on 2008-04-29
We support the work being done here. We think God supports the work being done here too. 

I urge you to also support the continuation of Gods work being done through this project. Not just support with words, but with money.

---

### Post by gusjones on 2008-04-29
can someone remind me the best place to donate to?

---

### Post by jonathonblake on 2008-04-29
> **waspinator said:**
> If they didn't suspect you then they wouldn't have taken it,

The police have to be able to prove a negative --- that the perp was not Jeremy --- when the case comes to trial.   The easiest way to do that, is to be able to provide forensic evidence that demonstrates that the data was viewed using the drive, but not created, downloaded, or transfered using Jeremy's system.   

Rephrased, for Jeremy's own protection, the police have to prove beyond any shadow of doubt that he (Jeremy) is totally innocent of any plausible charges that could be filed against the actual perps.  

xan

jonathon

---

### Post by Ripfox on 2008-05-06
> **Coords said:**
> [COLOR=Green][SIZE=3][FONT=Comic Sans MS]I am also looking forward to the eventual release of 8.04 CE, hopefully with the almost completed new version of The Word. Thanks Jereme.:)[/FONT][/SIZE][/COLOR]
[COLOR=Green][SIZE=3][FONT=Comic Sans MS]
Lets not forget to pray for the person involved in this porno. He is loved by and needs the salvation only Jesus Christ can bring!
[/FONT][/SIZE][/COLOR]

Or we could pray for the kids and send whoever made it straight to hell?

---

### Post by Eutaw on 2008-05-06
"Vengeance is mine, says the Lord, I will repay."
No one - not even 'religious' people - will escape Him. 

Jesus said, "but whoever causes one of these little ones who believe in me to sin, it would be better for him to have a great millstone fastened around his neck and to be drowned in the depth of the sea." (Matthew 18:6)

---

### Post by pwn2king on 2008-05-06
You can add my vote for E-Sword, it is just too important. And I’d like to help where I can. I have a laptop that one day just quit, who knows, you may be able to restore it. Also I have a new laptop HDD that I bought to use on that laptop before it finally shut down for good. I’d be happy to donate it. God Bless you for all your hard work.

---

### Post by Ripfox on 2008-05-07
> **Eutaw said:**
> "Vengeance is mine, says the Lord, I will repay."
No one - not even 'religious' people - will escape Him. 

Jesus said, "but whoever causes one of these little ones who believe in me to sin, it would be better for him to have a great millstone fastened around his neck and to be drowned in the depth of the sea." (Matthew 18:6)

Nice quotes. :rolleyes:

What the hell am I doing in here anyways:lolflag:

bye bye now

---

### Post by fachex on 2008-05-22
Jeremy, I can't thank you enough for all your work! I will beg you to re-consider your decision to put-off the UCE. There is so much need out there. I am trying to evangelize UCE to members of my church. As you might know, the Jews are working on  [Jubuntu]("https://launchpad.net/jubuntu") to be released anytime. There is a [UME (Musilm Edition)]("http://www.ubuntume.com") and it appears to be they did a good job with it, at least the GUI seems pretty nice. So, you are the only hope to put our (Christian Community) voice out in the FOSS world. 
I would love to see something like X3Watch for UCE. I don't know how hard that could be. It appears to be simple, I am not a programmer, but I have studied some Visual Basic in the past. 
Another reason that I would love to see UCE up, running and updated is because there are a lot of Christian that don't get quite well the legal issue of pirating software and I want to encourage them to see alternatives.  
I definitely vote for e-sword as a native application.  Also, I was thinking to make like "Christian" templates for OO Presentation. There already a lot of free themes like it on the web. 
I am glad that you've got your laptop back! 
God bless.

---

### Post by mhancoc7 on 2008-05-23
Hi all,
Here is a little update!

First let me say thank you to those of you who have donated. It touches my heart to think that you care enough to do that.

So here is where I am with things.

The person who owned the laptop that I discovered in the trash has left the area. I should explain that I live on a military base. That is one thing that makes this situation even more confusing. The person who owned the laptop lived in our building, but was not military. He is a dependent of a civilian that works as a teacher on base. It is really sad. Anyway, the person has moved back to the states in an attempt to duck the situation. I don't think they realize that they will not be able to run for this. 

I finally got reimbursed for my laptop!!!! My original laptop has been completely exonerated and was found to have ZERO inappropriate material on it. However, it can't be returned to me until after the possible trial since the defense will want to have their experts examine it. It is so "Law and Order". I was finally able to convince the authorities that I needed to be reimbursed. So long story short I have a nice new Toshiba!

Now the issue that I am having is that I can't get my wireless to work with this laptop and I quite honestly do not have the energy to deal with trying to get Ubuntu running properly on it. I have been a devote Ubuntu users for almost 4 years now, but I am weary of dealing with the unfortunate reality of proprietary driver issues. Now, I am sure I will start to miss my Ubuntu and will get cracking on it eventually. :) However, for now I am using Vista since I just need a laptop that works. I have several other projects that I work on and I have to consider them as well. My site [www.TheJesusTV.com](www.TheJesusTV.com) has really be taking off and I need to be able to keep working with it.

Now, I do plan to bring Ubuntu CE back. For those who don't realize it, Ubuntu CE was the catalyst for Ubuntu ME, Jubuntu, and other niche distros. The past releases pushed the envelope of what can be done. For instance including Windows programs (Virtual Rosary) and Installers for IE and Esword had never really been done to my knowledge. I am going to think long and hard about how to approach the future of Ubuntu CE. I want to give everybody what they want, but I also need to focus on something that I can keep up with and something that will be stable.

So, I really need feedback on what you guys think are the must haves. I know that Esword is at the top of the list, but I have to be honest when I say that Windows programs are going to have to be low on the list at least for the next release. There are just a lot of variables when it comes to including those.

Anyway, that is probably enough of an update for now. I just want you all to know that I am in no way abandoning this project. I just have to take care of things first.

By the way, my family and I are going to be moving back to the states in a few months so things are going to get a bit hectic on that end for me. We have been living overseas for over 3 years now so moving home is sure to have its challenges.

I hope you are all understand my situation and know that I am working hard to get back up and running.

God Bless, Jereme

---

### Post by ardvark71 on 2008-05-26
> **mhancoc7 said:**
> 
Well, I guess it wasn't a mistake because I am glad that I was able to help in the upcoming investigation. My bad I am getting ahead of myself. So, the hard drive had some teenage kids homework and such. I ran across some "adult" material. The only problem is that I started noticing that there were some odd things like tons of info on school shootings and terrorism. Then I found the worst thing that I have ever seen. It was a cache of child pornography. I immediately pulled the usb cord out of my laptop and tried to figure out what to do.

Now, I have two young boys of my own. I sat up almost all night worrying about my kids, the kids in the pictures and just completely disgusted at the whole thing. I decided that I had to inform the authorities. The next day I called and several detectives came to investigate. I was glad to be helpful, but I did not know that I was going to end up losing my laptop over it. 

God Bless, Jereme

How very sad. :(

But I'm happy you were able to get reimbursed and a new laptop! \\:D/

Best Wishes...

---

### Post by waspinator on 2008-05-27
I wish you all the best in moving back to the USA. I'm sure you can't wait to leave those perverted Japanese. May God send many disasters and spread death and destruction to their island of sin.

Back on topic, if you can't find the time and resources needed to further the UCE effort, I hope someone else will be able to pick up the torch.

Waspinator

---

### Post by abcStu on 2008-05-27
I would like to suggest that you consider how to use multiple CDs for distribution, with perhaps the more optional stuff on the second, and an option to continue into it, or use it for local package source, or some such, _rather_ than going to DVD.  I install onto abandoned, no longer wanted computers for people who cannot afford any, mainly families homeschooling.  I would like to have the free OS/distro be linux/ubuntu-ce for their sakes.  And such machines always have a CD reader but seldom a DVD reader.
I feel obligated to include the CDs used to install with the computer so that the new user will have the possibility to reinstall if essential.  I partition to have 55% of space for linux, 2GB for swap, and the balance as FAT32/LBA, so that they can use the latter for their wine files, or even (if they get a copy) for Wdoze itself, though I don't recommend it.
I applaud you for doing the right thing about the found HD, and wish the police could be a little more sensible:  Why, if **you** were the one who collected the trash, would you ever tell them?  God be praised for giving you grace to forgive stupid people.
I will install 3.3 (aka 7.04 based) for now and eagerly await the 8.04 based.  I have installed 8.04 desktop amd64, and it finished by rebuilding the initrd.img, but didn't keep the new, leaving only a initrd.img.bak so the link was broken!  Happily, I was able to figure this out from the slack 11 partition, but I haven't fixed it yet.  The Canonical folks still have some warts to remove from the install process.
Thanks, and God bless you for this work, and with time,
abcStu

---

### Post by mhancoc7 on 2008-05-27
> **waspinator said:**
> I wish you all the best in moving back to the USA. I'm sure you can't wait to leave those perverted Japanese. May God send many disasters and spread death and destruction to their island of sin.

Back on topic, if you can't find the time and resources needed to further the UCE effort, I hope someone else will be able to pick up the torch.

Waspinator

Hold on just a minute. The laptop that I found belonged to an American not a Japanese. I am also very disturbed by your comments. My family and I have had a wonderful experience here in Japan. We have found the Japanese to be a wonderful people. Of course they have their problems, but so does every culture. I am actually quite offended by your comments and hope and pray that you will see that intolerance and hatred towards anyone is not what Jesus would want.

> **abcStu said:**
> I would like to suggest that you consider how to use multiple CDs for distribution, with perhaps the more optional stuff on the second, and an option to continue into it, or use it for local package source, or some such, _rather_ than going to DVD.  I install onto abandoned, no longer wanted computers for people who cannot afford any, mainly families homeschooling.  I would like to have the free OS/distro be linux/ubuntu-ce for their sakes.  And such machines always have a CD reader but seldom a DVD reader.
I feel obligated to include the CDs used to install with the computer so that the new user will have the possibility to reinstall if essential.  I partition to have 55% of space for linux, 2GB for swap, and the balance as FAT32/LBA, so that they can use the latter for their wine files, or even (if they get a copy) for Wdoze itself, though I don't recommend it.
I applaud you for doing the right thing about the found HD, and wish the police could be a little more sensible:  Why, if **you** were the one who collected the trash, would you ever tell them?  God be praised for giving you grace to forgive stupid people.
I will install 3.3 (aka 7.04 based) for now and eagerly await the 8.04 based.  I have installed 8.04 desktop amd64, and it finished by rebuilding the initrd.img, but didn't keep the new, leaving only a initrd.img.bak so the link was broken!  Happily, I was able to figure this out from the slack 11 partition, but I haven't fixed it yet.  The Canonical folks still have some warts to remove from the install process.
Thanks, and God bless you for this work, and with time,
abcStu

Thanks for the kind words. I am going to try my best to keep it to a one cd install like before. 

Jereme

---

### Post by Matthew Wiebelhaus on 2008-05-27
This all sounds good. We all appreciate that you turned in the hard drive to the detectives. Hopefully they can find who this belonged too so your work wont go wasted. I've took a break from Linux for awhile but I installed the latest release and now im back. I will be working on the Ubuntu CE Wiki more once the next release of Ubuntu CE is out. And the website that you have been working on looks more than great.

---

### Post by mhancoc7 on 2008-05-27
> **Matthew Wiebelhaus said:**
> This all sounds good. We all appreciate that you turned in the hard drive to the detectives. Hopefully they can find who this belonged too so your work wont go wasted. I've took a break from Linux for awhile but I installed the latest release and now im back. I will be working on the Ubuntu CE Wiki more once the next release of Ubuntu CE is out. And the website that you have been working on looks more than great.

Hi Matthew,
Thanks for the kind words. The thing is that the authorities know who it belongs to. It is just a matter of going through the 'system'.

I plan on really beefing up the wiki. My hope is that the wiki can serve as the place to get info on installing stuff like e-sword and such since I don't believe I am going to be able to include it in future releases.

Thanks for your kind words about TheJesusTV.com. I have really enjoyed working with it and hope to continue to have it grow.

Thanks, Jereme

---

### Post by Matthew Wiebelhaus on 2008-05-27
So are you getting money for a new laptop or are they giving it back?

---

### Post by pastormick on 2008-05-27
Hi Jereme --

I've been watching this thread unfold and have to add my voice to the vote of confidence you have obviously earned by your actions. Unfortunately, like it or not, we can be slammed for doing the right thing just as easily as doing the wrong - you could also read that 'easy' - thing. 

I also look forward to the next release of UCE - it's encouraging to see how far it's come in such a short time. And be encouraged on the new project; it looks great!


Blessings,
Mick

---

### Post by waspinator on 2008-05-27
I'm sorry to have offended you; it was not my intention. Objectively though I am sure that you could come to a similar conclusion about the Japanese, (that they indeed are a perverted race), and that they spread their 'culture' to others, as seen in the American child rapist who has fallen. I hope he will change his ways now that he has returned to America. I will try to keep philosophical debate out of this forum, since I realize it is for Ubuntu.

I thank you for your hard work on UCE, and hope that you will be inspired to continue. In my opinion, a very important part of UCE is the parental control feature, and I hope that you continue to develop on your excellent work.

May your safely return to America.

Waspinator

---

### Post by mhancoc7 on 2008-05-28
> **Matthew Wiebelhaus said:**
> So are you getting money for a new laptop or are they giving it back?

I was actually reimbursed for the laptop. My 'orignial" laptop is still "in custody" and will be destroyed once the trial is over or the case has been closed.

> **pastormick said:**
> Hi Jereme --

I've been watching this thread unfold and have to add my voice to the vote of confidence you have obviously earned by your actions. Unfortunately, like it or not, we can be slammed for doing the right thing just as easily as doing the wrong - you could also read that 'easy' - thing. 

I also look forward to the next release of UCE - it's encouraging to see how far it's come in such a short time. And be encouraged on the new project; it looks great!


Blessings,
Mick

Thanks for those kind words. I am really hoping to get the next release out soon. I am working hard on it as we speak. :)

> **waspinator said:**
> I'm sorry to have offended you; it was not my intention. Objectively though I am sure that you could come to a similar conclusion about the Japanese, (that they indeed are a perverted race), and that they spread their 'culture' to others, as seen in the American child rapist who has fallen. I hope he will change his ways now that he has returned to America. I will try to keep philosophical debate out of this forum, since I realize it is for Ubuntu.

I thank you for your hard work on UCE, and hope that you will be inspired to continue. In my opinion, a very important part of UCE is the parental control feature, and I hope that you continue to develop on your excellent work.

May your safely return to America.

Waspinator

I appreciate your apology. I do not agree with you at all though. I have been living in Japan for 3 years now and feel like I have a fair understanding of their customs and lifestyle. To blame a group of people based on their race/culture for the actions of some one else is just an example of pure racism. I am not exactly sure what case you are talking about, but I have seen tons of examples that would show that we (Americans) are the horrible people.

Anyway, I do agree that this is not the place to discuss this. If you feel that you must respond then could you please create a thread in the Backyard and let me know so we can continue.

Thanks, Jereme

---

### Post by Matthew Wiebelhaus on 2008-05-28
I have to agree with Jeremy because all countries and cultures have many things wrong with them. The United States even has alot of perverted people there right now so it probably isn't right to say that the Japanese is the ones to blame.

---

### Post by mhancoc7 on 2008-05-28
> **Matthew Wiebelhaus said:**
> I have to agree with Jeremy because all countries and cultures have many things wrong with them. The United States even has alot of perverted people there right now so it probably isn't right to say that the Japanese is the ones to blame.

Especially since, in this case, the "pervert" is an American. 

Jereme

---

### Post by Phlinux on 2008-05-28
> **waspinator said:**
> I'm sorry to have offended you; it was not my intention. Objectively though I am sure that you could come to a similar conclusion about the Japanese, (that they indeed are a perverted race), and that they spread their 'culture' to others, as seen in the American child rapist who has fallen. I hope he will change his ways now that he has returned to America. I will try to keep philosophical debate out of this forum, since I realize it is for Ubuntu.

I thank you for your hard work on UCE, and hope that you will be inspired to continue. In my opinion, a very important part of UCE is the parental control feature, and I hope that you continue to develop on your excellent work.

May your safely return to America.

Waspinator


@waspinator:

The Bible makes no racial distinction when it teaches that the heart is desperately wicked: [KJV] Jeremiah 17:9: The heart is deceitful above all things, and desperately wicked: who can know it? 

It also makes it very clear that when we accept Jesus Christ as our LORD and Saviour that there is no longer racial, status-related, or gender-based distinction: [KJV] Galatians 3:28: There is neither Jew nor Greek, there is neither bond nor free, there is neither male nor female: for ye are all one in Christ Jesus.

Unfortunately with comments like yours I'm left thinking that you have very little understanding of God's nature and scripture in general. Do I just give up on my Japanese wife, my Japanese friends, and Japanese people in general and give them over to God's judgment, or do I stay here and do my part to fulfill HIS great commission to go into ALL the world? 

Please prove my assessment of you wrong by at least taking back your comments... and then people may even begin to take your non-philosophical comments regarding Ubuntu CE's direction seriously.

Blessings Phil

---

### Post by gusjones on 2008-05-28
+1 I wholeheartedly agree with Phlinux. Waspinator, perhaps you might reconsider your comments and take correction in this matter. I have found myself that often when I speak in haste, I must in the end apologise and retract after a period of thoughtful reflection.

---

### Post by waspinator on 2008-05-28
I agree that every culture has its faults. But we cannot be blind when it comes to recognizing what they are. The politically correct would have you believe that we are all equal, but we are not. Every culture has its strengths and weaknesses, and until we accept them we cannot help others or ourselves.

I try to offer constructive criticism, but sometimes I fall victim to my own blind rage. Child rapists, and those who create them, make me *very* angry, but I realize we must show compassion to all sinners to be able to help. After looking back on the matter I realize that the destruction of the Japaneses would not solve our sexual problems, and that God would most definitely not approve of my thoughtless comments. Sin exists in all of us and we must struggle to keep it out of our hearts. 

I hope that in the future I will be better able to control my rage and am truly sorry for any hurt I have caused.

---

### Post by mhancoc7 on 2008-05-29
> **waspinator said:**
> I agree that every culture has its faults. But we cannot be blind when it comes to recognizing what they are. The politically correct would have you believe that we are all equal, but we are not. Every culture has its strengths and weaknesses, and until we accept them we cannot help others or ourselves.

I try to offer constructive criticism, but sometimes I fall victim to my own blind rage. Child rapists, and those who create them, make me *very* angry, but I realize we must show compassion to all sinners to be able to help. After looking back on the matter I realize that the destruction of the Japaneses would not solve our sexual problems, and that God would most definitely not approve of my thoughtless comments. Sin exists in all of us and we must struggle to keep it out of our hearts. 

I hope that in the future I will be better able to control my rage and am truly sorry for any hurt I have caused.

I appreciate your apology. I am not Japanese, nor am I married to a Japanese women. I am simply an American who has been living in Japan for a number of years. I do agree that we can't turn a blind eye to problems and that sometimes be "politically correct" is not always in keeping with the truth of things. However, I do not believe that any one group should be singled out due to their ethnicity and blamed for the actions of anyone else. Have we not learned anything from the holocaust or the civil rights movement. I grew up in the Alabama and I know all too well about discrimination. I am a white male, so I do not know it as well as those who faced it directly. However, I do know that racism exists and is destructive. It flourishes in our ignorance of others and we should avoid it at all costs.

I understand how it is to speak too quickly. I have done that more times than I care to remember. I just hope that you will look towards the Japanese with compassion and not a sense of hatred.

God Bless, Jereme

---

### Post by david_kt on 2008-05-29
People make mistake, and I think Waspinator has clearly regretted for what he has written earlier. It is difficult to always do the right things, but it is even more difficult to admit our mistakes.

As such, I think Waspinator has done a great job, and it is time to move foward.

DK

---

### Post by mhancoc7 on 2008-05-29
> **david_kt said:**
> People make mistake, and I think Waspinator has clearly regretted for what he has written earlier. It is difficult to always do the right things, but it is even more difficult to admit our mistakes.

As such, I think Waspinator has done a great job, and it is time to move foward.

DK

I totally agree. I know I have made my share of mistakes.

Jereme

---

### Post by Diggs808 on 2008-06-28
Jerome,
Thanks for your hard work on Ubuntu CE!  It was the distro that got me hooked on Ubuntu.  I don't use it on my personal laptop but I do use it on a house laptop that guests in my home use.  Unfortunately, I have some trouble using a VPN client with DansGardian (for work related stuff) so I have to keep it off.  

One suggestion that I was going to make is this.  I don't know how you are packaging the Distro but there is a way to create your own customized distro using a program called RemasterSys.  The way that I use it to support my family members who are converting over to Linux using Dell Laptops is to build a distro with all the needed packages and repos, then create a redistributable distro dvd with that program.  Plus, It allows you to create a live CD environment without any hassle.  

If you would like info please feel free to PM me through here....I check the forums often.

---

### Post by Ritz Cracker on 2008-07-02
Hi there folks. I just wanted to ask how far the work with Ubuntu CE 8.04 is going... I am using general Ubuntu 8.04 (with Gnome) and it is really working better than the earlier releases of Ubuntu. In fact, I don't want to go back to an earlier version of Ubuntu just to use Ubuntu CE. Would be nice if the transformation script could be updated to work with Ubuntu 8.04..

---

### Post by Eutaw on 2008-07-03
I started with Ubuntu CE 7.01, then upgraded to 8.04, keeping the CE distinctives, no problem

---

### Post by Ritz Cracker on 2008-07-04
> **Eutaw said:**
> I started with Ubuntu CE 7.01, then upgraded to 8.04, keeping the CE distinctives, no problem

Ok. I will try that next time I am going to format my laptop :P (If Ubuntu CE 8.04 have not been released then)

---

### Post by seremina on 2008-07-05
Jereme,

I'm a Catholic Christian myself. I love your Ubuntu CE concept. I am just sorry I could not use it. I had to use Wubi Ubuntu 8.04.1 and I hope your Ubuntu CE will come out as a Wubi version. I would be really interested in it. If that can't be accomplished, then I would suggest a a pendrive version that'll work well in a 1 GB pendrive.

I thank you so much for listing your packages on your website. I have grabbed Virtual Rosary, so far. I just have to grab E-Sword now, too. Where do I find any additional Bibles and resources for it from?

---

### Post by david_kt on 2008-07-05
> **seremina said:**
>  I just have to grab E-Sword now, too. Where do I find any additional Bibles and resources for it from?

Dear Seremina,

For E-sword, you could try to install it manually using below instruction:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

If you face problem installing it or adding additional bibles, please let me know.

DK

---

### Post by seremina on 2008-07-06
Thank you so much, though that wasn't my question. I do have Jereme's auto-install package. What I am asking is where to find any add-ons for E-Sword? I am new to the program; I am tired of the Windows-only Bible program I bought and would like to try out something that's free and more community-driven rather than commercial-driven. The Bible program I bought has too few add-ons and not enough Bibles. All it gives is KJV or other Protestant versions. :( They're great for apologetics... but not for study.

---

### Post by GerhardKA on 2008-07-06
my question now, when Ubuntu CE 8,04 comes raus? if I read can the fact that one already works on it last it probably not more for a long time or?

---

### Post by david_kt on 2008-07-06
> **seremina said:**
> Thank you so much, though that wasn't my question. I do have Jereme's auto-install package. What I am asking is where to find any add-ons for E-Sword?

What I understand is Jeremy has some issue with license to continue e-sword auto install package. Anyhow, if you already have add-ons on your windows, you could copy and paste those add-ons to:


/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword

If you could not paste it using normal nautilus, open terminal and run:
```
gksudo nautilus
```

DK

---

### Post by beta.tester on 2008-07-08
> **seremina said:**
> Thank you so much, though that wasn't my question. I do have Jereme's auto-install package. What I am asking is where to find any add-ons for E-Sword? I am new to the program; I am tired of the Windows-only Bible program I bought and would like to try out something that's free and more community-driven rather than commercial-driven. The Bible program I bought has too few add-ons and not enough Bibles. All it gives is KJV or other Protestant versions. :( They're great for apologetics... but not for study.

Greetings Seremina

In Gnomesword there is the Douay Rheims version (shown as DRC:) I use it for my studies also :l) Not sure but I believe the DRC is in the e-sword. If it is not (I suspect it is) you can use:

(type:) sudo apt-get install Gnomesword <press ENTER key> (in a terminal window with a space as shown between the words)

Peace and all good

Greetings from another Christian who is also a Catholic :)

ps You have tried to change the source from local to remote, then refreshed, gone to install and opened bible => English +> lots and lots pls DRC and then clicked on INSTALL and seen the extra versions available?

---

### Post by christianLINUX on 2008-07-15
I read with interest this thread.

I would like to congratulate the efforts of the people in bringing out the Christian Edition of Ubuntu.

I would support to have esword and also on multiple CDs since there are many who would want to go for this option.

I would also want other DE options to be explored since gnome, KDE are more bloated than the others. Since they are more bloated people also require systems that are matching their system requirements.

gnome : RAM 384
KDE   : RAM 512

with higher processor specifications.

There are many who don't come under this category.

Hope this will be looked into when the next update is done.

God bless

---

### Post by nubdora on 2008-07-23
I'm new to Linux and I think the applications in CE will help me greatly in my Christian walk. In fact, I'm going to switch over from Hardy x64 to CE 7.04 and was wondering how the fellow above (Eutaw) could update but still keep the CE distinctives (I'm guessing web filtering, Bible apps, etc)? Also, would it be possible for me to update to x64 Hardy and keep the CE distinctives?

---

### Post by Eutaw on 2008-07-24
Hi nubdora
I had installed CE from the liveCD, and had esword up and running. I dual boot with Vista on my home pc and have been using esword for years (I'm a pastor). When Hardy 8.04 was released, I went to the site in CE and downloaded the upgrade. My main usage is the esword and Firefox. I have the wwjd toolbar for surfing, and dansguardian for filtering, and Open Office suite. For these and other apps you might need or want, you can get help here for downloading and tweaking, once you get specifics. 
Rick

---

### Post by k3lt01 on 2008-08-08
Hi everyone.

Just had a quick read through of this thread and thought I might just tell anyone interested that much of the "important" stuff in CE edition is actually in the Repositories of the standard Ubuntu edition.

Just go to Synaptic and click on the list and type "dansgaurdian" for example and it comes up on your screen. Click the box to install and its done. The same goes for GnomeSword, BibleTime, and Bible Memorizor. If you specifically want Windows style Bible programs install WINE and then install them, if they work let the people at Winehq know so they can put it on their list of working programs.

For those who want added security for safer surfing you can modify your hosts file to with extra entries which block unsavoury sites. Firefox also allows add-ons that help to make it even more secure than it already is with regards to unwanted scripts and advertisements.

I had and used UbuntuCE 7.04 and would use CE again if it was released in a new version but I want a stable PC and one that I can add to. I use mine for teaching and technology is a compulsory part of the curriculum in all subjects so I need to keep up to date with systems.

---

### Post by illumin8 on 2009-03-08
[I]Ok, so here is what has slowed things down. Ubuntu CE has many contributors without which Ubuntu CE could not exist. However, at the core Ubuntu CE is a one person "operation". I do not mean to diminish the efforts and contributions of the many Team members and forum members who have contributed. I just want people to understand the the website, distro, and all of the custom packages (dansguardian gui, esword installer, etc) are all built on my laptop. Which brings me to a bizarre situationi that started back in September.
[/I]

Thats the great thing about opensource...or truly open source...someone always has a copy of what you lost. The cord of 3 strands....

---

### Post by tom4jean on 2009-03-16
I just wanted to bring peoples attention to a great way to filter without installing software.
[www.opendns.com](www.opendns.com) is free and filters at the DNS server level.
I have it on my wireless router and it filters all the computers in my house including wireless laptops and the desktops that are plugged into the router.
It is MUCH easier to configure then Dansgaurdian and you don't have any software running on your computer using resources except for one small program that will update your IP address that you need if you use a dynamic IP address.

---

### Post by JSuresh on 2009-03-19
> **tom4jean said:**
> I just wanted to bring peoples attention to a great way to filter without installing software.
[www.opendns.com](www.opendns.com) IP address.

Does opendns have an option to send email notifications when you try to access blocked sites?  I'm searching everywhere for a good implementation of this for linux.

---

### Post by tom4jean on 2009-03-19
> **JSuresh said:**
> Does opendns have an option to send email notifications when you try to access blocked sites?  I'm searching everywhere for a good implementation of this for linux.

Sorry, No email notifications that I am aware of, just general reports when you log in at the website that let you see what sites where visited. They are not categorized onto users or anything, just listed with how many hits etc...
I don't know of a Linux filter with that.
tom

---

### Post by Anygma on 2009-03-24
> **k3lt01 said:**
> Hi everyone.

Just had a quick read through of this thread and thought I might just tell anyone interested that **[COLOR="DarkRed"]much of the "important" stuff in CE edition is actually in the Repositories of the standard Ubuntu edition.[/COLOR]**

Just go to Synaptic and click on the list and type "dansgaurdian" for example and it comes up on your screen. Click the box to install and its done. The same goes for GnomeSword, BibleTime, and Bible Memorizor. If you specifically want Windows style Bible programs install WINE and then install them, if they work let the people at Winehq know so they can put it on their list of working programs.

For those who want added security for safer surfing you can modify your hosts file to with extra entries which block unsavoury sites. Firefox also allows add-ons that help to make it even more secure than it already is with regards to unwanted scripts and advertisements.

I had and used UbuntuCE 7.04 and would use CE again if it was released in a new version but I want a stable PC and one that I can add to. I use mine for teaching and technology is a compulsory part of the curriculum in all subjects so I need to keep up to date with systems.

hi everyone, absolute newbie here, just finished reading the tread and felt compelled to join.  

i'm so new to all this that i haven't installed any ubuntu yet. it just dawned on me to look into linux a few days ago but i've spent many hours each day studying my options.  i already have the OS burnt. the only thing that i'm waiting for now is to get the Wii version of the workout program that is on this PC because it's the only place where there is room to do a workout. and the kids love that software. 

now, just like k3lt01 said, most of the applications in CE are available in the repository.  i'm a home school mom and after deciding on Ubuntu, i was thrilled to discover edubuntu, but still leaning toward the standard ubuntu until i found out that edubuntu use the normal ubuntu and just have a second cd for the specific educational settings, theme and applications.  they also seem to keep up to date on the releases.  

i just found out about ubuntu christian edition last night, which i thought was really nice concept but i'm wondering why it's not worked on as a separate cd like edubuntu?  that way i could install both :D  

and also being on a separate cd would resolve the issue of having to sacrifice some applications for the purpose of keeping to the limited space, because i suspect, if it is like any other OS, to take advantage of the ever more powerful hardware, the software will have to be bigger and eventually leave very little room for any applications to tag along in the one cd.

---

### Post by david_kt on 2009-03-24
> **Anygma said:**
> hi everyone, absolute newbie here, just finished reading the tread and felt compelled to join.  

i'm so new to all this that i haven't installed any ubuntu yet.

If you are very new to linux, I suggest to use linux mint as a start:

[http://www.linuxmint.com/](http://www.linuxmint.com/)

It is based on ubuntu as well. And from there you could slowly install any applications you want. You do not need to install multiple OS, just 1 is enough.

But if you want out of the box internet filtering, try ubuntu CE, and install other applications you need from there.

DK

---

### Post by k3lt01 on 2009-03-25
> **david_kt said:**
> If you are very new to linux, I suggest to use linux mint as a start:

[http://www.linuxmint.com/](http://www.linuxmint.com/)

It is based on ubuntu as well. And from there you could slowly install any applications you want. You do not need to install multiple OS, just 1 is enough.

But if you want out of the box internet filtering, try ubuntu CE, and install other applications you need from there.

DKI have to disagree with you David, I and many others hadn't used Linux before and started with Ubuntu.

Hi Anygma, Ubuntu is a great OS and the variants help to make it more useful for specific purposes. While it is true that the repositories contain everything that is available the concept of a specialist Ubuntu distribution like CE or Edubuntu makes it easy for people to get the style of distribution they need without extra packages that are not useful.

I would highly recommend Edubuntu to you as a good educational tool. If you can set it up with a Server and Thin Clients you will have a brilliant educational package. Then if it suits your purpose you can add CE type packages.

---

