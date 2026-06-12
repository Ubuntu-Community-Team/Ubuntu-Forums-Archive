---
title: "Is OpenOffice now the weakest link?"
date: 2009-08-27
forum: The Cafe
---

### Post by Aearenda on 2009-08-27
It seems to me that Ubuntu and other Linux distros have now developed to the point that they can easily supplant Windows. There is a great deal of rivalry between distros and projects, and this spurs them all on to ever greater things. 

However, the flagship open source office automation package, OpenOffice, does not seem to be advancing so rapidly, and after using it (running on Ubuntu) for four years of Masters study as well as numerous newsletters, address lists, posters and other items, during which time I have pushed it hard in several areas, it seems to me that it is OpenOffice that will hold back widespread adoption of Linux in ordinary office use from now on.

A case in point: a few months ago my wife's laptop was becoming increasingly unreliable on Windows XP. We could have got it with Vista, but chose not to. I had converted her to Thunderbird and Sunbird some time ago, so that we could easily share calendars. Not wanting to rebuild XP on it yet again, I persuaded her to try Ubuntu, and after some teething issues it ran really well, apart from the microphone quality (which turned out to be a hardware fault, worked around by proprietary software on Windows). 

However, OpenOffice was not the same success story. There were repeated layout problems for other people on opening Word-format documents she had sent them, which is essential for her in her work (and it wasn't just font difference issues). Impress was generally slow and animations a waste of effort. From time to time Writer forgets to update the UI, and it is necessary to press CTRL/R to get it to redraw the screen. Sometimes things disappear from the page, only to reappear next time the document is opened. And so on.

So we tried running her copy of Office 2003 in WINE. That didn't look so good on the screen, but did fine until she needed to add clipart. Fail.

So now she has Windows 7 RC, and a trial copy of Office 2007, and in spite of the ribbon (it got a few curses at first) she is loving it. Of course there are still niggles; but the niggles are in things she does occasionally, not things she uses every day.*

Today I switched our wireless network from WPA to WPA2 (should have done that ages ago). Windows 7 asked for some geeky info, and Ubuntu on my netbook just happily adapted without complaint. My wife's comment to that was, in effect, Ubuntu just did it because that's geeky stuff and Linux devs love to make that kind of thing work nicely, while on Windows it's the everyday office stuff that works nicely. And that's what triggered this post!

So there it is: in my view, OpenOffice needs some love, so that it can be a true rival to Office 2007 and 2010, rather than an Office 2000 look-alike. I can't do it: I'm no developer, and in any case, it's a big job - perhaps the biggest, after the Linux kernel. I know that Sun had a reputation for discouraging participation in OO - maybe now that Sun has been bought by Oracle things will open up. I can't see Oracle letting it die.

If enough of us agree about this, maybe the FOSS powers-that-be will notice and take action. Here's hoping!

[I](PLEASE don't reply with suggestions for fixing the issues I've described individually - that's not the point here.)
[/I]

* It's Office 2007 so that we can share calendars - Outlook 2003 couldn't do this, but Outlook 2007 can publish to a private webdav server (and it was easy to add that to Apache on our house server running Hardy). We could have used Thunderbird and Sunbird, but it seemed sensible to try Outlook since Sunbird's future is looking cloudy, and the poor performance of Lightning on my netbook wasn't inspiring. Evolution is just fine as far as speed is concerned, but my wife's calendar is complex, and Evolution doesn't always agree with other programs on how to interpret an iCal file, probably because the iCal definitions are somewhat fuzzy.

---

### Post by running_rabbit07 on 2009-08-27
Should maybe rant to Sun or whoever it is that sponsors development of OpenOffice. 

Personally, I don't use a calender, but I guess it would be nice to have in the future.

You did mention one of the answers to your problem. If someone in the community has an idea how to fix the problem, then they could share it with Sun or maybe even be written into Ubuntu's version of OO if there is one.

---

### Post by madjr on 2009-08-27
hm take a look at [koffice 2]("http://www.koffice.org/") (kinda being still ported and some features missing till 2.1 or 2.2)

very nice interface

and they welcome contributors

the head in charge of OOo will be Oracle i heard

also give google docs a try

if nothing works than what will work is running Office in a **virtual machine** (not wine)

you can even set the vm in **seamless** mode

---

### Post by oboedad55 on 2009-08-27
The word processor works as well or better than any Windows equivalent, but the spread sheet is not up to par yet.

---

### Post by hanzomon4 on 2009-08-27
Have any of you seen the show the "the weakest link"? :lolflag:

---

### Post by crush304 on 2009-08-28
> **Aearenda said:**
>  There were repeated layout problems for other people on opening Word-format documents she had sent them, which is essential for her in her work (and it wasn't just font difference issues). 

edit in whatever program you choose and then export as pdf to send to someone else. doc format whether created by microsoft word or open office writer is a horrible format for sending documents to someone else

---

### Post by JillSwift on 2009-08-28
No. The one thing that prevents a mass migration to some flavor of Linux is nothing more than inertia.

Windows and MS Office are known entities that get the job done. Even if it's provable empirically that it's getting the job done with far greater effort of upkeep and maintenance costs compared to a similar configuration of Linux, it matters little when the transition itself would be costly and turbulent (or for that matter, even if the transition actually would not be, but is perceived it would).

GNU/Linux has an uphill battle to fight against basic human psychology, but we can see by its growth and by its acceptance by significant companies and government agencies worldwide, it's making progress.

OOo is in the same position, really. But it, too, is making progress. I note that most complaints about OOo are in interoperability with Word/MS Office. I don't know that it's fair to call that a problem when Microsoft is making no effort to aid interoperability. They likely do not even want it. But, as time goes on and better standards for document storage are forged, there will eventually come one Microsoft is forced to adopt to keep up with the market, and the interoperability problem will be solved. (Well, I hope.)

I don't think there's anything to worry about on the acceptance and adoption front, the developers of FLOSS software just need to continue polishing and building, eventually Linux OSs will be mainstream.

---

### Post by mrgnash on 2009-08-28
Maybe it is, maybe it isn't.... I really don't know, as I haven't used it in a long time. When it comes to reading MSOffice documents, I use catdoc, catppt, or antiword, and they suit me just fine. As for the generation of new documents (especially for academic projects), I have found over the years that _every_ word processor is cumbersome at best, and inadequate at worst. Therefore, I use LaTeX, and would encourage others to do the same. Sure, hand-coding a LaTeX document may not be very newbie-friendly, (although it's really NOT that hard either), but that's where programs like LyX come in. To me, Linux is all about finding better (not necessarily intuitively easier) ways of doing things, and I don't believe that simply promoting it as having parity with Windows features/applications necessarily serves that end.

This seems to come up time and time again in different domains, with people wanting, say, full support for the MSN protocol in a messenger, rather than using XMPP and so on. From my point of view, if you mainly want to do Windows-centric things, then use Windows; Linux is all about (hopefully better) alternatives, unless you're only using it because it enhances your sense of self-righteousness or you're incapable of securing your Windows operating system to a reasonable degree so that you're not constantly falling prey to viruses, malware, and the like.

---

### Post by Aearenda on 2009-08-28
I did say in the original post, not even an edit, > PLEASE don't reply with suggestions for fixing the issues I've described individually - that's not the point here.It still isn't the point. 

> Have any of you seen the show the "the weakest link"?Full marks!

---

### Post by HappinessNow on 2009-08-28
> **Aearenda said:**
> It seems to me that Ubuntu and other Linux distros have now developed to the point that they can easily supplant Windows. There is a great deal of rivalry between distros and projects, and this spurs them all on to ever greater things. 

However, the flagship open source office automation package, OpenOffice, does not seem to be advancing so rapidly, and after using it (running on Ubuntu) for four years of Masters study as well as numerous newsletters, address lists, posters and other items, during which time I have pushed it hard in several areas, it seems to me that it is OpenOffice that will hold back widespread adoption of Linux in ordinary office use from now on.

A case in point: a few months ago my wife's laptop was becoming increasingly unreliable on Windows XP. We could have got it with Vista, but chose not to. I had converted her to Thunderbird and Sunbird some time ago, so that we could easily share calendars. Not wanting to rebuild XP on it yet again, I persuaded her to try Ubuntu, and after some teething issues it ran really well, apart from the microphone quality (which turned out to be a hardware fault, worked around by proprietary software on Windows). 

However, OpenOffice was not the same success story. There were repeated layout problems for other people on opening Word-format documents she had sent them, which is essential for her in her work (and it wasn't just font difference issues). Impress was generally slow and animations a waste of effort. From time to time Writer forgets to update the UI, and it is necessary to press CTRL/R to get it to redraw the screen. Sometimes things disappear from the page, only to reappear next time the document is opened. And so on.

So we tried running her copy of Office 2003 in WINE. That didn't look so good on the screen, but did fine until she needed to add clipart. Fail.

So now she has Windows 7 RC, and a trial copy of Office 2007, and in spite of the ribbon (it got a few curses at first) she is loving it. Of course there are still niggles; but the niggles are in things she does occasionally, not things she uses every day.*

Today I switched our wireless network from WPA to WPA2 (should have done that ages ago). Windows 7 asked for some geeky info, and Ubuntu on my netbook just happily adapted without complaint. My wife's comment to that was, in effect, Ubuntu just did it because that's geeky stuff and Linux devs love to make that kind of thing work nicely, while on Windows it's the everyday office stuff that works nicely. And that's what triggered this post!

So there it is: in my view, OpenOffice needs some love, so that it can be a true rival to Office 2007 and 2010, rather than an Office 2000 look-alike. I can't do it: I'm no developer, and in any case, it's a big job - perhaps the biggest, after the Linux kernel. I know that Sun had a reputation for discouraging participation in OO - maybe now that Sun has been bought by Oracle things will open up. I can't see Oracle letting it die.

If enough of us agree about this, maybe the FOSS powers-that-be will notice and take action. Here's hoping!

(PLEASE don't reply with suggestions for fixing the issues I've described individually - that's not the point here.)


* It's Office 2007 so that we can share calendars - Outlook 2003 couldn't do this, but Outlook 2007 can publish to a private webdav server (and it was easy to add that to Apache on our house server running Hardy). We could have used Thunderbird and Sunbird, but it seemed sensible to try Outlook since Sunbird's future is looking cloudy, and the poor performance of Lightning on my netbook wasn't inspiring. Evolution is just fine as far as speed is concerned, but my wife's calendar is complex, and Evolution doesn't always agree with other programs on how to interpret an iCal file, probably because the iCal definitions are somewhat fuzzy.

Google documents and Google Calendar would be the most viable and reliable solution.

If everybody simply adopted Google Docs/Calendar and dropped development of OOo/Abi etc. we would have fewer problems.

---

### Post by JillSwift on 2009-08-28
> **&#20170 said:**
> Google documents and Google Calendar would be the most viable and reliable solution.

If everybody simply adopted Google Docs/Calendar and dropped development of OOo/Abi etc. we would have fewer problems.
And what do you propose for those who would rather not keep their documents out in the cloud?

Or those without reliable access to the 'net?

---

### Post by lykwydchykyn on 2009-08-28
OpenOffice has its issues, though I think it's a bit sad that the number one issue everyone seems to cite is its inability to perfectly render MSO documents.  I've worked with a few different office suites in my time, and I can tell you that NO office suite has EVER perfectly rendered documents from another suite.  Maybe Corel has sorted out its conversion issues, but I've seen Wordperfect mangle Word documents (and vice versa) in ways that would turn OpenOffice green with envy.

> My wife's comment to that was, in effect, Ubuntu just did it because that's geeky stuff and Linux devs love to make that kind of thing work nicely, while on Windows it's the everyday office stuff that works nicely. And that's what triggered this post!

What's wrong with that statement is that it assumes that the "geeks" are just lazily sitting around not fixing things because they don't feel like it.  If the "geeks" didn't care, you wouldn't be able to open a docx or doc in OpenOffice AT ALL.  WPA2 "just works" because it's a simple, open standard, fairly simply implemented and incorporated into existing frameworks.  

doc is an undocumented file format for a program with 26 years of accumulated proprietary code base behind it.  docx (as produced by office 2007) is a not-quite-to-spec implementation of a 6000 page iso standard based heavily on the internals of that 26 year old code base.  

Implementing these things is not trivial.

That said, I've been hoping for a while that Koffice would really start to shine and provide a good alternative to OpenOffice, hopefully to foster both friendly competition and cooperation between the two projects.  To date, I just don't see koffice taking off.

---

### Post by HappinessNow on 2009-08-28
> **JillSwift said:**
> And what do you propose for those who would rather not keep their documents out in the cloud?

Or those without reliable access to the 'net?Kword :P or other.

---

### Post by JillSwift on 2009-08-28
> **&#20170 said:**
> Kword :P or other.
KOffice has its problems, too.

Well, for that matter so does MS Office.

Honestly, I see this interoperability thing as mostly a non-issue. Though, given the focus it gets, one I suspect the OOo developers are working on.

---

### Post by HappinessNow on 2009-08-28
> **JillSwift said:**
> KOffice has its problems, too.

Well, for that matter so does MS Office.

Honestly, I see this interoperability thing as mostly a non-issue. Though, given the focus it gets, one I suspect the OOo developers are working on.
Then lets hope they solve it soon so we stop hearing about it. :P

---

### Post by MikeTheC on 2009-08-28
@ OP: If you or your wife are active students, Microsoft does have a significant discount for U.S. folks. IIRC from what my [s]Microsoft[/s] er, Microcomputer Skills class' professor told us, go to MS's site and do a search for "ultimate deal". It's like the full-on version of Office 2007 for $50-odd. (Heck, better than paying more than that for just the student version that's lacking various other components.)

No, I don't much care for having to deal with Microsoft products, either, and I understand where you're coming from. the OO folks need to push harder and get more done with stability, UI refinements and features. Period.

---

### Post by madjr on 2009-08-28
get **[virtualbox]("http://seogadget.co.uk/how-to-install-virtualbox/")** (seamless mode is nice)

[IMG]http://farm4.static.flickr.com/3561/3409576683_ae7242ed34.jpg[/IMG]

---

### Post by running_rabbit07 on 2009-08-28
> **MikeTheC said:**
> @ OP: If you or your wife are active students, Microsoft does have a significant discount for U.S. folks. IIRC from what my [s]Microsoft[/s] er, Microcomputer Skills class' professor told us, go to MS's site and do a search for "ultimate deal". It's like the full-on version of Office 2007 for $50-odd. (Heck, better than paying more than that for just the student version that's lacking various other components.)

No, I don't much care for having to deal with Microsoft products, either, and I understand where you're coming from. the OO folks need to push harder and get more done with stability, UI refinements and features. Period.

Or sign up for a CIT related class and utilize the schools MSDNaa account if they have one.

---

### Post by JillSwift on 2009-08-28
> **&#20170 said:**
> Then lets hope they solve it soon so we stop hearing about it. :P
Hehehe +1

---

### Post by Aearenda on 2009-08-28
> **MikeTheC said:**
> @ OP: If you or your wife are active students, Microsoft does have a significant discount for U.S. folks. IIRC from what my [s]Microsoft[/s] er, Microcomputer Skills class' professor told us, go to MS's site and do a search for "ultimate deal". It's like the full-on version of Office 2007 for $50-odd. (Heck, better than paying more than that for just the student version that's lacking various other components.)

We're both part-time students but we don't get Uni email addresses, and that cuts us out of the deal!
EDIT: I asked her, and she has an address after all! So when we reinstall her laptop with Win 7 RTM, it'll be AU$75 for Office 2007 :-)

> No, I don't much care for having to deal with Microsoft products, either, and I understand where you're coming from. the OO folks need to push harder and get more done with stability, UI refinements and features. Period.

Thanks!

---

### Post by MikeTheC on 2009-08-28
> **madjr said:**
> get **[virtualbox]("http://seogadget.co.uk/how-to-install-virtualbox/")** (seamless mode is nice)

[IMG]http://farm4.static.flickr.com/3561/3409576683_ae7242ed34.jpg[/IMG]

Does that Word document say anything in particular?

---

### Post by running_rabbit07 on 2009-08-28
> **MikeTheC said:**
> Have you ever found something in the *second*-to-last place you looked?

Yes, I was at work and pretended to keep looking for something, so i could burn a few minutes off the clock. And so i could tell my boss it wasn't where he said it was.

---

### Post by JillSwift on 2009-08-28
> **MikeTheC said:**
> Does that Word document say anything in particular?

It says:
> Hello world, from Office within Windows XP SP3 virtual with VirtualBox (by Sun) running on Fedora 10 and the PC is a Dell Dimension 9200. Ahhh... and the cube is thanks to Compiz Fusion.

---

### Post by HappinessNow on 2009-08-28
> **JillSwift said:**
> It says:
hehehe,....beat me to it!

---

### Post by JillSwift on 2009-08-28
> **&#20170 said:**
> hehehe,....beat me to it!
Soy muy rápido! ;)

