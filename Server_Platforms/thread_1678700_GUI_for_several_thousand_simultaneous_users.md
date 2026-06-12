---
title: "GUI for several thousand simultaneous users"
date: 2011-01-30
forum: Server Platforms
---

### Post by Hedgehog1 on 2011-01-30
GUI for several thousand simultaneous users.

I know this post may at first seem a little out of place here when you begin to read it &#8211; but please bear with me and I think you will understand why I am seeking feedback here.

The company I work for (whose name I am withholding for now) is currently running a little over 5,000 Linux servers.  Each of these servers has a minimum of 500 users, some as many as 3,000 users on them during a business day.

These servers are serious pieces of hardware.  They have hot swappable raid arrays, redundant &#8211; well &#8211; most everything is redundant on them, frankly.

Our conversion to Linux took place about 8 years ago.  We have a proprietary database and development environment that was originally built in the 1970s.   All but the most recent applications run in this proprietary environment, whereas our newer applications are using PostgreSQL and executables that are delivered using Apache web server and run inside each users Windows Explorer session on their local PC.

Really, our situation is rather typical of any organization that has legacy software that still gets the job done &#8211; with the possible exception of the **massive** number of total users we keep up-and-running every day.

Now the reason for this post:

Network I/O is starting to become an issue of sorts for us.  Let me explain other changes going on that have helped to make this an issue.

In the past, when servers were not very powerful & Wide Area Network connections were still prohibitively expensive, we put a UNIX server (this was before our change to Linux) in every building our customers had.  Nearly all of the connections to UNIX servers were telnet from PCs or serial-ports to ASCII Terminals.  Each isolated Local Area Network had what we would consider to be 'very little traffic' by todays standards.

Of course, things are always changing.  Now the majority of our clients want the hardware to be 'out of their building and somewhere secure' as well as 'all in one system' so they can share data and roll-up sales and accounting information for the whole company at any moment in time.
This makes perfect sense.  It also makes for some challenges.

We installed over half our clients Linux servers in a Secure Data Center.  We do the back ups and some bulk updates that our clients regularly require. With all these systems so close together, we can do whole system fail-over. There are hardware nerds in the building to swap failed hard drives in raid arrays before our customer even know a disk went bad.  They can fix just about anything.

With the change from users running telnet sessions [text based UI] to running 'fat' clients on PCs with lots of network I/O, the network connections between all the buildings (often in different states) and the Secure Data Center, their network   can get overwhelmed at times.  We want excellent performance out of our systems.  So this is (at best) undesirable when it happens.

We are using the fastest WAN connections that are reasonably available.  Going any faster is cost-prohibitive.

To aggravate this Network I/O situation a little more, our next Linux servers are expected to support somewhere between 6,000-8,000 users [exact figure yet to be determined].  

You may ask &#8220;this is all very interesting &#8211; but why are you posting this here?&#8221;.

The answer goes like this: I am researching alternate ways of presenting attractive and functional GUI to users of Linux servers.  I find the Ubuntu GUI to be attractive and very functional.  I really appreciate the user input these forums get.  Finally &#8211; I am looking for points of view outside my own organization so I don't fall into the 'but we don't do it that way here' mental trap and miss a really great concept.

I have an idea about how to solve this growing challenge, and I want to present it here for your review and comments.  For those who might think &#8220;I have never worked on systems of this size; I can't imagine my opinion would be valuable&#8221; please remember this: &#8220;The Ark was built by a passionate volunteer;  The Titanic was built by paid professionals.&#8221;

So, I want a GUI from a Linux server for thousands of simultaneous users, but I also want to reduced Network I/O.

In addition, I want to avoid **requiring** bigger/faster PC for all the users.  I want a very thin client that will run on an older PC and still be just fine (Ever had to tell a customer they needed to upgrade 1,200 PCs before they can upgrade to the next software level on their current Linux server?  It is not a pleasant conversation!  A great deal of shouting happens in your ear for about 30 minutes, and then they hang up on you.)

The ultimate thin client is a text-based telnet session.  While it is very functional, it does not have the pizazz and appeal of a GUI display.  So telnet is not the main solution.

