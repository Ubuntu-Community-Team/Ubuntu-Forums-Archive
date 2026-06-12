---
title: "Linux Server ideas for SBS equivalent, plus Groupware"
date: 2011-07-27
forum: Server Platforms
---

### Post by pingadam on 2011-07-27
Hi,

I am researching the possibility of using a GNU/Linux distribution as the basis for a replacement for Microsoft SBS (Small Business Server) plus Exchange and SharePoint, and would welcome and be grateful for any input and advice.

I work with a small company whose main line of business is installing and maintaining servers into small businesses (although this isn't my own area of expertise, being a software and web developer myself): currently all these servers are running Microsoft Windows, in various flavours: some use SBS (Small Business Server) 2003, others SBS 2008, and a few I believe use the "full blown" MS Windows Server operating systems (both 2003 and 2008 editions). There are even 2 or 3 tiny peer-to-peer networks that utilise Windows XP as a kind of "pseudo-server"! Most use some form of tape drive for nightly backups (which is a pain for Windows Server 2008, as Microsoft in their wisdom have removed direct support for tape backups, you have to purchase separate software from around £150 or more extra!).

The MS Servers seem to generally work very well for their intended purposes, but are proving to be expensive for some very small businesses to contemplate, due to software licensing costs, not only for the initial Server software but also on a per-user basis, as each CAL (Client Access License) costs extra.

In particular, small business of 1 to 10 employees don't find using MS Servers to be cost effective!

The company has for some time been interested in researching the possibility of utilising Linux as a replacement for Microsoft SBS and Exchange in particular, but we don't currently have a great deal of experience of using this in the field (I myself have been using Linux on and off for around 10 years, but not as a production server system - I currently use mainly Ubuntu at home - but this is why I've been tasked to do the initial investigation and feasibility study into using a Linux-based server as an alternative to Windows SBS!).

One particular concern is how we can replace MS Exchange (and possibly SharePoint too) with Linux-based Groupware, for which there seem to be many different options, for example:

- Zimbra
- Zarafa
- Citadel
- Kolab
- eGroupWare
- OpenXchange
- SOGo

plus no doubt many others.

Also, I have found that Zentyal (see: [www.zentyal.org](www.zentyal.org)) seems to produce a nice Linux SBS based on Ubuntu Server 10.04 LTS (although you can also install Zentyal as a package on "vanilla" Ubuntu via the repositories), this uses Zarafa as the groupware. Plus it appears to have a nice web-based admin console.

Most of the client PCs for these servers will be running Windows, occasionally Mac OS X, and more rarely (if ever) Linux.

Most of the clients also currently use Microsoft Outlook as their email and groupware client.

The main basic requirements for the server are:

- File Server
- Printer Sharing
- Groupware
- Nightly Backup of all the above

The main requirements for us for Groupware are:

- Easy sharing of Calendars (including Appointments, Tasks and To-Do lists) on the LAN (Local Area Network)
- Sharing of Contact lists (Address Books)
- Centralised EMail storage
- NOT a monthly or yearly-based paid subscription (free/community/opensource edition, or one-off cost, are all possible)
- Ability to offload sending + receiving of emails to/from ISP (Internet Service Provider) servers

The last point above is important - currently we set up MS Exchange to use the "POP Connector" which relays outgoing emails to the ISP's SMTP server, and pulls in incoming emails from the ISP's POP server: this effectively means that the SBS + Exchange server is hidden from the internet behind a firewall and router, and is not directly exposed to the internet as a server - the ISP then handles all the "nasty" stuff (viruses, SPAM, DoS [Denial of Service] attacks, etc) on the "frontline" (of course the SBS still has anti-malware and SPAM security etc, but as a secondary line of defence). Basically, we don't want these small servers to be "in the line of fire" directly on the internet, but would rather have the ISP handle the frontline of defence, and have these small servers just on the company LAN.