---

### Post by Dr. C on 2009-08-28
> **JillSwift said:**
> And what do you propose for those who would rather not keep their documents out in the cloud?

Or those without reliable access to the 'net?

Many forget that Microsoft was instrumental in liberating computing from the cloud in the 1980's and early 1990's, in those days it was called the mainframe with the result of a significant increase in freedom for many computer users. 

To preserve the users freedom here are some options from most free to least free

1) Free Software, Free OS and Free Formats on a system you own. For example OpenOffice.org and .odf on Ubuntu.
2) Free Software, Non Free OS and Free Formats on a system you own: For example OpenOffice.org and .odf on Windows XP / Vista / 7
3) Free Software, Free OS and effectively Free Formats on a system you own For example OpenOffice.org and .doc on Ubuntu
4) Non Free Software, Non Free OS and effectively Free Formats on a system you own. For example Microsoft Office, and .doc on Windows XP / Vista / 7
5) Non Free Software, Non Free OS and Non Free Formats on a system you own. For example Microsoft Works, and .wks on Windows XP / Vista / 7
6) The cloud and the mainframe unless you own the servers where your documents are stored. 

The .doc format has been reversed engineered by so many of Microsoft's competitors for both free and propriety applications that it has become a effectively free standard at least for simple documents.

---

### Post by Giant Speck on 2009-08-28
Let's ask Anne Robinson.  Anne?