I could run X windows on the PCs.  Even a slow PC can become a decent X windows workstation (as seen by the many forum members who run Ubuntu on an outdated PC and still get great GUI performance &#8211; that old PC is running both sides of an X windows session).  Sadly, traditional X windows (even with data compression) still kills a network.  We would be worse off (network wise) if this was attempted.

I was on a business trip last year [I am not going off track, honest] and was loaned a gutless-wonder laptop for the trip (no way was I bringing my killer personal laptop!).  After it **finally** booted up in XP at the client site, I used Remote Desktop to connect to my office PC.

Once I was running remote desktop, the speed of the laptop became a non-issue.  The horsepower was on my desk at one coast, and the GUI was on the laptop on the other coast.  I was taken back by just how well it worked .

The idea of running something that is more 'remote-desktop' and less 'typical X windows' like makes sense to me.  However, the X windows look and feel of Ubuntu is rather appealing, and doing something similar for our own application still holds great appeal.

Here is my current thinking on a solution to this:

Apache Web Sever would deliver the thinnest remote-desktop-like client I am currently aware of: the NX client (offered by NoMachine).  This client is offered for MS Windows, Linux, OSX and Solaris operatng systems.  While we would not use the Solaris one at all, the MS Windows client with work for the **many** thousands of PCs already in the field, and the ability for our applications to run on iMacs and Linux workstations would a nice plus.

The NX client also appeals because it has a level of network overhead reduction that (as far as I can tell) the the best available (for now, at least).

Now each of the NX clients needs a X windows desktop session to 'remote' to.

This means that the Linux server needs to have anywhere from 500-8,000 X windows sessions running on ports 5901 and above.

These X windows sessions (I am avoiding using server & client terms with X windows as they are backwards from what most folks expect) are running on the Linux server only.  The users sees them only though the NX client, so the 'bulky & network killing X windows communication' never leaves the Linux server.  

I hope this all makes sense so far.  I would use a white board and draw indecipherable graphics for you normally, but as a kindness I have refrained (this time).

This leaves me with the question: Just how much overhead will running all these thousands of X windows sessions on the same Linux server really add?

Our systems today are running thousands of telnet sessions, plus high levels of Network I/O to feed data to the 'fat' client our applications currently use.

Will dropping the demands of the 'fat' clients and replacing them with so many local X Windows session be about a wash to the Linux server?  This I do not know. Not yet, anyway.  But with more testing I expect to be able to say for sure.

My initial testing was only with a few local X windows session on the Linux server (well, it was really a VM running Ubuntu so I could run the nice Ubuntu GUI on every session).  The first results were promising.

Have you ever tried something similar (even on a smaller scale)?  If so, what were your results? 

After reading this, do you see alternate solutions?  Holes in my thinking?  Justification for having me committed to a mental institution?

If you have a better idea, or want to suggest changes to my current idea, please speak up.  An earlier post mentioned x2go, and I will be looking at that shortly.

Now I turn this over to you dear forum readers and fellow Ubuntu fans.

---

### Post by Thirtysixway on 2011-01-30
It seems to me like you need a large-scale LTSP server.  I've never setup one, but from what I've read, the biggest issue would be RAM. You would have to have enough system resources to scale out to that many users.

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

With my inexpert opinion, it sounds like a pretty expensive server.  Or a cluster of some servers, which is probably the better way to go.  Hopefully someone with more skill in this area will respond, but what you're asking for is a big LTPS setup I think.

---

### Post by doogy2004 on 2011-01-30
Reading through your post my reaction was NX from the beginning.

You may want to check out Sun Ray

[http://www.oracle.com/us/technologies/virtualization/061984.html](http://www.oracle.com/us/technologies/virtualization/061984.html) 
[http://www.oracle.com/us/products/servers-storage/desktop-workstations/index.html](http://www.oracle.com/us/products/servers-storage/desktop-workstations/index.html)

---

### Post by Hedgehog1 on 2011-01-30
Thank you Thirtysixway; We have talked about clustered servers around the water cooler, I will check out your link.  The LSTP is new to me (here I am learning right away!)

Also, thank you doogy2004; The Sun Ray workstation looks interesting. IT costs to support PC, particularly in non office areas [warehouses and working areas] is really high.  We tried something like this for the current 'fat' client but the load was too much.  Now, for a true thin cleint, it would be great.

):P):P

---

### Post by HermanAB on 2011-01-30
Uhmm, no, the server should not run X at all and it definitely should not run thousands of X sessions.  X should be forwarded to the clients.  Also, the connection should be encrypted for security.

You could do it with simple SSH sessions or with nomachine.  For example, given a server with a Gnome desktop installed, but not actually running (running in runlevel 3) and a client wtih X installed (Linux, or Windows with Cygwin) you can do this:
$ ssh -X -C -c blowfish user@server gnome-panel

That will provide a remote Gnome panel on your client and you can then go click happy remotely.  Any program you launch from the panel will actually run on the server and X will be running on the client.

Nomachine does the same thing, but it has some impressive speed optimizations compared to simple SSH compression.

---

### Post by Hedgehog1 on 2011-01-31
The Linux Terminal Server Project (LTSP) is very much like my post.  To a large degree I am re-inventing the wheel.  This tells me that (1) the idea has merit and (2) I am not surfing the web enough!

---

### Post by Hedgehog1 on 2011-01-31
HermanAB,

I just looked at the NX drawings again.  

[IMG]http://www.nomachine.com/documents/img/getting-started/img4small.gif[/IMG]

You are right, in the NX way, the PC would be running the X session locally.

It is the nxagent that then compresses data and reduces network round trips.

Is the LTSP doing this also, or am I misunderstanding?

---

### Post by lykwydchykyn on 2011-01-31
Maybe it's just me, but I would think the overhead of all that X11 data -- nx compressed or otherwise -- is just a waste when you could be doing apps in the browser and just sending HTML data over HTTP.  Seems to me that would be an order of magnitude less traffic.

I realize browser-based apps aren't quite as appealing as desktop apps, and maybe that's not going to work for the type of software you're writing, but surely this is a better solution  (from a resource standpoint) than doing a full X11 desktop for thousands of users?

---

### Post by Thirtysixway on 2011-01-31
> **Hedgehog1 said:**
> HermanAB,

I just looked at the NX drawings again.  

[IMG]http://www.nomachine.com/documents/img/getting-started/img4small.gif[/IMG]

You are right, in the NX way, the PC would be running the X session locally.

It is the nxagent that then compresses data and reduces network round trips.

Is the LTSP doing this also, or am I misunderstanding?

I believe LTSP is more like remote desktop is on windows, or the X11 forwarding.  All the processing is done on the server, and the graphics data is sent to the client to be displayed.  So actually this may not work because you posted that it would be too much data transfer that way.

---

### Post by koenn on 2011-01-31
> **Thirtysixway said:**
> I believe LTSP is more like remote desktop is on windows, or the X11 forwarding.  All the processing is done on the server, and the graphics data is sent to the client to be displayed.  So actually this may not work because you posted that it would be too much data transfer that way.

What makes LTSP different is that it's meant for diskless clients. The video portion of it is actually pretty standard X stuff just like the other solutions discussed here. The additional stuff is a PXE boot environment, specialized init with ram drives for storage during boot, NFS for network storage during sessions, etc. 


NX also works like X, but the caching and compression make it more network-friendly. Compression is also what makes Microsoft's rdp usable over WAN links.

---

### Post by Hedgehog1 on 2011-01-31
> **koenn said:**
> What makes LTSP different is that it's meant for diskless clients. The video portion of it is actually pretty standard X stuff just like the other solutions discussed here. The additional stuff is a PXE boot environment, specialized init with ram drives for storage during boot, NFS for network storage during sessions, etc. 
 
 
NX also works like X, but the caching and compression make it more network-friendly. Compression is also what makes Microsoft's rdp usable over WAN links.
 
It is funny that everything old is new again. Many years ago, I had users PC's that booted off a floppy, connected to the network and used a virtual drive (really a directory on my Novell server for every user) to boot up Windows 3.1. These were diskless PCs (in those days, hard drives were **very** expensive). Once they booted up, the perfomance was OK (not great, but workable) and then they 'telneted' back to the mini computer.
 
Folks - this thread has been super helpful too me. Please contiune on posting! I have found new questions, and answers to earlier questions.
 
Thanks ever-so-much.):P

