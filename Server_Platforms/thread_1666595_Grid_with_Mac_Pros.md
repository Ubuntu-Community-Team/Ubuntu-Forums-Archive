---
title: "Grid with Mac Pros"
date: 2011-01-13
forum: Server Platforms
---

### Post by Lasastard on 2011-01-13
Hi,

we have recently purchased three Mac Pros with 8 cores each. One of our main interest lies in bioinformatics, including CPU-hungry, large scale data searches etc (e.g. BLAST, for those familiar with the term).

My personal platform of choice would be Ubuntu, because most programs we may encounter are generally more easily compiled under linux. However, being Macs, they come with Os X - including one OsX Server license. The latter is advertised to enable easy access to grid computing, which is an interesting option for the occasional computing problem.

My question(s):

- Which grid-computing solutions are generally recommended under Ubuntu? (links to tutorials would be appreciated)
- Does Ubuntu Server play nice with Mac Pros?
- Is it potentially possible to run the 'master' as ubuntu server and have the clients running Os X?

Cheers,
Marc

---

### Post by rubylaser on 2011-01-14
I run an OS X Xgrid farm here at work with 6 Mac Pros and two Xserves.  I've set it up with Kerberos and authenticate against Open Directory.  This works very well for us.  I'm working trying to use the Xgrid Java Agent on my Linux servers now.

[http://sourceforge.net/projects/xgridagent-java/]("http://sourceforge.net/projects/xgridagent-java/")

If you go this route, just use one of the Mac Pros with Snow Leopard server on it as the Xgrid controller.  Hope that helps.

[IMG]http://i1211.photobucket.com/albums/cc428/rubylaser/xgrid.png[/IMG]
***Note:** If you want your number of processors to show up properly you need to edit the xgrid agent plist on each agent computer.  I let it this way, so that I could easily see if all 8 of my agents are connected to the controller.

---