[img]http://daverattigan.typepad.com/the_grace_pages/images/anne_robinson_weakest_link.jpg[/img]

---

### Post by inobe on 2009-08-28
well it seems that microsoft was caught stealing again

[http://www.neowin.net/news/main/09/08/12/judge-orders-microsoft-to-stop-selling-word](http://www.neowin.net/news/main/09/08/12/judge-orders-microsoft-to-stop-selling-word)

---

### Post by dmizer on 2009-08-28
MS Word certainly isn't the only other office suite other than OOo, especially if you're willing to pay for one anyway. Why not investigate something like: [http://www.sun.com/software/staroffice/index.jsp](http://www.sun.com/software/staroffice/index.jsp)

Which in my opinion is much more pollished and functional than OOo or Word.

---

### Post by Aearenda on 2009-08-28
See the bigger picture, folks! What I was trying to say in the original post is that OpenOffice needs developer love, not work-arounds or switching away from, because it's starting to look like the poor cousin compared to Ubuntu itself (and several other polished distros), and that this will hold back Ubuntu adoption in places where Ubuntu would otherwise be a good fit.

---

### Post by keiichidono on 2009-08-28
I'm interested now. I'll hack up a good ui for ooo eventually.

---

### Post by mrgnash on 2009-08-28
> **Aearenda said:**
> See the bigger picture, folks! What I was trying to say in the original post is that OpenOffice needs developer love, not work-arounds or switching away from, because it's starting to look like the poor cousin compared to Ubuntu itself (and several other polished distros), and that this will hold back Ubuntu adoption in places where Ubuntu would otherwise be a good fit.

No, switching-away-from *is* the best option, because the whole "word processor" model is severely (and, I believe, irredeemably) flawed. Let us champion better ways of doing things, rather than trying to play catch up with the Windows/Mac world.

---

### Post by HappinessNow on 2009-08-28
> **mrgnash said:**
> no, switching-away-from *is* the best option, because the whole "word processor" model is severely (and, i believe, irredeemably) flawed. Let us champion better ways of doing things, rather than trying to play catch up with the windows/mac world.
+1

---

### Post by dmizer on 2009-08-28
> **Aearenda said:**
> See the bigger picture, folks! What I was trying to say in the original post is that OpenOffice needs developer love, not work-arounds or switching away from, because it's starting to look like the poor cousin compared to Ubuntu itself (and several other polished distros), and that this will hold back Ubuntu adoption in places where Ubuntu would otherwise be a good fit.

But you said that you were already implementing an alternative. Win7 and MS Word.
> **Aearenda said:**
> So now she has Windows 7 RC, and a trial copy of Office 2007, and in spite of the ribbon (it got a few curses at first) she is loving it.
So since you're already obviously ready to switch away from, then why not consider ALL options rather than defaulting to MS solutions? All the OOo developers in the world aren't going "fix" things overnight to the point where your wife will suddenly be pleased with it.

I know you're not really looking for solutions here, you're trying to motivate movement on a project, but I just found it odd that you indicated that your wife was pleased with everything except OOo, and that caused you to convert everything back to Microsoft, as though OOo was the only available solution for Linux.

---

### Post by Johnsie on 2009-08-28
OO is a good replacement for Excel and possibly Word... but until it has a decent exchange capable Email/PIM application it will be quite useless in an office situation.

The most used Office application in working offices is Outlook and until there is an equivalent to that which works with existing servers OO will fail to impress businesses.

Also, there is no access equivalent in OO

---

### Post by mrgnash on 2009-08-28
> **Johnsie said:**
> OO is a good replacement for Excel and possibly Word... but until it has a decent exchange capable Email/PIM application it will be quite useless in an office situation.

The most used Office application in working offices is Outlook and until there is an equivalent to that which works with existing servers OO will fail to impress businesses.

Also, there is no access equivalent in OO

OOo may not have a built-in email application, but then again, why should it? There is already Thunderbird, Claws, Mutt, Evolution, etc. 

Secondly, OOBase is an Access equivalent.

---

### Post by wersdaluv on 2009-08-28
I kinda gave up on OpenOffice. I never did my thesis there for formatting reasons. I always resorted to MS Office 2007 on Virtualbox.

---

### Post by NCLI on 2009-08-28
> **JillSwift said:**
> And what do you propose for those who would rather not keep their documents out in the cloud?

Or those without reliable access to the 'net?
Install Google Gears? :)

---

### Post by madjr on 2009-08-28
> **wersdaluv said:**
> I kinda gave up on OpenOffice. I never did my thesis there for formatting reasons. I always resorted to MS Office 2007 on Virtualbox.

if you are planning to export to .**doc** than i see why you gave up

but if you exported to **pdf** then not much of a need.

---

### Post by dmizer on 2009-08-28
> **madjr said:**
> if you are planning to export to .**doc** than i see why you gave up

but if you exported to **pdf** then not much of a need.

It's also not much of a problem if you use compatible fonts.

---

### Post by Johnsie on 2009-08-28
The reason why OO should have an email client is that the Outlook mail is one of the main tools used by people who work in an office. Evolution does not run too well on Windows and Thunderbird doesn't integrate with the Exchange server too well. Outlook is by far the best in it's genre and most office workers expect it or something that has the same features.

---

### Post by samjh on 2009-08-28
> **Aearenda said:**
> It seems to me that Ubuntu and other Linux distros have now developed to the point that they can easily supplant Windows. There is a great deal of rivalry between distros and projects, and this spurs them all on to ever greater things. 

However, the flagship open source office automation package, OpenOffice, does not seem to be advancing so rapidly, and after using it (running on Ubuntu) for four years of Masters study as well as numerous newsletters, address lists, posters and other items, during which time I have pushed it hard in several areas, it seems to me that it is OpenOffice that will hold back widespread adoption of Linux in ordinary office use from now on.

That's a brave assertion.  There are other aspects of Linux that are lacking in comparison to Windows too.  Wireless adapter support, is one sore point which is often complained about.  Yes, yes, I'm aware that it is a vendor problem rather than a FOSS/Linux problem, but to a potential new Linux user, the difference matters not.

About OpenOffice:

Just remember that OpenOffice is up against the most powerful, versatile, and widespread office suite ever in existence.  MS Office is no mean beast.  It probably has a tighter grip on the IT consumer market than even Windows.

Linux was first adopted into mainstream IT via enterprise servers (pedantically, it was academia, but a bunch of lab rats using Linux off a basement server hardly counts as "mainstream").  This had the trickle effect of improving back-end interoperability with MS Windows-based systems, then eventually added capability for the desktop end-users as well.  To put it simply, corporate IT accelerated both technical development and adoption of Linux like a snowball gathering in size and speed as it rolls down a snowy mountain slope.  Since Linux saw life in mainstream IT under the watchful eyes of IT professionals (many of them already familiar with Unix and Solaris), adoption of Linux is nowhere near as tricky as persuading often computer-illiterate end-users or impatient corporate executives to adopt a new office suite.

Unlike when Linux encroached into mainstream IT in the business sector, OpenOffice is having to win the battle against end-users who have used MS Office for many years and do not wish to deviate.  In my experience training business end-users, I can say definitely that technical prowess is no substitute for familiarity and compatibility when it comes to the non-tech Joe Blow user.  Basically what I'm saying is: it was an easier task to convince IT techies to try Linux than it is to convince business end-users to try OpenOffice.

What about home users?  Most brand-name computers come bundled with MS Windows and Office pre-installed.  Why change?  Some of us techies might spout reasons like "bloat", and "open document format".  That stuff doesn't matter at all to the average Joe Blow.  Why would a mother of three care about open-source or system resource efficiency when all she wants to do is type up a letter or do spreadsheeting for the household budget?  What does a high school kid care about "free" when he is busy trying to type up his next assignment (which may need to be submitted in Word .doc format)?  They don't care.  They don't want -- nor do they need -- to change.

I don't think OpenOffice is the weakest link in terms of technical development pace.  It's development has been very good.  I've been struggling with it for the past three years, with university papers, legal documents, and other shenanigans.  As version numbers have increased, compatibility, efficiency, and features, have increased noticeably to the extent that I now rarely use MS Office (just two years ago, I was forced to do all my word processing and spreadsheeting in MS Office because OO.org wasn't good enough).

