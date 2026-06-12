---
title: "Windows File Server with SubVersion/CVS"
date: 2007-05-10
forum: Server Platforms
---

### Post by munwin on 2007-05-10
OK, so we are redesigning our network.
We use Windows on the clients, and for most servers.
Yes, I am moving some selected servers to Linux.

The problems is thus:
We need a file server. 
Using Windows Server, and validating against our AD Domain is fine, but we need an additional bit.
The solution can be running on Ubuntu, RedHat or Windows. I don't care, as long as it works and is stable...
The clients must access the files, as usual. Permissions need to be validated against our AD Domain. NO additional logon/password request is acceptable.

Now, the tricky part.
Bearing in mind that NO additional work is to be requested from the user. 
They connect, open and save files as usual. AD does user validation silently.
I want it to work so that some version control package (be it CVS, Subversion, or whatever) see's that a file has changed, and commits the update. NO additional user interaction, remember.

The users use Windows Explorer. No plugins should be required. All "work" to be done server side.

The goal is to have a repository (which can be backed up), so we can go back to any previous version, and restore.

Basically equivalent to an incremental backup. But running constantly, so EVERY FILE is backed-up whenever it is changed...

Is this possible ?
Does this exist already ?
Even a commercial app would be OK.
It would make a KILLER app for an Ubuntu file server.

---

### Post by craigp84 on 2007-05-10
Hi,

You've got a couple of options, but you need to refine what you want here a bit more.

You mention samba etc. but it sounds like your just after a version control repository that doesn't prompt the user to add a note on their changes?

Then i interpret your goal as just being able to recover old revisions of files?

I dunno, you're giving me mixed messages here. It must be the windozer in you :) 

So if you want a version controlled repository, then you're looking to something like tortoiseSVN/CVS on the windows clients, or more likely given your (self-imposed?) constraints, miss out samba and go for the WebDAV support in SVN. The latter works, but means setting up web folders for the users, IIRC you can set up most of this client side via GPOs. Whatever, but you'd end up with a version control repository.

