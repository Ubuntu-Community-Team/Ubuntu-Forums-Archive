---
title: "$ Ubuntu Software Center's paid application's security. Is there any?"
date: 2010-11-20
forum: The Cafe
---

### Post by Isaacgallegos on 2010-11-20
Sorry, I'm having trouble finding this information:

I want to know if developers have any anti piracy security for purchased applications, which are done through 10.10's Ubuntu Software Center "For Purchase" section. In other words, once the purchased application is on someone's computer are there any deterrents in place to keep the user from freely redistributing the application? 

Thank you very much![COLOR="Red"][SIZE="5"]**&#9829;**[/SIZE][/COLOR]

---

### Post by czr114 on 2010-11-20
I recall Canonical announcing that the app store will have functionality for managing reinstallations when transferring purchased apps from one system to another.

I have seen nothing about client-side DRM, and I doubt that's coming to an open platform.

Preventing the transfer of paid software from one computer to another in violation of the license will require application logic making calls to an activation server. While the app store channel can prevent over-installation by registered accounts, there is no way it can prevent someone from accessing the binaries directly and transferring them to another machine without having some sort of kernel-level DRM.

It's a moot point, really. There has yet to be any application or scheme which has proven resistant to the best efforts of the top level warez crews. If people want to pirate the application, then it will be pirated. The best defense against that is adding value through regular updates (be sure to update the binary), good support, and paid subscriber services.

The best you can hope to do is prevent casual copying by limiting activated installations through app logic, and discouraging license sharing by using a key tied to a person's identity (name, email, etc).

If you do implement some sort of key, you'll want to use asymmetric cryptography to ensure that no key generators can be built by reverse engineering the application. That forces the warez crews to re-crack each binary release.

Honestly, the best thing you can do is prevent casual copying through application logic, and encourage sales by providing some sort of service which can't be infinitely copied by anyone with a BT client or Rapidshare account.

---

### Post by jdong on 2010-11-20
Currently there's no DRM-like application security system. Developers have to rely on the good will of the users to appreciate the fact that there's no DRM and show that they're responsible enough to not need any DRM.

Personally, I'd rather have platform-wide  standardized DRM managed by Canonical than every developer get paranoid and implement some DIY anti-copy method themselves. This model reminds me an awful lot of the iOS jailbroken community's "app store", and the things that developers do to ensure their paid apps aren't copied are crazy and border on privacy invasion.

---

### Post by aysiu on 2010-11-20
Amazon's MP3 store has no DRM, and I think it does just fine. I know I buy almost all my music from Amazon MP3. I don't think even iTunes as DRM any more.

I realize that's music and not applications, but piracy is for everything.

---

### Post by Isaacgallegos on 2010-11-20
> **czr114 said:**
> It's a moot point, really. There has yet to be any application or scheme which has proven resistant to the best efforts of the top level warez crews.

Of course not, but having some level of built-in default deterrent, which sounds like a great idea, will be an added incentive to providers. 

> **jdong said:**
> Personally, I'd rather have platform-wide  standardized DRM managed by Canonical than every developer get paranoid and implement some DIY anti-copy method themselves. 

And it would mean less development and resources required by the app developer to protect the product.

Oh well.. 11.04 maybe...

---

### Post by NCLI on 2010-11-20
As jdong said, there is currently no DRM system in place in the USC. It is definitely something Canonical is looking at, as I recall it being mentioned before, but it is not currently on the [Ubuntu Software Center roadmap]("https://wiki.ubuntu.com/SoftwareCenter#Roadmap").

Personally, I think it's a waste of time. All DRM methods are eventually broken, even methods engineered by huge corporations such as Sony and Microsoft, this won't be any different.

I know they're going to do it anyway, because it will attract more developers, but it will really just be for show.

---

### Post by Isaacgallegos on 2010-11-20
> **aysiu said:**
> Amazon's MP3 store has no DRM, and I think it does just fine. I know I buy almost all my music from Amazon MP3. I don't think even iTunes as DRM any more.

I realize that's music and not applications, but piracy is for everything.

Correct, which works fine if you plan on selling at a high volume at a low price, but protection would be better at low volume high-priced sales, which would be nice to see come to Ubuntu.

---

### Post by NCLI on 2010-11-20
> **Isaacgallegos said:**
> Correct, which works fine if you plan on selling at a high volume at a low price, but protection would be better at low volume high-priced sales, which would be nice to see come to Ubuntu.
Why? All of the popular music available from Amazon is already available from various sources for free(Neatly packaged by album and/or artist), and so will all of the popular applications from the USC, DRM or not.

