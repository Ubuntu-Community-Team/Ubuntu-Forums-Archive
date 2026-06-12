---
title: "Question about servers"
date: 2007-03-30
forum: Server Platforms
---

### Post by loserboy on 2007-03-30
My family is expanding our business, we are going to have 8-10 employees that need access to their own computer and within 2 years 20-30 employees that need access.

We will manufacture generators,  most of the computers will just be used for seeing inventory via SaaS or tracking out in and out shipments, thats sort of thing. My 1st thought is just get each person a desktop with ubuntu, because I can maintain them myself and really 10 computers isnt that many, also we don't have an IT pro, I'm as close as it gets (not very close).

but someone told me that we could get a single decent server, and just have access points at each office and that it would be fairly easy to maintain and cost effective. 

Is that possible?  I can hold my own when it comes to desktops, but I don't know anything about server hardware. what runs the video for each terminal? what are these terminals called? 

I really have to find a solution, so any help would be great, thanks

mike

---

### Post by Scunizi on 2007-03-30
It really depends on how you want to give access to the emps..  If they are running a full machine (harddrive etc), the server will not drive their video since each machine will be tied to the card that is installed in it.  Another solution, still using the server idea, is to use a CMR program that is web based.  There are a couple out there that are opensource, handle inventory, notes, customer support questions, followups, shipped date, billed, received etc.  The two that come to mind are SugarCRM.com and vTiger.com.  Sugar also has enterprise level support if you're willing to pay for it.  vTiger is, or was, an offshoot from SugarCRM.  There are others but they don't come to mind at the moment.  If you want to do a search, use something like "opensource CRM" as the arguement.

---

### Post by PilotJLR on 2007-03-30
By "access point," it sounds like you are referring to thin clients.

These basically create remote desktop sessions to a server. It works best for limited use desktops... personally, I would use ordinary PC's and keep databases / files / etc on a server with a disk array and regular backups.

---

### Post by loserboy on 2007-03-31
thanks for the response

although I would rather just give each employee their own Pc i have to find out if its feasable to use the server/thin client idea.

with that setup does each person just access via a virtual machine or what

and do you think it would be difficult for someone like me to maintain that has fair general knowledge but knows very little about about thin clients.

like i said I agree with you but what are the main disadvantages about this setup?


scunizi,
would the CMR program be installed locally or would it be a service hosted by a company that i can access kind of like "Software as a Service" thing, sorry for all the questions, this is just above my head, and I wanna make sure I learn what I can from you guys before I start doing in depth research. also even with this setup it looks like I still ahev to decide how to give everyone access be it thin clients or regular PCs

---

### Post by emid on 2007-03-31
CRM software such as SugarCRM would probably be installed on a server in your office.  Each desktop client would then access it through a web browser.  You could however have it installed  remotely.  In terms of thin client vs. desktop, it depends on what these stations are used for.  It is probably easier to just use some low cost commodity desktops.   If all these stations are basically doing the same thing, you can setup one and just clone it for all the other stations.  The more homogeneous your setup, the less work in maintaining them and potential for conflicts.  As mentioned above, if you do have the CRM stuff on a server in your location, you will need to make sure that regular backups are implemented as well as some kind of redundancy on the server itself (RAID etc.).

---

### Post by loserboy on 2007-04-03
ok.... well i'm learning alot

I may have made a wrong statement when I said what kind of software I need, because really I need alot more. I took a look at SugarCRM and I don't think it's gonna cover it all. I'm looking for something more like inventory control software such as this one I just found [Accvision]("http://www.accvision.com/product.htm") or [CISS]("http://www.cissltd.com/inventory_pro.asp"), but of course these only run on windows.

again sorry to have lead you off the wrong way, but I wasn't really sure what type of software I was looking for.

---