What OpenOffice needs is something that it can't control: more adoption in the corporate market.  But as long as non-tech managers, secretaries, and admin staff feel no need to switch, they won't switch.  They have neither the time or need for it.  And that will continue to impede OpenOffice development.  With Linux, techies were in good position to persuade the right people (corporate management).  With OpenOffice, techies are not in a good position to persuade the right people because the hassle of adopting OpenOffice will affect them directly everyday, rather than via layers of IT support personnel.

If you're looking for faster development for OpenOffice, I'll suggest looking at Go-OO: [http://www.go-oo.org/](http://www.go-oo.org/)
It's a Novell spin-off of OpenOffice, with less politics and faster feature integration.  Check it out.

---

### Post by Johnsie on 2009-08-28
The reason I wont migrate users to Linux where I work is mainly due to hardware support and some applications we need to use are only available for Windows. There is no UK certified MailSort software for Linux and I work in a mailing house. Linux also doesn't support Toshiba-Tec B-SX4 printers which are used by most mailing houses in the UK to print bag and tray labels.

I'd be happy enough to use open office and evolution on Linux, but on Windows there is no open source software that is as good as Outlook. Evolution for Windows doens't run to well and Evolution isn't as good as Outlook anyway.

---

### Post by Aearenda on 2009-08-28
Samjh, thanks for your reply. I'm glad you responded to the intent of the thread, and I do agree about the size of the competition and that OO has moved on well over the last few years - but just not as quickly as Ubuntu, it seems to me. I think I read somewhere that the OO in Ubuntu is derived from the Go-OO version, but I'll certainly take a look at that.

---

### Post by mrgnash on 2009-08-28
> **Johnsie said:**
> The reason why OO should have an email client is that the Outlook mail is one of the main tools used by people who work in an office. Evolution does not run too well on Windows and Thunderbird doesn't integrate with the Exchange server too well. Outlook is by far the best in it's genre and most office workers expect it or something that has the same features.

Well, if you're going to use the Exchange server then of course you should use Microsoft products with it... that's a no-brainer. But it's unreasonable to expect OOo or anything else to work with it, even if it DID have an email client included.

Also, Outlook is not best in class in my opinion. It's bloated and clunky, and I much prefer Mutt.

---

### Post by Aearenda on 2009-08-28
> **dmizer said:**
> 
I know you're not really looking for solutions here, you're trying to motivate movement on a project, but I just found it odd that you indicated that your wife was pleased with everything except OOo, and that caused you to convert everything back to Microsoft, as though OOo was the only available solution for Linux.
Ah well, it was the only solution that I had enough confidence in myself (and I have tried koffice in the past, though I confess not recently), and there is only a limited amount of wifely computer patience available :-)

---

### Post by Johnsie on 2009-08-28
Haha mutt, very funny. Exchange is by far the best email/user directory server available for companies. Thats why why most large companies use Outlook as their main email client and not the likes of thuderbird etc.