I've looked as various Groupware suites, some are completely open source and free to use (e.g. Citadel), others are split into free "community"/open source editions and paid-for commercial editions (e.g. Zarafa, Zimbra), and a few are paid-for closed source software only. Many of the commercial versions are based on annual paid subscriptions, and we want to avoid these (might as well use MS SBS + Exchange otherwise!). Some of them do have the ability to link to MS Outlook, others have limits where you can only use say 3 Outlook client connections with the free version and have to pay the annual subscription if you want more (e.g. Zarafa ?), others require you to use the commercial version if you wish to use Outlook (e.g. Zimbra ?), or you can in some cases purchase a per-user "Outlook connector" license (this is ok for us if not too expensive and a one-off per-user cost rather than a subscription). Outlook isn't a showstopper for us: some of the Groupware suites have their own client (e.g. Zimbra Desktop as part of the ZCS [Zimbra Collaboration Suite], which is cross-platform for Windows, Mac OS X and Linux), all seem to have web access to the email and calendars (Zarafa's looks very similar to Outlook Web Access), plus with many of them we could always try to get Mozilla Thunderbird + Lightning (calendar add-on for TBird) working with the groupware servers in place of Outlook, if it can be made to work reliably. (Use of any Linux-only client software, e.g. Evolution or Kontact, is out of the question as few if any of the client PCs will be running Linux).

Does anybody here have any suggestions or recommendation on Linux-based groupware servers for us to investigate? Zimbra seems to be one of the front-runners so far, as it's backed by VMWare and is becoming well-known with a large community of users and developers, but on the down-side seems to be a bit heavy on resources from what I've heard (and it would be quite nice to be able to utilise small "low-energy" servers for some of these small businesses if possible), and tricky to set up correctly. The Zentyal system looks quite good too, but currently uses Zarafa as the groupware server, and I'm not sure how this compares to Zimbra. It's limited to 3 Outlook connections for the free version (commercial version is not an option due to annual subscription), doesn't have it's own client software and looks difficult to use with Thunderbird, although it has a nice web interface. Citadel looks quite good too, but again I haven't investigated too much yet.

With all of these, I'm not sure how easy it is to isolate the groupware servers from the internet (similar to using MS Exchange's "POP Connector").

