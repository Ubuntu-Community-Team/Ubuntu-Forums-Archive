---
title: "Network conversion: Windows to Linux, or Windows with Linux"
date: 2008-08-04
forum: Server Platforms
---

### Post by Saghaulor on 2008-08-04
This post is intended to foster ideas and hopefully solutions for my dilemma. 

**First, I'd like to explain my situation.**

I'm tired of the Microsoft way of doing things, namely, paying a fee to do every little thing that is needed, and in return getting solutions that aren't exactly what I was hoping for.

I've been using Linux at home for several years. I like Linux, and I like what Ubuntu is trying to do. Therefore, I have much interest in converting my business network into a Linux network.

**Below, I'll detail some specifics about my current solution, and its pitfalls.**

I am currently running one Windows Server 2003 Small Business. This server hosts our company exchange accounts, functions as a file and print server, hosts one proprietary medical records database/application, and as a domain server. 

The server is on its last leg for a few reasons. First, it's running out of resources, which is easily resolved. Second, it doesn't have enough CALs, which are required for every user or device connected on the domain. Without enough CALs, not all users are able to do what they need, namely, print, access network shares, etc. Lastly, the our EUs are flooded with spam. We don't really use exchange to it's potential, and we need a gateway level spam/virus solution.

I have approximately 20 client computers connected to the domain.
Most of these computers are configured very similarly, with an office suite, a web browser, similar network shares, and printers. There are a few computers that are configured slightly different, one that uses Quickbooks, and several that use the client to the medical database software. Most users use MS Word and Excel to open community maintained documents and spreadsheets. 

I have three networked printers. 

I have a Sonicwall TZ-170 firewall at my gateway.

**What I'm hoping to accopmlish.**

When I upgrade to a new server, I'd like to switch my network over to Linux for a few reasons. First, safer and more secure computing. Also, I'm hoping to leave the Microsoft licensing model in the dust. It seems criminal to me to charge EUs for the Os license, and then CALs, not to mention forcing them to go through flaming hoops for security updates. Third, I don't know if there is natively Linux medical database software that will meet our needs, so we need to run Windows based applications on the/a server, and several workstations. Finally, in the future we're hoping to change our current medical database software, and such a change will mean using solutions that allow remote access to our server with medical database, along with allowing physicians to remotely connected to our network to supervise client care. 

So, I'm not sure how or what a solution would look like. I'm guessing it would be a Linux server as the main back bone, and a 
Windows application server to run our medical records database. The clients would run Linux and either some sort of virtualization with Windows to run the medical records client software, or running a few Native Windows machines with the medical records client software. 

What I'm asking for is ideas, suggestions, and comments on my thoughts and hopes for this potential project. Questions for more details to help foster a solution are welcomed. 

Thanks for your time and effort.

---

### Post by StickyStyle on 2008-08-04
I'll start with a word of caution, please don't take offense because all I know of your skills is what is in this one post...You may be biting off more than you can chew, using linux at home is quite a bit different than being a admin.  I've seen a lot of 'linux conversion' projects fail because the person implementing it wasn't fully aware of what is involved and didn't have an available and ready third party that was well versed in the linux admin ways to help when things (and they will) go wrong (forums and IRC are no good when your boss cannot work).

Now onto the fun part ;-)
There is really so many company specific issues to take into account with a conversion, so here is a generic migration idea...

I would start with either with replacing your file server with a samba box or if your already versed in email, a front-end spam postfix spam filter sever and run with that for a while.  After that perhaps roll out a CUPS print server on the samba machine.

If you decide to start moving desktops to linux I would look into having a MS Terminal Services server to host the windows applications and not mess around with virtual machines on the clients, you would then have two OS's on each client to manage with VM's.
Perhaps also start trying people on OpenOffice, this can be a lot more work than it sounds as some people live and die day by day with excel and you will have to be ready to show them how to setup there pivot tables, graphs, etc. in Calc

A drop-in replacement for Exchange/AD is a bit of a holy grail of the linux world.  I personally couldn't speak for any of them as I have never done a replacement, and my current employer never was a MS shop so the company doesn't follow the outlook/exchange workflow thus we have come up with our own unique solutions.  Although I have been looking at Kerio as a possible future option.  
In my situation I actually use a pair of OS X servers at my LDAP/kerberos (what AD is at its core) solution since it is just a matter of installing the OS to get centralized authentication system that is easily compatible with my linux and OS X boxes.

---

### Post by windependence on 2008-08-05
I agree with Sticky here, be very careful.

That being said, I am sure there is a major medical management system written for Linux. We have a consultant here who uses it all the time for medical offices. I am not sure of this is the package but take a look at this:

