---
title: "Kolab vs. Citadel vs. Zimbra: Your thoughts?"
date: 2009-02-06
forum: Server Platforms
---

### Post by BlakeM on 2009-02-06
I've heard Kolab is a lot harder to set up due to lack of easy to understand HOWTOs and documentation. But Citadel has features I don't need, like bulletin board and IM. Zimbra is attached to Yahoo,  good thing or bad? Alternatively, I might just piece together the various packages myself (dovecot, postfix, squirrelmail, etc.)

Which groupware is best if all I want is:

[LIST=1]
[*] Have multiple users with email accounts @mydomain.com
[*] Webmail access to these email addresses
[*] Use IMAP so my WM5 PocketPC, laptop and desktop all have access to one email account
[*] Similarly, have calendars, tasks and contacts synced between the three devices mentioned above. (Kolab using IMAP sounds very innovative...but how hard is it to setup/maintain?)
[/LIST]

The main recommendations seem to be Zimbra, Kolab and Citadel. What does everyone think of Yahoo owning Zimbra? Is it truly open source? Is Kolab really that hard to setup? Or are you best off just putting all the packages together yourself?

---

### Post by HermanAB on 2009-02-06
Citadel is a very good mail server, that comes packaged with a web mail system.  You don't have to use the web mail system if you don't like it:
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

You can use Citadel with Squirrel Mail or Roundcube if you want.

Cheers,

Herman

---

### Post by lsu_guy on 2009-02-11
You should really look at zimbra. It can do # 1-3 easily in the opensource version.

# 4 gets a little tricky. Their opensource version will not sync to your WM5 without zimbra mobile which you have to pay for. 

Their paid version allows things like easier backups, outlook connector (their server speaks the exchange server protocol), sync with any device that uses activesync 2003 and 2007.

If you have few accounts, I would suggest getting a zimbra hosting provider. If you have tonnes of accounts (enterprise level) then you can think of hosting your own server. This is because maintaining and upgrading zimbra can get tricky whereas the hosting provider has extra servers to test out all the updates before changing their servers over.

PS: I dont work for zimbra. I was trying to figure out all the same alternatives a few months back and I ended up getting zimbra.

---

### Post by kblood on 2009-02-11
Has anyone around here checked out Open-Xchange?
It is really easy to set up in Ubuntu, and has a lot of features, even the open source version.

I haven't tested it, but seems like a solid, but surprisingly unknown alternative.

---

### Post by hyper_ch on 2009-02-12
I setup my own postfix server and installed horde on that. Nr. # 1-4 are easily covered there.

---

### Post by freerkkalsbeek on 2009-02-16
Hi,

I'm struggling with the same question, except that Zimbra is out of the question since it is not GPL'd. I don't like dual licensed solutions. The community support of those products is not what you see for truly GPL apps.

I've tried to get Kolab running, but that's quite a job. bootstrapping the system results in numerous errors, since intrepid uses the new online configureable slapd and AppArmor prevents access to files that the kolab_bootstrap is trying to use.

It shouldn't be that hard. For every simple app needed in a business system there is a good GPL alternative, but for groupware it's just not that simple.

Most groupware systems are built on top of postfix and imap/pop so mail is not that difficult. It is getting complicated when adding calendar functions, tasks and shared addressbooks.

Maybe horde is THE solution. Haven't looked at it as a complete solution, only in conjunction with a server like Kolab. 

If horde is able to give me both webaccess to email/calendars and provide the same services for evolution/kontact I'm happy.

Citadel is just not what I'm looking for. 

Regards,
Freerk

---

### Post by hyper_ch on 2009-02-17
you can use standalone horde... I intended to write a simple howto for it on debian for a while but never gotten to it.

---

### Post by windependence on 2009-02-17
> **freerkkalsbeek said:**
> Hi,

I'm struggling with the same question, except that Zimbra is out of the question since it is not GPL'd. I don't like dual licensed solutions. The community support of those products is not what you see for truly GPL apps.

Regards,
Freerk

You are totally wrong about the community support as far a s Zimbra is concerned. Zimbra has a very vibrant, active community and help is only a google away in most cases if you need it. The community is actually much better than at least half of the OSS community support, and I would say it's right up there on top. I have always gotten my problems solved there, almost always without even posting.

I am an independent consultant, and I have several commercial customers using the OS edition of Zimbra. It is absolutely not crippled in any way and continues to be developed right along side the commercial edition. In fact, some features in the commercial edition still come from the OSS edition. It is absolutely rock solid and feature rich and requires very little maintenance. It just works.

