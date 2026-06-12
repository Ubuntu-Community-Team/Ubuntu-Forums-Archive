---
title: "http doesn't work, https works in firefox"
date: 2010-03-21
forum: Security
---

### Post by Jonas thomas on 2010-03-21
My wife has been messing with her mothers XP laptop over the weekend which has been very bizarrely. Pages loading that shouldn't and so forth..

She's been messing around with a huge number of virus scanners, updates etc... (Personally I think she should scrub it and re-install, preferably linux, but she likes xp. :(

Anyway... I suggested that if she was hooking up her mom's computer to the network, she should disconnect her's(which she said she did.)
We have dsl hooked up to a trendnet router, with the wireless disabled.  

I've been running Karmic with no special firewalls, thinking that I wasn't at risk, left everything connected during all this.(hopefully this was not a dumb idea)

So... the wife disconnects her moms computer,  we re-connect her XP computer,    I use it a bit, no problem.  She goes on later on and firefox start doing this bizare stuff that is non-unlike what was happening to her mom's computer...

From what I can see the browser can load https addresses but won't load http.  

I'm hoping this is coincidence, and between all her tune ups hosed something up... but... I guess I should ask the question... **Is there a nasty out there that has https working but http don't.?**

I guess in all her virus scans on her computer she picked up a corrupted file, azalia.exe  which I suspect isn't a big deal.

So... I think the next logical step would be to un-install and re-install firefox on her xp computer and see if the problem goes away. (She has tons of bookmarks she doesn't want to loose so she's not to keen on that and she tried this with her mom's computer only for it to exhibit the same problems in IE)


I've been trying to talk the wife into partioning her drive and installing linux and do her surfing that way... But she remembers the month's of trouble getting device drivers(with Hardy)

So... In summary...
Window XP filefox http (doesn't work) https does. (Anyone recognize this as a nasty?)

If there is a known infected windows XP computer on the network, with Linux computers, what precautions should be taken if any for the Linux computers..

My linux computer is working great. Is there a possibility that's something is piggy backing off of my computer? 

Any suggestions on a logical next step?

Thanks,

---

### Post by cdenley on 2010-03-22
If https works but not http, then I would check the proxy settings. You probably have a http proxy configured in firefox.

---

### Post by Jonas thomas on 2010-03-22
> **cdenley said:**
> If https works but not http, then I would check the proxy settings. You probably have a http proxy configured in firefox.

I need to look at that in detail when I get home.
I sent my wife a link this morning via gmail... but I change my gmail password yesterday (I wasn't sure if her computer was comprimized and now I can't get into at work)... Hopefully.... this is not a big deal, so I can't post the link)..
Anyway...
She says that Explorer and Firefox are both experiencing the same problem. Do FireFox and Explorer look to the same spot when configuring proxy settiongs???

Also, I booked up Karmic live session... Worked great on her machine.. (I think there will be some dual booting going on in the near future)...

Some things she's tried so far (without success)
[LIST]
[*]system restore(in safe mode didn't work.

[*]Reset winsock and winsock catalog 

[*]intip reset c:\resetlog.txt

[*]check msinfo.32]
(has 14 sections instead of 10 (all have MSAFD or RSVP
[/LIST]

Supposed anti-virus stuff might cause this to happen... 
She's running:
[LIST]
[*]Avast(recently install)
[*]Advance System Care
[*]Zone Alarm (recently  installed)
[*]Ccleaner
[/LIST]

Any idea's for a next step??

---

### Post by CharlesA on 2010-03-22
Try turning off zone alarm and see what happens.

Could be blocking something or another.

---

### Post by Jonas thomas on 2010-03-22
> **CharlesA said:**
> Try turning off zone alarm and see what happens.

Could be blocking something or another.

That did the trick...
My wife is happy, ergo so am I :D

Still, I think we're going go to dual booting....
I need to research wine and see if we can run the stuff that can only run in windows on that....

Many Thanks...
JT

---

### Post by TBABill on 2010-03-22
You should be able to go into Zone Alarm and there is a tab or setting where you choose which programs have access to the Internet, and to what degree. Try going into it and enabling items that appear to be related to your problem rather than just disabling Zone Alarm. That program is a pain in the butt, but at least it tries to help by blocking access to the net for any program you don't allow access to. When it's a new install it keeps popping up every time you open a new web application, but once it knows all your programs it sorta keeps quiet. 
 
I hated using it, but it's better than not using anything. There are better options out there (check download.com for free ones) or you can certainly buy good ones.
 
Just my humble opinion considering the fears her computer gave you all recently.

Good luck!

---

### Post by CharlesA on 2010-03-22
I usually just use the firewall that is included with Windows, since I have a HW firewall on my router.

Haven't had any problems as of yet.

---

### Post by Jonas thomas on 2010-03-22
> **TBABill said:**
> You should be able to go into Zone Alarm and there is a tab or setting where you choose which programs have access to the Internet, and to what degree. Try going into it and enabling items that appear to be related to your problem rather than just disabling Zone Alarm. That program is a pain in the butt, but at least it tries to help by blocking access to the net for any program you don't allow access to. When it's a new install it keeps popping up every time you open a new web application, but once it knows all your programs it sorta keeps quiet. 
 
I hated using it, but it's better than not using anything. There are better options out there (check download.com for free ones) or you can certainly buy good ones.
 
Just my humble opinion considering the fears her computer gave you all recently.

Good luck!

Just got home... Da wife is in a much better mood. I guess she had dialed up the security settings way up on zone alarm, she's working to get it to a level she's comfortable with.. I still she should dual boot, run Linux while surfing run wine on the everyday windows stuff (assuming it will run).  Our daughter and I like to play supertuxKart.. I was hoping for a networked version.  Apparently it's not ready yet [http://supertuxkart.sourceforge.net/FAQ]("http://supertuxkart.sourceforge.net/FAQ") :(

I downloaded wine this morning and I'm going to see if I can get our windows apps to run..

---