I would feel better about buying stuff from the USC without DRM.

---

### Post by aysiu on 2010-11-20
If you're planning to sell your software to Ubuntu Linux users at a high price... good luck with that, unless it's a native (non-Wine) Adobe Creative Suite.

---

### Post by NCLI on 2010-11-20
> **aysiu said:**
> If you're planning to sell your software to Ubuntu Linux users at a high price... good luck with that, unless it's a native (non-Wine) Adobe Creative Suite.
Why do you say that? If it's a quality application which cannot be matched by free software, I think the people who need it will buy it.

Do you have any reason to think they won't?

---

### Post by Simian Man on 2010-11-20
> **aysiu said:**
> If you're planning to sell your software to Ubuntu Linux users at a high price... good luck with that, unless it's a native (non-Wine) Adobe Creative Suite.

New games are around $50 at least and people buy them.  Compare that to a song from Amazon which is around $1.

---

### Post by czr114 on 2010-11-20
> **Isaacgallegos said:**
> Of course not, but having some level of built-in default deterrent, which sounds like a great idea, will be an added incentive to providers. 


The operative question must be "who is deterred?"

If the goal is to deter the application from making it into pirate ecosystem, then that effort will fail. If the app is good enough to catch the attention of the warez crews, then it will be cracked.

The only realistic chance to avoid lost sales is something which keeps a casual user from tarring up the install directory and sending it to a friend. That's going to require application logic binding the software to the hardware, in the absence of a DRM framework.

Application-specific logic is the best answer. The problem with providing one hardware activation API is that crackers need only provide one loader or OS patch.


> **jdong said:**
> 
Personally, I'd rather have platform-wide  standardized DRM managed by  Canonical than every developer get paranoid and implement some DIY  anti-copy method themselves. This model reminds me an awful lot of the  iOS jailbroken community's "app store", and the things that developers  do to ensure their paid apps aren't copied are crazy and border on  privacy invasion.

Platform wide DRM will completely kill goodwill among the FOSS  community. Short of wholesale for-profit GPL violations, there isn't  anything worse which could be done.

The problem with DRM is that it must be implemented at the kernel level  to even stand a chance of being effective. Add-in modules won't work as  they are too easily cracked.

The open nature of the kernel ensures that anyone who needs to break the DRM can build a kernel free of DRM pollution.

With all that code being open anyway, the DRM would be quickly rendered  moot among anyone who has the intent to commit piracy. It will be the  legitimate buyers and those not even in the market who are crippled by the DRM and offended by  having their system locked down by an external agent.

If Canonical wants to go down that road, a defective by design campaign will surely follow.

Part of the point of open software is that it is resistant to lockouts and control of users by publishers.

It's one thing to implement code which restricts the number of complimentary re-downloads of a paid application. It's another to make Ubuntu systems serve an external master.

---

### Post by bryncoles on 2010-11-20
When it was announced that yahoo would be the default search in Firefox, people were up in arms -- it was the worst corporate shilling ever, and people were ready to leave Ubuntu for good over it. With the proposed move to Unity as the default desktop, people are up in arms. It is the worst corporate shilling and people are ready to leave Ubuntu for ever over it. 

Now, were having a mature discussion about the merits and plausibility of implementing kernel-level drm, and no one has threatened to leave Ubuntu over it yet? What's with people -- this is actually an issue!

Well, I'll throw my toys out of the pram. I'll leave Ubuntu, and GNU/Linux over this. I'll get me of of those 'Difference Engines' or something...

---

### Post by zekopeko on 2010-11-20
> **jdong said:**
> Currently there's no DRM-like application security system. Developers have to rely on the good will of the users to appreciate the fact that there's no DRM and show that they're responsible enough to not need any DRM.

Personally, I'd rather have platform-wide  standardized DRM managed by Canonical than every developer get paranoid and implement some DIY anti-copy method themselves. This model reminds me an awful lot of the iOS jailbroken community's "app store", and the things that developers do to ensure their paid apps aren't copied are crazy and border on privacy invasion.

I think that the best solution would be Steam-like DRM. It's very sensible and non-intrusive. You would have a standardized DRM platform that would be opt-in.

Steam did what all the other DRM schemes failed to do. They made DRM a general non-issue simply because they made paid software with minimal amounts of DRM hassle free. The users win, the developers/publishers win.

---