As far as the GPL goes, have you ever actually read it? I guess of you are a pureist then it's for you, but I much prefer the BSD style licence myself. The GPL as of late IMHO has become rather restrictive, but that's just my opinion. If the application works for what you want to do and you are lucky enough no to have topay for it, what do you care what the licensing is unless you are going to modify and redistribute it? Are you? If not, don't worry about it.

The cold hard truth is that if an open source application becomes very popular and works well as in the case of things like Zimbra, VMware, Xen, etc, then sooner or later someone is going to take it commercial. Yahoo is fortunately one of the companies that still actively supports their OSS version. Some don't.

The only thing you really have to be aware of is that Zimbra really wants it's own server. It's not good to try to run other things on the same server as the zimbra box, but it runs fine in a VM and then you can run other VMs as needed.

-Tim

---

### Post by hyper_ch on 2009-02-17
the problem I see with BSD is that you can turn Open Source into Proprietary. GPL on the other hand ensures that it stays Open Source :)

---

### Post by songshu on 2009-02-17
i never used the others so can not comment on these, but i personaly use zimbra and really like it, it might be a bit heavy on resources but the mail client is really really superb.


The OS version can do #4 as well but you need to set up an extra step to do so, just let funambol sync with zimbra and your clients sync with funambol.
i have thunderbird and several mobiles syncing it and it works well, check the funambol site to see what they support.

i made my notes on how to do it on the link below

[http://www.songshu.org/index.php/sync-zimbra-contacts-with-funambol](http://www.songshu.org/index.php/sync-zimbra-contacts-with-funambol)

---

### Post by windependence on 2009-02-18
> **hyper_ch said:**
> the problem I see with BSD is that you can turn Open Source into Proprietary. GPL on the other hand ensures that it stays Open Source :)

Of course, you're right on this, but the point is you can, but you don't have to. With GPL, you simply cannot. That's not choice, open, or free IMHO. We in the community have taken this whole thing to an extreme. People still have to eat and should be able to make money if they want. If folks don't like the fact that they start charging for a product, they should make it know by not buying it in favor of something else. The only problem I have with proprietary software is the companies charging astronomical prices for an essential product like an office suite. Such is a company in Redmond. :D

-Tim

---

### Post by rampageoberon on 2009-03-11
> **hyper_ch said:**
> you can use standalone horde... I intended to write a simple howto for it on debian for a while but never gotten to it.

I'm interested in playing with horde and a guide would be quite useful. hyper_ch, f you could post here once you have a guide it will be much appreciated.

Thanks

---

### Post by BlakeM on 2009-03-14
I'll second that.

---

### Post by P Minix on 2009-07-06
Third, the request on Horde.  I am trying to trade Horde vs Zimbra vs Citadel/OpenGoo vs activeCollab.  I wish their communities would provide a turnkey image or vm for their solutions - it would make evaluation easier.

---

### Post by windependence on 2009-07-06
Well Zimbra has a live Demo:

