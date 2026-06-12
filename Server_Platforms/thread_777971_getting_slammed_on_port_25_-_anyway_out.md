---
title: "getting slammed on port 25 - anyway out ?"
date: 2008-05-01
forum: Server Platforms
---

### Post by neill on 2008-05-01
hi

i've started running a mail server in a DMZ. it's an out of the box solution (axigen) running on ubuntu server 7.10

for a brief period i had a configuration issue - my bad :( - and an open relay

i noticed something was wrong becuse the Rx/Tx lights on my router were going bonkers with no PCs running (except the mailserver)

so i checked the activity graphs on the firewall and there was a massive spike in traffic into and out of the DMZ where the mailserver resides

i ran a few tests and corrected the config so i am no longer an open relay (i now pass the tests at abuse.net and mailradar.com for example)

interestingly i think there was an open relay for about 8-12 hours but the graphs only show activity spikes starting at a specific time this evening - presumably the point at which the relay was 'discovered'

anyway ... 

despite having closed the relay i'm still getting multiple, multiple connections being made to my port 25 from servers all over the world (malaysia and brazil figure prominently in my whois lookups)with odd port numbers and, although nothing is coming of these connections as the mailserver drops them, the hits alone are causing bandwidth issues

has anyone any ideas how i might mitigate this ?

thanks as always

/neill

:confused:

---

### Post by ginjabunny on 2008-05-01
I don't know much about this but in a way it sounds like denial of service attack but you are probably just getting pounded by spammers trying to use your now closed smtp relay. I just searched for "ubuntu server how to stop dos attacks"
this came up top of the pile  [http://zedomax.com/blog/2007/11/06/diy-server-hack-howto-fightstop-dosdenial-of-service-attacks-using-open-source-code-ddos-deflate/](http://zedomax.com/blog/2007/11/06/diy-server-hack-howto-fightstop-dosdenial-of-service-attacks-using-open-source-code-ddos-deflate/)
might be helpful??

---

### Post by pbhj on 2008-05-01
> **neill said:**
> i've started running a mail server in a DMZ. it's an out of the box solution (axigen) running on ubuntu server 7.10

Who are you serving with your mail server. Can you do a restriction by netblock, or maybe move it to a different port and get the users to change their port settings?

They may not be making the connection but you'll be carrying out transactions with them. On what basis are you disallowing connections? Presumably just password, you have to try and find an easier one.

Could you look for multiple failed connections by IP and drop connections from those locations at your external router?

FWIW, just a few thoughts.

---

### Post by neill on 2008-05-02
thanks

i'll look into the anti-DDOS stuff - that seems quite interesting in its own right

at the moment the mailserver makes the connections then drops them because of the closed relay, but as you say that consumes bandwidth

what i will probably do is drop all connections to port 25 at the outside edge of the router unless they come from my ISP and see if that helps

interestingly since i closed the relay yesterday evening, traffic and hits have dwindled somewhat overnight

/neill

---

### Post by MJN on 2008-05-02
> **neill said:**
> what i will probably do is drop all connections to port 25 at the outside edge of the router unless they come from my ISP and see if that helps
 
If you do that you're not going to get any mail (incoming mail would not normally be coming via your ISP mail server).
 
Just ride it out - the connections are not a DOS attack hence you cannot mitigate them with anti-DOS tactics. They are 'genuine' connections to a service you previously offered and so you'll just have to stick it out until the machines realise you no longer offer the service.
 
The bandwidth consumed should not be too large in the greate scheme of things as presumably you are denying access in the SMTP stage in response to an off-net RCPT TO addresses, and hence you're not accepting their DATA. I suppose it depends on how many concurrent connections you're getting - have you measured this (even loosely)?
 
Mathew

---

### Post by neill on 2008-05-02
thanks MJN - that really does through some light on the problem

:)

principally it explains why, once i closed off the relay but did nothing much else, the connections dropped off overnight

i *am *able to count the simultaneous connections through my firewall heading to DMZ on port 25 and i guess at a peak last night we're looking at 30 or so 'established' connections but that's a guess/recollection

as for the ISP - they host my 2 domains and as far as i understand it they forward all mail destined for those domains, along with all my standard emails sent to me at my ISP address, to my fixed IP via SMTP from their servers

i am assuming that if you send me a mail, [email]me@neillsdomain.co.uk[/email], then it arrives at my IP *via *my ISP (certainly if you do [www.neillsdomain.co.uk](www.neillsdomain.co.uk) you get redirected to a webspace page splashed with my ISP logo)

i'm in the process of taking it up with then and i'll feedback

another suggestion i've heard - swap to SMTPS on port 465 and close off 25 altogether

i'm not convinced that won't simply lead to banging down 465 instead !!

/neill

---

### Post by MJN on 2008-05-02
neillsdomain.co.uk doesn't exist so I have no means of confirming how your mail gets delivered.

How you describe it could be right. It's not the 'normal' way of doing things, but still valid.

Depending on how you really are running this you could change the port, but only really if you are only using your mail server as a means for clients to send mail out, and this agreement you have with your ISP. However, I would not use port 465 as its use has largely fallen out of favour - use the standard submission port of 587.

Again though, it all depends on how you are running this setup and without the true domain it's difficult to comment.

Mathew

---

### Post by neill on 2008-05-03
hi matthew

it's moved on a bit now

as you quite rightly pointed out, not only has the traffic dwindled completely now i'm no longer an open relay, but my ISP also pointed out that i get my mail from all and every mail server, not just their's given that the MX records point to my IP !

spot on advice there - kudos  :cool:

given that the traffic is now more or less a non-issue i'll leave the status quo for the time being, and at least i've learned something valuable about how this all works

thanks

/neill

---

### Post by MJN on 2008-05-03
That's excellent - good to hear.

---

