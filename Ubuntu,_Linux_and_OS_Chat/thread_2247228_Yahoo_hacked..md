---
title: "Yahoo hacked."
date: 2014-10-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Old_Grey_Wolf on 2014-10-06
[Yahoo Says 3 Servers Hacked Via Shellshock, No Data Taken]("http://www.businessweek.com/news/2014-10-06/yahoo-says-no-data-stolen-in-shellshock-hack").

Even my computers are patched.

---

### Post by Michael_McKenney on 2014-10-06
I would not doubt more are getting hacked.  Upgrading servers is a pain.  They can't be done during production hours.  You also need to test the patches to make sure they don't break something else.

---

### Post by lisati on 2014-10-06
Doesn't surprise me one bit. It's Yahoo.

---

### Post by Old_Grey_Wolf on 2014-10-06
> **Michael_McKenney said:**
> I would not doubt more are getting hacked.  Upgrading servers is a pain.  They can't be done during production hours.  You also need to test the patches to make sure they don't break something else.

I agree that they are probably not the only one. After working as a system admin, Linux servers can be patched during production hours; however, if it required a reboot we would wait for off hours to reboot. Windows is another story but the Bash vulnerability is *nix. We evaluated all updates and if we thought we were vulnerable we accelerated the test schedule. I noticed in the article that after being hacked they are patching the servers. It seems to me that Yahoo may not have evaluated the vulnerability of their servers very well.

---

### Post by Michael_McKenney on 2014-10-06
Yahoo has tens of thousands of servers to upgrade and reboot.  It takes months to accomplish.  You have to test and verify no harm is done in the test lab.  Get 8 layers of management to sign off, The Office Space Effect.  Then, schedule the upgrades.  My Windows Servers are updated from the WSUS (Windows Server Update Services) Server.  It does upgrades on the weekends and reboots them.

---

### Post by SeijiSensei on 2014-10-06
You have to be running a pretty insecure setup to let someone exploit Shellshock remotely.  Either you're running bash cgi-bin scripts, or you have exposed the shell to connections over SSH or telnet.  Any competent administrator would never permit either of those.  There are many better alternatives to cgi-bin, and letting random remote users connect to a shell over the Internet is insane.  That's why I didn't get very agitated about Shellshock when it was announced, though I have updated my publicly-visible servers just in case.

I've seen commentary on how Shellshock is worse than Heartbleed.  Frankly, I think that's largely bunk.

---

### Post by Irihapeti on 2014-10-07
> **Old_Grey_Wolf said:**
> [Yahoo Says 3 Servers Hacked Via Shellshock, No Data Taken]("http://www.businessweek.com/news/2014-10-06/yahoo-says-no-data-stolen-in-shellshock-hack").


Surprised, NOT. Unfortunately.

---

### Post by mastablasta on 2014-10-07
> **SeijiSensei said:**
> 
I've seen commentary on how Shellshock is worse than Heartbleed.  Frankly, I think that's largely bunk.


yeah such comments look like they are made for stocks trading purposes only...

or as click baits.

---

### Post by Old_Grey_Wolf on 2014-10-07
More to the story. [http://www.bbc.com/news/technology-29520077](http://www.bbc.com/news/technology-29520077)

---

### Post by SeijiSensei on 2014-10-07
> "After investigating the situation fully, it turns out that the servers were in fact not affected directly by Shellshock, but by a minor bug in a parsing script," said Yahoo in a statement. 

The vulnerable servers were used by Yahoo to provide live sports updates and news feeds to users.

This still gives us no idea how the vulnerability was exploited.  Did someone manipulate the feeds to trigger the bug?  Who, outside of Yahoo, would know how these feeds are handled?

---

