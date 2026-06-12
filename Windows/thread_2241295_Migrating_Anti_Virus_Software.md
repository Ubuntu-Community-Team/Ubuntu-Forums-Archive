---
title: "Migrating Anti Virus Software"
date: 2014-08-25
forum: Windows
---

### Post by term3 on 2014-08-25
[FONT=arial]Dear all,[/FONT]
first of all. i would like to apologize if this is not the right place to ask.

[FONT=arial]i'm new to Info Security. [/FONT]
[FONT=arial]I would like to ask an opinion on migrating anti virus software for an Enterprise (1000 users).[/FONT]
[FONT=arial]Let say, i currently used AV from company A, and want to migrate the antivirus software to AV from company B. I have made a study on how we would like to deploy it. We plan to use Microsoft SCCM to uninstall current AV and install the new AV. My concern is on the virus spread if the installation of new AV if unsuccessful. Is there any best practice on changing AV software. What other things that need to put in consideration? [/FONT]

[FONT=arial]Anyone to share their experience.[/FONT]
[FONT=arial]Thanks in advance.[/FONT]

---

### Post by mikewhatever on 2014-08-25
[s]Try a MS support channel. We only support Ubuntu and derivatives here.[/s]

...never mind, we support everything here!

---

### Post by QIII on 2014-08-25
Although a Microsoft forum might be best, users are quite welcome to post in Other Operating Systems and Projects.

There are those who use Linux who are also proficient in Windows.

---

### Post by bashiergui on 2014-08-25
Do you have a single AV console to manage all the hosts in your environment? Or are you just installing AV independently on each endpoint?

I presume you have tested the new AV on some systems to ensure it's not going to do something stupid like quarantine Word throughout your enterprise .

If it were me I would have a weekend change window. One day I would rip out all existing AV. Then once I've confirmed it's completely out of my environment I'd install the new one everywhere. have a script that would do the same on endpoints that were offline during the change.

Problems ensue generally when you've got a few AVs on one box. They tend to conflict and/or quarantine each other.
> My concern is on the virus spread if the installation of new AV if unsuccessful.
I hope you're not solely relying on AV to prevent infections.   Anyway it's simple to test that AV is installed with an EICAR. Any AV will have an EICAR you can run on a random sampling of endpoints when you're done. Or build it into the deployment script.

---

### Post by term3 on 2014-08-25
Hi all,
Thanks for the reply.

I have tested the new AV on my testing machine, everything as expected but i think the real environment PC/laptop/server will be different right. 
Multi OS with different hardware spec with min 512MB RAM. 

And yes, i have the centralized AV management for the existing, where i can do uninstalling process from it.
i plan to go for a pilot testing first, with 100 users, and see what is the success rate from there before roll out to other users in stages (group by group).

i like the idea using EICAR testing, i can script it to test if the AV is working and at the same time it will communicate to centralized server to report it. End to end testing. =D

what do you mean by this? > [COLOR=#000000]I hope you're not solely relying on AV to prevent infections[/COLOR]
Did i need to consolidate the network that currently in process of migrating AV software?

---

### Post by bashiergui on 2014-08-25
I prefer to err on the side of caution, so your testing plan sounds solid to me. Make sure you're testing all the different OS's and hardware combinations. Just to be clear, the main concerns are software conflicts, cpu usage, and false positives.

---

### Post by bashiergui on 2014-08-26
> what do you mean by this? I mean AV costs more than it's worth generally. [http://mobile.techworld.com/news/security/3412999/antivirus-software-a-waste-of-money-for-businesses-report-suggests/](http://mobile.techworld.com/news/security/3412999/antivirus-software-a-waste-of-money-for-businesses-report-suggests/)

AV is often a requirement by regulations and business partners. I wouldn't get too hung up on which one you're using. Find a reasonably priced one and stick with it (assuming no production issues). 

Spend your time and budget on other things that will actually improve your security posture. EMET is free and is MUCH better at preventing malicious behavior [http://support.microsoft.com/kb/2458544](http://support.microsoft.com/kb/2458544)
You could build a squid proxy pretty cheap with OSS. 
Snort is free & is an open source IDS.

Meh. I tried not to be preachy. FAIL.

---

### Post by SeijiSensei on 2014-08-26
Like bashiergui, I think the best solution is to keep malware from coming into the organization at all.  At a minimum that means virus scanning of all inbound emails, but you should consider pushing all web requests through Squid with [SquidClamAV]("http://squidclamav.darold.net/") installed as well.  I would also disable USB ports on as many machines as possible, and certainly configure your AV software to alert you if someone inserts an infected USB stick.  People love to bring in USB drives with photos of their kids and some nice hidden malware as well.

---

### Post by term3 on 2014-08-26
Hi [COLOR=#000000]bashiergui/[/COLOR][COLOR=#000000]SeijiSensei,

Thanks for the input. Just to ask u, did i need to do some sort of benchmark in term of performance / security incident before and after the project?
Does it really matter?

For the testing part, i have identified 20 application, that need to avoid any conflicts with the new AV. 
After finish the testing ,then i deploy to first 100 users, for real production testing. 

Let say for example, during the deployment, there is incident of virus spread through network.
What is the best practice/ SOP to handle this issues. Have any standard to follow?


[/COLOR]

---

### Post by term3 on 2014-08-26
[COLOR=#000000]Hi SeijiSensei,

Just additional info, i will set the policy of the AV for device blocking for some user.
How you disable USB in your environment? 

[/COLOR]

---

### Post by bashiergui on 2014-08-26
> Let say for example, during the deployment, there is incident of virus spread through network.What is the best practice/ SOP to handle this issues. Have any standard to follow?If the only security product you have in the environment is AV, then let AV quarantine and remove the infections.  I can't imagine what else you could realistically do.

---

### Post by bashiergui on 2014-08-26
> **term3 said:**
> [COLOR=#000000]Hi SeijiSensei,
Just additional info, i will set the policy of the AV for device blocking for some user.
How you disable USB in your environment? [/COLOR]If you're not filtering email attachments at all then I don't really see the point of blocking USB ports. It would just encourage users to email themselves the malware instead of transfer it via USB stick.

---

### Post by SeijiSensei on 2014-08-27
> **bashiergui said:**
> If you're not filtering email attachments at all then I don't really see the point of blocking USB ports. It would just encourage users to email themselves the malware instead of transfer it via USB stick.

I absolutely agree that you should start by filtering email before you do anything else.  Still there is malware that can hide on a USB stick and runs with Autostart.  That kind won't be transferred by email.

I wasn't responsible for managing the USB ports.  I believe you can disable them using Active Directory policies.

To give you a sense of how pervasive infected email remains, the mail filtering software for that organization I mentioned with some 200+ users intercepted ***69 infected messages just yesterday alone***.  We use [MailScanner]("http://www.mailscanner.info/") with spamassassin and ClamAV to scan every message when it arrives.  Clean items are then forwarded to the organization's Exchange server.

---

### Post by sffvba[e0rt on 2014-08-27
In our organization that is seen as highly critical and also very much targeted USB's have been disabled from working on the PC's period.  When the IT Dept. needs to do something that can't be done via the network they have to use written CD/DVD's...

---

### Post by bashiergui on 2014-08-29
> **not found said:**
> In our organization that is seen as highly critical and also very much targeted USB's have been disabled from working on the PC's period.  When the IT Dept. needs to do something that can't be done via the network they have to use written CD/DVD's...
I agree it's critical. If the OP isn't going to do anything other than run AV on endpoints then I see it a little bit like filling the door and window in on this castle:
[ATTACH=CONFIG]255940[/ATTACH]

---

