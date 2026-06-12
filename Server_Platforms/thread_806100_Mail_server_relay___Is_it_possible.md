---
title: "Mail server relay  / Is it possible?"
date: 2008-05-24
forum: Server Platforms
---

### Post by rslrdx on 2008-05-24
This is what I like to achieve: be able to have a local mail server with all extra features, calendar, contacts, etc etc, that relays the email to an external server, however the external server is now even owned by me, its a paid shared hosting, and I need the local server to connect over imap to the remote server.

The Remote server is the server hosting the company internet domain, and email, its a shared hosting plan. 

While I can access the server with any email client over imap and pop3, I like to have the email available online and its also good in case the local mail server is down, besides, hosting the domain locally is not an option (too damn expensive down here) 

Here is why I want to have a internal mail serve, every time someone in the office saves a contact, that contact only exists in the machine that person is at, if the machine is not available, they cant do anything but use the online mail client which doesn't have any of the contacts or the calendar. also, if they are traveling they cant access the stuff they need because its all in a box, not on the server. using the online calendar is slow and not really able to share information easily with other people in the company.

if I have a local mail server that that can just relay the mail through the external server I`d be set, Then I can have all features virtually everywhere (even using vpn access).

So, here I am, asking the Ubuntu community for an idea. How can I achieve such setup? Is it even possible?

I guess I would have to setup a user on the external server and one with the same credentials on the local server or something along these lines.

I dont have any preferences in software other than ubuntu server

Thanks in advance,
Rodrigo.

---

### Post by geogur on 2008-05-24
It sounds like you want a contact data base. You might be able to set things up on your end to collect email contacts using a exfile/script to take new contacts and post then in your online data base. :-k

---

### Post by rslrdx on 2008-05-24
> **geogur said:**
> It sounds like you want a contact data base. You might be able to set things up on your end to collect email contacts using a exfile/script to take new contacts and post then in your online data base. :-k

Not even close to what i need... I need the full PIM options, only that I cant afford a good connection to host it in house (over 2k for that) nor can i afford hardware to host the domain locally in a proper way, so i need to just relay the mail as of right now.

---

### Post by rslrdx on 2008-05-25
I guess everyone can afford to host everything in house these days...

Anyone? Anything?

---

### Post by HermanAB on 2008-05-25
Here you go: [http://www.citadel.org](http://www.citadel.org).  It is easy to install - takes about 20 minutes and it can relay to a smart host.  So you can have it up and going today.  If you get stuck, send me a private message, since I don't monitor my posts.

---

### Post by rslrdx on 2008-05-26
> **HermanAB said:**
> Here you go: [http://www.citadel.org](http://www.citadel.org).  It is easy to install - takes about 20 minutes and it can relay to a smart host.  So you can have it up and going today.  If you get stuck, send me a private message, since I don't monitor my posts.

still doesnt answer my question. I dont need a web based pim as of yet, at least not untill I get the client based access setup, and at this point, I still like to know how and if the mail can be setup to relay mail as I described. now I'll go ahead and research a little more on smart-host and also check with my hosting company, but citadel is not quite the answer I was hoping for. 

Perhaps someone can shed some light on setting up sendmail (for example) as a relay for this setup.

Dont get me wrong, just like to see some other options first, maybe citadel is the only option, but I doubt that.

I'd like to have independent hostfor each function (sort of) a calendar server, a mail server, etc. etc. as I will have other types of software conectign to it, like CRM, ERP, and Task Management, that would easy off on the process load, and it even may provide a way for me to setup functions across diferent boxes (physical servers).

this might be the first of many setups I'll be doing, so I need to check every option.

---

### Post by windependence on 2008-05-26
> **rslrdx said:**
> still doesnt answer my question. I dont need a web based pim as of yet, at least not untill I get the client based access setup, and at this point, I still like to know how and if the mail can be setup to relay mail as I described. now I'll go ahead and research a little more on smart-host and also check with my hosting company, but citadel is not quite the answer I was hoping for. 

Perhaps someone can shed some light on setting up sendmail (for example) as a relay for this setup.

Dont get me wrong, just like to see some other options first, maybe citadel is the only option, but I doubt that.

I'd like to have independent hostfor each function (sort of) a calendar server, a mail server, etc. etc. as I will have other types of software conectign to it, like CRM, ERP, and Task Management, that would easy off on the process load, and it even may provide a way for me to setup functions across diferent boxes (physical servers).

this might be the first of many setups I'll be doing, so I need to check every option.

I don't know who told you it would cost you 2K to host your own site but I have a commercial site running on a plain old 1.5 mps connection with a static IP for about $30 per month. We get about 12,000 page views per day and 5 million hots per month and we have no problems. I plan to add my own mail server soon, and several more web site for customers. 

I don't quite understand what you mean by relaying. You can get your mail from the server with a simple mail client so why would you need to "relay" it? Your domain registrar should have forwarding accounts available for free or near free. If they don't, switch your domain to GoDaddy and get it for free. That way you can forward your domain mail to your ISP which is what I think you are saying here. Still, you could host the whole thing in house and then something like Citadel or Zimbra would be great for you. I have a company right now that hosts their e-mail server on a 64K line!

-Tim

---

### Post by rslrdx on 2008-05-26
Tim, I'm not in the US. things are not so cheap arround here. (Brazil)  

I personally use aplus.net for my own hosting, even thought i should careless as far as hosting, especially when considering people downhere dont speak english, so they usually choose a local hosting company so that they can get support in a language they understand

I need to relay the mail to the hosting company mail server, which will then send it to wherever it has to go. the reason i need this setup, is that usually the hosting company does not provide conections to the calendar and contacts functionality that i need, and if i have that in house I can use it but i would need to relay the mail to the hosting company server.

Make sense?

---

### Post by bmathis on 2008-05-26
Check into Zimbra Collaboration Suite ([http://www.zimbra.com/]("http://www.zimbra.com/")). Zimbra provides the PIM functionality you need via web client or the [Zimbra Desktop]("http://www.zimbra.com/products/desktop.html") client. You can also have Zimbra send outgoing mail through a smarthost via the Zimbra configuration panel.

The system requirements for Zimbra is 2.0 GHz processor with 2GBs or RAM, but I'm running it on a 1.4GHz processor with 786MB or RAM just fine. Check it out, if you want I can send you my notes, but they are incomplete.

-B

---

### Post by rslrdx on 2008-05-26
like i said, i dont need a full webbased pim just yet, just looking for a why to send and recieve mail through a local server which will relay and recieve messages from the externally hosted mail server.

Maybe it be easier if i draw a picture...

looked at zimbra, doesnt even support mapi connections, and it looks good if I was looking for a single limited software... but here is the thing, for example, for ldap, i plan to use openldap, for mail, I plan to use something like sendmail, exim, postfix, etc, etc, Mail transfer agents only, for the calendar, some sort of calendar server, for address book (contacts) something else perhaps and so on... as far as webbased clients, i have lots of options, openwebmail, squirelmail, RoundCube webmail, etc etc, at this point that is the last thing I need to setup.

that said, I've also looked at openXchange, great looking, seems simple, but HEY, still not what I want to find out with this post, I like to know if and how I can setup a Mail Transfer Agent locally to get the messeges in the mailboxes it hosts sent over to the external mail server and also check the corresponding mail boxes on the external server and bring them to the local mailbox

Please, forget the webpim functionality for now people, think MTA, external server, internal server.

---

### Post by bmathis on 2008-05-26
if all youre looking for is to get email from an external server and relay your internal email to an external server, then look at Postfix and Fetchmail. I wont point you to a tutorial cause there are tons on the web. 

Happy hunting.

(also, Zimbra supports MAPI with a paid license/plugin and uses openldap for authentication)

---

### Post by rslrdx on 2008-05-27
Exectly the type of answer i dont need.... i asked for IF and HOW... is that so hard to understand??? oh and exactly... zimbra supports it in the PAID VERSION... but if i was going to pay for that, might as well pay for moneysoft Outlook, or even better... pay for a in house hosting capable connection... 

There are tons of tutorials... most of which ARE NOT to setup things the way i need it... so a little help finding the right one is what I was looking for here... but i guess google is still more helpfull then people... and what does ubuntu stands for again? right... google should make a distro with a name that means "Google search helping people" 

thanks anyway

---

### Post by gtdaqua on 2008-05-27
rslrdx, why wont u consider consider Zimbra? because it has web-based PIM? You could ignore this and look at other features, mate. You want your emails to be available everywhere, then you got to connect to one server all the time. Of course there are other ways but I am not going to tell you how. There are ways. Thats it. And yes of course , your problems are solvable. But I am not going to say HOW. 

We had the same problem with our offices - emails dont follow roaming users. Sales contacts/leads are not distributed/synchronized for all. With Zimbra, we sorted it out. 

from what you have written, your current setup is very poor and is not how emails shud flow in the organization. Look elsewhere for improving your architecture first. This place is for specific questions on Ubuntu - not helping people setting their networks and email architechtures. Its a whole different area.

---

### Post by rslrdx on 2008-05-27
dont even know where to begin... you just save my day.... (BS)

your post did nothing to help and apperently you read some but not all of the info... i cant change the setup due to costs, but i'll gladly change it if you are willing to pay for the change... 

my mail is available everywhere, contacts and calendar are not, thats what i want to get it working... roaming users will access the internal server only when accessing via VPN, but thats a completelly different story... 


I've said already that i plan to user ERP and CRM stuff later, and none of the open source crm and erp documentation says anything like : "And for the mail portion we are going to connect to zimbra servers, the contacts are managed by zimbra or citadel, the calendar is also controled by something else..." well.. the documentation for other softwares usually say something like "mail server" LDAP server, Ical server, etc etc... 

and of course... this is a forum where we ask HOW to do stuff, we dont come here to find out that google is better than people when it comes to getting answers... Asking How to do stuff is OK, telling how is OK, doing someone elses job is not... i'm not here looking for someone who can do the things for me, only asking for guidance on this kind of setup.

This is a support forum, where we help each other find support, you post is totally against this idea... ubuntu is a distribution that has desktops and servers, i cant see how you can separate servers from network, if you think my network is wrong, tell me what i should be doing instead of telling me to go elsewhere... telling me to go elsewhere is not UBUNTU at all... 

Roaming is just an option at this point, i only care that i get the extra functionality with my desktop clients at this point, and without mail relay the extra stuff is abit pointless dont you think?

i even asked that web based pim option to be ignored, all i got was another person not ignoring that aspect

oh well.. i guess people only tell you the right stuff if you pay for it, obviously this is not a place to find the right people.

i`m done with this post... unless someone who has the capability of understanding the concept of ubuntu, support forum, and is willign to tell HOW, and understand that telling how is not doing someone elses job, please post the helpful information. I got the wrong answers already, no need for more.