---

### Post by winjeel on 2009-08-28
I agree with you. I've run into too many problems with OOffice Writer. Little problems, but just annoying with it becomes time consuming. I've used it for a few months, and have now effectively dumped it. I'm back to using MS Word 2000 through Wine, and so far, not a single problem. Word is an older program with a longer development time, longer history and pedigree, and perhaps designed with great customer feedback and research (though that doesn't explain the catastrophe that Office XP is). It is a far superior product, so far. I dare say that it will be surpassed. Nothing is number 1 forever; there will always be an underdog that'll take the lead. At the moment I use both Ubuntu and XP, as both have capabilities that the other hasn't. But for now, I'm content not using OO Writer, but hope it will improve. (I've had no problems with the spread sheet component). Oh, and OO doesn't have forums like these, so I think communication amongst them is perhaps not as fluent.

---

### Post by mrgnash on 2009-08-28
> **Johnsie said:**
> Haha mutt, very funny. Exchange is by far the best email/user directory server available for companies. Thats why why most large companies use Outlook as their main email client and not the likes of thuderbird etc.

I wasn't joking. But if you wish to contend that the popularity of a product is synonymous with, or equivalent to, its popularity then logically you must also conclude that Windows is superior to Linux.

---

### Post by mikewhatever on 2009-08-28
Hi Aearenda,

can you clarify a few things about your original post. What format did your wife use exactly, was it .doc?  What format did she use with Impress? Was it the native OO format? My memories of MS Office are unreliable, can you tell if they use an open format or a closed source MS only one?

I don't want to jump to conclusions, apologize if I got it wrong, but it seems like your opinion about Open Office has originated in the idea that it should be a free version of MS office, seamlessly supporting all its features. That will probably never happen, at least as long as MS keeps it closed.

---

### Post by MarcusW on 2009-08-28
Am I the only one who used OpenOffice even before I installed Ubuntu. I'm not gonna pay for/pirate something when the option is free and great. :) I suppose my needs aren't that hard to meet though, just some spreadsheets and a couple of essays for school.

---

### Post by bryncoles on 2009-08-28
> **mrgnash said:**
> No, switching-away-from *is* the best option, because the whole "word processor" model is severely (and, I believe, irredeemably) flawed. Let us champion better ways of doing things, rather than trying to play catch up with the Windows/Mac world.

spot on (as was your first post, where you mentioned LaTeX!). I find OOo meets all my needs simply enough, but i wish to (eventually) migrate to LaTeX, as it is a Better Way of Doing Things - though not initially an easier way. 

It would be nice if OOo stepped up to the plate, and became capable of flawlessly implementing / opening / handling MSO documents, but the simple fact there is its not OOo's fault, as they have had to *reverse engineer* the .doc and .docx formats, as while they are *effective standards*, they are not actual open standards. the best we can do is save as .odt's now that office 2007 has (broken) support for this format. then, our documents still wont work properly, but it'll be Microsofts fualt for implementing the standard ineffectively, rather than OOo's. and it'll be a problem that microsoft can fix, given that .odt is an actual open standard. 

alas, getting the world to move to properly open standards will be like swimming upstream for a goodly while yet...

---

### Post by bryncoles on 2009-08-28
> **MarcusW said:**
> Am I the only one who used OpenOffice even before I installed Ubuntu. I'm not gonna pay for/pirate something when the option is free and great. :) I suppose my needs aren't that hard to meet though, just some spreadsheets and a couple of essays for school.

no, you're not the only one. in fact, OOo and Firefox were my gateway drugs!

---

### Post by running_rabbit07 on 2009-08-28
> **Johnsie said:**
> Haha mutt, very funny. Exchange is by far the best email/user directory server available for companies. Thats why why most large companies use Outlook as their main email client and not the likes of thuderbird etc.

I thought they used Outlook because it comes bundled in with most Windows systems. I tried using Outlook several times with the email addresses that my ISP gave me and it never wanted to work well. Before dropping my MS partition in the waste basket I installed Thunderbird and it worked like a charm. Not as fast as it works on Linux, but nothing on MS was"fast."

We can write threads complaining about OpenOffice all we want. Fact is, they aren't going to see it. Be proactive and go to their website and get in touch with them.

> **MarcusW said:**
> Am I the only one who used OpenOffice even before I installed Ubuntu. I'm not gonna pay for/pirate something when the option is free and great. :) I suppose my needs aren't that hard to meet though, just some spreadsheets and a couple of essays for school.

Nope, you are not. I used it for a year or two now and think it works fine. I found it after going to Office Depot and seeing they had the top line MS office suite for $619.99. Of course I can get the same thing much cheaper, but why pay just to be able to do my homework?

---

### Post by Tibuda on 2009-08-28
> **running_rabbit07 said:**
> I thought they used Outlook because it comes bundled in with most Windows systems.

Outlook Express is bundled with Windows. Outlook is bundled with MS Office.

---

### Post by newbie2 on 2009-08-28
here are some international languages OOo forums for help :

[http://user.services.openoffice.org/](http://user.services.openoffice.org/)

:)

---

### Post by lykwydchykyn on 2009-08-28
> **Aearenda said:**
> See the bigger picture, folks! What I was trying to say in the original post is that OpenOffice needs developer love, not work-arounds or switching away from, because it's starting to look like the poor cousin compared to Ubuntu itself (and several other polished distros), and that this will hold back Ubuntu adoption in places where Ubuntu would otherwise be a good fit.

See I don't get this kind of post.  There are people developing OpenOffice.  Apart from community contributors, Sun, IBM, Novell, and others have full time paid programmers working on it.  It's not like someone just dropped this heap of code out there and said "good enough" and then moved on to work on Compiz.

I guess I understand the frustration with wanting to see free software do well and make progress, but Rome wasn't built in a day.  What we can do as users is submit bugs and provide feedback to the developers.  And then, be patient.

---

### Post by Jesus_Valdez on 2009-08-28
I used Writer to, well, write, my Masters degree thesis and it was really a nightmare until I gave up and decide to change to Word, wich cost me lots of time.

I don't know you guys, but around here the "real-world-people" needs a *.doc format file in order to edit and make changes easily.

Sometimes they (my thesis comitee) even reject me the PDF version for the same reason, the easiest way they know for reviewing a document its on word and they don't care if OO can't (for whatever reason, mostly MS fault) export and import complicated MSO documents.

Writer its great for easy stuff, "normal" homework, but I always keep virtualbox and Office at hand.

Now, I don't think that the "standard/regular" user needs other thing besides OOo, it is true that needs "love", its plain ugly, looks like Oficce 97 and its "far" from the "industrial-standard" but its a great suite.


