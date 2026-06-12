---
title: "Tor security problem: exit node redirecting traffic/spoofing?"
date: 2006-09-29
forum: Server Platforms
---

### Post by sktx on 2006-09-29
[FONT=Courier New][SIZE=3]First, a little bit of backstory--- 
[I]
I first looked into Tor as a way to more securely run an eggdrop bot from my local machine, instead of having to buy a shell and having to connect to a remote machine to tinker with plugins and configuration files.  My reasoning behind this was that an eggdrop attracts the ire of every little script kiddie who wants to mess with the channel, the channel in question was regularly attracting fairly hefty dronebot attacks, and I'd rather not waste my bandwidth getting packeted by some buttmonkey with a huge botnet of compromised Windows boxen on dsl/cable connections. Or worse, a competent cracker with a huge botnet of compromised boxen running miscellaneous OSes on fat pipes. 

I came to find out after I installed Tor that the irc network that my friend's channel is on has blocked Tor users, but decided to keep it anyway to try out after I'd found out about the hidden services, the interesting pages that people had put up on them, and the fact that, to a remote observer, my connection appears to be coming from a different country, and a different one every few minutes at that.  The novelty of the latter was enough, to me, to keep Tor around for a while.
[/I] 
Ok, backstory done.  On to the problem.

I noticed a little oddity today when, using Tor and Privoxy, I was connecting to an ubuntuforums member's blog (chickengirl.net) that I'd read an article off of yesterday.  I connected and read one page, but when I'd clicked on a link to another posting, I was redirected to a page similar to those generated en masse to catch clicks by pretending to be a page that contains the information for which you were searching (if you don't know what I'm talking about, an example of this sort can be found at [http://www.1howtotieabowtie80.info/index.html](http://www.1howtotieabowtie80.info/index.html))

I then disabled Tor, went back, and clicked the link again, and it sent me to the right page.  Next, I went to the Tor wiki at [http://wiki.noreply.org/](http://wiki.noreply.org/) and clicked on the link to test Tor via the page at [http://serifos.eecs.harvard.edu/cgi-bin/ipaddr.pl?tor=1](http://serifos.eecs.harvard.edu/cgi-bin/ipaddr.pl?tor=1) 

I also checked via [http://www.showmyip.com/](http://www.showmyip.com/) and it confirmed the result.

[/SIZE][/FONT][FONT=Courier New]> [/FONT]
**You are (probably) NOT using Tor.**

  You connected to this site from **83.227.89.154**, hostname **c-9a59e353.471-1-64736c10.cust.bredbandsbolaget.se**, which is NOT a valid Tor exit node.  If you are attempting to use a Tor client, please refer to the [Tor website]("http://tor.eff.org/") and specifically the [instructions for configuring your Tor client]("http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#ItDoesntWork").  If this is not the IP address from which you appear to connect when you disable your HTTP proxy, then it may be that the particular Tor node selected by your Tor client is multi-homed.
[FONT=Courier New][/FONT][FONT=Courier New][SIZE=3]I understand that it might possibly mean that the exit node is multi-homed, and I'm guessing (haven't read into it) that it means that the node distributes its traffic over a group to lessen the impact on any one machine and increase the throughput.  *Is this a correct assumption?*


I reloaded the page at [serifos.eecs.harvard.edu]("http://serifos.eecs.harvard.edu/cgi-bin/ipaddr.pl?tor=1")  and it returned this:[/SIZE][/FONT]
[FONT=Courier New]> [/FONT]
**You seem to be using Tor!**

  You connected to this site from **140.247.62.119**, which is a valid [Tor]("http://tor.eff.org/") exit node named **serifos**. Congratulations!
[FONT=Courier New][/FONT]
[SIZE=3]
[/SIZE][FONT=Courier New][SIZE=3]However, [showmyip.com]("http://ubuntuforums.org/showmyip.com") returned a different result when reloaded it as well.  

I reloaded the blog I was reading, and recieved a different page (another fake directory-page).  I then disabled Tor, reloaded, and got the real blog. 

I re-enabled Tor a few minutes ago and got another result.[/SIZE][/FONT]

[FONT=Courier New]_**> **_[/FONT]
**You are (probably) NOT using Tor.**

  You connected to this site from **204.13.236.244**, hostname , which is NOT a valid Tor exit node.  If you are attempting to use a Tor client, please refer to the [Tor website]("http://tor.eff.org/") and specifically the [instructions for configuring your Tor client]("http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#ItDoesntWork").  If this is not the IP address from which you appear to connect when you disable your HTTP proxy, then it may be that the particular Tor node selected by your Tor client is multi-homed.
[U]
[/U]
[SIZE=3]
[/SIZE][FONT=Courier New][SIZE=3]Which, when I reloaded, showed me the same "You're using Tor, exit node serifos, everything is peachy keen" page from before.

Last result, just 2 minutes ago, the [/SIZE][/FONT][FONT=Courier New][SIZE=3][serifos.eecs.harvard.edu]("http://serifos.eecs.harvard.edu/cgi-bin/ipaddr.pl?tor=1") Tor tester showed my IP as 140.247.62.119, which is the same result it's been showing on every reload, for the whole time I've been writing this post. 

The weirdness in this comes from [http://ipid.shat.net/](http://ipid.shat.net/) showing my IP as[/SIZE][/FONT][SIZE=3] 85.25.141.60 ([/SIZE][FONT=Verdana, Arial][SIZE=3][FONT=Courier New]echo931.server4you.de), different from the harvard.edu response.


The blog page I was reading is working fine now, but does anybody know what caused all this weirdness to go down? Is there any chance it could be a bad/malicious exit node? And are there any precautions or steps I should take in using Tor+Privoxy that I might not know about?


..*sktx*[/FONT] [/SIZE][/FONT]**[FONT=Verdana, Arial][SIZE=7][COLOR=#ff0000][/COLOR][/SIZE][/FONT]**

---