---

### Post by Hedgehog1 on 2011-01-31
> **lykwydchykyn said:**
> Maybe it's just me, but I would think the overhead of all that X11 data -- nx compressed or otherwise -- is just a waste when you could be doing apps in the browser and just sending HTML data over HTTP. Seems to me that would be an order of magnitude less traffic.
 
I realize browser-based apps aren't quite as appealing as desktop apps, and maybe that's not going to work for the type of software you're writing, but surely this is a better solution (from a resource standpoint) than doing a full X11 desktop for thousands of users?
 
This is what we are doing today. The 'fat' .net cleint that runs in IE has grown very large and complicated (we did not set out to build a fat cleint, it has happened over many releases). Just getting the binaries to several thousand PCs when we do an upgrade to the Linux server is a major task.
 
Right now, the network overhead of this method has slowly grown and become less and less desirable. I like the idea of X windows running on NX cleint with reduced network overhead - but in all honesty this really is a best fit for massive installs like we have. For someone running under 250 users, the browser based .net programs are just fine.
 
Sadly (or happlily), we don't have many cleints with less the 500 users.

---

### Post by koenn on 2011-01-31
> **Hedgehog1 said:**
> For someone running under 250 users, the browser based .net programs are just fine.
 
Sadly (or happlily), we don't have many cleints with less the 500 users.

