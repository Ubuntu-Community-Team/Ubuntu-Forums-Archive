---
title: "Clueless regarding a local mail server."
date: 2008-01-19
forum: Server Platforms
---

### Post by Dr. Strange on 2008-01-19
Hello, all;

I have a little problem that could use a nudge in the right direction.

I have a home network with a small server running Dapper in a stock LAMP configuration plus ddclient / DynDNS, Samba, OpenSSH, and Webmin. At the moment, it's essentially a fancy fileshare with a static IP in the network's local 192.168.0.x C-class, and the DynDNS setup isn't doing much of anything (yet). Everything works fantastically well - Ubuntu for the win. What I'd like to do is extend the server a bit for a specific e-mail function.

It's not uncommon for me to be out of town for days or weeks at a time. And, like most of us, I have multiple e-mail accounts - accounts that have a nasty tendency to fill up and start bouncing messages if they're not checked semi-frequently. Doing this on-the-road isn't really feasible - I have my workstation's Thunderbird installation set up with its Profile directory on the server's fileshare, allowing me to archive all my communications transparently, but only if the mail passes through this specific workstation. I've typically resolved this problem by leaving my workstation online whether I'm home or not, so that Thunderbird can download my mail every few minutes, thus keeping the mailboxes from filling and not breaking my archival scheme. Not really an optimal solution - I'd much prefer to be able to turn all my machines off when I'm away, and leave only my server running.

So, in essence, what I'd like to do is set up my server to download e-mail on a regular schedule (say, once every ten minutes) from about a half-dozen mailboxes scattered about the world, to an equal number of 'local' mailboxes on the server, which Thunderbird can then use as if they were the original mailboxes on the 'remote' servers.

Pointing Thunderbird at a different server should, to my mind, be trivial. However, I haven't the faintest idea how to make the server-side of this work. Is there a relatively painless way to pull this off?

Thanks.

---

### Post by HermanAB on 2008-01-19
Well, you could configure Tbird with multiple accounts and let it download your mail, but running a proper mail server is much more fun:   
[http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

Cheers,

Herman

---

### Post by kitterma on 2008-01-19
Fetchmail is the pretty standard solution to this problem.

---

### Post by HermanAB on 2008-01-19
Sure fetchmail is nice and simple, but if you are going to feed the data to Tbird anyway, then you can just as well define multiple accounts inside Tbird and let it handle it.

The overly complicate Super Geek solution is Citadel, which has a fetchmail feature built in, amongst a zoo of other niceties.

Cheers,

H.

---

### Post by Dr. Strange on 2008-01-21
Thanks for the suggestions.

I've looked over Citadel and... well, it's sort of a tactical nuke where I just need to clear a stump. It looks like a fine system, but I simply have no need for anything that elaborate.

Anyone know where I can find some documentation along the lines of "fetchmail for Total Server N00bs"? My initial Google-frenzy turned up lots of information, most of which was quite over my head.

Thanks!

---

### Post by Dr. Strange on 2008-02-26
After looking over the available options, I'm re-thinking my original opinion - it *does* sound like Citadel is the least-painful solution to my original problem... and then some.

What I'm thinking now is to have Citadel's fetchmail process grab all my POP3 mail from my various accounts, then serve it back out as IMAP for me to access.

Since I'm now looking at implementing a groupware server as opposed to some sort of e-mail drop-box setup, I had the thought of using IMAP on the Citadel side. This makes my mail archiving scheme entirely obsolete, since IMAP stores everything server-side anyway. Added bonus: if I'm reading things right, I can access my server from any internet connection in the world (say, from my laptop while I'm at a convention or some such), provided the mobile client machine I've got in-hand is configured properly (right login info, IMAP-compliant client software with the right settings, etc). In this mode, since the server is handling all the storage and so on (as opposed to the POP3 mode of "download everything received, and save everything sent, to the local system, using the server as a communications path only") accessing my e-mail from a laptop in some random hotel would be functionally no different (in terms of being able to send, receive, and have everything sent and received archived on the server) than accessing it from my workstation on my home LAN. 

Another bonus: if I'm reading this right, it seems that Citadel does calendaring and contacts storage/sharing and that setting up Thunderbird/Lightning to work with it is fairly trivial. Being able to get to my contacts and calendar from anywhere on the planet would be a big win.

As far as I can tell, Citadel is happy doing pretty much everything I want out-of-the-box, and there's some fairly good (read: "aimed at a n00bish target audience") documentation on the official site. So that's the direction I'm leaning in - using Citadel and either Thunderbird/Lightning or Evolution to do what MS Exchange and MS Outlook are theoretically supposed to do, in a manner that doesn't come with Microsoft's typical associated price-tag and general overall suck.


A few questions / potential gotchas:

1. Am I in fact reading the documentation right (I'd like to ask before I start modifying my server - just in case I'm thinking wrongly here) in that Citadel:
a) can fetch mail from multiple arbitrary POP3 boxes, 

b) can then serve that mail back out via IMAP while keeping each original account's mail separate (separate folders, preferably), 

c) allow this IMAP set can be accessed from any machine from anywhere provided login information and a suitably-configured client (my preferred options are Thunderbird/Lightning or Evolution), 

d) store all incoming and outgoing e-mail in a unified set of directories on the server, regardless of which machine (home workstation, mobile laptop, whatever) is talking to the IMAP server, 

e) store all contact info and calendar(s) on the server and allow them to be viewed/modified regardless of which machine is talking to the server,

f) import existing Thunderbird profiles (importing my existing e-mail storage files are absolutely essential, other stuff like configurations and preferences would be nice but not vital) in a relatively reliable and simple manner?


2. I don't have a FQDN... not a real one, anyway - the server in question is talking to the world by way of a free DynDNS account (which works as far as Apache is concerned - the port-forwarding and DNS seem happy). How much of an impact will this likely have on Citadel's ability to... well, do everything in Question 1, assuming that I have administrative access to the LAN's router,  can forward ports arbitrarily, and have administrative access to the DynDNS account?


3. Proving that nothing is ever easy, my current LAN setup doesn't like the DynDNS domain name. For example, pointing Firefox to the domain name from outside the LAN works great, but from *inside* the LAN doesn't work - the server is presently only capable of talking to the local computers via IP address. I suspect that this has something to do with what nameservers my behind-the-LAN machines are using - something is simply preventing the DynDNS domain from resolving right. Thoughts on fixing / working around this without breaking my current domain-name resolution (which works perfectly well save for this one hassle)? Or would it be simpler / even possible to leave the DNS as-is, point my workstation (which is always behind the LAN) to the Citadel server's IP address, and leave the DynDNS stuff there for accessing the server from elsewhere in the world?


Many thanks for your continued advice, and for putting up with my general lack of clue - this is my first attempt at building a server more complicated than SSH-and-Samba. :)

---

### Post by igknighted on 2008-02-26
Forward to Gmail where you get (currently) 6.4gb of space.  I haven't deleted an email in years and am only using 2%.  Way easier and more reliable then trying to set it up from your home.  Not to mention, you can use gmail to send mail from any email account too.

---

### Post by HermanAB on 2008-02-26
Citadel can do pretty much anything at all.  The zero setup option is to install VMware on a server and then use the preconfigured Citadel VMware image available on the Vmware web site.

The Gmail option is also a very good solution for a single user.

---