### Post by phrostbyte on 2010-11-20
Adding any form of DRM to the GNU/Linux OS is sacrilege. [-(

Although I would find it almost amusing if Canonical did so. As others have said, there are companies that spend millions engineering super complicated DRM schemes only to have them cracked by a high school student in Sweden on his Spring break. :P

---

### Post by Isaacgallegos on 2010-11-20
> **zekopeko said:**
> I think that the best solution would be Steam-like DRM. It's very sensible and non-intrusive. You would have a standardized DRM platform that would be opt-in.

Steam did what all the other DRM schemes failed to do. They made DRM a general non-issue simply because they made paid software with minimal amounts of DRM hassle free. The users win, the developers/publishers win.

Exactly! [img]http://ubuntuforums.org/images/icons/icon2.gif[/img]There could be a new and exciting market that will try to compete with the neighboring open-source repos, which have always done really well. Providing protection for the purchased software will only bring a new kind of developer which, in turn, will help Canonical make a larger profit. Why is that so bad? I want them to do well.

---

### Post by zekopeko on 2010-11-20
> **phrostbyte said:**
> Adding any form of DRM to the GNU/Linux OS is sacrilege. [-(

Considering how many people want Steam on Linux apparently it's not.

---

### Post by czr114 on 2010-11-20
> **phrostbyte said:**
> Adding any form of DRM to the GNU/Linux OS is sacrilege. [-(

It does go against the basic spirit of the OS, and would be a quite reasonable basis for switching distros.

Unity is well-intentioned and can be easily replaced. No harm there.

The app store is also well-intentioned and can never be opted into (provided they don't start forcing it). While it might hurt future FOSS development, the software itself isn't a problem for those who don't use it.

The sort of kernel-level DRM necessary to have even a remote chance at effectiveness is an absolute sacrilege and would affect everyone who installed something defective by design. That's a much different proposition from users choosing to opt into hardware activation following informed consent.

(By "DRM", I'm referring to the sort of low-level module that enforces access policies on encrypted binaries, not a Steam-like download restriction, or application logic checking licensing status.)

> **Isaacgallegos said:**
> Exactly! [IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG]There could be a new and exciting market that will try to compete with the neighboring open-source repos, which have always done really well. Providing protection for the purchased software will only bring a new kind of developer which, in turn, will help Canonical make a larger profit. Why is that so bad? I want them to do well.

It can be bad if it encourages developers to defect from FOSS projects. The pro and con arguments were hashed out fairly evenly in a recent thread.

---

### Post by czr114 on 2010-11-20
> **zekopeko said:**
> Considering how many people want Steam on Linux apparently it's not.
To be fair, Steam is a combination of download count restrictions and application logic. It's not infesting the OS itself the way media restriction does on Windows/OSX or the way the TCG has proposed for end-user TPM modules.

There's a big divide, both ideologically and practically, between an application that won't allow unlicensed installation and an OS which acts as an agent of someone other than the machine's owner in the enforcement of third-party licensing schemes and the proliferation of content which is unintelligible except through interpretation by a low-level black box.

---

### Post by zekopeko on 2010-11-20
> **czr114 said:**
> To be fair, Steam is a combination of download count restrictions and application logic. It's not infesting the OS itself the way media restriction does on Windows/OSX or the way the TCG has proposed for end-user TPM modules.

There's a big divide, both ideologically and practically, between an application that won't allow unlicensed installation and an OS which acts as an agent of someone other than the machine's owner in the enforcement of third-party licensing schemes and the proliferation of content which is unintelligible except through interpretation by a low-level black box.

Why are we even talking about OS-level DRM when it's simply not going to work on Ubuntu and is nigh improbable that Canonical is going to take that route? The only sane thing they can do is Steam-level DRM.

---

### Post by czr114 on 2010-11-20
> **zekopeko said:**
> Why are we even talking about OS-level DRM when it's simply not going to work on Ubuntu and is nigh improbable that Canonical is going to take that route? The only sane thing they can do is Steam-level DRM.
Because low-level DRM is real DRM, and that's what would be required to even have a chance at slowing down piracy.

Something like:

```

if ( ! licensed )
{
     exit();
}

```

fails as effective DRM in the real world. It's little more than a check to keep honest people honest.

Patching one single opcode (jne->je/nop) in the generated binary renders the above code worthless.

Using the term DRM in the context of software or media evokes feelings of a black box that doesn't release content until certain conditions are met. While it can technically apply to other things, many people generally assume it's more than a registration check. That's one linguistic quirk which arose out of the buzzword itself being much newer than the older registration checks which managed digital restrictions prior to "DRM" solutions being flogged as a complete answer to executable patching or broadcast flag removal.

I chose to discuss both approaches because one is absolutely worthless for deterring professional pirates in the real world, and the other can actually be a barrier to lower-skilled crackers.

I agree that anything low-level and closed such that it might have any practical effect of slowing piracy is a complete non-starter. Canonical would have a revolt on their hands if they implemented it - which is why developers should understand the difference and not hope for a "DRM" panacea to stop piracy. The best they can do is stop a copying of the application directory with an hardware check and provide enough service, updates, and support so that the licensed product is superior to the pirate version which will emerge eventually.

---

### Post by Isaacgallegos on 2010-11-21
You realize having no protection for purchased software is going to drive, what could be a large number of, potential developers away, right?

Windows and Android might not have to worry about this, since they have most of the global market share. (Yes Android is that big now.)

---

### Post by Isaacgallegos on 2010-11-21
> **phrostbyte said:**
> Adding any form of DRM to the GNU/Linux OS is sacrilege. [-(

Everyone! I'm not talking about protecting software installed through the Ubuntu Software Center that's not for purchase. I think a few here believe that's what I'm talking about...

---

### Post by zekopeko on 2010-11-21
> **Isaacgallegos said:**
> You realize having no protection for purchased software is going to drive, what could be a large number of, potential developers away, right?

Windows and Android might not have to worry about this, since they have most of the global market share. (Yes Android is that big now.)

The problem with Windows is that it doesn't have a per application DRM that is part of the Windows development platform so various developers implemented their own DRM schemes that were in some cases very nasty and anti-user.

AFAIK Android has DRM but it's opt-in.

---

### Post by Dr. C on 2010-11-21
> **zekopeko said:**
> The problem with Windows is that it doesn't have a per application DRM that is part of the Windows development platform so various developers implemented their own DRM schemes that were in some cases very nasty and anti-user.

AFAIK Android has DRM but it's opt-in.

The biggest problem with Microsoft Windows is DRM and its support for DRM, not the lack of DRM. DRM has done enormous damage to Microsoft, it products and its shareholders since Microsoft turned to the dark side and embraced DRM 10 years ago. If Bill Gates can become a billionaire and the world richest man by selling propriety software ***without*** DRM, I am certain that vendors in the Ubuntu Software Center can sell software without DRM. There is no need to cripple Ubuntu with DRM as Windows was crippled 10 years ago. 

By the way there is allready enough GPL v3 code in Ubuntu to prevent any kind of effective DRM in Ubuntu anyway, thanks to Richard Stallman and the FSF, so there is not much for those of us who see DRM as the evil it really is to worry about.

---

### Post by Simian Man on 2010-11-21
> **Dr. C said:**
> If Bill Gates can become a billionaire and the world richest man by selling propriety software ***without*** DRM, I am certain that vendors in the Ubuntu Software Center can sell software without DRM.
It's true that Gates made most of his money before DRM was commonplace, but this was also a time before the proliferation of high-speed internet connections.  Even if Word was **free** to download, I'd have rather bought it in a store than download it on my old 56K connection :).

> **Dr. C said:**
> By the way there is allready enough GPL v3 code in Ubuntu to prevent any kind of effective DRM in Ubuntu anyway, thanks to Richard Stallman and the FSF, so there is not much for those of us who see DRM as the evil it really is to worry about.
Ubuntu is not a single piece of software, but a collection of a ton of different programs.  The fact that some are licensed under a certain license is irrelevant to the licenses of other pieces.  There is no legal problem with including DRM'd components in a Linux distro.

---

### Post by Dr. C on 2010-11-21
> **Simian Man said:**
> It's true that Gates made most of his money before DRM was commonplace, but this was also a time before the proliferation of high-speed internet connections.  Even if Word was **free** to download, I'd have rather bought it in a store than download it on my old 56K connection :).


Ubuntu is not a single piece of software, but a collection of a ton of different programs.  The fact that some are licensed under a certain license is irrelevant to the licenses of other pieces.  There is no legal problem with including DRM'd components in a Linux distro.

DRM was commonplace in the 1980's and 1990's. It was just called "copy protection" and consisted of deliberately creating bad sectors on 5.25in floppies to create "key disks" among other bizarre things. Also software in those days was a lot smaller and would fit on a handful of floppy disks. Downloading Windows 3.1 at 56K is not that different from downloading  Windows Vista via broadband time wise. 

What GPL v3 prevents is the taking away of root from the end user in order to implement DRM. Taking away root is critical to the DRM in iPhones, iPads, Android Phones, other smart phones, Game Consoles, eBook readers and of course the TiVo. Once these devices are "rooted" or "jailbroken" it is the end of the DRM.

---

### Post by phrostbyte on 2010-11-21
> **Dr. C said:**
>  
What GPL v3 prevents is the taking away of root from the end user in order to implement DRM. Taking away root is critical to the DRM in iPhones, iPads, Android Phones, other smart phones, Game Consoles, eBook readers and of course the TiVo. Once these devices are "rooted" or "jailbroken" it is the end of the DRM.

[quote=General Public License v3]
No covered work shall be deemed part of an effective technological measure under any applicable law fulfilling obligations under article 11 of the WIPO copyright treaty adopted on 20 December 1996, or similar laws prohibiting or restricting circumvention of such measures.

When you convey a covered work, you waive any legal power to forbid circumvention of technological measures to the extent such circumvention is effected by exercising rights under this License with respect to the covered work, and you disclaim any intention to limit operation or modification of the work as a means of enforcing, against the work's users, your or third parties' legal rights to forbid circumvention of technological measures.
[/quote]

Basically, the GPLv3 allows for DRM, but it doesn't allow you to sue people for breaking the DRM system. 

For example: TiVo can still have DRM, but they can't sue people for breaking their DRM system. If they do, they will be in violation of the GPLv3 and thus committing copyright infringement themselves.

The whole philosophy of the GPL is not to tell you what you are allowed to with a piece of software, but stop you from telling OTHERS what they are allowed to do (especially though legal action). 

IE: If you want to make a DRM system or a nuclear weapon from GPL software, that's your call. But you can't prevent me from using the same system in any way I want. :)

---

### Post by phrostbyte on 2010-11-21
> **zekopeko said:**
> so various developers implemented their own DRM schemes that were in some cases very nasty and anti-user.

Wait are you implying that there is a DRM system that is not very nasty and anti-user? :lol:

I figure DRM is by definition anti-user, since it's entire purpose is to restrict what the user can do with a piece of software. 

It's kind of interesting (in a sad way) that in this industry there are people who spend their entire careers working to make their principal product, software, less useful overall. 

I wish I could make an analogy to some other industry, but I don't there are any analogies. It's kind of embarrassing. I'm sure once the computer industry matures a little more there will be laws preventing defective by design product.

---

### Post by Isaacgallegos on 2010-11-21
> **Dr. C said:**
> What GPL v3 prevents is the taking away of root from the end user in order to implement DRM. Taking away root is critical to the DRM in iPhones, iPads, Android Phones, other smart phones, Game Consoles, eBook readers and of course the TiVo. Once these devices are "rooted" or "jailbroken" it is the end of the DRM.

Good good point, but [img]http://ubuntuforums.org/images/icons/icon4.gif[/img]_I've never said anything about kernel-level DRM in any of my posts._ I'm simply suggesting some form of protection by the software center for purchased applications. How could that possibly be bad for Ubuntu, even if it's not perfect security? It's unobtrusive to those who don't buy and helpful for the providers that make sales, by offering minimal protection...

---

### Post by czr114 on 2010-11-21
> **Isaacgallegos said:**
> Good good point, but [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]_I've never said anything about kernel-level DRM in any of my posts._ I'm simply suggesting some form of protection by the software center for purchased applications. How could that possibly be bad for Ubuntu, even if it's not perfect security? It's unobtrusive to those who don't buy and helpful for the providers that make sales, by offering minimal protection...

Because the honest users get all the hassles of registration and DRM and it does nothing to slow down the pirate scene. Zero. Zip. Zilch. Nada.

You could spend a year building what you think is the perfect anti-piracy system, and it will be undone by a pirate in maybe a day. The licensed users have to put up with that system, not the hardcore pirates and frustrated licensed users who head straight to TPB or IH to get around that system.

Developers can't have an arms race with pirates without making collateral damage of legitimate users.

The best an application developer can do is prevent an app's installed files from being tarred up and emailed to a friend, by way of a little application logic.

The next step in the arms race is very low level black boxes acting to interpret completely encrypted binary content. The serial check and hardware activation are about as useful as a lock on a screen door. They can be removed by a 13 year old kid in maybe half an hour, up to a few if the packer is nasty.

---

### Post by Isaacgallegos on 2010-11-21
> **czr114 said:**
> Because the honest users get all the hassles of registration and DRM and it does nothing to slow down the pirate scene. 

Why would it be any more "added registration"? You buy through the USC and your account stays with them. Why assume it would require anything more?


You quoted me saying, "How could that possibly be bad for Ubuntu, even if it's not perfect security? It's unobtrusive to those who don't buy and helpful for the providers that make sales, by offering minimal protection..."

How is that implying a "perfect anti-piracy system"? Those are you exact words.

I honestly feel like you didn't read my post.

---

### Post by Simian Man on 2010-11-21
> **Dr. C said:**
> What GPL v3 prevents is the taking away of root from the end user in order to implement DRM. Taking away root is critical to the DRM in iPhones, iPads, Android Phones, other smart phones, Game Consoles, eBook readers and of course the TiVo. Once these devices are "rooted" or "jailbroken" it is the end of the DRM.

You totally missed the point.  The GPL only applies to *works that are licensed under the GPL*.  The fact that there is GPLv3 software on a computer doesn't put any restrictions on other software the user wants to install.  If someone added DRM to a program that was already licensed under the GPLv3, then that would be a problem.

If what you said was true, then if I installed a GPLv3 program like gcc on my Windows machine, then that would make the games I have that use DRM violate the gcc license.  Obviously that's not right, and there's no difference here.  I'm not arguing that distributing DRM on Linux is a good idea, but it most certainly would be legal.

---

### Post by Dr. C on 2010-11-21
> **Simian Man said:**
> You totally missed the point.  The GPL only applies to *works that are licensed under the GPL*.  The fact that there is GPLv3 software on a computer doesn't put any restrictions on other software the user wants to install.  If someone added DRM to a program that was already licensed under the GPLv3, then that would be a problem.

If what you said was true, then if I installed a GPLv3 program like gcc on my Windows machine, then that would make the games I have that use DRM violate the gcc license.  Obviously that's not right, and there's no difference here.  I'm not arguing that distributing DRM on Linux is a good idea, but it most certainly would be legal.

The difference in Ubuntu is that key operating system components (many of the GNU tools) that need the permission of root to modify them are licensed under GPL v3. So one cannot "tivoize" Ubuntu to protect the DRM without infringing on the GPL v3 copyrights. 

Microsoft spent 5 years and billions of dollars rewriting Windows between XP and Vista in order to attempt to protect the DRM in Windows by preventing the administrators from having access to certain process. Ever wonder why it took 5 years for Microsoft to come up with Windows Vista, only to receive such a poor reception in the marketplace? It is because Windows Vista was really all about DRM. 

The real wrong with DRM is that it breaks the trust between software developers, and users and among the software developer communities. This is bad enough for propriety software companies, such as Microsoft or Apple, but it is even worse for FLOSS projects. A case in point one of the common ways to "root" an Android phone is to find privilege escalation vulnerabilities in Linux. We now actually have the unfortunate situation that certain vulnerabilities in Linux are kept secret in order to "root" Android devices. Ubuntu users are already paying the price for the DRM in many devices that use Linux. If Linux were released under GPL v3 there would not be any incentive to keep these vulnerabilities secret.

---

### Post by czr114 on 2010-11-21
> **Isaacgallegos said:**
> Why would it be any more "added registration"? You buy through the USC and your account stays with them. Why assume it would require anything more?

Right. That's one hassle. In terms of cost, giving up that privacy to buy a trivially-priced app will drive people to piracy, as the need to register and pay for yet another service is a nuisance which outweighs whatever the trivial price might be.

That's not what I was talking about, though. Many apps use some sort of serial registration scheme to supposedly prevent piracy. There isn't any reason to believe this practice will stop, especially among pre-existing applications being transitioned to the app store.

Thus, "added registration" would be that above and beyond what's necessary for the channel itself.

> **Isaacgallegos said:**
> 
You quoted me saying, "How could that possibly be bad for Ubuntu, even if it's not perfect security? It's unobtrusive to those who don't buy and helpful for the providers that make sales, by offering minimal protection..."

How is that implying a "perfect anti-piracy system"? Those are you exact words.

I honestly feel like you didn't read my post.
It can be unobtrusive and it's still little more than an enhanced honor system. If it doesn't get in the way of the user, then great.

Many anti-piracy technologies do get in the way of the legitimate user.

None of them have stopped pirate releases.

It's one thing to not vocally object to something which isn't excessively ideologically impure and not a practical hassle, but that's speaking purely of a hypothetical system. I'm trying to balance that with the real-world nuisances and lack of effectiveness.

---