Backing up a VC repo is dead easy, so it could be an ok way to go. Long term though, you need to factor in space consumption. Remember you'd be saving a binary diff (in SVN's case) or the full file (in CVS's case) each time the user clicks save (the MS apps create a new temp file, delete the old unmodified one, then rename the new temp file).

The down side to this approach is the learning curve for your users is pretty steep. No matter where you go for your VC repo, it's a pretty difficult concept to grasp for some folks, so you'd need to think carefully about how much time you have to train the users.

If you just want backups, and to be able to recover old versions, look to something like rsnapshot, coupled with a read-only export / share from SAMBA. I've done this loads of times for home directories & shared folders, it's dead easy to setup, and just works.

The real benefit of this method is that it works exactly like users would expect. Most people take to this like a duck to water. I have nothing but positive things to say about this approach. It's also a hell of a lot faster.

To make it even easier, i normally roll out a link to the user's desktop which points to the read-only backup share. I don't remember fielding a single 'i lost my file' call after going live with this approach.

Highly recommended.

If you're after a document repository, somewhat like sharepoint, then there's *loads* of options, see google or freshmeat.

Alternatively, if you're already paying for the windoze licences, then there's Volume Shadow Copy + a client for XP which can be rolled out via GPO to allow anyone to recover old versions of the files. It's kinda flaky in my experience (hangs explorer.exe, but you can work around this quite easily). We migrated away from this in one job to the rsnapshot solution above.

There's also sharepoint on the windoze side, this gets good reviews in most places i look, but i don't have much first hand experience.

Other than that, i'd need more details about the specific business need.

-c

---

### Post by munwin on 2007-05-10
Thanks for the comments.
Some background. We're a Windows shop (for worse), and there will be no moving the clients from this - software written in VB, and supported by an external company. Short answer - NO, we CANNOT move from Windows on the clients.
The clients are either WinXP, or 2003 Terminal Server.
Terminal Server clients are PCs using Pilot Linux boot disks - highly recommended.
The clients save documents (mainly Word & Excel files) on a central (currently Windows) server.
What folders they can access is determined by AD groups and users.
We currently backup the folders each night to a tape archive.
The backup software (which shall remain nameless) is ..... we, let's just say I don't really like it, and leave it there.

So I'm thinking, why not use SVN in some way, to keep versions of all the files ? Or something similiar...

Our users are BASIC. To the extent that they call me over to their desk when a power cord falls out of their monitor, and "my computer doesn't work". I kid you not. That's why the requirement that it be invisible to them. They just won't cope. Before you ask, no educating them is not an option.

Below are the responses...

> Then i interpret your goal as just being able to recover old revisions of files?
Yes.

> The down side to this approach is the learning curve for your users is pretty steep. No matter where you go for your VC repo, it's a pretty difficult concept to grasp for some folks, so you'd need to think carefully about how much time you have to train the users.
As stated above - no go.

> If you just want backups, and to be able to recover old versions, look to something like rsnapshot, coupled with a read-only export / share from SAMBA. I've done this loads of times for home directories & shared folders, it's dead easy to setup, and just works.

The real benefit of this method is that it works exactly like users would expect. Most people take to this like a duck to water. I have nothing but positive things to say about this approach. It's also a hell of a lot faster.
Your views interest me, and I would like to subscribe to your newsletter !!! Tell me more.

> If you're after a document repository, somewhat like sharepoint, then there's *loads* of options, see google or freshmeat.
Will check them out, but no real need for this.

Am wishing for a Linux (Ubuntu) solution for this. I think it could fill a great need for small/medium business. Here's a file server for your Windows clients, it keeps a version of every file you ever save. Would be a great sell.
What would be needed would be an easy interface for admin, backup, etc. Maybe a way to say, OK, delete all versions of files older than xx days/months. Or maybe, archive to DVD all versions older than xx days/months.
See where I'm going - a package that "just works" for storing files.... None of the install Samba, then SVN, then config the clients, then, blah, blah - to hard. I'm thinking apt-get install file-server. Done. I know we won't get there (in this thread), that's OK, I like building stuff, but maybe an idea for Ubuntu.

Thanks again.

---

### Post by David Brown on 2007-05-10
Have you looked at FUSE?  Something like CvsFS might be of interest:
[http://fuse.sourceforge.net/wiki/index.php/FileSystems](http://fuse.sourceforge.net/wiki/index.php/FileSystems)
[http://cvsfs.sourceforge.net/](http://cvsfs.sourceforge.net/)

The idea of FUSE is that it lets you make user-level file systems - other software sees these as normal file systems on a mount point, but any reads or writes are translated into user-level commands.  So in this case, you have a cvsfs filesystem mounted and shared with samba.  Any writes to files will be translated into cvs check in commands, while reads will be translated into check out commands.

Another alternative would be to combine dnotify with rsync, rsnapshot, or some other snapshotting or backup software that copies using hard links where possible, or possibly a version control system.  The point is to use dnotify to watch the samba-shared directory, and take a snapshot any time something changes.

Remember, however, that all this is useless unless you have thought through how users will be able to see older versions of their documents.

---

### Post by craigp84 on 2007-05-10
Hmmm... you still come across as confused.

Where's the VoIP forums? Some things just don't lend themselves to discussion via text forums.

Windoze clients aren't so bad so long as you don't involve internet access, normally they work ok.

Windoze servers is where it goes downhill - for me anyway. Thankfully i no longer deal with those (2000ish CPUs Linux / Solaris only), so i am a happy man these days!

Maybe try going for [www.openfiler.com/screenshots/](www.openfiler.com/screenshots/) - rather than trying to bolt it all together yourself. Have someone else do it for you, then you can tweak as needed.

---

### Post by craigp84 on 2007-05-10
p.s. you touched a nerve with "easy interface" and "server" in the same post.

Great for desktops, but you really want your sysadmin to know exactly what he's doing, and a sysadmin that knows exactly what he's doing will choose power & flexibility over shiny config tools which rail road you into 1 or 2 specific configurations.

Encouraging people without the skills to believe they have the skills causes P1S1 outages. I've suffered as a result of too many of those too ever be able to agree with you on this.

Right now computing is not infallible. When things go wrong, it's really better if your man knows what he's doing.

---

### Post by David Brown on 2007-05-10
> **craigp84 said:**
> p.s. you touched a nerve with "easy interface" and "server" in the same post.

Great for desktops, but you really want your sysadmin to know exactly what he's doing, and a sysadmin that knows exactly what he's doing will choose power & flexibility over shiny config tools which rail road you into 1 or 2 specific configurations.

Encouraging people without the skills to believe they have the skills causes P1S1 outages. I've suffered as a result of too many of those too ever be able to agree with you on this.

Right now computing is not infallible. When things go wrong, it's really better if your man knows what he's doing.

I don't agree entirely with this philosophy.  Where do sysadmins get their skills?  From the same place as everyone else - partly from courses and education, from books, websites, from discussions with other experienced people, and from trial and error and learning experiences.  A great deal of what I know I have learned by trying things - by definition, I did not know exactly what I was doing at that time.  Clearly a good sysadmin will take steps to limit possible mistakes (such as using a test server first), but there will always be times when you are crossing your fingers and hoping you are not going to spend the weekend restoring the system from backups after a mistake.

There is also the question of what skills make sense for a particular sysadmin.  For example, if you need a basic dns setup, is there any point in learning the details of bind configuration?  Time and money spent on learning it, or employing someone who knows bind already, is wasted - you are better off using a simpler system like dnsmasq, or using a gui like webmin.  These will be more limited, and will hide you from some of the complexity, but they will make it easier and faster to configure the system, and make it far easier to get it right.

I'm not advocating windows-style point-and-drool interfaces for important server functions.  But there are good reasons for having front-ends that handle configuration of various services or functions.  You should know how these work, and be able to understand the results, but it's important to choose tools at the right level for the job.

---

### Post by craigp84 on 2007-05-10
> Where do sysadmins get their skills? From the same place as everyone else - partly from courses and education, from books, websites, from discussions with other experienced people, and from trial and error and learning experiences.

Exactly! This step is normally missed out when hand-holding-rail-roading-simple-as-can-be GUIs are introduced. Do you believe that simple GUIs encourage and develop understanding of the tasks they simplify? Show me a windows sysadmin that "gets" DNS - they're pretty rare in comparison to the number that don't understand it. Quite unbelievable given how *absolutely critical* DNS is to Active Directory (and nearly all the windoze admins will work in AD envs).

> For example, if you need a basic dns setup, is there any point in learning the details of bind configuration?

Probably not. Just as there is probably not much point in using bind for this if you're not going to learn it anyway. There are alternatives, which work for simpler deployments, and are extremely easy to "get" c.f. Dnsmasq.

Are you advocating people deploy software into production they don't understand and so cannot hope to support?

> Time and money spent on learning

This is normally a small / med business concern. Ideally everyone could get proper training before going live. In the real world this will clearly never be possible for a whole range of reasons.

I agree that sometimes you just have to hope for the best, and minimise risk wherever you can.

But show me anything here that's difficult? There's nothing that cannot be learned, noone's being asked to balance on a tightrope, or demonstrate high levels of hand-eye coordination - these are genuinely difficult if you cannot already do them.

It's certainly different coming from a windows background, but i strongly disagree that anything posed here is difficult.

---

### Post by David Brown on 2007-05-10
> **craigp84 said:**
> Exactly! This step is normally missed out when hand-holding-rail-roading-simple-as-can-be GUIs are introduced. Do you believe that simple GUIs encourage and develop understanding of the tasks they simplify? Show me a windows sysadmin that "gets" DNS - they're pretty rare in comparison to the number that don't understand it. Quite unbelievable given how *absolutely critical* DNS is to Active Directory (and nearly all the windoze admins will work in AD envs).

I am not advocating GUIs as a replacement for understanding the service or feature you are working with - I am advocating use of higher-level front-ends (GUI, or text-based - such as shorewall for iptables) in addition to the understanding, and as an alternative for learning the syntax of the underlying tools.  Thus you should not use webmin for bind configuration because you don't understand how DNS works - you should use it because it lets you set up a working bind configuration faster and with a lower chance of error than learning the bind syntax.
> 
Probably not. Just as there is probably not much point in using bind for this if you're not going to learn it anyway. There are alternatives, which work for simpler deployments, and are extremely easy to "get" c.f. Dnsmasq.

Are you advocating people deploy software into production they don't understand and so cannot hope to support?

No, I am merely suggesting that people can deploy software with an understanding of their functionality, but without being expert in the underlying tools and their syntaxes.

For a comparison, look at the world of embedded programming (as that's my main job - I am a sysadmin on the side).  When you are working with small processors, it is normally important to write small and fast code, since that translates into cheaper systems and lower power.  I think it is important for programmers to have an understanding of the assembly language for their target processor, but in almost all cases it makes more sense to program in C.  However, a developer who wants to use Visual Basic is definitely in the wrong job!
> 
This is normally a small / med business concern. Ideally everyone could get proper training before going live. In the real world this will clearly never be possible for a whole range of reasons.

I agree that sometimes you just have to hope for the best, and minimise risk wherever you can.

But show me anything here that's difficult? There's nothing that cannot be learned, noone's being asked to balance on a tightrope, or demonstrate high levels of hand-eye coordination - these are genuinely difficult if you cannot already do them.

It's certainly different coming from a windows background, but i strongly disagree that anything posed here is difficult.

I work for a small business - there are clearly different concerns, different balances, different requirements and different facilities for a large business.  If we want to use a new service or new software, then I have to learn it until I'm confident I can get it running securely and reliably - the level of detail I need to understand will vary.  If it's an internet-facing application, then I need to know all the details.  If it is internal, then a point-and-click interface to get it up and running could easily be the best solution.

I'm not suggesting in any way that, for example, an internet-accessible web server should be configured by an amateur using a configuration wizard - just that simpler to use, higher level tools have their place even for the most experienced and knowledgeable admins.

---