dunno about that.
the current trend is to do combinations of web applications, application virtualization, desktop virtualization, ... that whole cloud thing you may have heard about. 

With the volume of servers and customers you talk about, you probably should be offering "cloud solutions" to your customers, rather than plain remote desktops. 
Have a look at eucalyptus. 


I'm getting curious as to what company you're working for.

---

### Post by tgalati4 on 2011-01-31
I'm going to guess that it is not google.  Google's chomeOS is designed to operate in the cloud, low overhead, low network latency, and designed to roll out in a massive scale.  Applications are hosted on Google's servers and just about any client that can run a browser can access the apps.  So perhaps you should design a google application, host it on their servers and maintain both your current services and new google cloud services side by side.

Of course, you have to get over the nauseous feeling of having google hold all of your data.

---

### Post by lykwydchykyn on 2011-01-31
> **Hedgehog1 said:**
> This is what we are doing today. The 'fat' .net cleint that runs in IE has grown very large and complicated (we did not set out to build a fat cleint, it has happened over many releases). Just getting the binaries to several thousand PCs when we do an upgrade to the Linux server is a major task.
 
Right now, the network overhead of this method has slowly grown and become less and less desirable. I like the idea of X windows running on NX cleint with reduced network overhead - but in all honesty this really is a best fit for massive installs like we have. For someone running under 250 users, the browser based .net programs are just fine.
 
Sadly (or happlily), we don't have many cleints with less the 500 users.

So... your "browser apps" are .net applications that are downloaded and run on the clients?  Sorry, I'm hazy on the details there.  I can see that being heavy.

---