[http://x-med.com/](http://x-med.com/)

More packages like that are available. Search for medical practice software Linux on google.

Also, Zimbra is a great replacement for Exchange, in fact there is even an exchange connector for it (paid license though).

-Tim

---

### Post by Saghaulor on 2008-08-05
I thank you for you word of caution.

I don't have the hubris to be a fool in thinking that my limited expertise in Linux would be enough to pull off this kind of operation.

Primarily, what I'm digging for is solutions, that I may familiarize myself with, and then put it to the scales against Microsoft. If it wins, then it's time to start looking for someone who has the skill set to pull this kind of thing off.

There were some things that I wasn't very clear about.

We use exchange, but we don't have to use exchange. As I was trying to say, we don't even fully utilize all of the features of exchange. Basically, all we use it for is email, and we're not even using that to it's fullest, namely, community address book, etc. 

In the future, I'd like to have my field staff using laptops and remote connections to our application server.

I am interested in some kind of Active Directory/ Domain solution. We have to do some logging for HIPAA which is easier to do with something like AD, something that authenticates and logs users  in.

Also, AD is rather convenient to establish access privileges. I'm sure there is something for Linux that could replace this.

So let me be clear, I don't really care about saving anything from Windows, except the industry specific (home health care) applications that will only run on Windows.

I'm not worried about ease of use, because I've tested Ubuntu on a few people, and they've used it without realizing it wasn't Windows. On top of that, it's so customizable that I could make it look like Windows if need be.

Lastly, regarding your concerns with Excel, I don't believe that there is anything going on in my office that couldn't be done just as easily in Calc, as most of our spreadsheet are actually just tables.

So, please, keep the ideas rolling. The more specific the more helpful.

---

### Post by Saghaulor on 2008-08-05
Additionally, I forgot that more and more home health care software developers are offering web based solutions, which means that we could potentially have an entirely Linux based network, I believe. 

We do use the ATT Global Network Dialer to connect to Government information systems in order to check claims and correct billing errors. That may still require Windows, or some parts of it.

---

### Post by StickyStyle on 2008-08-05
> **Saghaulor said:**
> 
We use exchange, but we don't have to use exchange. As I was trying to say, we don't even fully utilize all of the features of exchange. Basically, all we use it for is email, and we're not even using that to it's fullest, namely, community address book, etc. 

Ah, perfect.  Because once you start the crack that is outlook/exchange it's a hard one to break.  If your users are just using basic email you could try switching them to the windows based thunderbird now (or windows evolution, but i have no experience with the windows version - so i cannot advice on it) and make the transition to desktop ubuntu that much more seamless since they will be using the same tool they are used to.  Then down the road when you build yourself a SMTP+IMAP server on linux you can just repoint your clients to the new server and no one will even know you switched from exchange to a OSS solution (well, your person that handles the budget might ;) )


> **Saghaulor said:**
> 
I am interested in some kind of Active Directory/ Domain solution. We have to do some logging for HIPAA which is easier to do with something like AD, something that authenticates and logs users  in.

Also, AD is rather convenient to establish access privileges. I'm sure there is something for Linux that could replace this.

Yeah, AD at its core is just LDAP + kerberos.  The combination is quite common in the linux world for user authentication and the ubuntu-server team is working to make the installation and usage of this combination as easy as possible.
The LDAP functionality would also give your users a global address book in the mail client just like exchange.  You can have windows machine auth against this by using samba as a PDC, but I cannot speak to the technical challenges of that issue.

> **Saghaulor said:**
> 
Lastly, regarding your concerns with Excel, I don't believe that there is anything going on in my office that couldn't be done just as easily in Calc, as most of our spreadsheet are actually just tables.

Then you can also follow my advice above about ThunderBird and migrating them to windows OO.org now to make the transition easy.

---

### Post by StickyStyle on 2008-08-05
> **Saghaulor said:**
> Additionally, I forgot that more and more home health care software developers are offering web based solutions, which means that we could potentially have an entirely Linux based network, I believe. 

Providing they don't do something stupid and lazy and make the site work only with IE ](*,)

---

### Post by Saghaulor on 2008-08-05
I have been thinking more and more about this over the past few days.

I think that a thin client network might be the best solution for us, as most of our users are doing the same thing day to day. From what I understand, this would reduce security concerns, as well as maintenance labor. However, I still don't know much about it. For instance, I'm not sure how people would use individual email. I know an IMAP solution would work, but what about POP?

I'm trying to think about this as scalable solution. I don't know how well a thin client network will work when in the future I plan on having most of my field staff armed with laptops and PDAs to do in the field data entry. I'm guessing it wouldn't be too big of a problem, as the web based solution is OS independent, so the thin client core network doesn't really matter.

So if I can find a non-IE friendly web based home health care solution, I'm hoping the thin client linux network would work.

---

