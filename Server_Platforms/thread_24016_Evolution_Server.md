---
title: "Evolution Server"
date: 2005-04-05
forum: Server Platforms
---

### Post by richard42 on 2005-04-05
I want to have a network of Ubuntu machines, with the clients running Evolution which connect to a server to get their data. I want their email, tasks, and calendars to all be held on the server.

What suggestions do people have for setting this up--Courier-mta? Dovecot? Something else? Any HowTo's exist?

Thanks,
Richard

---

### Post by paretooptimum on 2005-04-05
...and I would like it to install just by selecting one package in synaptic and a pony!

---

### Post by richard42 on 2005-04-05
[QUOTE=paretooptimum]...and I would like it to install just by selecting one package in synaptic and a pony![/QUOTE]
 Sarcasm?

---

### Post by nocturn on 2005-04-05
[QUOTE=richard42]I want to have a network of Ubuntu machines, with the clients running Evolution which connect to a server to get their data. I want their email, tasks, and calendars to all be held on the server.

What suggestions do people have for setting this up--Courier-mta? Dovecot? Something else? Any HowTo's exist?

Thanks,
Richard[/QUOTE]

E-mail in no prob at all, just use any IMAP server (I have cyrus).
Contacts should also work if you use an LDAP server.

Calendar and tasks are another issue though... You could check out openxchange, but it is still in developement.

Let us know if you find something good though.

---

### Post by paretooptimum on 2005-04-06
Yes, but not directed at you, more my long search for the same answer. I have a similar question sitting in the forums right now, on sharing contacts only.

A "drop-in" microsoft exchange server is the holy grail of most small businesses looking to make a switch to linux. I have looked and looked. There isn't an easy solution right now. There are a lot of piles of parts with some vague instructions for assembly. Hula looks promising, though very new.

I will watch this thread to see if anyone has a good suggestion - this is certainly a problem I would like to solve.

Tim

---

### Post by richard42 on 2005-04-06
[QUOTE=paretooptimum]Yes, but not directed at you, more my long search for the same answer. I have a similar question sitting in the forums right now, on sharing contacts only.

A "drop-in" microsoft exchange server is the holy grail of most small businesses looking to make a switch to linux. I have looked and looked. There isn't an easy solution right now. There are a lot of piles of parts with some vague instructions for assembly. Hula looks promising, though very new.

I will watch this thread to see if anyone has a good suggestion - this is certainly a problem I would like to solve.

Tim[/QUOTE]
 Yes, sounds like you've had pretty much the same experience as I have had. Looking at all the possibilities, but none of them seem to 'just work' very easily.

Could you put the link to the other thread you referred to about sharing contacts.

Thanks,
Richard

---

