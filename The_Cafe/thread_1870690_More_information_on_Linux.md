---
title: "More information on Linux"
date: 2011-10-27
forum: The Cafe
---

### Post by codym9184 on 2011-10-27
I have been assigned a project exploring the advantages of switching my companies computers over to Linux from Windows. Is there anyone who can advise me on this.

---

### Post by 11jmb on 2011-10-27
IMHO the best thing about Linux over Windows is the community. Because it is free and open source, people take ownership, and more bugs get fixed faster. MS hides behind closed-source and eula's, so important bugs can go unfixed for quite a while.

Do you want to know about advantages Windows has for enterprise customers? because there are a few.

---

### Post by jonobr on 2011-10-27
Hello there


this is a pretty open ended question.
The advantages could go on for a while, and there are disadvantages too.

I recommend going at this from a different direction.
You need to evaluate what is required from your new deployment.
What software and services are required and how your going to move them over.

I think the important thing about considering a move like this is will things be at least equivalent to what you left behind.

You could have all the advantages in the world, however, if  a few users cant use Microsoft project or an equivalent, or  
there is something that only works with windows and will never work with ubuntu, your advantages will be outweighed by a bunch of users who cant do stuff

---

### Post by oldos2er on 2011-10-28
Not an Ubuntu support question; moved to Community Cafe.

---

### Post by Paqman on 2011-10-28
> **codym9184 said:**
> I have been assigned a project exploring the advantages of switching my companies computers over to Linux from Windows.

That really depends on what your company does with its IT, how big it is, how much money you've got to spend, and what your objectives are for switching.

---

### Post by Paddy Landau on 2011-10-28
In general, the bottom line for any company is, well, the bottom line.

[LIST]
[*]Will moving to Linux save the company money?
[LIST]
[*]license costs
[*]hardware costs
[*]IT costs
[*]staffing costs
[*]support contracts (Windows vs. Canonical)
[*]staff satisfaction (for those frustrated by Windows problems)
[*]reduced costs of antivirus
[/LIST]
 
[*]Will moving to Linux cause the company to spend money?
[LIST]
[*]retraining
[*]redundancies
[*]data conversion
[*]hiring new staff
[*]staff dissatisfaction (for those emotionally attached to Windows)
[/LIST]
 
[*]Will moving to Linux cause money to be lost?
[LIST]
[*]lost data (e.g. losing the ability to read Publisher files)
[*]lost functionality (e.g. mandatory Windows-specific programs that do not **easily and flawlessly** run on PlayOnLinux (Wine))
[*]inability to share data with associate companies that rely on Windows
[*]current hardware that is incompatible with non-Windows (e.g. certain printers and fax machines; telecommunications equipment)
[/LIST]
 
[/LIST]
You also need to persuade the people at the top.

[LIST]
[*]What emotional attachment (however much they may deny it) does the top management have for Windows?
[*]Does the top management answer to a higher boss outside the company?
[*]Who *really* makes the final decision?
[/LIST]
Additionally, the managers involved will want to "play safe". Therefore, you need to look at:

[LIST]
[*]Stability: Will the move from Windows to Linux be phased, controlled, measured and reversible?
[*]Reliability: Will Linux give the same reliability as Windows?
[*]Peers: Have other major corporations, schools and government organisations successfully gone the Linux route? (The answer is 'yes', but you need to list specific examples.)
[*]Interoperability:
[LIST]
[*]Will Linux be able to connect to the company network?
[*]Will directors still be able to take their work home, use it on their Windows computer, and bring it back to work and continue working on it?
[/LIST]
 
[/LIST]
On top of all that, nothing convinces quite like a demonstration.

[LIST]
[*]Organise a demonstration of two computers side-by-side.
[LIST]
[*]Run through several examples of something you would do at the company, demonstrating them simultaneously.
[*]Demonstrate how you can start something on the Windows computer; copy it to Linux and carry on working; and copy that back to Windows and still continue to work.
[*]Demonstrate how the Windows and Linux computers can see each others' public folders -- but only if that fits with your company's policy.
[*]Demonstrate how the Linux computer can access the company's network.
[*]Bonus points:
[LIST]
[*]1 point if Linux doesn't crash even once
[*]20 points each time Windows crashes
[*]200 points if Windows gets a porn virus while you are demonstrating :evil:
[/LIST]
 
[/LIST]
 
[/LIST]
Finally, you are important:

[LIST]
[*]Do not become emotionally attached to the outcome, otherwise your discussions will be ignored. Be objective and dispassionate, and be honest with the downsides.
[/LIST]

---

### Post by SeijiSensei on 2011-10-28
I'd start by looking at the server side of your business. Tasks like authentication, file-sharing, web service, and e-mail might be replaceable by Linux servers.  If you're heavily invested in Microsoft technologies (Exchange, Active Directory, SharePoint, etc.), chances are good that switching to Linux will be very disruptive and may not be worth the cost of changing.  You probably have an IT staff with a lot of investment and experience running Windows networks and few comparable people with solid knowledge of Linux.

If you're not so invested in the Windows world, I'd start small and consider using Linux for web services (Apache), DNS (BIND), and file-sharing (Samba).  If you're looking to run an internal mail server, Linux is a fine choice for that as well.  (Depending on the size of your userbase, you can run all these services on a single box.)  If you're running an expensive SQL server from Oracle or Microsoft, you might be able to replace it with a Linux box running PostgreSQL depending on how savvy your SQL folks are and how flexible the client software making SQL queries is.

Linux on the desktop is a whole other matter.  Now you're faced with retraining your workforce to use an entirely different desktop environment and an array of unfamiliar applications: LibreOffice instead of Microsoft Office, Thunderbird instead of Outlook, GIMP instead of Photoshop, etc. Linux advocates will say that such retraining shouldn't be all that hard, but there's a not-insignificant group of computer users who react badly if an icon is moved on their desktops, never mind having to use an entirely new piece of software. That's why I suggest bringing Linux into the server room first.

---