### Post by doogy2004 on 2011-01-31
Check out NX Web Companion ([http://www.nomachine.com/products.php](http://www.nomachine.com/products.php))

It allows you run a thin NX client on remote computers.

---

### Post by ragtag on 2011-01-31
Like lykwydchykyn said earlier (nice nick btw), why not go with simple HTML, CSS and JavaScript. No need to use .net or Java or any other fat client.

You can do relatively nice GUI in a browser these days, and you wouldn't have to send updates to thousands of clients at once, as everything would be on the server side. It would also be completely cross platform, so your clients could be running pretty much any OS, even a phone OS.

I have no experience with running thousands of X sessions from one server, so I can't really help there. It sounds to me like it could potentially be terribly slow, but I don't really know. :)

---

### Post by Thirtysixway on 2011-01-31
While I'd be all for suggesting to rewrite them into web apps, it doesn't mean you can rewrite them.  Sure it's easier to manage the server if it's just a giant LAMP cluster, but there's more to it.

The biggest concern is the end user.  Think about how much time and effort it will take to train the thousands of users, and their managers, and any other support person.  It may be easier to change the server/delivery infrastructure than changing that and rewriting applications in a new language with different ways of running.  Training manuals only go so far.  It would be nice to make it stay working (close) to the same way as it has been for the last 8 years.

But I mean if it's on your list of possible solutions, take a look at it.  It's much easier to manage and scale web applications especially if you're the one coding them. It's also client independent, you could have the most basic linux system with only a webbrowser for clients to use. Or they can attend meetings and have access on their laptop or smartphone.

---

### Post by Hedgehog1 on 2011-01-31
> **lykwydchykyn said:**
> So... your "browser apps" are .net applications that are downloaded and run on the clients?  Sorry, I'm hazy on the details there.  I can see that being heavy.

Inside MS Internet Explorer, it is possible to run very large .net programs.  IE is used to get the binaries to the client, and then you can go so far as to hide the original IE browser session away and present your application as if it loaded from the local disk.

This was not the plan we were reaching for. It began as reasonably small HTML and some Java scripts to complement the telnet sessions.  Folks liked it, and kept asking for additional features.  Over time it has grown into what it is today.

I have always found the fact that we are sending windows executables to IE browsers using a Linux server to feel 'sorta wrong'.  It functions, but it seems to violate some inner 'code of conduct'.  
:lolflag:

---

### Post by Hedgehog1 on 2011-01-31
> **tgalati4 said:**
> I'm going to guess that it is not google.  Google's chomeOS is designed to operate in the cloud, low overhead, low network latency, and designed to roll out in a massive scale.  Applications are hosted on Google's servers and just about any client that can run a browser can access the apps.  So perhaps you should design a google application, host it on their servers and maintain both your current services and new google cloud services side by side.

Of course, you have to get over the nauseous feeling of having google hold all of your data.

No, I do not work for Google.  Sounds like a killer gig, though. 

The lovely cloud!  We have enough users and servers that we would overrun a cloud that did not belong to us.  Additionally, the data we store is not ours, but our clients. They have demanded complete traceability of where every system is and back-up is.

I would be exactly the same way about my data.

---

### Post by Hedgehog1 on 2011-01-31
> **doogy2004 said:**
> Check out NX Web Companion ([http://www.nomachine.com/products.php](http://www.nomachine.com/products.php))

It allows you run a thin NX client on remote computers.

I completely agree - right now this does indeed seem to be the most likely option.

Of course, if folks have other ideas, I want to be exposed to them as well.  The best ideas often come from the most unexpected places.

---

### Post by Hedgehog1 on 2011-01-31
> **koenn said:**
> dunno about that.
the current trend is to do combinations of web applications, application virtualization, desktop virtualization, ... that whole cloud thing you may have heard about. 

With the volume of servers and customers you talk about, you probably should be offering "cloud solutions" to your customers, rather than plain remote desktops. 
Have a look at eucalyptus. 


I'm getting curious as to what company you're working for.

I am starting to read up on eucalyptus, thanks!

Here is the basic diagram:

[IMG]http://www.eucalyptus.com/themes/eucalyptus/images/eee_arch.jpg[/IMG]

I believe that we would most likely go with the VMware cluster, if we did this (the lower part of the image to the right).  If I am understanding this correctly, the VMware broker hands out VMware sessions that are required as users need them.

The 'cloud' is a collection of linux servers that actually run the VMware sessions for each user.  Then each user sees the Vmware session belonging to them using something like remote desktop.

The advantages to something like this is that a 'cloud' that supports 10,000 sessions can be shared by 15,000 users when not everyone is using the 'application' all day long.

In our case, everyone does use their 'application' all business day long.  We have a shift between east coast and west coast, but during the busy part of the day we need 15,00 sessions for 15,000 users

Here is my example of where this would work great:

If I were running a call center with 3 shifts of 5,000 workers, I could have 5,000 desktops (of some kind) and 5,000 VMware sessions but 15,000 VMWare images, one for every worker.  In this situation I save needing 10,000 extra 'computers' and cubicles.  It would be a huge cost savings.

**However**, if I used this same hardware and office for 5,000 'Nine-to-Five' office workers, and the systems were unused at night, my cost savings would only be the centralized management of the 5,000 desktop 'systems'.  That has value as well, but the savings is much less.

Am I understanding this correctly?

---

### Post by Hedgehog1 on 2011-01-31
> **ragtag said:**
> Like lykwydchykyn said earlier (nice nick btw), <snip>

I have no experience with running thousands of X sessions from one server, so I can't really help there. It sounds to me like it could potentially be terribly slow, but I don't really know. :)

I also have no experience running so many X sessions.  Keeping it from running slow is a real concern for me, too.

I find myself thinking of a hybrid cloud idea.  I will call it a 'Fog' just for fun.  In 'Fog' computing instead of VMware Linux servers that run windows sessions, those same servers could run many more X sessions that the users see via a remote desktop.

Wait I minute - I think I have gone full circle.

Let me find a white board somewhere...  I hate it when I end up where I started...

---

### Post by Hedgehog1 on 2011-01-31
> **Thirtysixway said:**
> While I'd be all for suggesting to rewrite them into web apps, it doesn't mean you can rewrite them.  Sure it's easier to manage the server if it's just a giant LAMP cluster, but there's more to it.

The biggest concern is the end user.  Think about how much time and effort it will take to train the thousands of users, and their managers, and any other support person.  It may be easier to change the server/delivery infrastructure than changing that and rewriting applications in a new language with different ways of running.  Training manuals only go so far.  It would be nice to make it stay working (close) to the same way as it has been for the last 8 years.

But I mean if it's on your list of possible solutions, take a look at it.  It's much easier to manage and scale web applications especially if you're the one coding them. It's also client independent, you could have the most basic linux system with only a webbrowser for clients to use. Or they can attend meetings and have access on their laptop or smartphone.

The cost of retraining end users to use a vastly changed application is, indeed, very high.  This is made worse by the fact that our users count every key stoke and mouse click it takes to do there data entry.

We have a (small) war about why the 'heads down data entry' folks prefer the simple *but very fast* telnet sessions.  They never leave the keyboard to click a mouse.  Many users typed so fast the older servers took a while to catch up with them at times.

Also, the nature of our data entry is very complex, and requires constant checking with the database to make sure the data is right as soon as possible during the data entry session.

If I made them press 'save' and then tell them the fields that are wrong and force them to re-key that late in the process, they would hurt me (not kidding, they would!).

Ahh, the joys of a system first built in the 1970s.  Some users want change, others don't.  OK - now this time I did get off subject, sorry.

---

### Post by psusi on 2011-01-31
I once worked for a large company that ended up doing something similar to what you are considering.  It was for the company internal payroll and accounting program, which was written as an Oracle Forms application.  It was found that it generated much less network traffic to run the client on a citrix server and remote desktop in than to run it directly.

This told me that the original Oracle Forms application was a horrible pig of a beast to begin with, that generated FAR more network traffic than it should have.

The web app that you have now is the ideal solution.  If it is written poorly, you might see gains going to a terminal server, but if it is written right, then you won't.  You want to be careful that the server sends the minimum amount of data that the client needs, and all that can be cached is.

For instance, most of a typical web page is formatting and the dynamic part pulled from the database is only a small part.  Factor the formatting out into a stylesheet and that will only be downloaded by the client once and cached, then you only need to send the result of the database query to the client and let it add all of the formatting.  If the client requests a bunch of data then processes it down to a smaller amount that makes it to the screen, then move that processing to the server.  Another big source of latency is recursion.  If the client ends up having to make one request, then based on the results of that, another, and another, then the latency of the connection can really add up.  Make sure that your design allows one user request to translate to only one request to the server.

If you optimize the web app then it will give you the best performance, and cause the least disturbance to your customers since they need no new software.  Of course, you might find some benefit in the terminal solution that uses far less of your time, then you will have to decide how much your time is worth.

---

### Post by Hedgehog1 on 2011-01-31
> **psusi said:**
> I once worked for a large company that ended up doing something similar to what you are considering.  It was for the company internal payroll and accounting program, which was written as an Oracle Forms application.  It was found that it generated much less network traffic to run the client on a citrix server and remote desktop in than to run it directly.

This told me that the original Oracle Forms application was a horrible pig of a beast to begin with, that generated FAR more network traffic than it should have.

The web app that you have now is the ideal solution.  If it is written poorly, you might see gains going to a terminal server, but if it is written right, then you won't.  You want to be careful that the server sends the minimum amount of data that the client needs, and all that can be cached is.

For instance, most of a typical web page is formatting and the dynamic part pulled from the database is only a small part.  Factor the formatting out into a stylesheet and that will only be downloaded by the client once and cached, then you only need to send the result of the database query to the client and let it add all of the formatting.  If the client requests a bunch of data then processes it down to a smaller amount that makes it to the screen, then move that processing to the server.  Another big source of latency is recursion.  If the client ends up having to make one request, then based on the results of that, another, and another, then the latency of the connection can really add up.  Make sure that your design allows one user request to translate to only one request to the server.

If you optimize the web app then it will give you the best performance, and cause the least disturbance to your customers since they need no new software.  Of course, you might find some benefit in the terminal solution that uses far less of your time, then you will have to decide how much your time is worth.

psusi - Thank you or your real world experience.

Do you recall from the 'internal payroll and accounting program', were the users centralized (one building/one campus) or separated by distance and needed WANs?  I guess I am wondering if the slower WANS made the conversion to Citrx server worth the effort, or if the network overhead reduction was still worthwhile on a local network?  Of course, depending on how long ago it was, the network speed may have been 10 or 100 megabits rather than the  giga bit speed we run on local networks now.  If the local network was 10 mega bits, then I would guess a savings over the LAN as well.
 
Optimizing the current web application is an ongoing effort.  However, any speed we gain is promptly lost by adding more features into it.

We are also quite guilty about doing recursive lookups.  We imitated the telent sessions that do this. Telnet does it without any real penalty; 'fat' client web apps pay a high price.

We do have one large customer that is running Citrix server and smaller desktop 'appliances' [I had forgot about them - thanks for the reminder].  They modify our install process for the 'PCs' to make it work.  I think I will ask for permission to contact them (engineers are not allowed to contact customers without a note from their boss).

We have a larger issue in that the web applcation still does only about 5% of what the telent version does.  To grow it to do the other 95% means it could become too unwieldy [network wise].

You have given me much to think about - thanks!

---

### Post by Thirtysixway on 2011-02-01
I know at Meijer, we use citrix to open remote applications to look up information and check timeclock data. I'm not a manager so I wouldn't know how extensively they use it or the network setup. Citrix seems to be a solution for some.  Meijer is a chain of grocery stores, so they do have a large network. Not sure if they host local servers or if it's all on one big WAN, though.

---

### Post by HermanAB on 2011-02-01
Note that whatever you do, if you need to run 'thousands of X servers', then you are doing it wrong.

---

### Post by spynappels on 2011-02-01
I work for an Electronic Medical Records company, and we would have many clients accessing the same system at any one time, from a variety of different locations, both through LAN and WAN links. 

The only way we can provide the same experience, no matter where the user is or what platform they are using, (think Windows XP through 7, Mac OSX, the odd Linux client and iPhone/iPad) is by going web browser based. 

We use HTML, Java, PHP and MySQL, but the end user has a fully functional GUI to enter and access the data, through a standard web browser. We use HTTPS to access the server from any client, so it is secure in transit, and bandwidth friendly. A decent server can easily serve thousands of Web requests referencing a back-end database, and with decent styling, it can be made to look almost identical to legacy GUIs. HTML5 is also looking like a very useful addition to the arsenal here.

If this is looked at carefully, you might find that retraining costs are low if the initial design is done carefully, as the end-user experience will not change very much. In any case, as lykwydchycken said, it will scale much better and be more platform independent.

You're not in the insurance business are you by any chance?

---

### Post by psusi on 2011-02-01
> **Hedgehog1 said:**
> 
Do you recall from the 'internal payroll and accounting program', were the users centralized (one building/one campus) or separated by distance and needed WANs?  I guess I am wondering if the slower WANS made the conversion to Citrx server worth the effort, or if the network overhead reduction was still worthwhile on a local network?  Of course, depending on how long ago it was, the network speed may have been 10 or 100 megabits rather than the  giga bit speed we run on local networks now.  If the local network was 10 mega bits, then I would guess a savings over the LAN as well.

Our campus had 3 buildings, one of which housed the data center.  Most of the network was 100mbps with trunked gigabit fiber backbone links.  We had several remote offices that saw the most gains from the citrix migration.  This tells me that the application was indeed making recursive calls where the latency really mattered, so moving it to the server eliminated that problem.  Local clients also saw some benefit, though not much.  It did lighten the load on the local network segments though, which tells me that the application was sending a lot more data back and forth than it needed to.
 
> **Hedgehog1 said:**
> We are also quite guilty about doing recursive lookups.  We imitated the telent sessions that do this. Telnet does it without any real penalty; 'fat' client web apps pay a high price.

When you are looking at the code you should be thinking to yourself "does the telnet client have this data sent to it?".  If the answer is no, then the web client doesn't need it either.  If you need to do recursive lookups, the telnet client does not do that; the server does, then just feeds the results to the client.  Make the web app behave the same way.  Push that complex work to the server and let it boil it down to just the part the client needs to see and send only that.

---

### Post by doogy2004 on 2011-02-01
Check out Feng Office [http://www.fengoffice.com](http://www.fengoffice.com) (previously OpenGoo).

---

### Post by Hedgehog1 on 2011-02-01
> **spynappels said:**
> 
 
You're not in the insurance business are you by any chance?
 

 
spynappels - No we don't do insurance. And we are not Google. :KS
 
I don't mean to torment anyone - honest - but I am being rather cautious about sharing any more info other than purely techincal details that any group of engineers would talk about when they meet up.

---

### Post by Hedgehog1 on 2011-02-01
> **HermanAB said:**
> Note that whatever you do, if you need to run 'thousands of X servers', then you are doing it wrong.
 
Herman,
 
Assuming that (1) the X 'servers' are running one on each PC (2) we have thousands of PCs and (3) we use NX for compression - would that feel more comfortable to you?
 
This still seems a prefectly reasonble possibility to me (assuming the network traffic can really be kept down to a decent level). 
 
The what-iffing with the cloud idea where the instead of windows VMs we ran Linux VMs using X windows felt like a fair trade oof we had to go with a cloud.  I fear for the complexity of running a cloud of the size we  would need. 
 
But it is important to me that I am open to any ideas shared.  I am tryng to be an idea sponge...

---

### Post by Hedgehog1 on 2011-02-01
> **psusi said:**
> Our campus had 3 buildings, one of which housed the data center. Most of the network was 100mbps with trunked gigabit fiber backbone links. We had several remote offices that saw the most gains from the citrix migration. This tells me that the application was indeed making recursive calls where the latency really mattered, so moving it to the server eliminated that problem. Local clients also saw some benefit, though not much. It did lighten the load on the local network segments though, which tells me that the application was sending a lot more data back and forth than it needed to.
 
 
 
When you are looking at the code you should be thinking to yourself "does the telnet client have this data sent to it?". If the answer is no, then the web client doesn't need it either. If you need to do recursive lookups, the telnet client does not do that; the server does, then just feeds the results to the client. Make the web app behave the same way. Push that complex work to the server and let it boil it down to just the part the client needs to see and send only that.
 
psusi - thanks again fior the additional data. I am pleased you remembered the network speed from back then! 
 
The need to do lookups in the middle of the UI is an emotional issue for many here. We have yet to find a compromise that we can all live with.

---

### Post by Hedgehog1 on 2011-02-01
> **doogy2004 said:**
> Check out Feng Office [http://www.fengoffice.com](http://www.fengoffice.com) (previously OpenGoo).
 
I was just looking at this link (thanks doogy2004).  This is a pretty slick product/service.
 
Their 'Feng Sky' product runs from their servers and offers a full ser of 'office' and email support.  it appears to be all web based.  Since it supports IO, Safari and Opera, it look like the a 'HTML, Java, PHP' sort of solution.
 
Very nicely done...  Gotta think about this a bit..

---

### Post by doogy2004 on 2011-02-03
You may want to check out eyeOS as well - [http://www.eyeos.org/](http://www.eyeos.org/)

---

### Post by Hedgehog1 on 2011-02-05
> **doogy2004 said:**
> You may want to check out eyeOS as well - [http://www.eyeos.org/](http://www.eyeos.org/)

More interesting reading - thanks very much doogy2004.

:KS

---

