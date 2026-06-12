---
title: "Xubuntu, default Email Client"
date: 2007-01-06
forum: The Cafe
---

### Post by racoq on 2007-01-06
I discovered Claws Mail ([http://www.claws-mail.org/)](http://www.claws-mail.org/)), its a very fast and full featured email client, for low end machines. I find it very light weight, and it eats half resources than thunderbird. Since in Xubuntu we want performance, and we want it to run on low end machines, i encourage you all to try claws email and them answer which email client should be the default one in next Xubuntu release. I vote for Claws Mail

---

### Post by tbroderick on 2007-01-06
mutt

---

### Post by racoq on 2007-01-06
Well... I mean a graphical email Client,bundled with Xubuntu

> **tbroderick said:**
> mutt

---

### Post by happy-and-lost on 2007-01-06
Yup, seems like a much more logical choice.

---

### Post by maxamillion on 2007-01-06
We discussed this in the development mailing lists, I'm not even entirely sure we have come to a complete agreement of what will be included in Feisty just yet but if I remember correctly, both are being managed upstream so if we decide on over the other at a later time, inclusion will be easy.

---

### Post by tbroderick on 2007-01-06
> **racoq said:**
> Well... I mean a graphical email Client,bundled with Xubuntu

Why can't mutt be bundled with Xubuntu?

---

### Post by racoq on 2007-01-06
Yes it can, but its a command line email client (we have pine), that's fine by me if the Xubuntu crew feels that way. However we are discussing here the possible replacement of thunderbird, with an lighter graphical approach.

> **tbroderick said:**
> Why can't mutt be bundled with Xubuntu?

---

### Post by tbroderick on 2007-01-06
> **racoq said:**
> Yes it can, but its a command line email client (we have pine), that's fine by me if the Xubuntu crew feels that way. However we are discussing here the possible replacement of thunderbird, with an lighter graphical approach.

First, we don't have pine because of it's license. It's not even in the repo's.  

Second, you are limiting the discussion to only GUI's. Mutt is just as full featured as sylpheed-claws or thunderbird and is much lighter on resources then both of them.

---

### Post by racoq on 2007-01-06
You are right  on the first point . About the second point, try to convince an newbie in Xubuntu, and an inexperiensed PC user, to use mutt....

I rest my point

> **tbroderick said:**
> First, we don't have pine because of it's license. It's not even in the repo's.  

Second, you are limiting the discussion to only GUI's. Mutt is just as full featured as sylpheed-claws or thunderbird and is much lighter on resources then both of them.

---

### Post by tbroderick on 2007-01-06
> **racoq said:**
>  About the second point, try to convince an newbie in Xubuntu, and an inexperiensed PC user, to use mutt....

I rest my point

I'm not trying to convince anyone to use mutt. I don't see why any discussion about what email client should be the default in Xubuntu should be limited to claws or thunderbird. Your first post stated how much lighter and less resource heavy claws was to thunderbird. Nothing about newbies or inexperienced PC users. For those people, I would recommend just using a decent webmail account like gmail or yahoo.

IMHO, the best full featured, light, low resource, works best on low end machines,  email client is mutt.

---

### Post by Polygon on 2007-01-06
he is taking votes for which [COLOR="Red"]***_GUI_***[/COLOR] email client to use.

you know what he means, you are just giving him a hard time.

---

### Post by tbroderick on 2007-01-06
> **Polygon said:**
> he is taking votes for which [COLOR="Red"]***_GUI_***[/COLOR] email client to use.


I guess I missed the part where it said GUI only. Maybe you can point me to it. I'm just adding my opinion that I think mutt is a better choice then claws or thunderbird. I really don't see the harm in that. I guess my opinion it not wanted. I didn't mean to offend you. :???:

---

### Post by racoq on 2007-01-06
Yes you took the words right out of my mouth :D 

Although, i might agree as a console email client, mutt should be included in any distribution of Ubuntu.

However is GUI email clients that i'm trying to discuss here,  since i think that thunderbird is far from being an optimal solution for Xubuntu, I'm proposing Claws mail. I'm open to discussing other GUI email clients that can be more lightweight than thunderbird. I suggested Claws Email because it is the more lightweight GUI Email Client that i know,  that is most actively mantained by the official Ubuntu repositories, and Claws author's even provided repositories for Ubuntu dapper and Edgy of the latest versions. Those reasons make it ideal for being deployed in the next Xubuntu release, in my opinion.

However i want to see people opinions on that.
> **Polygon said:**
> he is taking votes for which [COLOR="Red"]***_GUI_***[/COLOR] email client to use.

you know what he means, you are just giving him a hard time.

---

### Post by colinleroy on 2007-01-06
Hi,

As a developer of Claws Mail, I have to say I'd strongly support such a decision :-), and by support I also mean help the Xubuntu team to provide a great user experience.

---

### Post by maxamillion on 2007-01-06
[http://www.xubuntu.org/devel](http://www.xubuntu.org/devel) 

Join our mailing list and post out that you are interested so we can start making steps to keep in contact/collaborate.

---

### Post by kalikiana on 2007-01-06
I like Claws Mail as it feels like two times as fast as Thunderbird. However, there are two important drawbacks I'd ask to be overcome before it is used as the default client:

[LIST]
[*]The current support for html mails is incomplete. I don't send any html mails but some mails I receive are not detected as html and in fact reading source code is not very convenient.
[*]Claws Mail doesn't use the user's Gtk+2 theme and preinstalled themes don't even include Tango.
[/LIST]

---

### Post by TuxCrafter on 2007-01-07
Hello,

I want to have them both by default. The trick to acceptance is usually that it is not forces and goes slowly but stable. If we take away Thunderbird the step from windows to Linux would be more difficult that is not a good thing. So keep Thunderbird in it. However I am in favor of a replacement of Thunderbird because I don't stand behind the technic's used for it, GTK is much better. But I need all the functionality of Thunderbird to just be able to work with it. It it already a treat of between evolution and Thunderbird.

So to conclude don't remove Thunderbird, add Claws Mail. Let it improve and be accepted then there may be a option to remove Thunderbird.

---

### Post by daWB on 2007-01-07
> **kalikiana said:**
> 
[LIST]
[*]The current support for html mails is incomplete. I don't send any html mails but some mails I receive are not detected as html and in fact reading source code is not very convenient.
[*]Claws Mail doesn't use the user's Gtk+2 theme and preinstalled themes don't even include Tango.
[/LIST]

Regarding support for html mails being incomplete. Claws Mail does not send HTML mail, it's plaintext only. This is only thing that qualifies its html mail support as incomplete. When receiving an html mail Claws will, by default, strip out the html tags, make any links clickable, and render the message as plaintext. However, there are 2 plugins which will show the html like a webpage, with all the formatting. They are the Dillo Browser plugin and the gtkhtml2_viewer plugin.

Regarding your other point, on the contrary, Claws does use the user's Gtk+ 2 theme. The icons used by Claws are handled by Claws, but they are themeable. There are 2 Claws icon themes available that are based on Tango, they are TangoClaws and TangoOrbit and are available from the Claws site.

---

### Post by daWB on 2007-01-07
> **TuxCrafter said:**
> But I need all the functionality of Thunderbird to just be able to work with it.

Claws is fully-featured, I think you'll find all the same functionality, possibly more.

---

### Post by TuxCrafter on 2007-01-07
> **daWB said:**
> Claws is fully-featured, I think you'll find all the same functionality, possibly more.
I do not agree with that, I have tested claws for a week, and I find it not yet ready for a production machine there are to many things that just do not behave as aspected also the look of the program does not really appeal. I now there are lot of things that you can do about it. But it will not make me work faster or better, so no reason to switch over. I am not going to defend all my statements it is just to much work. But I will say geep going to improve it.

---

### Post by daWB on 2007-01-07
> **TuxCrafter said:**
> ...snip...I find it not yet ready for a production machine there are to many things that just do not behave as aspected...snip...

I won't ask you to defend all your statements, but what did not behave as expected?

---

### Post by racoq on 2007-01-07
First of all i don't agree with you, in my point of view claws mail is as appealing as easy to interact as thunderbird. It's layout is very similar with thunderbird outlook, and  evolution. Probably it has more options and maybe it requires a little more time to set up

> **TuxCrafter said:**
>  the look of the program does not really appeal. 


second point i think that it can make your work faster because claws mail is twice faster than thunderbird and doesn't has so much memory leaks. I have an AMD k6-450 MHZ and while thunderbird drags itself, claws mail works wonderfull

> **TuxCrafter said:**
> 
 But it will not make me work faster or better, so no reason to switch over. 

While featuring in feisty thunderbird and claws mail at the same time, that is not an option since ubuntu does not include gui  applications that can do the same task.

---

### Post by TuxCrafter on 2007-01-07
I will gather some feedback and will make my stand over a week or so with more information.

---

### Post by racoq on 2007-01-08
Just to say in this matter that i submitted this issue, on the Ubuntu launchpad, i hope that someone, picks this up:

[https://blueprints.launchpad.net/ubuntu/+spec/xubuntu-email-client-replacement](https://blueprints.launchpad.net/ubuntu/+spec/xubuntu-email-client-replacement)

---

### Post by TuxCrafter on 2007-01-20
My feedback as promised:

There is no thunderbird import or export function for filters, email, and adressbook.
If the connection with the IMAP server falls away the program stops responding.
Opening of attachment is not asking to open with a default application, you have to set it yourself.
If you select a message of big size, and then select a new message, the program keeps fetching the big message and then after that it goes to the new selected message.
The program is unstable it is stops responding frequently.
Customizing of the too bars doesn't work as expected, I can't add a button in the toolbar to be able to fast change the language.
When the program starts it does not go automatically to the inbox of my IMAP folder, I set this in the preferences but I doesn't do it.
There is a slow response when a message is send, and the program should go back to the main window.
Removed IMAP messages get the color gray and a cross flag, very annoying.
I had the manually set every folder to disable treated view mode, and sort on date, with more then 30 folders this is very annoying.
Personally I can't get used to the quoting system but that is something personal I think.
Icons and interface is ugly even with the TangoOrbit theme.
To much space is used in the left tree to give information about the amount of new, new read, and total amount of message's. Use thunderbird style!
There is no HTML rendering by the default, very annoying.

Conclusion, I think it's not mature enough in the sens of usability and intuitive GUI design.
Follow the gnome specifications of icons and gui layout and get some help with usability issues.

---

### Post by daWB on 2007-01-21
> There is no thunderbird import or export function for filters, email, and adressbook.
A one-time operation should not clutter the menus. There is a script to convert a thunderbird mailbox available in the tools/ directory of the distrubuted tarball, it is also available from the Claws Mail site.
> If the connection with the IMAP server falls away the program stops responding.
It will reconnect, and keep trying until the user settable timeout is reached.
> Opening of attachment is not asking to open with a default application, you have to set it yourself.
Not true. It uses the system's mailcap file, or this can be overridden by the .mailcap file in the user's homedir. To open an attachment you use the Open contextual menu item, (or double click the attachment's icon), to use your default application for that mimetype. You can also use the Open With... menu item to be presented with a list of apps to choose from. From this dialog you can use one of the items in the list or write another into the entry box, choosing whether to save this app for this mimetype, (and so having it written to ~/.mailcap), or just using it the one time. So, it does use the default application, or you can set a new default yourself. 
> If you select a message of big size, and then select a new message, the program keeps fetching the big message and then after that it goes to the new selected message.
Claws Mail is quick. On my system, which is not high-spec, if I select a message with a fairly large body of text, (1.72 MB), it is displayed before I even have a chance to select another message, i.e. in less than a second. Maybe you can explain better what you tested in order to reach your conclusion.
> The program is unstable it is stops responding frequently.
Maybe you can explain what you mean by 'unstable' and 'stops responding' here, because in my experience it is not.
> Customizing of the too bars doesn't work as expected, I can't add a button in the toolbar to be able to fast change the language.
This statement appears very subjective, it, of course, depends on the user's expectations.
> When the program starts it does not go automatically to the inbox of my IMAP folder, I set this in the preferences but I doesn't do it.
There is a preference to go to the inbox after receiving mail, but I think you've found something here. On IMAP it does not go to the Inbox on receiving mail, (POP is fine). We'll look into that bug. 
> There is a slow response when a message is send, and the program should go back to the main window.
I don't notice any slow response, and it does indeed go back to the mainwindow. Can you explain a bit better what you mean?
> Removed IMAP messages get the color gray and a cross flag, very annoying.
You have the option 'Execute immediately when moving or deleting messages' turned off.
> I had the manually set every folder to disable treated view mode, and sort on date, with more then 30 folders this is very annoying.
Threaded or non-threaded view are set per individual folder, as is the sort mode. Sorting by Date is the default sort mode. You don't have to go through every one of your 30 folders at once to set it to unthreaded, you can do it the first time you have an actual need of entering the folder. Anyway, it's  a one time operation, can be soon forgotten about, but perhaps it is a worthy feature request, maybe we can add it to the folder properties, which can be applied recursively, then you could select the parent mailbox and set it here. 
> Personally I can't get used to the quoting system but that is something personal I think.
It is flexible and has many available symbols, I guess it is a personal thing.
> Icons and interface is ugly even with the TangoOrbit theme.
It's a GTK+ app, that is your personal view.
> To much space is used in the left tree to give information about the amount of new, new read, and total amount of message's. Use thunderbird style!
The columns in the Folder List are customisable, you can hide the new, unread, and total columns and have the unread number displayed next to the folder name. You can also resize the the pane in the standard way.
> There is no HTML rendering by the default, very annoying.
Yes there is. The standard HTML rendering is to present it as plaintext with clickable links. You can use one of the two HTML rendering plugins if you prefer.
> 
Conclusion, I think it's not mature enough in the sens of usability and intuitive GUI design.
Follow the gnome specifications of icons and gui layout and get some help with usability issues.
As is clear from my repsonses above, I think your conclusion is wrong. We do attempt to follow the freedesktop.org standards, help and suggestions on this matter is always welcome.

---

### Post by ButteBlues on 2007-01-28
Has anyone else using feisty had issues installing from the Edgy repos?

---

### Post by Joer4x4 on 2007-02-25
I voted for Claws since I am going to try Xubuntu. I really don't care about the desktop as much as the applications. I want to get things done. 

Even on my 2G box TB is slow. Cross platform is fine but at least write it so it executes quickly or optimise the code. It can be done. Don't know what they're thinking!

Just 2 irritations with Claws.

When I first tried it and had it download my imap folders, I could not find a way to stop it. On a phone line it takes a few hours. I prefer to do a bit at a time.

Second, I can't write mail in RTF. Sometimes a little emotion is need to be understood properly or to key in on certain phrases. On their web page they say it's not wanted? My question is by who? Are they trying to protect me from myself? An add-on is needed here!
Yes, I understand the hazards of html email. But I am a big boy an can take care of myself. Besides it's my decision not theirs! :)

Any way it seems the best of the lot of what's available!

---

### Post by racoq on 2007-02-26
> **Joer4x4 said:**
> I voted for Claws since I am going to try Xubuntu. I really don't care about the desktop as much as the applications. I want to get things done. 

Even on my 2G box TB is slow. Cross platform is fine but at least write it so it executes quickly or optimise the code. It can be done. Don't know what they're thinking!

Just 2 irritations with Claws.

When I first tried it and had it download my imap folders, I could not find a way to stop it. On a phone line it takes a few hours. I prefer to do a bit at a time.

Second, I can't write mail in RTF. Sometimes a little emotion is need to be understood properly or to key in on certain phrases. On their web page they say it's not wanted? My question is by who? Are they trying to protect me from myself? An add-on is needed here!
Yes, I understand the hazards of html email. But I am a big boy an can take care of myself. Besides it's my decision not theirs! :)

Any way it seems the best of the lot of what's available!

It seems like the majority of people want claws mail in Xubuntu. But the people in charge of the project are no willing to accept that change, and there isn't anyone, who is willing to take responsibility in maintaining claws mail with upload rights, the following entry in the mailing list is still a issue:

[https://lists.ubuntu.com/archives/xubuntu-devel/2007-January/002916.html](https://lists.ubuntu.com/archives/xubuntu-devel/2007-January/002916.html)

I think that Claws deserves a little more attention.

---

### Post by maxamillion on 2007-02-26
We mainly just need a devel to handle it ... or atleast a MOTU to sponsor it, but yes I agree that it deserves a little more attention.

#I swore we beat this thread to death long ago :tongue:

---

### Post by Joer4x4 on 2007-02-26
> **racoq said:**
> It seems like the majority of people want claws mail in Xubuntu. But the people in charge of the project are no willing to accept that change, and there isn't anyone, who is willing to take responsibility in maintaining claws mail with upload rights, the following entry in the mailing list is still a issue:

[https://lists.ubuntu.com/archives/xubuntu-devel/2007-January/002916.html](https://lists.ubuntu.com/archives/xubuntu-devel/2007-January/002916.html)

I think that Claws deserves a little more attention.


So does a lot of other applications. Linux itsself is great, stable, and better than MS. But on the application side MS is still way ahead of the game. The only complete applications that I see is (everyday use) Openoffice.org and Firefox.

The applications directly reflect what the developers want, not what the users want or could do to increase productivity. This not a slam, just "what is" as I see it after using linux for the last 6 months or so.

---

### Post by TuxCrafter on 2007-02-26
I have tested claws mail for 2 weeks with xubuntu and imap system, I found to many issues that prevented me from working efficient with this mail client. Until they fix those issues or promise that they will work extremely hard to solve the problems. And also solve problems the developers do not see as a problem but a user can. It will not become the default mail program!

---

### Post by racoq on 2007-02-26
> **TuxCrafter said:**
> I have tested claws mail for 2 weeks with xubuntu and imap system, I found to many issues that prevented me from working efficient with this mail client. Until they fix those issues or promise that they will work extremely hard to solve the problems. And also solve problems the developers do not see as a problem but a user can. It will not become the default mail program!

You are talking of only a feature, as it would be all the applications that is the problem, i work with Claws mail every day, and i find it very useful for everyday tasks.

Even if there is a problem in that feature (that i don't use), it would be addressed by the Claws mail staff, since they offered that support to work hard to eliminate all the flaws that claws mail can have, in order to increase Xubuntu users experience. You don't get better support than this, from the Thunderbird staff. We should take advantage of this.

The issue is not one or two flaws, as it was referred earlier, Claws mail needs a user with upload rights, in order to update frequently Claws mail releases, instead of synchronizing with debian, maybe work closely sometimes with the Claws mail development team, and other issues that can come with.

Please understand that.

P.S.
I do not belong to Claws development team, and am not related to anyone of them. I only think that a lightweight distro like Xubuntu, deserves a better alternative than Thunderbird

---

### Post by doobit on 2007-02-26
I like Sylpheed. Has anyone considered that one?

---

### Post by daWB on 2007-02-27
> **TuxCrafter said:**
> I have tested claws mail for 2 weeks with xubuntu and imap system, I found to many issues that prevented me from working efficient with this mail client. Until they fix those issues or promise that they will work extremely hard to solve the problems. And also solve problems the developers do not see as a problem but a user can. It will not become the default mail program!

You seem to keep saying this kind of thing, but will not explain in more clarity. I responded to each of the points that you previously raised to try to get some kind of clearer response from you, some greater detail - things can't be fixed if all we have to go on is the equivalent of "*it don't work right*".

Many of the issues that you pointed out before are non-issues, unless you take the extremely subjective view. I suspect, even, that it's not so much to do with any issues as it is to do with the fact that you have a personal preference for thunderbird.

---

### Post by colinleroy on 2007-02-27
> **TuxCrafter said:**
> Until they fix those issues or promise that they will work extremely hard to solve the problems

I promise to work extremely hard to solve your problems once you paid me extremely well for whatever amount of time I need to solve your problems.

What the hell, did you read your post before sending it? The world's not kneeled before you, you know.

---

### Post by TuxCrafter on 2007-02-27
OK, I don't want to hassle everyone. I am a good guy and you do good work. I don't have a special preference for thunderbird. (I really dislike emulated gui's that are slow!)

So lets work together and make clawsmail the best lightweight mail client.

I will address one problem at a time and. If we can tackle one problem in 2 weeks than within a year I think we can make a new default mail client!

If you can give me all the info you want to fit me in your development en debug process!

Like:
Development reports and lists
Testing reports
Debug reports
etcetera

Than we can begin this week.
If the process is good, i will maintain the ubuntu package for a while!

---

### Post by TuxCrafter on 2007-02-27
Sent this to xubuntu-devel

```
http://ubuntuforums.org/showthread.php?p=2219597#post2219597
http://www.claws-mail.org/

Hello guy's,

There have been a lot of heated discussions about the default mail client for xubuntu.

Clawsmail vs Thunderbird

I believe that Thunderbird is on this moment the best client for the normal non geek user and clawsmail need a lot of work. But there are people that disagree with that, so I tried to convince them. But they are fanatic and want more information (I like that, means they stand behind what the do!) 

So I made a decision's. I will be the package maintainer for the next 3 or 2 releases of xubuntu. Then we will come together again and decide if clawsmail is user friendly enough to become the default mail client for xubuntu.

I will work together with the clawsmail developers to address problems and do debugging and feature request etcetera.

What do you people think of it!
```

---

### Post by kawazu on 2007-02-27
> **TuxCrafter said:**
> I have tested claws mail for 2 weeks with xubuntu and imap system, I found to many issues that prevented me from working efficient with this mail client. Until they fix those issues or promise that they will work extremely hard to solve the problems. And also solve problems the developers do not see as a problem but a user can. It will not become the default mail program!

Not sure whether I'm to say something on that as I am just "another user", but actually I switched from Thunderbird to Claws some time ago (read all the reasons why [here]("http://dm.zimmer428.net/index.php/archives/217") if you're interested). My basic "issues" with Thunderbird, outlined in a rather short way:

- It's heavy on memory, even with little extensions installed. Given that Xubuntu aims at being "lightweight", burning > 256M RAM (on my machine) for an _MUA_ is not the way to go. Claws is lighter here.

- Thunderbird also seems to be somewhat broken on IMAP, not just talking about a known bug with IMAP on HT/DualCore CPUs. I don't consider the idea of leaving _all_ the mail marked as deleted on the server not really that user friendly given the user doesn't know about the "gory details" of IMAP and one day wonders why his/her mailspool is full.

- Junk filtering (given bogofilter is installed) is _way_ more usable on Claws than on Thunderbird.

Just my €0.02 on that.
Kris

---

### Post by graabein on 2007-02-27
How does [Sylpheed]("http://sylpheed.sraoss.jp/en/") compare to Thunderbird and [Claws Mail]("http://www.claws-mail.org/")? I would think Sylpheed is more mature than Claws Mail but I might be wrong. Anyone willing to explain?

---

### Post by colinleroy on 2007-02-27
> **TuxCrafter said:**
> 
Development reports and lists
Testing reports
Debug reports
etcetera

Than we can begin this week.
If the process is good, i will maintain the ubuntu package for a while!

Good things may come out of this! So,

You have the MLs for general questions/ideas etc : [http://www.claws-mail.org/MLs.php](http://www.claws-mail.org/MLs.php) 
Bugzilla: [http://www.thewildbeast.co.uk/claws-mail/bugzilla/index.cgi](http://www.thewildbeast.co.uk/claws-mail/bugzilla/index.cgi) where you can report bugs and RFEs
daily CVS snapshots (updated 3 times a day): [http://www.claws-mail.org/snapshots/](http://www.claws-mail.org/snapshots/)
Buildbot reports : [http://buildbot.colino.net/logs/](http://buildbot.colino.net/logs/) (it tests minimal build, full build, make dist/install), and full plugins build/dist/install)
CVS tracker: [http://colino.net/claws-mail/](http://colino.net/claws-mail/)

---

### Post by kawazu on 2007-02-27
> **graabein said:**
> How does [Sylpheed]("http://sylpheed.sraoss.jp/en/") compare to Thunderbird and [Claws Mail]("http://www.claws-mail.org/")? I would think Sylpheed is more mature than Claws Mail but I might be wrong. Anyone willing to explain?

Claws-Mail used to be Sylpheed-Claws, a patched-up bleeding-edge version of Sylpheed, so by now Claws-Mail is supposed to be ahead of Sylpheed at least in terms of features available. Back in the sylpheed/sylpheed-claws days, being an end-user quite often using plain Sylpheed seemed to be a better solution if you cared about maturity / stability of the code, but, right now, given that Claws-Mail is a piece of software on its own, I think at least from the stability/maturity point of view they're on par.

Cheers,
Kristian

---

### Post by graabein on 2007-02-27
Thanks for clearing that up Kristian. I did not know Claws Mail was a fork of Sylpheed. 

I personally use webmail but for those who have experience with both Claws Mail and Thunderbird I suggest giving detailed feedback to the Claws devs now that we've got their attention. Good luck to everyone!

---

### Post by kawazu on 2007-02-27
> **graabein said:**
> Thanks for clearing that up Kristian. I did not know Claws Mail was a fork of Sylpheed. 


You're welcome. I made my first experiences with sylpheed in early 200, I guess, when searching for a replacement to XfMail which has an easy-to-use interface and provides for powerful filtering rules without having to go through procmail and friends. :)

> 
I personally use webmail but for those who have experience with both Claws Mail and Thunderbird I suggest giving detailed feedback to the Claws devs now that we've got their attention. Good luck to everyone!

For what I experienced so far (on the s-c mailing lists earlier), the Claws developers overally are just a kind bunch of people who never hesitate helping users out given they're in trouble. Discussing the inclusion of claws-mail as xubuntu default mailer, however, seems to have been rather "emotional" at times, leaving facts and comparisons aside and mainly focusing on "bashing" weaknesses exposed by the one or the other application.

As an end-user, I do not really care given that I can install whichever program I want from the package repositories. For what I see, however, given that Xubuntu is supposed to be a lightweight version of Ubuntu, probably most of the discussion is pointless - in terms of being lightweight, Thunderbird probably is far beyond being a good choice... 

Cheers,
Kristian

---

### Post by dlpfmVfH on 2007-03-05
The new Claws-mail for ubuntu now including feisty packages
 
			[www.claws-mail.org]("http://www.claws-mail.org/ubuntu/")

Add this to /etc/apt/sources.list:
			      For 6.06 Dapper: 
deb [http://www.claws-mail.org/ubuntu/dapper/](http://www.claws-mail.org/ubuntu/dapper/) ./
			      For 6.10 Edgy: 
deb [http://www.claws-mail.org/ubuntu/edgy/](http://www.claws-mail.org/ubuntu/edgy/) ./
			      For 7.04 Feisty: 
deb [http://www.claws-mail.org/ubuntu/feisty/](http://www.claws-mail.org/ubuntu/feisty/) ./

he packages are signed, add [Colin's key]("http://colino.net/colin.publickey") to your APT keyring, using sudo apt-key add colin.publickey

---

### Post by h.aling on 2007-03-09
This is what I think is still missing in Claws to kick TB's behind:
* Full HTML compose and display support (and the ability to choose the default render engine)
* GUI cleanup (icons, colors and 'screen clutter', maybe call in an interface expert from somewhere???)

Stability and additional features will develop itself when the userbase grows and bugreports / feature requests start coming in. Also a wider userbase will probably attract more developers...

Feisty may be a bit too soon, but v7.10 should definitely be achievable...

---

### Post by LanDan on 2007-03-19
> **h.aling said:**
> This is what I think is still missing in Claws to kick TB's behind:
* Full HTML compose and display support (and the ability to choose the default render engine)
* GUI cleanup (icons, colors and 'screen clutter', maybe call in an interface expert from somewhere???)

Stability and additional features will develop itself when the userbase grows and bugreports / feature requests start coming in. Also a wider userbase will probably attract more developers...

Feisty may be a bit too soon, but v7.10 should definitely be achievable...

ben het hier wel met je eens, maar HTML compose is niet iets wat de ontwerpers "nog" niet voor elkaar hebben, maar meer een standpunt wat ze innemen 
"het enige waar HTML in een mailtje goed voor is is het verbergen van code voor de ontvanger" kan ze hier wel gelijk in geven want het is ook een onzinnige feature,,, maar goed, aangezien ik zelf XFCE (niet Xubuntu) aan een hoop gebruikers geef is dat toch iets wat ik niet uit kan leggen, 
mijn stem gaat dus naar Thunderbird, ondanks dat Claw qua features, snelheid en stabiliteit alle andere mailers ruimschoots achter zich laat, Claws is dus niet een buggy stukje software zoals je hier voorstelt, integendeel zelfs.

---

### Post by racoq on 2007-03-19
> **LanDan said:**
> ben het hier wel met je eens, maar HTML compose is niet iets wat de ontwerpers "nog" niet voor elkaar hebben, maar meer een standpunt wat ze innemen 
"het enige waar HTML in een mailtje goed voor is is het verbergen van code voor de ontvanger" kan ze hier wel gelijk in geven want het is ook een onzinnige feature,,, maar goed, aangezien ik zelf XFCE (niet Xubuntu) aan een hoop gebruikers geef is dat toch iets wat ik niet uit kan leggen, 
mijn stem gaat dus naar Thunderbird, ondanks dat Claw qua features, snelheid en stabiliteit alle andere mailers ruimschoots achter zich laat, Claws is dus niet een buggy stukje software zoals je hier voorstelt, integendeel zelfs.

Speak english, please....

---

### Post by TuxCrafter on 2007-03-19
echt geniaal lekker in het nederlands lullen op het forum hi hi :lolflag:

---

### Post by raul_ on 2007-03-23
> **TuxCrafter said:**
> I also the look of the program does not really appeal. 

did you try other skins? The default gtk theme is ugly in any application. I'm using the TangoClaws theme and it's really neat

---

### Post by diskotek on 2007-03-23
i already check the website of claws; it really looks cool & functional gui mail client. i think i'll change my email client before xubuntu feisty :D 

btw, i also checked "mutt" because of the discussion on the first page. that's pretty hard for newbies and first time users...

---

### Post by racoq on 2007-05-07
Hello TuxCrafter and Colinleroy. Since i last checked, you guys were working together to push Claws Mail harder to address some claws mail issues, making it possible, to include it as the default email client in Xubuntu. How's work doing friends? Will the Xubuntu community have a more lightweight email client at Gutsy Gibson?

As this thread showed the majority of the Xubuntu users, would like to have it by default, and if possible in Gutsy Gibbon

I'm relaunching this thread for the community, to know hows the status of this effort.

Best regards

---

### Post by colinleroy on 2007-05-07
> **racoq said:**
> Hello TuxCrafter and Colinleroy. Since i last checked, you guys were working together to push Claws Mail harder to address some claws mail issues, making it possible, to include it as the default email client in Xubuntu. How's work doing friends? Will the Xubuntu community have a more lightweight email client at Gutsy Gibson?


We didn't hear back from Tuxcrafter after he dropped by on our IRC channel once.

---

### Post by racoq on 2007-05-07
> **colinleroy said:**
> We didn't hear back from Tuxcrafter after he dropped by on our IRC channel once.

Oh thats to bad friend :(  you guys are pushing it all the work yourselfs, if i add some more knowledges and time i would really love to help. Well i'm going to try to propose the replacement in a launchpad issue for gutsy gibbon,

By the way great work you've been doing., your port to maemo platforms looks really awesome. And the great support you are giving in your versions to XFCE, and new features are making claws mail, a beautiful, and well polished email client.

Well i must ask again, if anyone is interested in REALLY helping the Claws Mail team, for improving their experience for inclusion in Xubuntu Gutsy Gibbon, now is the time.

---

### Post by TuxCrafter on 2007-05-07
> **colinleroy said:**
> We didn't hear back from Tuxcrafter after he dropped by on our IRC channel once.

Hi colinleroy, yes it has been a long time indeed. I have discussed the situation with Jim Campbell some time ago and I decided not to continue supporting clawsmail anymore.

There were too many issues about the different views of usability of a mail client.

To summary, I would like to build to a fast low resource footprint gtk program with at least the same functionality and usability as Mozilla Thunderbird.

The clawsmail developers do not share this vision and want to create there own unique program with a different angle of attach (definitely not a fast Thunderbird clone).

Being at this point, I decided not to put a lot my of time and effort in this program.

If a user decide to try clawsmail they can manually add the Debian repository of there own package server in the apt sources list.

I now put my time in the FSFE and open source software licensing issues

---

### Post by aysiu on 2007-05-07
I voted Claws even though I like Thunderbird better *and* found Claws to be a lot like what people accuse KDE of being--full of too many confusing configuration options.

The only reason I voted Claws--speed. Most people use Xubuntu because it's lighter, and it's often recommended for older hardware. Claws is light and so perfect for the job.

---

### Post by jerrylamos on 2007-05-07
I run on several computers and even a couple different locations so I use AOL Mail and Yahoo Mail so I can always access them wherever I am.  default Email Client on any Ubuntu for me is the one that is the smallest and hides in the corner without affecting anything else, and nothing else has any dependencies on it.

Cheers, Jerry:)

---

### Post by h0bbe on 2007-05-07
> **aysiu said:**
> I voted Claws even though I like Thunderbird better *and* found Claws to be a lot like what people accuse KDE of being--full of too many confusing configuration options.

The only reason I voted Claws--speed. Most people use Xubuntu because it's lighter, and it's often recommended for older hardware. Claws is light and so perfect for the job.

I agree. I'm looking for a light-weight easy-to-use mail client and find claws rather confusing (just started using it). Have been looking around for another one but I can't find any other active light gtk mail client available.

Guess I have to stick to Claws until i understand its benefits.

---

### Post by racoq on 2007-05-07
> **TuxCrafter said:**
> Hi colinleroy, yes it has been a long time indeed. I have discussed the situation with Jim Campbell some time ago and I decided not to continue supporting clawsmail anymore.

There were too many issues about the different views of usability of a mail client.

To summary, I would like to build to a fast low resource footprint gtk program with at least the same functionality and usability as Mozilla Thunderbird.

The clawsmail developers do not share this vision and want to create there own unique program with a different angle of attach (definitely not a fast Thunderbird clone).

Being at this point, I decided not to put a lot my of time and effort in this program.

If a user decide to try clawsmail they can manually add the Debian repository of there own package server in the apt sources list.

I now put my time in the FSFE and open source software licensing issues

I don't judge your decision, or opinion on the issue. But you could warn Colin of your decision, leaving place for other volunteer enthusiast to work with the Claws mail Team, making that extra effort.

That was a bad call, and not very polite from you, since you've made your personal commitment here in this forum, in front of everyone to the Claws Mail team.

---

### Post by daWB on 2007-05-08
> **TuxCrafter said:**
> I have discussed the situation with Jim Campbell some time ago and I decided not to continue supporting clawsmail anymore.

That's a 'strange' way to let us know TuxCrafter. How long does it take to drop by the IRC channel??

Many thanks!

---

### Post by TuxCrafter on 2007-05-08
> **daWB said:**
> That's a 'strange' way to let us know TuxCrafter. How long does it take to drop by the IRC channel??

Many thanks!

My apology, I have discussed it in the #xubuntu IRC channel. I also should have visit the #claws. I have been very very busy, and didn't pay attention to this problem anymore. Would not happen again!

---

### Post by colinleroy on 2007-05-08
> **TuxCrafter said:**
> To summary, I would like to build to a fast low resource footprint gtk program with at least the same functionality and usability as Mozilla Thunderbird.

The clawsmail developers do not share this vision and want to create there own unique program with a different angle of attach (definitely not a fast Thunderbird clone).

Indeed, we don't want to do a Thunderbird clone. I just don't see the advantage. We do Claws Mail with its own strenghts, Thunderbird people do Thunderbird with different ideas. No need to write the same thing twice in my opinion.

Well, anyway, that's not really a problem in my opinion: people who prefer Claws Mail for what it is won't have a hard time installing it, packages exist for most distros.

---

### Post by h.aling on 2007-05-08
I like Claws. That is, it seems to be really good coded as it's light and feature full...

I just don't like the interface very much, nor does my mother or my grandparents... They do like/understand Thunderbird...

I'm not suggesting that Claws should look like Thunderbird, but Claws sure needs a interface cleanup or some innovative interface ideas to be 'sexy' and easy for everybody...

Maybe call in an 'interface/usability expert' from somewhere? (Example: [http://thorwil.wordpress.com/](http://thorwil.wordpress.com/))

-H-

---

### Post by wgscott on 2007-08-27
I've been using the  sylpheed-claws-gtk2 mail program both on Xubuntu and on OS X.  (I use it on OS X as a mail-reader for incoming mail I sort with procmail).

I think it is superb, completely flexible and customizable, and very stable.  I used kmail for a while and found it clunky and unstable. 

Being able to install sylpheed without the gnome or kde cruft is a real advantage.

---

### Post by julian67 on 2007-09-18
Thunderbird has to be default because users coming from Windows can just drop their profile in and be up and running. And a user who has nothing to migrate but has gmail or yahoo mail or similar with free POP and smtp access and wants to try it will find step by step guides on setting up Thunderbird from yahoo/gmail/whoever and a hundred other places. For a distro that sees novice users and people migrating from Windows as important/core target groups this kind of ease of use is surely essential and non-negotiable?  Adding another application to do the same job seems to contradict the Xubuntu approach of one application per task as default.  If a migrating user cannot get his/her email client up in a very short time that user will very quickly quit migrating and be booting back into Windows or MacOS. Btw I use Xubuntu but don't use  Thunderbird *or* Claws, but if I set up *buntu for a user coming from Windows it would be Thunderbird every time. I have migrated my substantial mail archive several times across operating systems and clients and there are very few ways of doing it easily and confidently...Most mail clients make you feel as locked in as any proprietary vendor has ever achieved. Thunderbird (or having your own imap server!) seems to me to be a great enabler as well as a good email client. As a default client Claws is more suitable for distros aiming for experienced users  ...who probably prefer to make their own choices anyway ;-) A default has to be the choice which suits most people most of the time, not necessarily the ultimate solution for the knowledgeable user.

---

### Post by Gargamella on 2007-09-18
Thunderbird is a well-known software, but since we're talking about xubuntu I trust claws-mail.
I installed it and I like it very much... thank you for the tip.

+1 for claws

---

### Post by K.Mandla on 2007-09-18
> **julian67 said:**
> Thunderbird has to be default because users coming from Windows can just drop their profile in and be up and running. ...
I'm going to disagree on this point. I've heard the whole ease-of-switching argument many, many times and I respect it. But I believe the core issue is deeper than that.

Xubuntu was, two years ago, a solution for older hardware that kept to lightweight, GTK2 applications [as a matter of principle]("https://wiki.ubuntu.com/Xubuntu"). Somewhere along the line that changed, and what's coming down the pipe now is essentially Gnome Ubuntu, with a few sprinkles of XFCE to make it vaguely different. You can differ on that, if you like.

I'm not a developer and I don't run Xubuntu any more, but the argument at hand is really lightweight-but-functional versus popular-but-bloated. (I apologize if you're really a huge Thunderbird fan, but I'm not particularly fond of overweight software. I check my mail with Sylpheed-GTK1, by the way. ;) ) It's the old, original goal of Xubuntu, as a lightweight distro for older hardware, versus its own maturation into a full heavyweight.

At the same time, if I have to coax someone through the change between Windows and Linux, and I have to rely on Thunderbird to do it, that's fine. But Linux is not Windows, and at some point, that has to be learned. 

And from my experience, giving someone the blue pill and letting them discover Linux is more gratifying and successful than giving them a mock XP layout and a few transitional programs to wean them off MS. It's like jumping into a cold lake. You either do it or you don't. Some people want to, and can. Others don't really want to, and never will.

So you can argue that Thunderbird -- popular but heavy, beyond what Xubuntu intended to do -- will make it easier for someone to make the switch. I don't think that's enough of a reason to use it as the default, mostly because there's only one person who knows if they'll switch, and they're the ones at the keyboard.

Anyway, that's where I'm at on the whole issue. :mrgreen:

---

### Post by julian67 on 2007-09-18
> **K.Mandla said:**
> I'm going to disagree on this point. I've heard the whole ease-of-switching argument many, many times and I respect it. But I believe the core issue is deeper than that.

Xubuntu was, two years ago, a solution for older hardware that kept to lightweight, GTK2 applications [as a matter of principle]("https://wiki.ubuntu.com/Xubuntu"). Somewhere along the line that changed, and what's coming down the pipe now is essentially Gnome Ubuntu, with a few sprinkles of XFCE to make it vaguely different. You can differ on that, if you like.

I'm not a developer and I don't run Xubuntu any more, but the argument at hand is really lightweight-but-functional versus popular-but-bloated. (I apologize if you're really a huge Thunderbird fan, but I'm not particularly fond of overweight software. I check my mail with Sylpheed-GTK1, by the way. ;) ) It's the old, original goal of Xubuntu, as a lightweight distro for older hardware, versus its own maturation into a full heavyweight.

At the same time, if I have to coax someone through the change between Windows and Linux, and I have to rely on Thunderbird to do it, that's fine. But Linux is not Windows, and at some point, that has to be learned. 

And from my experience, giving someone the blue pill and letting them discover Linux is more gratifying and successful than giving them a mock XP layout and a few transitional programs to wean them off MS. It's like jumping into a cold lake. You either do it or you don't. Some people want to, and can. Others don't really want to, and never will.

So you can argue that Thunderbird -- popular but heavy, beyond what Xubuntu intended to do -- will make it easier for someone to make the switch. I don't think that's enough of a reason to use it as the default, mostly because there's only one person who knows if they'll switch, and they're the ones at the keyboard.

Anyway, that's where I'm at on the whole issue. :mrgreen:

I almost agree with you and if you were talking about Zenwalk or another Xfce distro I'd completely agree with you, but Xubuntu isn't Zenwalk or Kate or Lunar. It's a subset of Ubuntu and that means we must always be mindful of  Bug #1. 

> Microsoft has a majority market share in the new desktop PC marketplace. This is a bug, which Ubuntu is designed to fix.

I think that statement and the "Linux for Human Beings" tag means that user friendliness and convenience have a greater importance than they might in other distros, Debian would be a fine and relevant example. Fixing Bug #1 means specifically getting people to migrate from Windows to FOSS, and initially the *buntu flavours of FOSS. When you consider that many Windows users are going to be unsure (but not incapable) of migrating their mail from Outlook to Thunderbird within Windows, or even unaware that there is a choice, then you can see that some things just have to be as easy and quick as possible on day one. I think there are areas where people might expect a learning curve on a new system (graphics or video editing for example) but an easy/familiar email client had better just be a given. Just migrating from different clients with no decent export/import tools and different storage within Linux can be a problem, what to speak of doing it as a noob in an unfamiliar environment. 

But you might be right, I'm just expressing my opinion. And anyway I'm a kind of criminal as I run Evolution in Xfce :lolflag: (these gnome apps can be really fast when you don't manage your desktop with Nautilus). OK now to hide behind the sofa while the ad-hominem bombardment begins......... :)

---

### Post by K.Mandla on 2007-09-18
> **julian67 said:**
> But you might be right, I'm just expressing my opinion. 
Same here. No hard feelings. ;)

---

### Post by kadath on 2007-09-18
I agree with K.Mandla's post above about Xubuntu becoming essentially regular Ubuntu with Xfce thrown on top. The devs just keep adding more and more GNOME components, always justifying it with "well the dependencies aren't too bad" or "well the dependencies are already in there" blah blah blah.

I tried Zenwalk and it didn't like my hardware as much as Xubuntu did, unfortunately :(

---

### Post by K.Mandla on 2007-09-19
> **kadath said:**
> I agree with K.Mandla's post above about Xubuntu becoming essentially regular Ubuntu with Xfce thrown on top. The devs just keep adding more and more GNOME components, always justifying it with "well the dependencies aren't too bad" or "well the dependencies are already in there" blah blah blah.

I tried Zenwalk and it didn't like my hardware as much as Xubuntu did, unfortunately :(
If you're after a XFCE-driven desktop, I had [good luck]("http://kmandla.wordpress.com/2007/09/09/wolvix-110-on-450mhz-k6-2-256mb/") with Wolvix on old hardware. It's what I would be running if Ubuntulite hadn't been [resurrected]("http://kmandla.wordpress.com/2007/09/16/against-all-odds-ubuntulite-fights-back/").

---

### Post by kadath on 2007-09-19
> **K.Mandla said:**
> If you're after a XFCE-driven desktop, I had [good luck]("http://kmandla.wordpress.com/2007/09/09/wolvix-110-on-450mhz-k6-2-256mb/") with Wolvix on old hardware. It's what I would be running if Ubuntulite hadn't been [resurrected]("http://kmandla.wordpress.com/2007/09/16/against-all-odds-ubuntulite-fights-back/").

Well my major problem is I like the convenience of a Debian-based system. On Slackware-based distros, you're constantly compiling *everything*, and I'm not exactly too interested in that.

Someday when I have more time I might look into installing straight Debian with Xfce over it.

---

### Post by Kangarooo on 2010-06-20
I woukld like to have option make default Gmail witch opens in default webbroser.

---