Also, does anyone have any good recommendations for a Linux equivalent to MS SharePoint, to make is easy for the company to share information, set up internal bulletin and notice boards, etc? (I must admit that personally I haven't used MS SharePoint, but apparently some of our customers find it very useful).

One other thing - what is the Linux equivalent for Microsoft's VSS (Volume Shadow-Copy Service)? This enables you to make snapshot copies of files for backup, even if the file is locked an in-use by a user or program.

As I said before, this is really only for small businesses of 1 to 10 people at the moment, plus probably for our own in-house use.

Any other recommendations, ideas, hints + tips, etc,  would be very welcome.

Many thanks in advance,

Kind regards,

Adam.

---

### Post by HermanAB on 2011-07-27
KnowledgeTree.

You can get everything you need here:
[http://bitnami.org/stacks](http://bitnami.org/stacks)

---

### Post by Gyokuro on 2011-07-27
Take a look at ClearOS ([http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)) - it's based on CentOS and should do the job.

---

### Post by pingadam on 2011-07-29
Hi,

Many thanks for your replies, sorry for my own late response. (And sorry for the length of my original post, I was just trying to lay out the background to my requirements).

Herman, KnowledgeTree looks very interesting as a Document Management System, it could perhaps replace some (or all) of the functionality of SharePoint (or it may at least be "good enough" for our intended customers) - I'll investigate further.

Gyokuro, the ClearOS (formerly ClarkConnect ?) looks very interesting too, similar to Zentyal in some ways. I wasn't sure what Groupware system they use, it isn't made clear on the website, although the forums mentioned integration with Zarafa (as used also by Zentyal) and SOGo - both of these 2 Groupware servers seem to be quite popular.

I'll continue investigating Linux-based Groupware - so if anyone else has some recommendations, that would be great. In the meantime, thanks for the suggestions so far.

Kind regards,

Adam.

---

### Post by drdos2006 on 2011-07-29
Another one to have a look at could be [http://www.citadel.org/doku.php](http://www.citadel.org/doku.php)

regards
[edit]
oops.. You have that listed....
[/edit]

---

### Post by SeijiSensei on 2011-07-30
I'll answer your specific question about exchanging mail with your ISP.

On the sending side, you would configure the mail server software to use a "smart host".  In Postfix, for instance, you'd enter the IP address of the ISP's SMTP server in the "relay host" directive; in sendmail, you'd assign it in the sendmail.mc file before building sendmail.cf.

On the receiving side, you can install [fetchmail]("http://fetchmail.berlios.de/"), a simple utility that will download the mail from the ISP's POP3 mailbox and distribute the messages to the local accounts.

---

### Post by pingadam on 2011-08-02
@DRDos2006: Thanks for the suggestion of Citadel (yes I had already listed it), I'll take a closer look at this one.

@SeijiSensei: thanks for the information on using Smart Hosts / Relay Hosts for sending and Fetchmail for receiving emails to/from the ISP servers. I think that Zentyal makes it fairly easy to configure these (for Zarafa groupware), so no doubt this can be adapted generally for most Groupware systems (e.g. Zimbra, Citadel, etc).

So far I'm tending to favour using either Zarafa (via Zentyal), Zimbra, SOGo or Citadel for Groupware, but will continue investigating.

Many thanks again for the information, suggestions and help provided.

Kind regards,

Adam.

---

### Post by zerubbabel on 2012-01-15
It's been awhile since you posted this, but if you're still looking for a document management solution, I'd recommend Nuxeo over KnowledgeTree. We used KnowledgeTree for several years, but recently switched to Nuxeo and find it much faster, more versatile, and a much nicer user interface.

---

### Post by pingadam on 2012-02-03
@zerubbabel: many thanks for your suggestion (I've only just seen your reply!), I'll take a look at Nuxeo, sounds interesting.

As a general update, I'm still investigating Groupware, but now Linux (and also Mac) clients have become more important (and Outlook less so!), as some of our customers are expressing an interest in moving their client office PCs to Linux! So, I'm still investigating Groupware servers, but with an emphasis on those that support cross-platform (Windows, Linux & Mac) clients, in particular Thunderbird + Lightning. Zarafa was looking good, but unfortunately it seems geared to a Web Interface (which is ok as backup, but insufficient for main use, as we need offline access to emails) and MS Outlook: we would prefer groupware to work well with TBird + Lightning (Zarafa doesn't support sync for TBird Contacts). Does anyone have any further recommendations? Is SOGo a good option? Or Citadel?

I'll probably look to working with Thunderbird version 10, as this is flagged as an "Enterprise" release (similar to the Ubuntu "LTS" system I guess).

Many thanks.

---

### Post by pout on 2012-10-12
Hi,

again your last post was a while ago.
Zarafa has a CardDav Server so you can sync Contacts with Thunderbird using the SOGo Connector Add-On ([http://sogo.nu/downloads/frontends.html](http://sogo.nu/downloads/frontends.html)), I guess.
I do this with a tine20 installation([http://www.tine20.org/](http://www.tine20.org/)), which also uses the Sabredav-Server like Zarafa. 

I am also still searching for the best collaboration software.

I like tine20, but missing the full text search for emails on the webapp. Whats also missing is the task-sync.

What I like on zimbra is, that it has its own Desktop-Software also for offline working. In the zentyal forum sombody wrote about a separate zimbra-server and syncing LDAP with zentyal. 
Maybe thats a solution. Active Sync is missing in the Open Source Edition. But ther ist a z-push project for zimbra or for Android you can use the carddav- and caldav-sync apps.

regards

---

### Post by foxuser on 2012-10-12
Hi

You have also this option:

[http://www.zentyal.org/](http://www.zentyal.org/)

---

### Post by LHammonds on 2012-10-12
> **foxuser said:**
> Hi

You have also this option:

[http://www.zentyal.org/](http://www.zentyal.org/)

You did not read his 1st post which already mentioned that one.

@OP, I am in similar boat and going from Exchange 2003 to Zimbra and have documented a step-by-step how-to for Ubuntu 10.04 and Zimbra 7.20....now I'm working on a new document for Ubuntu 12.04 and Zimbra 8

I also use Zentyal for a print server and slowly moving queues over to it.

I don't have a file server solution yet but it would have to play VERY nice with Active Directory and complex, yet seamless user/group permissions.  When I get to that step, I think the only option is something called Likewise.

LHammonds

---

