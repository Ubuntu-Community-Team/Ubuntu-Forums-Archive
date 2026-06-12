---
title: "PC Pro magazine are running their entire office on Ubuntu for one day and blogging it"
date: 2011-02-10
forum: The Cafe
---

### Post by Sealbhach on 2011-02-10
Follow it here:

[http://www.pcpro.co.uk/blogs/2011/02/10/live-blog-running-pc-pro-on-ubuntu/](http://www.pcpro.co.uk/blogs/2011/02/10/live-blog-running-pc-pro-on-ubuntu/)

and on Twitter:

[http://twitter.com/search?q=%23ubuntupro](http://twitter.com/search?q=%23ubuntupro)

I can't start a new thread in the Community Cafe for some reason. :confused:

Anyway, check it out, it's gonna be interesting.

---

### Post by gaz77 on 2011-02-12
Hi There,

there is an intresting article about Ubuntu being trialled at pcpro

[http://www.pcpro.co.uk/blogs/2011/02/11/running-pc-pro-on-ubuntu-the-verdict/](http://www.pcpro.co.uk/blogs/2011/02/11/running-pc-pro-on-ubuntu-the-verdict/)

This could give some idea on future development

---

### Post by Dragonbite on 2011-02-22
It sounded like if they could get Evolution working (with their system, which is Microsoft Exchange) it would have been a 90%-win situation.

I hope Ubuntu, Novell and Red Hat take notice and work on making Evolution a better drop-in replacement for Outlook.

The rest of the issues seemed to be the unfamiliarity with the applications and a few where the program could not perform what they wanted/needed.

All-in-all it looks like it was a successful experiment in my eyes, and a number of issues (except the Evolution-Exchange issue) would be worked out if they gave it a try for a week or month instead of a day.

---

### Post by themarker0 on 2011-02-22
Evolution is almost a failed cause. Its a great program, but its ignored to no end, its terrible to see that.

---

### Post by Khakilang on 2011-02-23
I am sure Microsoft will try to keep whatever OS to work with their software. Even if Evolution dev make it work. Microsoft will make sure it doesn't happen.

---

### Post by Witch Lady on 2011-02-23
That was interesting read, both the day-blog and the verdict. Thanks for sharing. ^^

I have to check their guide they wrote about, too.

---

### Post by TheFunkeyGibbon on 2011-02-23
> **themarker0 said:**
> Evolution is almost a failed cause. Its a great program, but its ignored to no end, its terrible to see that.

It's a shame but at the moment this a big stumbling block for me. I want to learn more Linux by using it day-to-day. I work doing tech support in a Windows environment and need to use Exchange 2010 on an ongoing basis, I can't choose not to.

I installed Ubuntu 10.10 from the PC Pro DVD that was promoted by this issue and in the main found it to be a pretty reasonable experience with the following exceptions:

1) As mentioned Evolution is an EPIC fail when it comes to Exchange 2010. I understand there is lead time on the developement but EWS has been out for a while now and since it's SOAP\XML based there should be no excuse not to be catching up as soon as possible. Microsoft have even been very unlike themselves by *documenting* EWS here -->[URL]http://msdn.microsoft.com/en-us/library/bb204119.aspx

]I'm no programmer so maybe I'm underestimating what is required but I'm pretty sure that people who could implement WebDAV and MAPI connections can manage this.

2) Ubuntu hangs on shutdown on my laptop (HP ProBook 4250s). I understand this is almost certainly a driver issue but frustratingly the scant support on HP's own site appears to be limited to a bunch of tars that they lable up as being for SLED\OpenSuse. I'd guess this is actually not the case and they are generic enough to use with most Linux implementations but I've not tried yet.

3) Unity. I made the mistake of trying this. Looks like it'll be awesome on touchscreen devices but man, it's frustrating as hell to use on a Desktop. If this truly represents the future of Ubuntu maybe the current King is heading for a fall. It's simpley not designed with multiple windows in mind, which is exactly what the desktop is about. Unity seems to be the iOS approach to UI - one thing at one time. Sure you can multitask but you are 'encouraged' to only use one application at a time. Removing flexiblity from how a PC is used? Isn't that a backwards step?

Oh and I totally killed my desktop by trying to remove it using the package manager. Now I log in and get a white screen and nothing else. I realise this was my ignorance as much as anything but it wasn't clear how I could switch back away from Unity to the regular Gnome desktop when I realise I didn't want to use it.

I'm going to keep at it but is Linux ready for business? Not unless they are prepared to make wholesale changes to their environment (new mail server, new applications for Office, CRM, accounts etc) and that's too hard a sell.

---

### Post by Dragonbite on 2011-02-23
In Linux's defense Exchange, Office and Active Directory are probably the three biggest "vendor lock-in" tools Microsoft has.  These are the tools that I hear the most often are the stumbling block to migrating away from Microsoft and at this time I don't see a Linux replacement for them yet.

Google doesn't cut it for corporate entities, they want absolute power and control over their data, files and etc.  That's why I still say the "cloud computing" that will bring the cloud to critical mass will be "private clouds" that corporations can run in their own server rooms, but have all of their employees (in the office, satellite offices and out on the road) able to access ALL things in ONE place.

ASP.NET and SQL Server may be seconds, but those are more easily replaced and there are corporate competitors so the typical proprietary vs. open source arguments are nullified.

---

### Post by Scabby_al on 2011-02-23
I've been a loonnng time Linux user and been on-board with Ubuntu since '04 and have been lurking here for a long time.

I'm using Ubuntu every day to perform sys-admin work in a Windows/Exchange 2010 environment with the help of a Win 7 VM when I need it. The killer thing for me right now is email. We are a small shop that has been bought out and we currently connect to Exchange via rpc over HTTPS which isn't supported by any mail client. There are a few ways you can overcome the email issues:

- You can Firefox and have access to Exchange 2010's premium interface which is pretty slick (though lacks any decent message notification)

- You can use davmail to access your server and it supports EWS. You can use it with Evolution, Kmail, Claws, Thunderbird, or whatever you choose. I find davmail very buggy sometimes...especially with calendering. Not a knock on the developer, more against MS.

- You can kindly ask your Exchange admin for imap access. You will be able to get your mail but it won't solve syncing any contacts, calendar, etc.

- Lastly, I googled how to spoof the user agent for Chromium and made an "app" so it was like I had outlook installed but in reality it was just a stripped out Chromium window running Outlook Webmail. It was very buggy though and the agent spoof would randomly not work.


Overall though, I love my Linux experience and everything else is really easy to use and maintain and the experience has gotten better leaps and bounds since the "early days".

---

### Post by Dragonbite on 2011-02-23
There are ways to try and get Linux to access Exchange server (e.g. using the web interface), but it isn't sufficient yet.  Evolution ha_d_ the best chance and unless somebody picks it up (yeah Novell, you!) and works on this Linux will not make any sizable dent in the front end of corporations.

The alternative is to use a different PIM system which *IS* compatible with Linux (Zimbra? Lotus?) and with enough "oomph!" either from a big company backing it up (IBM, Oracle, etc.) or open source and feature-full.

During the Novell-Microsoft collaboration I was hoping that some effort would be placed to help Evolution. I know some Active Directory benefits were supposed to come out of that deal but Evolution got overlooked.

Kontact would be the next logical choice, but KDE isn't big enough in corporate environments (e.g. Ubuntu, Red Hat, etc.) to be able to force anything. That doesn't mean they are not able to, but they are more largely on their own than Evolution should have been.

*Mind you, this is all only my opinion, and subject to change without notice.*

---

