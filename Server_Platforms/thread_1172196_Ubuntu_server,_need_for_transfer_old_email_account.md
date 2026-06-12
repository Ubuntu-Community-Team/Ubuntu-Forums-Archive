---
title: "Ubuntu server, need for transfer old email accounts after host change"
date: 2009-05-28
forum: Server Platforms
---

### Post by gemaneog on 2009-05-28
Here is the thing:

I work in a company that had a few websites in its old (shared one) server (preconfigured with cPanel). They recently decided and bought another server (dedicated this time, not preconfigured, ubuntu server 8.04 lts on it) in order to move all the websites on this new one and stop paying the old one. 

The problem is that along with these websites (example [www.domain.com](www.domain.com)) there were some email accounts, only for administration purposes (like [email]postmaster@domain.com[/email], [email]webmaster@domain.com[/email] etc.), each domain having it's own ones created via cPanel. How can i move these email accounts from the old server to the new one? I have to setup a mail server, right? (it should have a mail.domain.com link to open the corresponding mailbox which means there should be a webmail ui like horde). 

I could really use some help here, and it would be great if it was quick (it is my first priority job).

---

### Post by LepeKaname on 2009-05-29
Hi, 

First of all I have no experience with cPanel, but still I think I can help.
You need to create a mail server in your ubuntu box... for that I have a script that will do exactly what you need. Check it this link: 

[http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html](http://www.alepe.com/about_computers/about_linux/setting_up_a_mail_server_in_ubuntu.html)

It will setup accounts for several domains, such in a way you can use:
[email]info@domain1.com[/email] and [email]info@domain2.com[/email] ... 

I recommend you to scan or read the tutorial in there so you can know exactly what the script is doing, and if that is what you want.

To move the email accounts, you may need to do it manually (copying the mail files). Usernames, passwords and settings will change, so you will have to notify the users about it. 

I have done that before and the only painful part is the beginning, then you can sit and do other things...

I hope it is helpful..

---

### Post by gemaneog on 2009-05-30
LepeKaname thnx for the reply,
sorry that it took me so long to post back, i had some issues with my isp (for your sake, if you ever come to greece, do it only for vacation, not for work :P).

so, what really matters here is not actually the mails themselves as are the mailboxes. i mean, is it possible to move all accounts into new server when this mail server is up and running? how will i disable the old postmaster accounts since the previous host is actually preventing us from deleting postmaster@domain accounts? and if we disable them (as it seems, only by stop paying), will we be able to set up the new ones at once or will it take some time? 

to quote from the old hosts online manual : 

> IMPORTANT: The postmaster email box is a mail box which you can neither delete nor change its quota. However the webmaster email box works as normal and counts towards your total email box limit. 

old host is [ixwebhosting]("http://www.ixwebhosting.com/index.php/v2/pages.manual9")

---

### Post by HermanAB on 2009-05-30
In my experience, the easiest way to move email around is to bounce it through an IMAP server.  If you install Citadel (which takes less than an hour), then you can move mail from wherever it is to Citadel and then move it again to the new place.  However, once you have Citadel running and the mail in it, you could just keep it there.

---

### Post by gemaneog on 2009-05-31
> **HermanAB said:**
> In my experience, the easiest way to move email around is to bounce it through an IMAP server.  If you install Citadel (which takes less than an hour), then you can move mail from wherever it is to Citadel and then move it again to the new place.  However, once you have Citadel running and the mail in it, you could just keep it there.

i can see your point here, but the thing is that my boss won't accept this kind of handling in his server. and what do you exactly mean by saying 'bounce it through an IMAP server' ? (that's why i am asking for intel here, i am a complete noob concerning mail servers)

---

### Post by HermanAB on 2009-05-31
Howdy,

IMAP servers have some commands that POP servers don't have. It is easy to move mail in bulk to/from an IMAP server.  Goto [http://google.com/linux](http://google.com/linux) and look for "IMAP mail server move scripts".  There are also special tools for it like this one [http://migrationtool.sourceforge.net/](http://migrationtool.sourceforge.net/)

So, I would set up a Citadel VM ([http://www.citadel.org/doku.php/installation:appliance](http://www.citadel.org/doku.php/installation:appliance)) as a local mail store and copy everything there and back it all up. Then you can carry on experimenting with move scripts, safe in the knowledge that you have all mail saved on a DVD.

Hope that helps!

---

### Post by gemaneog on 2009-06-01
so, new data. My boss is interested in moving the mail accounts in gmail (google apps imap migration tool). 
i'm reading the documentation of google atm and it says it is only possible for imap (and i think the old server is set in pop3). 

is it possible after migration that the old mail accounts will exist in google apps in some way (he said sth about domain alias)? 

plz don't blame me if i ask stupid things, i already said i'm way too noob concerning mail servers, i'm trying to learn though.

---

### Post by LepeKaname on 2009-06-02
Hi gemaneog,

You can import pop3 accounts into Gmail:

[http://www.webhostingshow.com/2008/08/28/import-pop3-accounts-into-gmail/](http://www.webhostingshow.com/2008/08/28/import-pop3-accounts-into-gmail/)

I done that once and worked very good... you just have to wait cause the process take some time.

That's all.

---

### Post by gemaneog on 2009-06-04
and again, thnx for the answer. the point here is that we will stop paying the old host (which will erase all of these email accounts), so we don't just need to fetch mail from server to server, but actually move these accounts (and their existing mails). 

one more thing (i hate it when i'm not fully informed as i should): there actually are some user mail accounts in there (not quite as i informed you and as i was informed) besides the ones for administration. 

i give you the link for google's server mail migration so you can understand what i'm talking about 

[Google email migration service documentation]("http://code.google.com/intl/el-GR/apis/apps/email_migration/developers_guide_protocol.html")

---

### Post by LepeKaname on 2009-06-05
I have never used that one... Just importing each email's account into google mail it will be enough, I think. Once you have all your mails there, you have to inform your users about the settings. And the rest will be the same. Why it doesn't work for you that way?

---

### Post by gemaneog on 2009-06-09
i guess because probably it doesn't take over from old mail server, it just redirects mails to gmail account. but i've only tested it on a hotmail account, i don't really know if it will work the way you say it will. just give me some time till i make some tries (i haven't been to work past few days for i am concerned with other matters about my university atm). when i test it, i will let you know.

---