it was such a simple question, is it possible and HOW. Never asked for anyone to do my job.... go figure.

---

### Post by NateMan on 2008-05-27
Ok why don't you calm down and not take offense, that's not going to get any help. However, I believe that the confusion is coming from the posts, which are somewhat confusing. That's cool but why don't you put it all in an easy to read way? Are you trying to get mail to go from your hosted site to your home server or is it the other way around? Your not worried about the calendar, blah blah stuff at the moment correct? Please clear this up and I'm sure that people will be much more willing to help. It seems that most of the people who you attacked were just trying to help, but confused by your post. Why don't we start from the beginning and see what can be done. And always remember, people don't have to help you. You can always pay to have canonical provide you with tech support and service if you really need the help that badly and immediately. Don't knock what people are doing for free out of niceness. That's UBUNTU.(Knocking people for attempting to help and insulting their intelligence is not.)

---

### Post by rslrdx on 2008-05-27
Already writting another thread... this one has gone wrong completelly... from all parts involved, including me. if i had the money for canonical support, perhaps i could than use the same money to get a connection to host all things in house. BTW, i'm through discussing about the stuff not related to the task at hand

to clarify, i'm trying to get mail from the hosted site to may in house host as well as sending mail through the hosted site from the in house host. users will only access the in house host for mail and everythign else.

thanks.

---

### Post by NateMan on 2008-05-27
Well if that's the case sendmail should be capable of doing that. I found a guide for another distro (redhat) that should help: [http://www.akadia.com/services/sendmail_relay.html](http://www.akadia.com/services/sendmail_relay.html) You'll have to change stuff to the debian way, but it seems to be a good guide. You do have access to the hosted mail server to change its configuration too correct?

---

### Post by rslrdx on 2008-05-27
i belive that i cant do much on the hosted server besides manage users and disable smtp... its a shared hosting plan, but i might be able to talk to the hosting company depending on what the changes are...

---

### Post by NateMan on 2008-05-27
I think there is some configuration on their level. You might need to read that guide and see if it applies to your situation.

---