### Post by stl on 2005-04-07
Probably the best thing out there which is close to Exchange is SuSE OpenExchange but that is a commercial product.  If you're looking for free then Hula is your best hope, but there are also other options.  KDE's Kontact documentation lists quite a few: [http://www.kontact.org/groupwareservers.php](http://www.kontact.org/groupwareservers.php)

---

### Post by deuce868 on 2005-04-07
anyone tried out Hula?

---

### Post by Ric_ on 2005-04-08
I know the feeling of the long search for a "exchange" replacement. There is some hope.

The sticking point was the calendar's, in particular when the management wanted shared ones!

At the time i was running courier-imap (just apt get install it) and individual calendars seemed to be ok. I was trying it with a plugin in outlook and basically it creates a imap folder and gives it a new view. Not sure if evolution supports this. I now understand the newer versions of courier-imap supports acl's so this may let you create shared folders and calendars.

The plugin was called Insight connector and can be found at [http://www.bynari.net/index.php?id=500](http://www.bynari.net/index.php?id=500)

Looks like they have gone all corparate on us  :-? But if you find another project that does the same please let me know this would be a massive step forward. I know its a different way of attacking the problem but it could be useful.

Hope this helps

---

### Post by paretooptimum on 2005-04-08
I have found a decent discussion here:

[http://ephemeron.infopop.net/3/OpenTopic?a=tpc&s=7552915347&f=6182915347&m=1622956847&r=1622956847](http://ephemeron.infopop.net/3/OpenTopic?a=tpc&s=7552915347&f=6182915347&m=1622956847&r=1622956847)

...though it is out-of-date and not exclusively a linux discussion.

---

### Post by goofrider on 2005-04-08
[QUOTE=stl]Probably the best thing out there which is close to Exchange is SuSE OpenExchange but that is a commercial product.  If you're looking for free then Hula is your best hope, but there are also other options.  KDE's Kontact documentation lists quite a few: [http://www.kontact.org/groupwareservers.php](http://www.kontact.org/groupwareservers.php)[/QUOTE]


Novell has open sourced Open-Xchange a couple months ago. The commercial version is largely identical to the open source version.

[http://open-xchange.org/ox/EN/community/](http://open-xchange.org/ox/EN/community/)

---

### Post by goofrider on 2005-04-09
[QUOTE=paretooptimum]Yes, but not directed at you, more my long search for the same answer. I have a similar question sitting in the forums right now, on sharing contacts only.

A "drop-in" microsoft exchange server is the holy grail of most small businesses looking to make a switch to linux. I have looked and looked. There isn't an easy solution right now. There are a lot of piles of parts with some vague instructions for assembly. Hula looks promising, though very new.

I will watch this thread to see if anyone has a good suggestion - this is certainly a problem I would like to solve.

Tim[/QUOTE]


Drop-in Exchange replacement for Linux **is** the holy grail. There are a few commercial products that claim to be drop-in replacement for Exchange.

[list]
[*][Samsung Conacts](http://www.samsungcontact.com/) 
[*][Insight Server with Ingiht Connector](http://www.bynari.net/) 
[*][Exchange4Linux with MAPI Provider for Outlook](http://www.exchange4linux.org/) 
[/list]

Note that E4L is GPL, only the Outlook connector is proprietary commercial. Some open source groupware servers like Kolab and OpenGroupware also supports a number of Outlook connectors, most of these connectors are proprietary commercial.

The primary reason that there's no open source Exchange replacement is (IMHO) primarily because some of the Exchange features have no open standard equivalent. CalDAV is still new, and I think there's still no standard way of handling server-side personal address book storage, and server-side notes storage.

If you choose to use any of the above drop-in Exchange replacements, then you'll be locked-in to the Exchange/Outlook network layer. You're only options for desktop clients will be Outlook and Evolution (though u can still use any POP3/IMAP clients for email). I believe The open source community as a whole is trying to develop open standards that'll eventually replace all of Exchange's functionality, and then develop groupware severs that utilize these open standards, instead of built-in open source groupware servers right now using M$ Exchnage's protocol.

That's my primary concern: if you choose a groupware product today solely based on its ability to support Outlook, then you'll still be locked-in to Outlook. The above commercial groupware servers provide very little imformation abuot how they work with open source clients like Mozilla Sunbird or Kontact.

Lastly, FWIW, Hula is not a drop-in replacement for Exhcnage. It's just another groupware server. Whether Outlook can use Hula's groupware features natively will largely depend on whether an Outlook/MAPI provider will be developed.

---

### Post by goofrider on 2005-04-09
[QUOTE=richard42]I want to have a network of Ubuntu machines, with the clients running Evolution which connect to a server to get their data. I want their email, tasks, and calendars to all be held on the server.

What suggestions do people have for setting this up--Courier-mta? Dovecot? Something else? Any HowTo's exist?

Thanks,
Richard[/QUOTE]

These are conceptually different features:

[list]
[*]mail server
[*]global directory
[*]contact server
[*]calendar server
[/list] 

The mail server is the easiest part, u can use any POP3 server or IMAP server (Qmail, PostFix, Qpopper, Courier-IMAP, UW IMAP, Cyrus IMAP, etc.)

A global directory allows you to maintain a company-wide contact list (a directory of all your employees, partners, their email addresses and phone #s). You can use LDAP for that. Though I find OpenLDAP difficult to configure. Does anyone know of a GUI/www admin tool for OpenLDAP?

The contact server component lets the user to store their personal contacts on the server and is available only to themselves. So that they can log in from anywhere and still have the same personal address book. I don't know if LDAP can do that or not. Does anyone know how Evolution and Kontact handles server-side personal contact storage?

The calendar server allows the users to store their calendar on the server and share with others, and help them to schedule events and meetings with others. The newly rectified CalDAV standard is supposed to provide that and it supercedes iCal. It's an extension to WebDAV (hence it uses plain old HTTP as its transport). Evolution, Mozilla Sunbird, Kontact and various open source calendar clients already support or plan to support the new open standard.

A number of open source groupware servers exists:

[list]
[*][Novell/SuSE Open-Xchange](http://open-xchnage.org/) 
[*][Novell Hula](http://hula-project.org)
[*][OpenGroupware](http://opengroupware.org)
[*][Kolab](http://kolab.org)
[/list]

Kolab and OpenGroupware both been around for quite a while, they both support Outlook via commercial third-party proprietary plugins. I think they can also work with Mozilla Sunbird, Kontact and Evolution via open standards. Kloab also has its own native desktop client on Linux.

Open-Xchange is the GPL version of SuSE's OpenExchange server, which Novell released as open source recently. Hula is based on Novell's NetMail product, orginally written for NetWare and is used on MyRealBox.com (Novell's NetMail beta server for public testing). Novell plans to use Hula to power future versions of NetMail. So Novell is now in the intersting postion of having 2 open source groupware products. I'm not sure how they plan to differentiate the two.

The decision of which Linux groupware server to choose will remain quite complicated until there's some open standards for all of the features required in groupware applications. In the mean time, your choice will probably largely depend on which groupware client(s) you choose on your desktop. I'll suggest that we can make a sticky and closely follow the developement of these 4 open source groupware servers. Surely there are many other open source groupware servers, though I feel Kolab and Opengroupware are probably much more mature than most others with the most support from other open source groupware clients and commercial support for proprietary connectors, while the Novell projects will have the most momentum simply because they're backed by Novell and undoubtly will integrate easily with Evolution, SuSE and Groupwise.

If you plan to use Evolution on the desktop primarily, Hula and Open-Xchange seem to be the logical choice since they're both developed by Novell.

---

### Post by Ubuntu Warrior on 2005-07-13
We have tried unsuccessfully to install openxchange. There seems to be some problem with support for Debian/Ubuntu??? Does anyone know whether it is possible to install and configure ox using apt? If not possible now, any idea on when it will be supported in the repositories?

---

### Post by habbers on 2005-08-05
There are debian packages for Open-Xchange although I haven't successfully installed it using those packages. I have got it successfully running on a debian sarge server by following the instructions from [http://www.open-xchange.org/oxwiki/OXInstallations](http://www.open-xchange.org/oxwiki/OXInstallations) that describe installing it from source using with Apache2. The webinterface to Open-Xchange is great, the best interface of any of the groupware apps I have been looking at in terms of usability. One problem with Open-Xchange is that it doesn't have a open-web based interface although, people have written there own and hopefully they will develop into projects in their own right. You do get a web-admin interface if go with the Commercial version. The project itself seems great, very active lists and forums. If the install can be made a bit easier it would be great, although I had had little to do with java, tomcat, openldap and cyrus before so that caused me most of my problems. It would be great if there was more documentation on cyrus, I have been using courier qmail combination before and find it so much easier getting things to work with that because there is a lot more documentation for these, the qmailrocks.org website being a great example. 

Would love to get Open-Xchange to work with a qmail courier setup.

cheers
John

---

### Post by jfdill_2 on 2005-10-20
[QUOTE=paretooptimum]...and I would like it to install just by selecting one package in synaptic and a pony![/QUOTE]
egroupware (eGW) is pretty close to that, just install apache or apache2 first, then get egroupware from the Universe repository, then run the install.php to set it up, all of that is very easy.  egroupware doesn't have a built-in e-mail server, though, it just uses IMAP or POP3 to connect to a separate server.  BUT design-wise, I'd rather have a separate e-mail server that is a solid e-mail server, there are a lot of good e-mail servers already out there.  eGW does interface with LDAP for authentication but that sounds a little complicated to set up.

My only complaint about eGW is some features are still experimental or not implemented yet, like Exchange connector, PDA sync, when you put stuff in Projects it does not automatically show up in the Calendar etc.  But all the basic stuff works great--photo gallery, shared folders, built-in wiki, e-mail, calendar, trouble ticketing system.

At the moment, I am trying to install Open-Xchange (which is how I stumbled onto this thread) to see what it can do and check out the Project interface and if that syncs up with the calendar.  What I don't like about it is that it's a Java app and needs Tomcat and I haven't set that up before, it could be a pain.

---

### Post by cactus on 2005-10-20
[QUOTE=goofrider]Does anyone know of a GUI/www admin tool for OpenLDAP?[/QUOTE]

phpldapadmin
[http://phpldapadmin.sourceforge.net/](http://phpldapadmin.sourceforge.net/)

---

### Post by needplants? on 2005-10-20
I ran into zimbra
[www.zimbra.com](www.zimbra.com)
it looks pretty nice although I haven't used it.  they have a nice tour.

E.

---

### Post by twistedbrain on 2005-10-21
> 

[...]

A number of open source groupware servers exists:

[list]
[*][Novell/SuSE Open-Xchange](http://open-xchnage.org/) 
[*][Novell Hula](http://hula-project.org)
[*][OpenGroupware](http://opengroupware.org)
[*][Kolab](http://kolab.org)
[/list]


And what about [egroupware](http://www.egroupware.org)?

Andrea

---

### Post by Bill_Albertson on 2006-01-30
Just an update on hula, as I just installed it, thinking that what was written in the description as being "a mail, calendaring, and addressbook server" was actually true.  As of the time of this post:

Mail works for hula.  For me, this is not a high requirement- there are plenty of other mail servers out there that I understand how to configure without a gui.

Calendaring doesn't really work at all.  What I mean by this is you are able to perform read-only actions with evolution using the hula server.  I can see how this could be useful for some kind of announcement calendar, but I could configure webdav under apache2 and have more functionality, or I could get the same functionality out of the sushi calendar on my wall.  What is still missing is the ability to collaborate in any useful way without being destructive to the calendar data.  Webdav is still the way to go for now...

Addressbook functionality.  My criticisms of this are wholly from the point of view that this is supposed to be, and claims to be, a groupware project.  As far as I can tell, it is still not at all functional for a client application like evolution in a groupware environment.  I can't take my addressbook in any reasonable fashion and migrate it than I already could more easily with other LDAP projects.  More importantly, there is absolutely NO way to update or further share or migrate the data from the client.  None.  All of this needs to happen on the server side by the administrator- I guess.  After reading documentation for over 3 hours, this is still not clear.

I will also make it very clear here that much of this product DOES have web functionality for most of these features, but if I wanted that, I would be using gmail, or phprojekt, and not evolution.  The Hula project is claiming integration with clients, and that is the functionality I was looking for.  There are plenty of other mature projects out there that provide web access for all of these functions.  My criticism comes from the point of view that this is a client/server groupware system as claimed by Hula.  Also, I want other people to be very clearly aware of the problems that they will run into if they should go this route, as there seems to be a lot of enthusiasm out there for Hula, but not a lot of clear caveats on its limitations.

The administration gui still has acknowledged usability problems, in that the gui needs lots of explanation so that the admin/user can do simple things, like add a user, or sharing their read-only webcalendars.  Moreover, none of the backend items that this application serves as glue for are really visible or apparent which would have helped greatly in figuring out stuff without the documentation.  The gui basically adds more cruft than it takes away.  Hopefully, this will improve over time.

Normally, this a lot of this is not an issue for some people.  They can dedicate 10+ work hours to making all of the non-functional items work, or research on how to integrate the workarounds.  

This doesn't work for me though.  Since I have a family and I am doing this in my spare time, this is DEFINITELY not a replacement for anything that I have already tried and had a greater degree of success with (some MTA + APACHE2/WEBDAV + LDAP/LAT).  

Hula shows promise as a really great gui-managed groupware project, but two things need to happen.  First- the parts that are claimed as "working" need to actually work in the context of the claim.  Second- claims that calendaring and other features "work" need to be dropped until that functionality really exists in some usable fashion.  Any packages out there should make very clear that this is not a functional groupware or calendaring solution, but still an incomplete project, and state which functionality does not exist.  Which, in the case of current Hula development, are things that define groupware- like the ability for clients to access and manage their remote calendars and contacts.

I wish I could be more kind about my assessment, but raising a two year old will rapidly shorten one's tolerance for anything that claims it is something that it is not.

---

### Post by Bill_Albertson on 2006-02-01
I have now been looking at other options, and found that schoolbell rocks for calendaring.

After more research I also discovered that NONE of the GUI thick clients work reliably for handling remote calendar data.  Seems that ALL of them want to put their special imprint on the data stored locally, which means that there is always going to be something that refuses to work and will be incompatible.  By all, I mean Kontact, Evolution, and Sunbird.  And, yes, I have tried them all - in the sense of trying EVERY bell and whistle, and using it as thouroughly as possible, trying every feature over and over.

I started doing this when Kontact ate about 4 months of calendar data.  Ouch.  Even on restore from backup, the application would not view the data.  I read the dev site, and the one guy who was the head person working on that feature refused to acknowledge there was a bug, in spite of multiple requests by others (including one pseudocode listing, showing the direction of the problem).  Faced with this, I could rebuild my system and pray it wouldn't happen again, or stop using a thick client remotely.  

Fast forward to now, and I still can't find a reliable client.  None of them work remotely, yet.  I do have hope for one working reliably some day.  As I stated, each project wants to mangle the data in their own way.  Evolution actually destroys remote calendar data when you try and update free/busy information (and doesn't publish the information).  Sunbird doesn't present the data reliably, but does reliably erase it after one successful update and reload, and now gives intermittent java console errors pointing to a corruption in the sunbird calendaring database (why a java based pseudo database? why?).  I won't try Kontact again- I don't like the lack of documentation surrounding the architecture of the KDE ~/.directories (it took forever to find my calendar data), and I don't like it when people can't admit to problems.  Also, none of the projects' clients give clear success/failure messages when remote updates occur or fail (but they do this for mail, reliably).

But, and this is important- all of them are moving ahead, and may actually be usable in the forseeable future...  And I won't go into Outlook's built-in limitations for calendaring, as those are the reasons I tried everything else.

Ok, even better than that, it looks like Schoolbell really works as a server solution if you are going to be tied to the webbrowser, or own a Mac (which has had working remote calendars for a while).  It installs from synaptic, it runs on install, and the only caveat is that you need to go to [http://yourhost:7180](http://yourhost:7180) to get in, and type admin/schoolbell to get started.  The interface is the easiest by far to use (and I have tried phprojekt, egroupware, blah blah blah), with no learning curve required even for people who don't regularly use computers.  It also runs on top of zope in the Ubuntu incarnation, but you don't really have to wrestle with that at all (whew).  Compared to vanilla flavored Zope, or Hula, or even Apache+Webdav, its just about as point-n-click as I have seen it get.

Tomorrow, I will see what I can do for customization, and may post back here.  Hope this saves someone else two or three days of research in the future. :mrgreen: 

Or, I could get off my dead butt and code a cal.app or something for gnustep...hmmm....

---

### Post by Bill_Albertson on 2006-02-01
Some more information on using Schoolbell:

The default site is [http://yourhost:7180](http://yourhost:7180)

The default login is manager and the password is schoolbell.

The only difficulty I have had with this is understanding the permissioning system.  If you set this up, make sure you understand how it works by breaking it several times before letting anyone else log on.  I can't stress that enough.  They aren't joking that chaos can ensue when you start using groups, and it can ensue from the moment you add a new user.

To understand how this works, on every page there is a link called Set Up Access.  This doesn't just apply to the site- this applies to every page view that you see this link on.  As the manager, you can make some things world writable very quickly without intending it, and never know it happened.  Moreover, you don't directly control what each user can see and do - that link is on every users page view that they have any access permissions to as well.

I would recommend logging in as manager, changing your password, and learning permissioning before letting anyone else log in.  Do NOT do this on the manager account.  You will end up re-installing the whole app if you try this.  Instead, create a test user and go from page to page changing their access wherever you can.  Then, log in as that user, and see what you can and can't change from that view.  Remember that each of these users has their own view of what can and can't be changed from their own account for each page's "Set Up Access" security setting.

Then add a second test user, and do the whole thing again with all the users and the manager account.  You want to shoot for making sure that a user can't supercede your manager permissions to change things, so test changing the manager's user info.  Once you understand permissioning on a user level, then go on to adding one group.

There are two default groups already- Authenticated Users and Unauthenticated Users.  Both of these groups should have the minimum permissions, and as a test user, you would have to restrict these as well.  Basic rule is to restrict the group, then the users.

When you add a new group, understand that it will have a lot of permissions.  These permissions are a default setting for that view for any user that also is in that group.  The setting in the create group page is the default template for creating permissions for any other page view.  Have them set to what you want be fore adding members.  You can restrict or grow permissions for a group setting for a specific page view, but remember that a group member of a group is not going to ever have higher permissions than that group's default for that page.

You can either start off with a restrictive group setting, and add group permissions for each view.  Adding or removing group permissions affects the permissions for each user in that group for that page as well.  Or, you can permit just about anything, and kill permissions later- but this means you will have to log in as each user to do it if you want to restrict one person, or create a special group just for bad users, etc.  Either way, the manager user is going to have to be a permissioning expert with this system to avoid headaches later.

I hope this is helpful to whoever finds it.

---

### Post by dgermann on 2006-03-04
Bill--

Yes, it is very helpful.

A quick question: as far as I see, Schoolbell has no task list or to do list function, as does say Evolution. Have you found any? The notes function does not really seem to do that sort of thing.

---

### Post by Bill_Albertson on 2006-03-06
No, there is no native tasks support for schoolbell.  Their notes are really all they have that comes close, and they are not the same thing.  My main reason for picking schoolbell at the time was that I wanted a solid, easy to use, calendaring server which would allow me to run simple-publishing self and calendaring out of the same Ubuntu box.  I have since settled on wordpress for self-publishing, which changes my calendaring requirements a little.  Also, at the time of my post, OpenBSD did not have package support for wordpress, so Ubuntu became my best next choice because I wanted to keep my installations as clean and easy to manage as possible.

Since then, I have done more research on my needs, and will probably be creating packages under OpenBSD for a multi-user install of wordpress, along with integrating webcalendar and coppermine into the mix.  This came from the realization that neither Ubuntu nor OpenBSD support the combination of a simple online publishing tool for words, media and calendaring/tasking.  Ubuntu does support wordpress, but only in a single user installation.  Webcalendar is also there, but no security updates have been committed for it as a package.  

Also, I loathe the idea of trying to install and manage a mixture of packages and source on a debian based system as I am just not very familiar with it and have had nightmare issues with apt from the command line in a past Debian install (something about following apt's man page to the letter, and having apt completely make the entire box unworkable- I am sure there are forums that would correct my "mistake", but I tend to be picky about using tools that have bad or obscure man pages for such a critical tool).  So, unless I can do it from synaptic under Ubuntu, chances are I won't do it on Ubuntu.  I do make a few exceptions, but that is my general rule.

I have three other reasons for this decision- I am much more familiar with the OpenBSD pkg creation system, I don't like the idea of my managing both Zope and Apache (schoolbell is zope based) on the same box, and I am much more familiar with running and optimizing OpenBSD as a server than I am Ubuntu.

A lot has happened since I wrote my last post, so let me make some clarifications:

1.  Schoolbell is kind of like a version of schooltool lite.  It does calendaring very well, but it does not integrate with any other web application aside from providing calendaring and a URL for the ICS file.  Also, there are a couple of feature bugs (like not being able to schedule recurring 1st week of the month items correctly) that were to have been recently fixed, but an update has not been provided by the Ubuntu package maintainer yet, AFAIK.

2.  If you want integration with something like wordpress, you might want to try [webcalendar]("http://www.k5n.us/webcalendar.php"), as it has many more features, and is supposed to integrate well with wordpress, and possibly other applications.  However, I have not had the opportunity to fully test and use it yet, so don't take what I just said as any kind of endorsement.

3.  I have also not tested dotplan yet, but it is supposed to have task integration features.  Again, since I have run into several projects that make "very conditional" claims, I can't say whether it does or doesn't have support for tasking, or for calendar uploads/downloads.  But it may be worth looking at.  Its on my list of stuff to try, right after webcalendar.

3.  Since I am also an OpenBSD user, I have found that phpicalendar is distributed as a package by them.  Sometimes this means that someone has an irrational love for the application.  Other times it means it is really solid.  I have never used it, but I thought I should mention it, because there is a 50% chance it may be worth your time.  I have no intention of testing this one because it also does not integrate into wordpress, or provide any other features I might use (like dot plan may), but you may want to try it.

4.  If you can deal with really poor documentation and a wonky interface, Hula is supposed to support those features, or at least plans to.  But I found that the claims did not match the reality when I last tried it.

---

### Post by dgermann on 2006-03-07
Bill--

I enjoy reading your posts--you are great at giving useful and to the point info.

Last Saturday I spent all day trying schoolbell, hula, and one other. I sorta settled on iCal.

Sound strange? Well, not exactly. I have 4 people in the office and want to move from Win to Linux on the desktop. Two machines are about ready to go (once I figure out how I screwed up my main server--I can no longer log in there). The third is a WinXP box which we will probably keep to power a scanner and to run AABBY Finereader--a function I have been unable to find in the linux world. 

The 4th machine is a Win95 box that is used to do our billing and accounting--until I get someone to design a good database to take over those tasks for me.

I could probably set up the Win95 box to use RealVNC and we could simply login in there to post our time entries.

So I needed something that my Win boxes could see and edit for our one office calendar. iCal seemed to offer that. Except that when the user of the system logs out for the night, the calendar shuts down!

Our work is somewhat sensitive so I am leery of going to some web-resident calendar. So if there is some way I can get a calendar that is strictly web-based, but which I could run off one of my local Ubuntu boxes or the WinXP, I will try it out.

Oh, I looked at the zope calendar, too, but it was too much learning curve just for a calendar. If nothing else, I can set up a word processing file as a calendar--that's what we do now.

So, Bill, are you using WordPress for a website, or interally in your business? I have WordPress on my website....

---

### Post by Bill_Albertson on 2006-03-08
It doesn't sound strange to me at all.  Everybody has their needs that they have to meet.

My own needs revolve around my wife and I both being very mobile people.  She is very involved with our daughter's development, and so she is not often at home, but trying to find new places for our daughter to explore.  She doesn't need a SAMBA server- she needs something web based, with a low learning curve, that can be easily secured for remote access.  I also need the same thing, because I provide some services in my spare time to social organizations and to my church, and they have almost the same needs as my wife.

The decision on Wordpress comes after using Joomla! for my previous side business, as well as trying several other CMS/DMS solutions out there.  Since I am the only one who will be making it all work, the solution has to be simple and well documented.  Then, it needs to install and be updated quickly and reliably.  Those are my only requirements, but they are strict requirements.  If nothing fits the bill, I don't use it beyond my lab.  And I do have a "production" and "lab" environment at home, as small as they are.  

Back to my choices.  I settled on SFTP to a server for direct access to files like OOo/MSWord docs.  There are SSH/SFTP clients for every platform, and Ubuntu (our primary client platform) has the ability to map SFTP accessible directories for easy access.  

I also need something for simpler docs, like recipes, journals, etc.  I chose Wordpress, because it is fairly straghtforward to secure anything you don't want publically accessible.  WP also integrates with a calendar system, MyCalendar, without needing to be a rocket scientist.  Same goes for Coppermine as a multimedia repository.  

My wife now could share all of her multimedia stuff without worrying about who is looking at it.  She and I can also have very complicated calendaring for our entire extended families, with selective access to who can view what.  This last part is probably the most used feature for us, which is why I started on my calendar server quest (and found this thread).  

My testing with MyCalendar will be running over the next three days, so I will post on it, as well as my experience on integrating it with Wordpress under Ubuntu.  I still may opt for OpenBSD as my final server solution, but that depends on whether I can figure out how to create packages under Ubuntu without tearing my hair out.  I also need to run some security testing against Ubuntu as well.  

There is a caveat in all of this as well.  I am more knowledgeable about OpenBSD as a server or firewall.  Unless I can feel assured that I can safely give limited public access to this system under Ubuntu as a server, this whole setup will probably be running under OpenBSD.  But, I figure it is worth testing, because I have had a lot of success with Ubuntu's package installations using Synaptic, and Ubuntu's packages seem to work with attention paid to package feature dependencies that OpenBSD has lacked in the past.

Eventually we will add other features, like secured messaging over TLS/SSL, and a VOIP gateway, but that will probably be at least a year away.  I also need to get back to work on mapping out different IPSEC vpn configurations between Ubuntu clients and OpenBSD router/firewalls as well, so it may be longer.

---

### Post by dgermann on 2006-03-08
Bill--

> 
I also need something for simpler docs, like recipes, journals, etc. I chose Wordpress, because it is fairly straghtforward to secure anything you don't want publically accessible. WP also integrates with a calendar system, MyCalendar, without needing to be a rocket scientist. Same goes for Coppermine as a multimedia repository.


Does this mean you can run WordPress just on your "office" network, without involving the Web? If that could be done, and the Webcalendar integrated into it, that might be exactly what I am looking for.  Tell me it can be done... and as easy as synaptic!

Thanks, Bill!

---

### Post by Bill_Albertson on 2006-03-17
Well, I will be going through with the install of WordPress, WebCalendar, and Coppermine- just not on Ubuntu.  If you don't want or need to read my rant and general advice regarding WebCalendar under Ubuntu, then you don't need to read much further.

Dgermann- Regarding running WP, WC, and Coppermine as a server for your office- it doesn't matter whether the server is on the internet or on your local area network.  Just make sure nobody else outside of your work's LAN can get to that data from the internet.  If you aren't sure how to do this, I would check around your local area, and try to find someone who knows internet security and data security requirements (like HIPAA, Sarbanes/Oxley, etc) really well.  Don't leave that part to chance and try to learn on the job without some kind of professional help.

Also, to get wordpress running under multi-user, there are numerous ways of doing it.  The easiest way is the hack from [Mertner]("http://www.mertner.com/allan/index.php?p=15") where separate user tables are created, giving each user a blog, but leaving the entries in one database that can be easily backed up.  There is an additional hack for listing a link for all users at the top of the index page for each blog.  Pretty nice.


While the Wordpress install went great, the webcalendar install was at best confusing (I understood the issues, but I am looking at this as if I were one of my friends, or my wife, trying to do this install).  I allowed debconf to "configure" the application on install.  Without any reference or clarifying notes, I was requested to type in a username, table name, and password.  While *I* know what they are for, your average user might have typed in a user already in use, or an easily forgettable password, etc.  

I was then informed that I had to run some script to create the table manually, because while debconf can apparently change a config file (the easy part of an install), it can't create any tables.  What!?!?  Ok, great, now- in creating a table, are there any caveats?  Table constraints? Special features to enable?  I don't know, and even more so, I didn't know that I would need to write down a very long file path to an obscure script that would handle this little problem.  I also have no reference to the username I just typed in earlier, but I would guess that I might use that in creating the mysql table- if I remembered it.  So, with debconf having done the easiest part of editing a php conf file, I am left with the hard part of figuring out how to manually create a mysql or postgresql table.  And, btw, I don't know which one to create- debconf never told me, which would be bad if I ran both of those databases concurrently.  Same goes for the default admin password- why tell me to change it manually when I am using an autoconfiguration tool?  It would have been MUCH easier to simply put "read the installation notes in /foo/bar/notes.txt", and not touch anything, because I would be having to touch the config files anyways.

Worse yet, I was also given the option of emailing this information to myself, but when I checked, nothing was ever mailed.  Joy.  Had I been the average user, this would have meant a completely borked install, because I would never be able to find the table creation script directory for webcal that I had been informed would be mailed to me.  This is a configuration option.  Having no reference to what debconf would and would not do left me in a bind, and wondering why somebody even bothered offering an option to use it.  

All in all, the install was really frustrating, and left me wondering why I didn't just do this from source?  Yes, it is possible to install this package- no, I don't think this is something a regular user could do or would even want to be bothered with (which is the point of view I am coming from with this criticism- if I wanted to spend lots of time applying my expertise at home, I would have built everything from source, not bothered with debconf, et cetera).

As for my future installs under Ubuntu, they will likely be only for desktop installations, and not for any ad hoc server activity.  I will reserve all of my future server installs for another distribution.  If you do decide to continue with webcalendar as a server under Ubuntu, be sure to take lots of notes and read all of the project's documentation well in advance of starting.  Or use schoolbell- it is pretty easy to include a calendar path as a link in the sidebar, even if you aren't going to get a quick minicalendar view.

---

### Post by lqqkout4elfy on 2006-03-21
Anybody here looked at Multisync yet? You can sync with another Evolution very easily via SyncML...

---

### Post by dgermann on 2006-03-22
Bill--

Sorry to not reply to you sooner. I have been snowed under with other parts of my install recently, especially a problem not being able to get my samba and OOo conbination to lock files. Still no answer on that, so we are trying to stay way from the same files at the same time. ](*,) 

I will take your advice about the security issues.

You don't really say in your post why you are staying away from Ubuntu--it reads as if the real problem were WC (= water closet? ;) ).

As far as a calendar is concerned, I decided to do what I have been doing in Ami Pro for years: do the calendars in word processing. I came up with some tables and even figured out how to have them automagically add the date once I put in the date of the first Monday of the month. So it is something familiar, simple, and it works. The todo lists the same way--word processing files under OOo: simple tabbed lists.

I enjoy conversing with you, Bill.

---

### Post by Bill_Albertson on 2006-04-06
WC would be webcalendar :)

---

### Post by Bill_Albertson on 2006-04-06
Nope, haven't even begun looking at Multisync yet, but I have heard good things about it- mostly for syncing calendar data between Kontact clients.

---

### Post by Bill_Albertson on 2006-04-06
Last post for me on this thread-

My search for a calendaring server is over.  Its not the fault of most of the servers (though, honestly, most of those are only partially finished).  The fact of the matter is that Ubuntu's default desktop mail/calendaring/whatever client just doen't work unless you have an exchange or groupwise server to connect to.

The problem is not with the Open Source servers out there lacking support, but with the available clients.  Evolution does not work as a calendaring client, except with proprietary servers.  It probably NEVER will work with anything but proprietary servers, and there are several old bounties out there that prove my point.

My thoughts on Mozilla's Sunbird functionality are that it corrupts its own database, fails to negotiate network connections in any reasonable sense, and provides no error messages and almost no meaningful debug info.

Kontact is supposed to have excellent support.  The last time I used it, there was a display bug that prevented me from finding my calendar data.  I have since found out why that issue occurs.  The problem is that Kontact does not have the same kind of exception handling for unsupported data display modes that other clients do.  This means that you can create a task or recurring event, save it, and when something related to that event occurs at a later date- BAM, no visible data.  KDE's team has since addressed some of those issues, and thankfully they have fixed their user feedback so that these issues get stomped faster instead of being ignored like in the past.  If you need a fully featured calendaring/time management system under linux, run, do not walk, RUN from evolution and don't look back.  Just make sure you make regular (as in daily) backups of your calendar data so you can restore in the event of the above mentioned issue - you do perform regular backups, right ;) ?

My solution, which would have been Kubuntu, ended up being something else entirely.  The last Ubuntu kernel patch, or something else that was updated, caused my networking under Ubuntu gnome to go completely haywire.  Reverting made no difference once the update was completed.  I lost all available configurable interfaces but loopback.  I could see them with ifconfig on the command line, but Ubuntu's gnome could not, would not, and would not let me perform any work on the network.  AFAIK, this tool is also used under Kubuntu.  This made my laptop completely worthless, so no more (K)Ubuntu.  I wish everyone else the best of luck.

---

### Post by widjajayd on 2006-04-12
hai FYI
Egroupware just released version 1.2 
it's seems there is integration with evolution and it can be good if we can make howto Egroupware with ubuntu Dapper server

see [www.egroupware.org]("http://www.egroupware.org")
:p

---

### Post by florizs on 2006-04-26
I'm also looking for an opensource collaborations server and this looks like it is the most promising server so far. 
I believe that a collaboration suite is one of the most essential tools for computers in companies weather large or small.

I  hope that there will be much more priority in developing this from the Linux community in the future.
wouldn't it be an idea to start a discussion/thread about this?

---

### Post by Zwalther on 2006-04-27
Bill, thanks for all the info you provided. I was also looking for a calendar server to synchronize my calendars at home and at work. You saved me a lot of work.
Because I'm a Gnome user, I wanted to use Evolution, but it seems like that's not going to happen.

Did you have problems with Ubuntu Dapper? Because there were some networking bugs in Dapper that have now been fixed.

---

### Post by yurtboy on 2006-05-17
Sorry to read about the previous users problems with (K)Ubuntu.
I still lean between evolution and kontact.
In the bigger picture Ubuntu and Kubuntu
For the integration is key.
So my question becomes can Evolution integrate with Egroupware?
If so then great
If not the Kolab and Kontact?
Else?
Hula? 
It's setup wnet well for me but my use for it was more due to ease of install and setup including antivirus and spam.
Though was it easier the postfix etc?
I've tried some of the others, that is postfix, exim, dovecot, courier etc.
Just hula installed well and set up antivirus and spam easily.
The calendar sharing will be ideal as well and maybe it will happen soon?  Maybe it already happended.
Anyways this is a good thread and I will try egroupware and evolution and hula and evolution though over all I want document centralization with checkout support that is easy to use.  Maybe Openoffice since I want the enduser to use a spreadsheet or word that integrates into a database which the gui editors may not be able to do ie fields for querying data.
Well I will check in again after looking at some things.

---

### Post by nocturn on 2006-05-18
[QUOTE=yurtboy]
Anyways this is a good thread and I will try egroupware and evolution and hula and evolution though over all I want document centralization with checkout support that is easy to use.  Maybe Openoffice since I want the enduser to use a spreadsheet or word that integrates into a database which the gui editors may not be able to do ie fields for querying data.
Well I will check in again after looking at some things.[/QUOTE]

Evolution only supports calendars on a caldav server (a relatively new standard).  Unfortunately, Hula seems the only groupware offering that at this point.  There's also cosmo (a Tomcat app) which is a standalone caldav server.

The lack of a good integrated groupware server in the Free Software realm is becoming hurtfull at this point.

---

### Post by ChristofPetig on 2006-08-30
I spent nearly a week looking for a decent free solution and finally stumbled over a brand new openGroupware.org evolution connector which uses GroupDAV.

See here for a SVN address [http://http://mail.opengroupware.org/pipermail/evolution/2006-August/000618.html]("http://http://mail.opengroupware.org/pipermail/evolution/2006-August/000618.html")

I'll report again once I have more experience with it.

---

### Post by si285 on 2006-08-30
I tried to install HULA on a newly installed Dapper 6.06.1 server without success.  I may be wrong but most if not all of the successfull installs seem to be on earlier version of Ubuntu.  

I can follow instructions but I don't think there are any really good instructions on how to do this.  Every set seems to lack something because knowledge of how to compile, install and configure is assumed so small details a knowledgable Linux admin knows are somehow overlooked.

I wish someone would come up with an installation option like the LAMP one except for email.  This would go a long way towards helping new Linux users get productive fast.  It also helps insure uniformity when installing more than one. 

Sometimes I just don't have the time to spend fiddling with something to get it working, I just need it to work so I can configure it and move on...

That's why I gave up on Hula.  It took too long and know one responded to my request for help.

---