EDIT:  Man I love the """ thing.

---

### Post by azangru on 2009-08-28
> **Aearenda said:**
> What I was trying to say in the original post is that OpenOffice needs developer love, not work-arounds or switching away from, because it's starting to look like the poor cousin compared to Ubuntu itsel

But so do most of the alternatives to commercial software, most noticeably to MS Office and Adobe Creative Suites :( Everything you said about OOo can be applied to The Gimp, Scribus, video editing software, and so on. In their polish, they miserably lag behind the distros themselves :(

---

### Post by Chronon on 2009-08-28
> **Jesus_Valdez said:**
> I used Writer to, well, write, my Masters degree thesis and it was really a nightmare until I gave up and decide to change to Word, wich cost me lots of time.

I don't know you guys, but around here the "real-world-people" needs a *.doc format file in order to edit and make changes easily.

Sometimes they (my thesis comitee) even reject me the PDF version for the same reason, the easiest way they know for reviewing a document its on word and they don't care if OO can't (for whatever reason, mostly MS fault) export and import complicated MSO documents.

Writer its great for easy stuff, "normal" homework, but I always keep virtualbox and Office at hand.

Now, I don't think that the "standard/regular" user needs other thing besides OOo, it is true that needs "love", its plain ugly, looks like Oficce 97 and its "far" from the "industrial-standard" but its a great suite.

For any simple documents, I think OO Writer suffices.  I really prefer LaTeX for anything more than dashing off a page of text, though.

EDIT:  Man I love the """ thing.

Well you let your committee bully you and that's unfortunate.  I give PDF versions of chapters to my committee along with the LaTeX source.  I refuse to work any other way.  It's easy enough for them to compile it and if they make edits I can simply make a .diff of the changes.  Word processors, in general, produce very low quality typesetting for any writing that contains symbols of varying heights (such as in math).

More to the point of this thread, I can't think of situations where I would avoid Writer to use Word.

---