[http://www.zimbra.com/products/demos.html#demo](http://www.zimbra.com/products/demos.html#demo)

Or you can download a VM:

[http://www.vmware.com/appliances/directory/94533](http://www.vmware.com/appliances/directory/94533)

Either way, it's easy to evaluate the software.

-Tim

---

### Post by HermanAB on 2009-07-06
Citadel has an installed and configured VMware image for download.  It even includes SpamAssassin and ClamAV.

BTW, there is a new Blue Theme for Citadel in Beta - it looks very nice.

---

### Post by windependence on 2009-07-06
Hey Herman, why don't we just create an auto reply to all these e-mail threads? ;-)

BTW, Herman is my Dad's name.

-Tim

---

### Post by kustomjs on 2009-07-06
I like my own setup with postfix+dovecot+mysql+spamassassin+maia mailguard+custom email forwarder+ custom maillog+ custom email manager.

---

### Post by windependence on 2009-07-06
> **kustomjs said:**
> I like my own setup with postfix+dovecot+mysql+spamassassin+maia mailguard+custom email forwarder+ custom maillog+ custom email manager.

Then we should add you to the canned response. All solutions in one place! :-)

-Tim

---

### Post by HermanAB on 2009-07-07
Hmm, Zimbra is just about the only mail server I haven't tried yet.  If it can handle Yahoo mail, then it must be good.

Does anyone know what Microsoft use for Hotmail?

---

### Post by P Minix on 2009-07-07
I'm trying to replace an Exchange 5.5 setup -- biggest problems are email backups, calendars, syncing sent mail from webmail (host provided) and blackberry (BIS)) sync with sent and deleted mail.  

Ten heavy users on mixed clients: evolution, t-bird, and outlook; mixed os windows, ubuntu, suse, and mac.  Simple POP3/IMAP hosting with webmail handles current needs, old exchange server sort of handles archiving, public folders, contacts, and calendars

Horde's enforced routing rules interest me as I need to control all email sent to non-US addresses (anything not .us or on an internal list) by forwarding it to a manager for release.  Currently doing using some clunky rules in Outlook clients - doesn't cover BB or webmail.

The only thing I can't do is take away peoples BB or force Outlook users to change.  I can make the geeks change from t-bird to evolution or command line mutt.

So I am testing approaches, VMs are cute - but don't utilize hardware in the same way as the production machine - so I am building a disk installation for each and trying it.  That why I wished the communities for each approach had a turnkey iso.

Also, is there a way to write out the apt-get history or log it?

---

### Post by P Minix on 2009-07-07
add ebox to that list above

---

### Post by artcancro on 2009-10-02
Hey everyone, just checking in (and yeah, add my lines to the auto-reply too... <grin>)

Kolab and Citadel and Zimbra all "do the job" with flying colors, so just pick the one whose feature set best matches your needs.  Kolab, as you might expect, has the best integration with KDE.  Citadel is insanely easy to install; its user interface is unconventional but many people find it more intuitive than the myriad of Outlook clones once they get used to it.  Zimbra is pretty well focused on meeting Microsoft head-to-head in the enterprise space.

(As has been mentioned before, I'm not thrilled about Zimbra's "free tier / proprietary tier" model, but that doesn't bother some people.  YMMV.)

---

### Post by internalkernel on 2010-01-06
This thread seems to have gone a bit silent...but I'll throw in my two cents anyways. I came across this thread in my search for a replacement to Zimbra... 

I've used Zimbra for about two years now, and I'm over it... it's so heavey on resources and the web interface feels clunky to me. Missing basic features... etc. Anyways, I came across OpenGoo (now rebranded as Feng Office Suite) which has solved the majority of the collaboration issues I was facing. But, it does not provide a mail server... so I need a solid backend to do all the heavy lifting between clients. 

I just tried citadel... and wasn't overtly impressed - it was extremely easy to setup and configure though. I'm aiming towards Kolab/Horde but I have not found any docs discussing installation since Ubuntu 6.06... If anyone has any pointers, please post them... 

Thanks

---

### Post by caseygibbs on 2010-02-07
Being basically an amateur who has spent several weeks now fooling around with mail servers trying to set a decent one up for himself and his family, I thought I'd chip in, though yes, this list seems to have gone cold. I wanted secure IMAP/POP, webmail, and calendar; I wanted it to be light on resources, and I needed it to be easy to install. I tried several things, including Zimbra, Dovecot-Postfix w/Roundcube, and Horde; though I initially sort of despised the webmail interface on aesthetic grounds, I eventually figured out the nearly obvious superiority of Citadel, and am currently very happy with it. 

I have it running inside a virtualbox image for security and backup purposes. It's tiny, fast, and never fails. It was ridiculously easy to install. At home I connect to it over the network with Evolution and Thunderbird (mail and calendar); at work I use Thunderbird. WebCit, the webmail interface, once you get used to it, is totally serviceable (though, again, I won't sugarcoat its appearance, which leaves a lot to be desired).

---

### Post by Xianath on 2010-02-07
Just want to point out that Zimbra is now owned by VMware. Also, have you considered PostPath (now owned by Cisco)? It can do all of these and supposedly you shouldn't even have to reconfigure existing Outlook clients. Finally, the commercial offering for Google Apps comes with mobile sync capabilities. It may turn out to be the cheapest solution overall in terms of TCO, since it's hosted.

Cheers,
Peter

---

### Post by Railsbuntu on 2010-02-20
A few years ago I was looking for an SMTP server, and in some other thread HermanAB talked about Citadel. So I installed it.

It has been running for 3 years now, and I haven't had any issues.

It's webcit client is really really strange at first. Simply take care of the "Email", "Administration" and "Advanced" tabs at first, and you're good to go.

---

