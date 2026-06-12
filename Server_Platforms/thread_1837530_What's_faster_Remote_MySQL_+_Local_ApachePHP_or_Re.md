---
title: "What's faster? Remote MySQL + Local Apache/PHP or Remote MySQL + Remote Apache/PHP?"
date: 2011-09-01
forum: Server Platforms
---

### Post by JoeSabido on 2011-09-01
Hi there,

This is a bit of a question regarding architecture, something I'm not at all good at, so to most of you it will be quite basic. I'm going to try to describe the situation as good as possible, so be patient.

The company I work for, has a central building and several branches connected using OpenVPN over the Internet. Each of these branches have a local server ("branch server") which acts as a server to the computers of that branch and at the same time acts as a client to the main server ("VPN server").

There's an application that runs locally on these branches, which uses MySQL as its DB engine.

Now management wants me to develop a web application that will run on the main server, and will be accessible to Users that will be connected to the VPN.

This application should retrieve information that is stored on the branch servers, manipulate it, format it and display it to the Users.

My question, as the title says, is quite simple.

What would be faster (query times, HTML rendering times)? And what would take less resources over the overall network?

Option 1
--------
1) MAINSERVER is running Apache/PHP
2) User logins to MAINSERVER (Where the Web Application is running)
3) MAINSERVER connects to BRANCHSERVER's MySQL and retrieves the requested data
4) MAINSERVER formats the data and displays through Apache/PHP

Option 2
--------
1) MAINSERVER is only used as the VPN Server
2) BRANCHSERVERS are running AMP
3) A copy of the Web Application is running on each of the BRANCHSERVERS
4) Users login to BRANCHSERVER and do their thing (see reports, graphs and whatnot)

I've made a crude graphic, they say an image says more than 1K words.

Thanks!

---

### Post by DPJB on 2011-09-02
Not an exact answer to your question, but why not install the app(s) on the mainserver. If the HTML output is not too big and the VPN connections are of reasonable speed, this should work fine. It also saves you from setting up and maintaining multiple (L)AMP installations.

---

### Post by 11notes on 2011-09-02
like this?

---

### Post by JoeSabido on 2011-09-02
DPBJ:

That would be my first option, which is why I labeled that setup "Option #1", but I'm wondering if there are any speed gains using "Option #2".

11notes:

I'm not sure that would work in this case. The branches need to see each other, so they all need to be connected to the VPN server.

---

### Post by SeijiSensei on 2011-09-02
Raw speed is only one of the criteria I'd use to determine the best strategy.

You didn't give us any indication of the types of loads this application would need to support.  If we're talking about hundreds or thousands of transactions per hour, then speed is obviously very relevant.  If we're talking about an application that managers use a few times a day or less, speed is much less relevant.

Personally I'd stick with the central application/dispersed databases model.  First, any bug fixes, updates, etc., need be made in only one place.  The other model requires distributing the updates across all the branches each time.  With a single centralized application, you can be sure that any problems users have is limited to the central installation, and that any fix for one of the branches will fix them all.

If your connections are reasonably high-speed, I don't think transaction times are going to matter much at all.  How about mocking up a simple test and doing some timings?

On the other hand, centralizing the application creates a single point of failure.  So another criterion might be whether the branches can do their work if their connection(s) to the main server are broken.  How reliable has your VPN network been?  If outages aren't really an issue, that strengthens the argument for a centralized application.  You might consider, though, what happens if the central server goes down.  Do you have a hot spare waiting in the wings?  Perhaps you use replication?  Reliability might matter more than performance.

---

### Post by snek on 2011-09-02
The usual setup I have worked with would suggest using a single database server with multiple webservers which are mirrored. User connects to loadbalancer which determines which webserver to use and sessions are stored in the database so it doesn't matter which webserver you are connected to.. Of course you would want the database server on a direct connection to the webservers for optimal speed.

In general your webservers also don't need as much in terms of ram as compared to the db server.

I don't really see the point in running the webservers remote, unless you count using a loadbalancer as such..

---

### Post by JoeSabido on 2011-09-02
SeijiSensei:

Databases on BRANCHSERVERS are around 100mb each. Management would use the Web Application to generate reports 2 - 5 times a day, but the reports can be quite big. Some of the reports call for complex queries that return up to 500 rows and take a few seconds to return results.

The VPN has been reliable so far, on each of the BRANCHSERVERS the downlink is 4mb, but the uplink is only 512k, the downlink on MAINSERVER is 6mb, and there are 15 branches.

If I go with Option 1 then yes, I would have a mirror server on standby in case the first one goes down or when maintenance is required. I still need to look into that.

As for Option 2, maintenance or updates of the Web Application could be addressed by maintaining the latest version on the MAINSERVER and scheduling a CRON that points to a PHP script on the BRANCHSERVER which would FTP into MAINSERVER to download the latest updates once a week.

Now, I've made a quick test and it seems I have answered my own question. 

The thing that bugs me about Option 1, is that for large queries, MAINSERVER apparently has to wait until the query results finish arriving before they can be manipulated by PHP.

With Option 1, after the user clicks "Generate Report", the browser "hangs" for several seconds while MAINSERVER performs the query remotely on BRANCHSERVER, plus the time it takes for those results to arrive, and THEN it starts rendering the HTML.

With Option 2, the HTML starts rendering a lot sooner, although HTML itself takes a little longer to render because BRANCHSERVERS are less powerful than MAINSERVER.

*sigh* I guess now my dilemma is to either add complexity and gain performance or keep the complexity level and clog the network when management starts asking for those reports from all branches at the same time.

---

### Post by SeijiSensei on 2011-09-02
> **JoeSabido said:**
> Databases on BRANCHSERVERS are around 100mb each. Management would use the Web Application to generate reports 2 - 5 times a day, but the reports can be quite big. Some of the reports call for complex queries that return up to 500 rows and take a few seconds to return results.

100 MB is pretty small actually.  Do you have indexes developed to match the queries you run routinely?  I don't use MySQL (I use Postgres), but is there are way to run a query analyzer for the standard queries in your reports?  You might find adding a few indexes will make things run a lot faster.

Is there a reason why the branches need to maintain separate databases and servers?  Might it not be faster to consolidate all the data on a single, high-performance server that runs both MySQL and the PHP application(s) and treat the branches as clients?

---

### Post by JoeSabido on 2011-09-03
SeijiSensei:

Thanks, I appreciate it.

When we were going to implement the software, we made tests with a central database and the performance does suffer. The software is used as a Point Of Sale and they need it to be very responsive (retail stores), and even though queries would be greatly optimized by indexes, the time it takes data to travel from MAINSERVER to BRANCHSERVER would be the same.

There are up to 8 clients inside each branch, plus, even though the VPN link is stable, sometimes it goes down. It doesn't happen very often, but it is a requirement (from the bosses) that if the DSL link goes bad, the branch can work stand-alone until the link is re-established.

Certainly a centralized DB server would reduce complexity and increase performance, but the whole thing would depend greatly on the only thing outside our control (the DSL links from the ISP), and I don't even want to think what would happen if the DSL link of MAINSERVER went down for several hours, it would be total madness :(

---

