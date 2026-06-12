---
title: "ATI/AMD's real stance on Open Source drivers; not what you've heard recently"
date: 2007-05-16
forum: The Cafe
---

### Post by jiminycricket on 2007-05-16
[http://airlied.livejournal.com/43520.html](http://airlied.livejournal.com/43520.html)

> **AMD/ATI drivers media grab**
So a marketing dude said something about open drivers for AMD/ATI gpus and working with the community.

Can people get excited when AMD/ATI actually do something rather than showboat for media headlines?

Like ATI won't let me release my [r500 source]("http://airlied.livejournal.com/31180.html") because I shouldn't have used a utility they gave me under NDA on those cards, now the thing is I done the correct thing and contacted them asking if I could release the code, so far this has just been stonewalled by their Linux driver management and their "legal" department, this isn't the action of a company trying to interact with the community or one that gives a rats **** about community..

Something most people may not know is that ATI do have engineering resources to support the open source driver, we get patches to it via Novell or RH every so often, these patches are invariably of dubious quality and are to fix Dell or IBM servers, however in fixing Dell or IBM they invariably break at least one other working platform if not more, again this is not interacting with the community this is pushing code via vendors who don't really understand the intricacies of the driver...

Maybe if ATI/AMD fix the above two things I might believe they are interested in working with the community... or even if someone from either side of the conglomerate was to contact me and ask how they could work with the open source driver going forward...

[http://digg.com/linux_unix/ATI_Real_Position_on_Open_Source_Drivers](http://digg.com/linux_unix/ATI_Real_Position_on_Open_Source_Drivers)

Just like many of us suspected in the past threads on ATi "open sourcing" their drivers (I'll bet it'll turn out just as good as Creative's purportedly open source, then binary, then delayed, then [cancelled]("http://ubuntuforums.org/showthread.php?p=2639487") X-Fi drivers did).  ATI won't even let [X1***]("http://ubuntuforums.org/showthread.php?t=414194") card owners have at the bare minimum 2d use from an open source driver created in ***2006***.

---

### Post by Anthem on 2007-05-17
AMD wants it to be open-sourced, ATI does not.  AMD will win in the end, but it's going to take time.

---

### Post by joe.turion64x2 on 2007-05-17
> **Anthem said:**
> AMD wants it to be open-sourced, ATI does not.  AMD will win in the end, but it's going to take time.
AMD is the boss there, isn't it?

---

### Post by jiminycricket on 2007-05-17
AMD on ATI, last year: [http://liquidat.wordpress.com/2007/03/13/amdati-linux-interview-with-terry-makedon-the-head-of-software-development/](http://liquidat.wordpress.com/2007/03/13/amdati-linux-interview-with-terry-makedon-the-head-of-software-development/)

> Anyway, opening the drivers is no alternative for Makedon: first of all there is too much 3rd party technology in the drivers &#8220;like for example compression algorithms&#8221;. The 3rd party companies certainly wouldn&#8217;t allow AMD to release that source code.
Second there is too much IP in the drivers. He compares the situation with McDonalds which will not release the recipe to the sauce of the BigMac also: &#8220;It is just not economically justifiable to do that.&#8221;
Also, an NDA like Intel uses is not possible because - according to Makedon - there is not &#8220;so much 3D intelligence&#8221; inside the Intel drivers.
However, he adds that the 2D part is already open source and that there are discussions to also release other parts like the install routines as open source as well. He cannot say never, but that AMD will not take this path for at least the next 6 till 12 months.

That little manpower problem could be solved by giving driver specs to people who actually *want* to write drivers for GNU/Linux, Terry...hint, hint.  I truly don't understand how anyone could arbitrarily buy ATI for Linux because of their low-quality, too.

---

### Post by dspari1 on 2007-05-17
I don't think that everything has to be opensource in order to be successful. The real problem with ATI is that their drivers for Linux just plain sucks.

With the restricted driver management, Nvidia drivers install and work out of the box. (kubuntu is still behind in this department). Cedega and Beryl under AIGLX work perfectly. Do I care that it's not open source? Not really as long as what I am getting is of high quality. 

The point is that if AMD/ATI do not want to open their drivers, then at pressure them into writing good drivers by voting with your wallet. I know we are a minority, but as more people migrate to Linux, they will be pressured to compete eventually.

---

### Post by prizrak on 2007-05-17
> **dspari1 said:**
> I don't think that everything has to be opensource in order to be successful. The real problem with ATI is that their drivers for Linux just plain sucks.

With the restricted driver management, Nvidia drivers install and work out of the box. (kubuntu is still behind in this department). Cedega and Beryl under AIGLX work perfectly. Do I care that it's not open source? Not really as long as what I am getting is of high quality. 

The point is that if AMD/ATI do not want to open their drivers, then at pressure them into writing good drivers by voting with your wallet. I know we are a minority, but as more people migrate to Linux, they will be pressured to compete eventually.

Actually nVidia drivers have quite a few very annoying problems. It's pretty much impossible to suspend/hibernate if you are using them. If you have a mobile card and use Beryl/Compiz the card runs out of memory causing a "black window", that is you have the frame around a completely black window. There is also no power management in nVidia drivers for Linux despite having it in Windows, this has and adverse effect on battery life. 

nVidia knows about all of the above problems and has known for a while yet they have not been fixed. The powere management issue has been around for more than one release of their drivers. It is quality software sure but if it were open source all those issues could have been remedied already. Not to mention that the driver could have been included out of the box with no outrage in the community. There are also pretty serious maintenance benefits with the source available. 

I believe in using what works well but there are cases where open source is just plain better.

---

### Post by dspari1 on 2007-05-17
> **prizrak said:**
> Actually nVidia drivers have quite a few very annoying problems. It's pretty much impossible to suspend/hibernate if you are using them. If you have a mobile card and use Beryl/Compiz the card runs out of memory causing a "black window", that is you have the frame around a completely black window. There is also no power management in nVidia drivers for Linux despite having it in Windows, this has and adverse effect on battery life. 

nVidia knows about all of the above problems and has known for a while yet they have not been fixed. The powere management issue has been around for more than one release of their drivers. It is quality software sure but if it were open source all those issues could have been remedied already. Not to mention that the driver could have been included out of the box with no outrage in the community. There are also pretty serious maintenance benefits with the source available. 

I believe in using what works well but there are cases where open source is just plain better.

Turn off the blur effects and use AIGLX instead of raw Nvidia mode in Beryl to get rid of the black borders. I haven't gotten a black border since.

---

### Post by prizrak on 2007-05-17
> **dspari1 said:**
> Turn off the blur effects and use AIGLX instead of raw Nvidia mode in Beryl to get rid of the black borders. I haven't gotten a black border since.
Thanks, I know though. I'm also not using Beryl I'm using Feisty's Desktop-Effects. Point is more along the lines of problems with closed source software than it is with that particular issue.

---

### Post by DoctorMO on 2007-05-17
> Do I care that it's not open source? Not really as long as what I am getting is of high quality. 

Typical short sighted user response. what you don't understand is that there are programmers out there making your computer work; they are doing it for free and can not fix any problems you may have with these proprietory drivers.

You only get hurt in the end because convenience isn't a replacement for the advantages of freedoms.

---

### Post by prizrak on 2007-05-17
> **DoctorMO said:**
> Typical short sighted user response. what you don't understand is that there are programmers out there making your computer work; they are doing it for free and can not fix any problems you may have with these proprietory drivers.

You only get hurt in the end because convenience isn't a replacement for the advantages of freedoms.
Now we just have to make freedom convenient ;)

---

### Post by dspari1 on 2007-05-17
> **DoctorMO said:**
> Typical short sighted user response. what you don't understand is that there are programmers out there making your computer work; they are doing it for free and can not fix any problems you may have with these proprietary drivers.

You only get hurt in the end because convenience isn't a replacement for the advantages of freedoms.

Linux has room for both open source as well as proprietary.

If you want to talk about short sighted, think about what would happen if Nvidia compromises their secrets by opening their drivers. I rather have a high quality videocard with proprietary drivers like Nvidia does than a substandard videocard with open drivers like Intel does. 

Intel videocards do not have anything worth keeping in secret, so it's OK for them opening their source. Neither Gamers nor Graphics professional do not even consider buying videocards from Intel because it is only suitable for office environments and nothing more. How is Intel going to care about keeping drivers secret if the only information that they are disclosing is information that everyone else already has? Both Nvidia and ATI have a lot more to lose.

If ATI and Nvidia both feel that opening their drivers will compromise their secrets that are keeping them in business, then they have every right to keep their drivers closed (or the portion that they feel should remain closed) if they desire to. 

However, what I do want is proper driver support, and I believe Nvidia has done a good job thus far.

---

### Post by Extreme Coder on 2007-05-17
Intel has revealed that it will develop discrete graphics soon, with open drivers as well.

Extreme Coder

---

### Post by jiminycricket on 2007-05-17
> **dspari1 said:**
> Linux has room for both open source as well as proprietary.

If you want to talk about short sighted, think about what would happen if Nvidia compromises their secrets by opening their drivers. I rather have a high quality videocard with proprietary drivers like Nvidia does than a substandard videocard with open drivers like Intel does. 

Intel videocards do not have anything worth keeping in secret, so it's OK for them opening their source. Neither Gamers nor Graphics professional do not even consider buying videocards from Intel because it is only suitable for office environments and nothing more. How is Intel going to care about keeping drivers secret if the only information that they are disclosing is information that everyone else already has? Both Nvidia and ATI have a lot more to lose.

If ATI and Nvidia both feel that opening their drivers will compromise their secrets that are keeping them in business, then they have every right to keep their drivers closed (or the portion that they feel should remain closed) if they desire to. 

However, what I do want is proper driver support, and I believe Nvidia has done a good job thus far.

I on the other hand have an nVidia card and am NOT happy with the drivers.  nVidia drops support frequently and doesn't contact developres.  Prizrak already stated the problems with their drivers which I have also experienced.  You said they deliver drivers for high end graphics professionals; I concur.  They don't care about desktop users like us.

Have you sent any dumps to Nouveau?  You might find in the end that free software developers can (and have) do a much better job than people who care mostly about Windows give Linux drivers as an afterthought.  Like you said, Intel has high quality open drivers.

Especially people with things like old TNT2s can't get Beryl to run because nVidia dropped support; if Nouveau can support their cards, there's that much more hardware support and portability and of course fewer bugs.

---

### Post by prizrak on 2007-05-17
> Intel videocards do not have anything worth keeping in secret, so it's OK for them opening their source. Neither Gamers nor Graphics professional do not even consider buying videocards from Intel because it is only suitable for office environments and nothing more. How is Intel going to care about keeping drivers secret if the only information that they are disclosing is information that everyone else already has? Both Nvidia and ATI have a lot more to lose.

Intel actually has a market share that is higher than both ATI and nVidia combined last I heard it was 60%. The thing is that for alot of things Intel cards do just fine and are a great alternative to both ATI and nVidia. On the other hand both ATI and nVidia also have integrated and low end solutions. There is also a matter of ATI/nVidia chipsets that must use closed source drivers. I'm not sure how well they support Linux on that front but you must admit that support for a chipset is quite a bit more important than video card. 

ATI/nVidia have absolutely more to lose than Intel. If they are licensing 3rd party technology there is no way they could ever release their drivers. On the other hand if they just release the specs to their cards the community could create the driver. Perhaps they will not be as polished and capable at first but they will provide a certain minimum right off the bat.

This thread isn't really about whether proprietory is good or bad, the problem here is that they have promised open drivers and are now backpeddling out of it. No one made them promise open drivers. For the most part we have accepted how the things were done and started trying to reverse engineer things on our own.

---

### Post by Polygon on 2007-05-17
i heard somewhere that intel is going to get into the powerful 3d graphics card market, i hope thats true cause that means open drivers and even more competition = better products all around.

---

### Post by DoctorMO on 2007-05-17
> Linux has room for both open source as well as proprietary.

Only if your really stupid, the only place for proprietary code in the end is custom specification work. it does no good to go all idealogical by attempting to exact a middle ground on a political agenda because my point is that the practical system of proprietary drivers doesn't work, it can deliver once, maybe twice. but your in for a sharp shock in the end because you've sold out your freedom to look after your own property to someone else on the nod that it is some how fair to occupy a middle ground between two ideologies you find extremist. In the end it doesn't matter, systems are systems and they don't care what you think. You'll come a cropper in the end.

> If you want to talk about short sighted, think about what would happen if Nvidia compromises their secrets by opening their drivers. I rather have a high quality videocard with proprietary drivers like Nvidia does than a substandard videocard with open drivers like Intel does.

I'm thinking about it.... thinking about it... still thinking about it.... nope. can't see anything bad happening should allow the public to understand how they build their cards. if they want protection why don't they use patents and at least allow us to understand how they work? oh wait you can't patent protocols and that's all we want to have. I don't care for their drivers to be honest but I'd like a law requiring all hardware makers to make their protocols available to customers.

> If ATI and Nvidia both feel that opening their drivers will compromise their secrets that are keeping them in business, then they have every right to keep their drivers closed (or the portion that they feel should remain closed) if they desire to.

Every right? I don't believe they do have every right. what about the rights of the customer to be able to maintain their legally paid for hardware?

> However, what I do want is proper driver support, and I believe Nvidia has done a good job thus far.

As long as it's closed source I'll consider it second rate and potentially risky.

---

### Post by Death_Sargent on 2007-05-17
> **joe.turion64x2 said:**
> AMD is the boss there, isn't it?

good point however as Novell learned first hand just because they are the boss does not mean their subordinates will be defiant of opensource changes.

---

### Post by prizrak on 2007-05-18
> Only if your really stupid
Dude you need to calm down a bit.

---

