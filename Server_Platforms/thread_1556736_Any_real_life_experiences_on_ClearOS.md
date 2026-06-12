---
title: "Any real life experiences on ClearOS?"
date: 2010-08-19
forum: Server Platforms
---

### Post by SteveHillier on 2010-08-19
Has anyone out there really used ClearOS in a production environment?
Clearfoundation of course will make the product look good and my initial foray makes it worth spending more time on.
We currently support a number of clients on Win 2003 server domains and - OK it has it's quirks but it generally does OK with Windows clients.
One client we installed Win 2008 SBS - and I don't want to have to do that again.  It suffers from all the bad things in Vista and such things as group policies take a lot more to configure than in 2003.
Our clients don't know how to maintain their server box so it will make little difference to them if the box were something like ClearOS (I haven't yet looked at e-box and smeserver) as long as the client side functionality is effectively the same.
The cost of the Windows product is ridiculous especially if you have to add extra CALs.
So I ask in this forum if anyone out there can give real life critiques of ClearOS?
Many thanks
Steve

---

### Post by daveloper on 2010-08-20
I used to work at a company that was named the #1 MSP by the VARguy and we used this for clients that were sub-25 users all the time. Because of the simple interface, we were able to accomplish most helpdesk tasks (95%) on Clarkconnect/ClearOS on tier 1. We even delegated the web interface controls to the helpdesk without giving the tier 1 guys root access.

After using these systems for a year on new and returning clients (we replaced SBS in some cases) we performed end user satisfaction surveys (NPS: Net Promoter Score) and to our surprise the clients using Clarkconnect were happier by a significant amount than clients on SBS or Windows2003 server. You can contact Aaron Bylund on the ClearFoundation site and he can put you in direct contact with other vendors/VARs/MSPs using ClearOS.

ClearOS works well as a server for clients running Windows 7, MacOSX, and Ubuntu.

I was so pleased with how well it worked that I joined their team.

---

### Post by SteveHillier on 2010-08-20
Daveloper,
Many thanks for that endorsement.
I shall set up a full testbed.
Steve

---

### Post by SteveHillier on 2010-08-29
> **daveloper said:**
> ClearOS works well as a server for clients running Windows 7, MacOSX, and Ubuntu.
Daveloper, can I explore this last bit with you.

I have now set up a working ClearOS 5.2 system and have been able to configure it in a way that would replicate our own Win 2003 server.  I have also got a Win XP client working and have logged on with a number of users and can get the logon scripts working OK.

The next task I want to achieve is getting an Ubuntu client to talk to the ClearOS server

In th epast for my purposes only I have mapped samba links to Win server based directories and have mounted them automatically on logon, but this would not work properly if the Ubuntu client was used by a number of different users.

Any clues appreciated.

Steve

---

### Post by daveloper on 2010-08-30
So, you are able to mount the shares properly but you need multi-user support for the client Ubuntu workstation?

ie. You can do this ok from Ubuntu to the ClearOS domain server:

mount -t cifs -o user=username,password=secretpassword //server_address/share_name /mnt/test

updated 31 Aug 2010

---

### Post by daveloper on 2010-09-01
@SteveHillier I've put together a [howto]("http://www.clearfoundation.com/docs/howtos/add_linux_workstation_to_the_samba_domain") for you and the rest of the community. Most of this is just my experiences setting up Ubuntu workstation on a ClearOS domain and it definitely needs some real world testing. I've also included some thoughts for the [script you mention]("http://www.clearfoundation.com/docs/howtos/add_linux_workstation_to_the_samba_domain#add_home_directory"). 

I'm still exploring the best place to put the script so that it is called on boot or connection. Overall, if you use the gvfs in Ubuntu to your advantage, it can save you a lot of headache by mounting the shares on a per-user basis. Moreover, the users can cache their connection passwords on their key-chain very similar to the way Mac OSX works.

Ubuntu has done a great job of making their user interface flexible in this manner. Most people don't realize that the samba tools on their linux server can be used as clients and not just servers. You can use a product like Likewise Open, but there is not need. If there is enough support and demand for it, I'd be interested in helping craft tools to 'automate' this configuration, perhaps through a script.
[]("http://www.clearfoundation.com/docs/howtos/add_linux_workstation_to_the_samba_domain#add_home_directory")

---

### Post by SteveHillier on 2010-09-01
David,
Thank you for the email.
You have now found me on two fora!  Help!  No hiding from you now!!

Thank you for the trouble of putting together the Howto.  It looks to be just the sort of thing I needed.

I cannot try this out just at the moment.  A couple of reasons.

1.  I was using a computer that I had put up for sale on Ebay - it had been up for a few weeks and I was about to withdraw it from sale but someone has bought it!!  So I now have to find a new machine to set this up on but I think I am ready for a production build.
2.  I am taking a week off from Friday - the first in 3 years so I will not get back on to it until I return.

I will inform back of the forum when I have tried it all out.

Once again, many thanks

Steve

Depending on which forum you read first this might look familiar!

---

