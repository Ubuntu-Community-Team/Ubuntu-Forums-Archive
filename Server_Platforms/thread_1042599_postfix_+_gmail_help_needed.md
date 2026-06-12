---
title: "postfix + gmail help needed"
date: 2009-01-17
forum: Server Platforms
---

### Post by MountainX on 2009-01-17
So I set up my blog on Ubuntu hosted at Linode.com. As part of the setup, I followed [this guide]("http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps").

I don't really understand what I did, but it seems to work.

Now, I just came across this article about [How To Fight Spam Using Your Postfix Configuration]("http://www.howtoforge.com/virtual_postfix_antispam"). That sounded like a good idea, so I attempted to move forward and I realized that I really don't have the background to follow this how-to guide.

Can anyone recommend some very simple guidelines so that I can ensure my postfix settings are properly restrictive. I only want email from my blogs and from the system to go out. Nothing more.

I use Google "apps for your domain" for my email.

---

### Post by mbeach on 2009-01-18
I think you'll be needing some certificates.

It looks complicated, but if you follow it through you should be in good shape:
[http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)

---

### Post by MountainX on 2009-01-25
Have you ever been so lost you can't even ask an intelligent question? That's how I feel right now.

I do have postfix working. (I did not need certificates because I already had completed that step.)

Here are my current issues:
1. I don't want any mail delivered locally. Right now my user account and the account "nobody" are sometimes receiving emails (particularly regarding failed delivery or errors). I want every single email addressed to a local user account (root, my user, etc.) to be delivered to a specified external email address. How do I ensure that happens?

2. When email is sent to a local account (root@localhost, etc.) I want it to show up in my gmail sent folder (for the gmail account used for smtp) and I want it to show up in the inbox of the external account that is specified in step 1 above. And I want this to work even when these two external accounts are the same.

3. I want postfix to be really secure and spam-proof and I don't have the basic knowledge to understand the how-to guides, so if anyone has a "for dummies" version of setting postfix up with advanced security, please let me know. What I've done so far does seem to be working. So maybe I have already done enough...

Thanks.

---

### Post by HermanAB on 2009-01-26
No, there are no dummies guides for Postfix, since it sure isn't...

If you want a mail system that is super easy to configure, then you got to have a look at Citadel:
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

Compared to Citadel, anything else is a total waste of time.

Cheers,

Herman

---

### Post by MountainX on 2009-01-26
I am close to having Postfix working the way I want it to, so I'd rather just solve these problems than start with a whole new set of problems (e.g., how to make Citadel work with Google Apps/Domain).

Besides, the areas where I'm having problems are not Postfix so much as I just don't have any background with mailservers. I'd probably have the same issues with Citadel.

---

### Post by MountainX on 2009-01-26
My current question: the DenyHosts report is sent out from nobody@localhost. How do I change that?

Here's an example:

From: DenyHosts <nobody@localhost>
To: root@localhost
Subject: DenyHosts Report
Date: Mon, 26 Jan 2009 10:46:03 -0500

How do I control/change the sending (and receiving) accounts? Thank you.
Regards,
MountainX

P.S. Background info:
I'm using Google Apps/Domain and I set up Postfix according to this guide:
[http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps](http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps)

Then I applied some spam settings (without understanding a word of it) from this guide:
How To Fight Spam Using Your Postfix Configuration
[http://www.howtoforge.com/virtual_postfix_antispam](http://www.howtoforge.com/virtual_postfix_antispam)

And I have read a bunch of stuff, starting with this:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by ojay on 2010-09-01
[QUOTE=
P.S. Background info:
I'm using Google Apps/Domain and I set up Postfix according to this guide:
[http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps](http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps)
[/QUOTE]

Hi this particular link does not exist again....does anyone have the proceeds downloaded or printed in .pdf to share. I also need to configure postfix on ubuntu to work with google APPs.

Thanks

---