### Post by Aearenda on 2009-08-28
> **azangru said:**
> But so do most of the alternatives to commercial software, most noticeably to MS Office and Adobe Creative Suites :( Everything you said about OOo can be applied to The Gimp, Scribus, video editing software, and so on. In their polish, they miserably lag behind the distros themselves :(

I agree, but office automation is the bread and butter of many people's day, and that's what niggles people the most. That said, thanks for responding to the intent of this thread!

To other posters, many of you have valid points, thank you. As I have said before, I didn't start the thread to look for technical solutions, but rather to promote the idea that OpenOffice needs love, so that its overall quality can match that of Ubuntu.

---

### Post by Aearenda on 2009-08-28
> **lykwydchykyn said:**
> ... There are people developing OpenOffice.  Apart from community contributors, Sun, IBM, Novell, and others have full time paid programmers working on it.  It's not like someone just dropped this heap of code out there and said "good enough" and then moved on to work on Compiz.

I guess I understand the frustration with wanting to see free software do well and make progress, but Rome wasn't built in a day.  What we can do as users is submit bugs and provide feedback to the developers.  And then, be patient.

I know - but I want MORE working on it, so that its quality improves compared to Ubuntu's.

---

### Post by Ric_NYC on 2009-08-28
I think it is possible OO is the weakest link.
In my opinion the way software is installed on Linux is the weakest link.
How many threads asking "how do I install this or that"?

It would be more productive if we had more threads asking "how do I use this software that I installed"...

Don't you agree?

---

### Post by Mateo on 2009-08-28
> **crush304 said:**
> edit in whatever program you choose and then export as pdf to send to someone else. doc format whether created by microsoft word or open office writer is a horrible format for sending documents to someone else

You often don't have a choice.  You have to send to what the receiver wants/expects.

---

### Post by Aearenda on 2009-08-28
> **mikewhatever said:**
> Hi Aearenda,

can you clarify a few things about your original post. What format did your wife use exactly, was it .doc?  What format did she use with Impress? Was it the native OO format? My memories of MS Office are unreliable, can you tell if they use an open format or a closed source MS only one?

I don't want to jump to conclusions, apologize if I got it wrong, but it seems like your opinion about Open Office has originated in the idea that it should be a free version of MS office, seamlessly supporting all its features. That will probably never happen, at least as long as MS keeps it closed.

I know I gave document layout as my first example, but it wasn't meant to imply importance, and I wish I hadn't mentioned that bit. A much bigger issue to me is usability - e.g., making it obvious how to change one page to landscape layout in a primarily portrait document (you have to create a page style - it is actually a much better solution technically, but really hard to discover) and reliability - e.g. the times when Writer doesn't refresh the screen, the regression in 3.1 where copying and pasting a whole slide in Impress corrupts its layout where it is pasted (3.0 works fine).

I don't think OO should be a MS Office clone personally, but that's what a lot of first-time users will expect to see, especially if they have used Windows/Office before. Which is partly why Microsoft makes Office so cheap for students! 

I just want OpenOffice to match Ubuntu in quality, and this needs wider attention :-)

---

### Post by Mateo on 2009-08-28
OO is definitely the weakest length... it has barely changed since I started using linux in 2003!  but the same can be said for a lot of software, Evolution comes to mind.

---

### Post by Aearenda on 2009-08-28
> **Ric_NYC said:**
> I think it is possible OO is the weakest link.
In my opinion the way software is installed on Linux is the weakest link.
How many threads asking "how do I install this or that"?

It would be more productive if we had more threads asking "how do I use this software that I installed"...

Don't you agree?

Well no, actually, I don't! I love having everything available in one place (Synaptic, in my case) and installable without worrying about unwanted toolbars being added on, or worse, and *properly uninstallable* without leaving stuff behind.

But this functionality is being worked on in karmic, I gather. So is OpenOffice. I just want OpenOffice's quality to increase :-)

---

### Post by JDorfler on 2009-08-28
Am I the only one who doesn't have a problem OOo and find easier and better to use than MSFT Word?  With the right plug ins everything is perfect.

---

### Post by Mateo on 2009-08-28
> **mrgnash said:**
> This seems to come up time and time again in different domains, with people wanting, say, full support for the MSN protocol in a messenger, rather than using XMPP and so on. From my point of view, if you mainly want to do Windows-centric things, then use Windows; Linux is all about (hopefully better) alternatives, unless you're only using it because it enhances your sense of self-righteousness or you're incapable of securing your Windows operating system to a reasonable degree so that you're not constantly falling prey to viruses, malware, and the like.

I think people want to use Windows-centric applications because many of their contacts (friends, family, business associates) use Windows.  I believe that "isolation" is not a good strategy for the Linux community to take.  I think "big tent" is the best approach.

---

### Post by BuffaloX on 2009-08-28
> **Aearenda said:**
> There were repeated layout problems for other people on opening **Word-format documents** she had sent them, which is essential for her in her work (and it wasn't just font difference issues). Impress was generally slow and animations a waste of effort. From time to time Writer forgets to update the UI, and it is necessary to press CTRL/R to get it to redraw the screen. Sometimes things disappear from the page, only to reappear next time the document is opened. And so on.


Which is probably part of the reason why it is now **ILLEGAL** in Denmark, for a public office to send **Word-format documents** to citizens.

If Word-format documents really are essential, you probably need MS-Word, that's a major part of the whole idea behind MS-Word format right from the beginning. It's designed to be hard to comply with to prevent competition, which is the exact reason you should never use it.

Maybe things will improve faster now, SUN was much criticized for not accepting and including improvements to Open Office made by 3rd parties. 

Personally I use neither, I use Scribus and Inkscape.

---

### Post by madjr on 2009-08-28
and **OOo** will stay the weakest link thanks to **HP and Dell**..


[Dell and HP rush to Microsoft's defence in Word legal battle]("http://www.theinquirer.net/inquirer/news/1531734/dell-hp-rush-microsoft-defence")


**DEll's ideastorm**:

[Pre-Installed OpenOffice | alternative to MS Works & MS Office]("http://www.ideastorm.com/ideaView?id=0877000000006pjAAA") (**115,680** votes)

**Dell status update**: *As this is available for **free** today, we do not currently plan on offering this as an option to factory install*.


**wtf**..



> **BuffaloX said:**
> Which is probably part of the reason why it is now **ILLEGAL** in Denmark, for a public office to send **Word-format documents** to citizens.

If Word-format documents really are essential, you probably need MS-Word, that's a major part of the whole idea behind MS-Word format right from the beginning. It's designed to be hard to comply with to prevent competition, which is the exact reason you should never use it.


+1

---

### Post by cprofitt on 2009-08-28
> **MikeTheC said:**
> @ OP: If you or your wife are active students, Microsoft does have a significant discount for U.S. folks. IIRC from what my [s]Microsoft[/s] er, Microcomputer Skills class' professor told us, go to MS's site and do a search for "ultimate deal". It's like the full-on version of Office 2007 for $50-odd. (Heck, better than paying more than that for just the student version that's lacking various other components.)

No, I don't much care for having to deal with Microsoft products, either, and I understand where you're coming from. the OO folks need to push harder and get more done with stability, UI refinements and features. Period.


Its actually the ultimate steal -- [http://www.microsoft.com/student/discounts/theultimatesteal-us/default.aspx](http://www.microsoft.com/student/discounts/theultimatesteal-us/default.aspx)

---

### Post by cprofitt on 2009-08-28
> **Johnsie said:**
> OO is a good replacement for Excel and possibly Word... but until it has a decent exchange capable Email/PIM application it will be quite useless in an office situation.

The most used Office application in working offices is Outlook and until there is an equivalent to that which works with existing servers OO will fail to impress businesses.

Also, there is no access equivalent in OO

This, of course, assumes that people want to use Microsoft Exchange as their email server.

---

### Post by cprofitt on 2009-08-28
Personally one of the issues to me is that schools continue to push MS Office. I can not, for the live of me, figure out why a public K-12 school system would want to perpetuate inequity in schools by using an expensive office suite instead of one they could give kids to use at home for free. Some of of, those who pay school taxes, should potentially ask that question at the next budget meeting.

I fully appreciate the fact that the transition would be a bit painful, but the end result would likely be positive. If need be keep the administrators and support staff on MS Office, but for teaching kids how to write business letters and having them create school papers I would think Open Office would work fine.

---

### Post by Brian Vaughan on 2009-08-28
I found the title of this thread arresting, as one of the many reasons I'd switched to GNU/Linux was that even when I was using Windows XP, most of the applications I depended upon for practical work were FLOSS, and the FLOSS applications were usually better than the applications I'd actually paid for. In part, that was because I couldn't afford most commercial software, and I was determined to avoid pirated software.

To be honest, I always found OpenOffice.org to be somewhat more clumsy than Microsoft Office. But it was good enough, and it was free (as in beer).

While improving the quality of OpenOffice.org is important, of course, I don't think that's the reason that FLOSS isn't more widely used. The real problem is Microsoft's deliberate policy of lock-in. Microsoft Word is, after all, not open source, and its file formats are not openly documented, which means FLOSS developers have to reverse engineer the formatting. Microsoft unilaterally changes its file formats every year or two, making new files unreadable by old software.

Microsoft has hundreds of billions of dollars at stake in maintaining its near-complete monopoly of office application software. Microsoft is not interested in playing fair and making it easy for other software applications to produce files with full compatibility. Wars have been fought, and atrocities committed, over smaller amounts of wealth.

As I understood, HTML is a document-type definition within SGML, which was developed as a universal document format, specifically because of the problem of government documents being produced in proprietary software with undisclosed document formats. As proprietary software disappeared, due to obsolescence or business failure, those documents became unreadable.

Pause here for a moment and consider how many historically valuable documents may be unreadable due to proprietary file formats.

Anyway, the point is that it's not OpenOffice.org's fault that when Writer exports in .doc format, it's not certain that it will be displayed properly in Microsoft Word. It's not OpenOffice.org's incompetence, it's Microsoft's malice.

It is very short-sighted of many institutions to insist on Microsoft format only, given that it costs nothing but a small amount of labor time to install OpenOffice.org, if only to display documents. Managers are often short-sighted, however.

By the way, I'm inclined to think, in terms of actual document production, that mrgnash is right. Word processors are excessively complex, and it's exceedingly rare for users to properly structure a document, using styles in a logical and consistent fashion. (Come to think of it, one of my problems with OpenOffice.org Writer is that it's difficult to make use of styles.) More fundamentally, word processors blur writing and revising, editing, and formatting, which are distinct steps in the process of creating a document. That is, it's quite hard to resist the urge to apply boldface and other font effects to a section heading, even though properly that should be done by designating it as a "section heading," and formatting should only be applied when the document nears completion.

---

### Post by Brian Vaughan on 2009-08-28
> **cprofitt said:**
> Personally one of the issues to me is that schools continue to push MS Office. I can not, for the live of me, figure out why a public K-12 school system would want to perpetuate inequity in schools by using an expensive office suite instead of one they could give kids to use at home for free. Some of of, those who pay school taxes, should potentially ask that question at the next budget meeting.

I fully appreciate the fact that the transition would be a bit painful, but the end result would likely be positive. If need be keep the administrators and support staff on MS Office, but for teaching kids how to write business letters and having them create school papers I would think Open Office would work fine.

One thing that saddens me is that in nearly every nonprofit social service organization I see, every computer is running Windows and Microsoft Office. These are organizations that run on shoe-string budgets, and would benefit enormously from free operating systems and free application software. Moreover, many people in FLOSS see what they're doing as a service for the public good, just as non-profit social service workers do. There's a natural alliance to be made here.

I think Canonical, and similar organizations, would do well to find ways to work with non-profits (assuming they're not already).

---

### Post by madjr on 2009-08-28
> **Brian Vaughan said:**
> One thing that saddens me is that in nearly every nonprofit social service organization I see, every computer is running Windows and Microsoft Office. These are organizations that run on shoe-string budgets, and would benefit enormously from free operating systems and free application software. Moreover, many people in FLOSS see what they're doing as a service for the public good, just as non-profit social service workers do. There's a natural alliance to be made here.

I think Canonical, and similar organizations, would do well to find ways to work with non-profits (assuming they're not already).

this is mostly the vendor's (**HP, DELL**, etc.) fault like i [cited]("http://ubuntuforums.org/showpost.php?p=7863704&postcount=71") above

you buy the machines, but they pre-load most of that software (specially student discounted computers **pre-loaded with windows-office** combo, no extra charge)

it's exactly the same as when you see windows computers being sold cheaper than most of the ubuntu/linux ones

---

### Post by phrostbyte on 2009-08-29
I agree that OOo is not as featureful as MS Office. But I think it's "good enough" that many people and even businesses aren't going to drop $400 for MS Office. Hence why suddenly you see Microsoft offering Office at 80% discount to some demographics. This is new, and I think it shows OOo is having some influence.

Personally I think the fundamental approach both MS Office and OOo take to the Office productivity deal is flawed. Both were architecture when the global persuasive Internet was just a glimmer in Al Gore's eye. I think Google has the right idea going with Docs, but I get this impression that they don't take it seriously. I haven't noticed any major changes in Docs for a long time.

---

### Post by mrgnash on 2009-08-29
> **Mateo said:**
> I think people want to use Windows-centric applications because many of their contacts (friends, family, business associates) use Windows.  I believe that "isolation" is not a good strategy for the Linux community to take.  I think "big tent" is the best approach.

What you would call "isolation", I call "specialization." Of course its not for me to say where developers for Linux should focus their efforts, but I do think they would be most profitably spent catering to the "workstation" market, rather than trying to appease desktop users who want to do all the same stuff they did under Windows, and who probably should have remained with that platform. I could be completely wrong, but I fail to see how becoming a second-rate Windows is going to be of any benefit, given that such efforts will be disregarded by people like me, and will never completely satisfy those who want 1:1 parity with Windows software/formats.

---

### Post by madjr on 2009-08-29
> **mrgnash said:**
> What you would call "isolation", I call "specialization." Of course its not for me to say where developers for Linux should focus their efforts, but I do think they would be most profitably spent catering to the "workstation" market, rather than trying to appease desktop users who want to do all the same stuff they did under Windows, and who probably should have remained with that platform. I could be completely wrong, but I fail to see how becoming a second-rate Windows is going to be of any benefit, given that such efforts will be disregarded by people like me, and will never completely satisfy those who want 1:1 parity with Windows software/formats.

you forgot the people in the middle (a BIG bunch)

it works for me just as it is (could get better or easier? bring it).

the mac people do have office but lack many other programs and that's why lots use parallels, virtualbox, etc.

when people **choose** something, they also choose to live with it's pros/cons (kinda like when you get married)

**mindshare** is key

---

### Post by BCPlanner on 2009-08-30
> **crush304 said:**
> edit in whatever program you choose and then export as pdf to send to someone else. doc format whether created by microsoft word or open office writer is a horrible format for sending documents to someone else

That only works if the person receiving the PDF either (a) does not need to edit/format/import the document or (b) if the person receiving the PDF file has a PDF editor (e.g., Adobe Acrobat).

BCPlanner at gmail dot com

---

### Post by Brian Vaughan on 2009-08-30
> **mrgnash said:**
> What you would call "isolation", I call "specialization." Of course its not for me to say where developers for Linux should focus their efforts, but I do think they would be most profitably spent catering to the "workstation" market, rather than trying to appease desktop users who want to do all the same stuff they did under Windows, and who probably should have remained with that platform. I could be completely wrong, but I fail to see how becoming a second-rate Windows is going to be of any benefit, given that such efforts will be disregarded by people like me, and will never completely satisfy those who want 1:1 parity with Windows software/formats.
There are those who feel that GNU/Linux developers are spending too much time on workstations and supercomputing, and not enough on personal computing:
[Supported Features]("http://xkcd.com/619/")

Of course, there are lots of GNU/Linux developers, on lots of different projects. This is not a problem of dividing up a finite pie -- and one of the benefits of increased FLOSS influence in personal computing is that it will increase the pool of software developers.

And this discussion is happening on the forums for Ubuntu, the flagship of GNU/Linux distributions designed for personal computing. It's not that Ubuntu's not good for server applications -- Wikimedia seems happy with Ubuntu servers -- but user-friendliness is what Ubuntu's known for. I'd think that involvement with Ubuntu implies a support for developing a personal computing operating system, one that's not just a second-rate Windows, but better than Windows.

In many respects, I think Ubuntu is significantly better than Windows now, even for those who are not technically adept. Ubuntu's default installation has all the software most people need, ready for use. The Add/Remove Applications applet is a far easier way to find and install applications than the process one has to follow for installing applications for Windows -- provided one doesn't try to install applications the way it's done in Windows.

But I think it's most important to value the ethical principles of free software. There's a real social question at issue here: whether technology is to be controlled by people, or people by technology. If there's one change I'd make to Ubuntu's default setup, come to think of it, it would be to place an icon for Gnome Terminal alongside the icons for Firefox and Evolution, so that it's front and center. I do not like the way Windows and OS X try to pretend that the GUI is the entire OS.

---

### Post by NormanFLinux on 2009-08-30
Open Office already offers a database program similar to Access. Next year, a notetaking application similiar to Microsoft OneNote is being planned for the next Open Office release. Its already a mature office suite. The main difficulty is Microsoft has used proprietary format for handling Office files. A uniform file standard would remove the problem of reading documents.

---

### Post by madjr on 2009-08-30
i wished you could export to **ODF.exe** (or similar executable. note: not a virus as some may discuss, but instead **viral marketing**)

which would prompt you to download a small **Odf reader**, Writter or the full OOo to view the document in case you don't have it installed

i usually tell my friends to download OOo but at 100mb+, most of the time they prefer to open it with ms office since it's already installed and saves time. If an Odf reader were 5 to 10mb it would be much quicker (would be **like how codecs installation is prompted in ubuntu**)

an exporter from pdf to .doc would also help, but i prefer ODF to spread

msft took advantage of viral marketing, we could do too.

---

### Post by mrgnash on 2009-08-30
> **Brian Vaughan said:**
> There are those who feel that GNU/Linux developers are spending too much time on workstations and supercomputing, and not enough on personal computing:
[Supported Features]("http://xkcd.com/619/")

Of course, there are lots of GNU/Linux developers, on lots of different projects. This is not a problem of dividing up a finite pie -- and one of the benefits of increased FLOSS influence in personal computing is that it will increase the pool of software developers.

And this discussion is happening on the forums for Ubuntu, the flagship of GNU/Linux distributions designed for personal computing. It's not that Ubuntu's not good for server applications -- Wikimedia seems happy with Ubuntu servers -- but user-friendliness is what Ubuntu's known for. I'd think that involvement with Ubuntu implies a support for developing a personal computing operating system, one that's not just a second-rate Windows, but better than Windows.

In many respects, I think Ubuntu is significantly better than Windows now, even for those who are not technically adept. Ubuntu's default installation has all the software most people need, ready for use. The Add/Remove Applications applet is a far easier way to find and install applications than the process one has to follow for installing applications for Windows -- provided one doesn't try to install applications the way it's done in Windows.

But I think it's most important to value the ethical principles of free software. There's a real social question at issue here: whether technology is to be controlled by people, or people by technology. If there's one change I'd make to Ubuntu's default setup, come to think of it, it would be to place an icon for Gnome Terminal alongside the icons for Firefox and Evolution, so that it's front and center. I do not like the way Windows and OS X try to pretend that the GUI is the entire OS.

Well, I certainly agree that one way to make an OS better than OSX and Windows is to use the terminal more :P But yeah, I never said that I didn't think that Ubuntu or any other distro should not aim to be better than mainstream operating systems like Windows and OSX, even for home users, but that simply mimicking these operating systems was not the way to go about it. My belief, and I may be wrong, is that maintaining a workstation focus, but making things as easy as possible (without dumbing down), strikes the best balance between a not-too-steep initial learning curve and efficiency/power. By way of example, I always found that Windows NT, and then Windows Server, were better (though still not as good as Linux) operating systems than the lousy crap they fobbed off on the home users; and the initial learning curve wasn't _that_ much higher.

---

### Post by matthew.ball on 2009-08-31
Like one of the posters here (sorry I forget your name), I actually came to Linux because I found myself using only FOSS on Windows.

For the past few years I have always installed OpenOffice for friends, and I actually haven't received any bad stories (perhaps they just don't use it?).

I try not to push the Linux idea onto many people, I guess this goes against most people's ideals, but I find it wrong to change someone's opinion when they don't know all the details (and I'm not about to give them a run down) - if they cared, they would do the questioning themselves.

I just show them Linux programs which are available for Windows. 

OpenOffice happens to be a big hit with most people I know, I have also discovered a few people wanting GIMP.

---

