---
title: "Rejecting certain stacks of ips from spam?"
date: 2007-04-13
forum: Server Platforms
---

### Post by mickbuntu on 2007-04-13
Hello,

I need some help regarding postfix rejections ability. I am trying to reject a certain sets of ips. What would I need to change in the line below.  I am a visual learner so like to see.  Thanks a bunch in advance. Oh and it just got wrapped here in nano it is one line.

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination, reject 121.128.0.0-121.191.255.255, reject_61.216.0.0-61.223.255.255


Been  trying google but no go so did my homework really. Searched here no help either so turn to community.

P.S:  The stack is large as problems here seem to come from that region.  Spammers seem to  be shifting their tactics.

---

### Post by MJN on 2007-04-14
What about genuine mail from within those netblocks? Seems like a dangerous strategy to me...

Anyway, it's your server so if you must then create a file (say, /etc/postfix/access) with the lists of IPs you want to ban (see [http://www.postfix.org/access.5.html](http://www.postfix.org/access.5.html) for further details) e.g.

```

# Ban 10.1.2/24
10.1.2 REJECT

```Then convert this raw text file into an indexed file using **sudo postmap /etc/postfix/access**.

Then reference this indexed (.db) file in your postfix config with:

```

smtpd_recipient_restrictions =
   permit_sasl_authenticated
   permit_mynetworks
   reject _unauth_destination
   check_client_access hash:/etc/postfix/access
   .
   .
   .

```Restart Postfix and you'll be done.

But do note the warning that the banning of such large netblocks as proposed will almost certainly lose you legitmate mail (and don't fall into the trap of 'I dont know anyone in China hence why do I want to accept mail from there' because you don't know where other companies/organisations have got their servers residing).

May I suggest instead looking into Realtime BlackLists (RBL's) as they (mostly) attempt to pinpoint spamming IPs but individually rather than tarring whole netblocks.

Mathew

---

### Post by mickbuntu on 2007-04-14
[SIZE="3"] Mathew,

Thanks


I see your concern on the level of breaking email exchange at large.  My problem is not with the Chinese people. It so happens that they own that stack and I am starting to get flooded.  I have Chinese friends both in Toronto and  various other parts of the world. Who are of Asian origin  they do not come to  me in separation.   Nor Black people, I had those type of friends too.  My point I am trying to make is that I have nothing towards people that look different. We are all made out of the same dough in the end.


My problem is rather with the  large amount of bulk that comes within that area "stack."    Currently my business  is not based overseas. My  Asian / European "insert here" friends / contacts. They all use my private email address to speak to me. Also instant messenger so do not have their issues.   Perhaps spammers are shifting operations their as some other Countries are getting tougher. By actually  jailing  spammers and taking possessions away.    Now  their large circus  is  becoming based in Asia and actually South Africa.    What  found other day is instead of blocking access to a Country. I could  actually  just make  postfix talk to a known spam database. Honestly, I do not know postfix yet that much to do that. Nor do I want to right now  try to do anything out of the ordinary. By potentionally  trying  that option above and  accidently  leaving an open hole.  


As I learn more the open source postfix client. Or, my mental abilities could master the command line of it.  I might just stick to postfix  but   so far been very frustrated. I learn by "seeing" very visual. Not by lots of text.

Anyhow,

I'll see what I can and can not do what are my limitations when it comes to  postfix. I am running a  Business and  currently can not afford to make large changes.

:popcorn: [/SIZE]

---

### Post by MJN on 2007-04-14
> **mickbuntu said:**
> [SIZE=2] Mathew,
[/SIZE]
[SIZE=2] Thanks

I see your concern on the level of breaking email exchange at large.  My problem is not with the Chinese people. It so happens that they own that stack and I am starting to get flooded.  I have Chinese friends both in Toronto and  various other parts of the world. Who are of Asian origin  they do not come to  me in separation.   Nor Black people, I had those type of friends too.  My point I am trying to make is that I have nothing towards people that look different. We are all made out of the same dough in the end.[/SIZE][SIZE=2]
You misunderstand my point. I was not for one moment saying you were racist, or anything similar. This is a technical discussion. Period. I was merely pointing out that the location of the mail servers for your genuine contacts could be almost anywhere (China was an example - feel free to insert a random country of your choice), if not geographically then topologically across the whole IPv4 address range.

> What  found other day is instead of blocking access to a Country. That'd be virtually impossible anyway, not to mention risky as far as false positives are concerned. IP allocations have on the whole not been made geographically. Even where they have at the top-level the lower-levels are very much allocated all over the place.

> I could  actually  just make  postfix talk to a known spam database.That'd be your best approach. No point reinventing the wheel as you'd never be able to keep up with manually populating IP blacklists. Let the distributed systems out there already doing it do it.

 Mathew[/SIZE]

---

### Post by mickbuntu on 2007-04-14
> **MJN said:**
> [SIZE=2]
You misunderstand my point. I was not for one moment saying you were racist, or anything similar. This is a technical discussion. Period. I was merely pointing out that the location of the mail servers for your genuine contacts could be almost anywhere (China was an example - feel free to insert a random country of your choice), if not geographically then topologically across the whole IPv4 address range. 

 Good to know  then that I was not misunderstood on my intentions :-) Did not take any offense just having trouble comprehending  text  sometimes.

> **MJN said:**
> 

That'd be virtually impossible anyway, not to mention risky as far as false positives are concerned. IP allocations have on the whole not been made geographically. Even where they have at the top-level the lower-levels are very much allocated all over the place.


You probably  heading  on the path towards forged ips.

> **MJN said:**
> 
That'd be your best approach. No point reinventing the wheel as you'd never be able to keep up with manually populating IP blacklists. Let the distributed systems out there already doing it do it.

 Mathew[/SIZE]


I will just  keep  postfix then talking to all ips  and for now just ignore   the initial handshake logs. They are just  initial handshakes without authorizations.  As  long as postfix does not allow the email to be sent.   But once  get hang / "if"  will implement  then the above. Of postfix speaking to known databases of spammers.   The whole reason of  me wanting to stop spammers evening helo. Is it  is just access better to cut off the spammer before even  postfix  gets busy with first sentences  with them. See what trying to say?   So this is a  good idea to make postfix :

Hi     <  -spammer

Postfix  < --- one sec looking up the database  if  your a known human.

postfix  < --- spammer  conenction closed.


What ppostfix does now is  still allow  the spammer to initally carry a  conversation with the program.

---

