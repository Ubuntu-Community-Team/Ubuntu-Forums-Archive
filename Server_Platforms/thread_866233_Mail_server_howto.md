---
title: "Mail server howto?"
date: 2008-07-21
forum: Server Platforms
---

### Post by Gyppie on 2008-07-21
Hi!

I am a Linux noob. I have played around with Ubuntu server 8.04 for a while now, and I'm lovin it more and more.

We are 3 in my house, and we want to set up a mail server, but we want to use our isp provided mail adreses. So is it possible to set it up so the mail server collects and send the mail trough our isp provider? 

We also want to access the mail internaly in my household by using Microsoft outlook (Windows clients), and externaly when we are not home and still get access to our mail and contacts. Is there a good howto?

Sorry for my bad english.


Gyppie

---

### Post by theonegod on 2008-07-21
Why do you want to use your own mail server for this? It sounds like your ISP is already providing you with your Email and thus all the services you are looking for.

---

### Post by Gyppie on 2008-07-21
> **theonegod said:**
> Why do you want to use your own mail server for this? It sounds like your ISP is already providing you with your Email and thus all the services you are looking for.

Hi!

Becouse of storage restrictions. I think it is 15 mb of storage. I know there is a lot of other free mail providers like gmail, hotmail and so on. I have used my mail adress for about 8 years now, and I dont want to change it.

Gyppie

---

### Post by Titan8990 on 2008-07-21
Mail restrictions are easy to get around. If your ISP offers a POP server than you can use a MUA such as Evolution or Thunderbird to download mail out of your account and to your local machine.

Setting up an email server is by no means an easy task. It will be filled with frustrations. It is a rewarding experience once you finish.

First thing you will need to select a email server.

Postfix is the officially supported email server for Ubuntu. Exim4 is the officially supported server for all the debian based distros (meaning supported by Ubuntu as well).

What you will be doing is configuring your email server to use a "smarthost" (SMTP Server).

Your ISP may not allow this. You may want to contact them for more information.

Personally, I wouldn't do this at all unless it was for educational reasons.

---

### Post by songshu on 2008-07-21
pulling the mails from the server to your own and then read it from anywhere is fairly easy, "fetchmail" could do that i think although never used it myself.

keeping the contacts and calendar thing in outlook synced with the server is a little bit more hassle, since microsoft likes to get paid for that kind of thing. (please correct me if i'm wrong) i think you need something called MAPI for that.

you might want to consider if you want the contacts as well, since this will influence the options you have.

---

### Post by chilinski on 2008-07-22
This can be a lot of work, but very educational. Sitting at home, you could easily have a mail server that uses something like fetchmail to get your mail from the ISP's server and stores it locally. You could then configure your email client to go to your internal email server to check your email. You would configure the outgoing/SMTP side of your client to use the ISP's smtp server. For example, your client may have a pop3/IMAP server address of 10.0.1.60 (which would be the email server in your house) and an outgoing/smtp address of 201.202.203.60 (or something like smtp.myisp.com) to send mail.

When you're "on the road," it might be better to use a web-based email client to a webmail "server" on your machine. For example, I run Openwebmail on my mail server and I can check email on it by going to a web address. Sendmail and Openwebmail can handle your connections from the outside world.

You'll end up investigating DNS, too, I suspect. Most ISPs give you a dynamic ip for your home network, so it can change frequently. If you have to use an ip when you're on the road, you can't be sure that the one you have in your client setup will still be valid for your network. They should be able to keep track of your isp and map it to a domain name so it always knows how to get to you.

Then you need to run some sort of firewall/router that allows specific ports to pass through to the mail server (generally ports 110, 25, 443, 993) for mail and port 80 if you want the webmail client. 

Another alternative would be to run OpenVPN on the home machine and connect to it via the OpenVPN client when you're on the road, which would eliminate the Openwebmail setup and allow you to keep the same settings in your email client no matter where you are.

As I said, there's a lot of learning here. There's lots of options and not one correct way of doing it. And though some of what I told you above may work for me, others will have other ways of accomplishing the same things and may find my way outdated because I haven't set one up in awhile.

---

### Post by cdtech on 2008-07-22
I run a small email server, only for server information that I email to my cell phone. My ISP will not allow an open email port so I have to use a relay for postfix to work in this manor. Most providers will not allow open ports of this nature do to spam.

Hope this helps........

---

### Post by zdude on 2008-07-22
I've been running my own mail server for about 8 years or more. It was a pain to setup but it is rewarding to have your own system. As others have stated, most ISPs do not allow for port 25 to be used and you have to relay via some proxy or the ISPs (if they allow that). I am lucky that my provider doesn't block any ports so I do what I want ;) 
Anyway, to make a long story short, do a google for "intalling postix amavis clamav" and you will see quite a few how tos. These helped me setup my system and I've since expanded it with CourierSSL, Imap, squirrelmail, etc. It works great and I have encrypted mail where ever I travel.

---

### Post by HermanAB on 2008-07-22
Install Citadel [http://citadel.org](http://citadel.org).  Set it to forward your mail to a smart host (your ISP mail server).  Setting it all up using the Easy install script should take about 20 minutes.  There is nothing easier.

Cheers,

Herman

---

