---
title: "Exploring a &quot;groupware&quot; solution"
date: 2007-03-11
forum: Server Platforms
---

### Post by Brazen on 2007-03-11
I'm looking for a groupware server to replace our Exchange 2000 server.  At first I was looking at the groupware packages such as eGroupware or Zimbra, but they each have failings and I'm starting to think I would be better off setting up the features I want with individual, better-supported, more-popular packages.

I need everything to work over a web interface and also be available for offline access through local client software on Windows machines.

We have Outlook 2000 right now, but I'm wanting to switch to an open source client, probably Thunderbird with the very beta (unfortunately) Lightning add-on.  The only two features I can think of needing are email and calendars.  I'm pretty sure that is all anyone uses Exchange for in our organization.  If anyone can think of any other necessary features, let me know.

So for email, I'm thinking Postfix, plus Dovecot for IMAP (for offline access) and then I'll need something for the web interface.  For calendaring, I have no idea.  I will need each user to have a personal calendar and then also shared calendars.  Again, the calendars will need to be available offline either through Outlook or (preferably) Thunderbird's Lightning.

Thanks.

---

### Post by Brazen on 2007-03-11
Oh, contacts would be another necessity - again, available through the web and the local client.

---

### Post by elcasey on 2007-03-12
There's a groupware app called "Citadel" that was recently reviewed in, I think, Linux Magazine (UK). I'll try to hunt it down and post again with links and a few quotes.

---

### Post by rennen01 on 2007-03-12
I, too, would be interested in the suggestions you find.  I am searching right now as well.

Thanks in advance.

---

### Post by Brazen on 2007-03-12
I found Citadel after elcasey's suggestion and it does look nice and it supports groupDav, which I am hearing is the next best thing for synching groupware servers with local clients and is supported by Thunderbird/Lightning.  It's not supported by Outlook, though, and I have realized I also need some solution for syncing with PDA's.  If Citadel would support SyncML, then the PDA issue would be solved.

I'm going back and looking at eGroupware.  I don't like the interface.  I think it looks cold, unfriendly, and cluttered.  It looks like it has excellent syncing facilities though, which makes it very attractive.  I'm still at a standstill; I may just have to keep Exchange a while longer.

---

### Post by elcasey on 2007-03-12
I was mistaken, Citadel was reviewed in the February 2007 issue of *Linux Journal*. In the article they set it up to deal with KMail, Kontacts and KOrganizer. So I feared it wouldn't support Windows clients so well....

---

### Post by wayne_za on 2007-03-22
Try and look at the site opensourcecms they have groupware section and live demo's to try out.

[http://www.opensourcecms.com/]("http://www.opensourcecms.com/")

---

### Post by EricWiz on 2007-06-14
I am also looking into replacing an aged Exchange server and would like to find either a groupware package or as Brazen was looking to do, build the solutions with seperate packages. 

What is everyone using for email, calendar and contacts in a biz environment?

---

### Post by Frosty Cold Drink on 2007-06-14
Just as a note to you guys with larger staffs, eGroupWare supports SyncML, which means you can throw a SyncML client on your mobile phone or PDA and sync contacts and calendars over the air. Its not a seamless as BES, but its a big plus for eGroupWare, and some other packages support it to. Funambol has a GroupDav connector, so if something supports GroupDav you could theoretically tie in Funambol for your wireless devices, but I'm not sure how well that works.

---

### Post by nkassi on 2007-06-15
There is always chandler and cosmo which are made by the osafoundation. They are not in the spotlight these days but it's not a bad project.

[http://www.osafoundation.org/](http://www.osafoundation.org/)

---

