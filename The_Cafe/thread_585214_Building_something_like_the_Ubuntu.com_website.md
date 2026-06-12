---
title: "Building something like the Ubuntu.com website"
date: 2007-10-21
forum: The Cafe
---

### Post by argux on 2007-10-21
Hi, does anybody know what software the ubuntu.com website uses?

I have a project that could use a similar design to that one, and I don't want to reinvent the wheel if I can avoid it.

The project was actually inspired on how knowledge is created (or found) in the ubuntu community. 

[LIST]
[*]Somebody has a problem and posts in the forums
[*]People brainstorm ideas, the original poster tries those ideas and eventually find a solution (or not, but it's documented that at some point in time, a group of people tried and couldn't find a solution to X)
[*]Whatever the outcome, if there's enough interest, somebody will post the information in the wiki
[*]Another person runs into the same problem, googles, finds the wiki and the information on what to do (or that there's no solution and he might try a different approach or give up, in any case, he would save some time).
[*]Profit!
[/LIST]

My project is very similar, but instead of only Ubuntu-related problems, the problems discussed would be about everyday stuff. Like, How do I get rid of an ant invasion at home? or What can I do with my organic waste? or What can I feed my cat instead of processed food?

And the process would be the same. Post a question in the forums, gather knowledge from people around the world, find one or several "best anwsers", and post them to the wiki. That's it.

Since this was inspired by the Ubuntu community, I suppose a website layout similar to the Ubuntu main page would be good: A main page explaining what the thing's about, and linking  to the forum and the wiki. Hence the question, what software does the Ubuntu web site use?

I have tried TikiWiki, and I don't really like it. I think the design isn't very easy to understand. The menus are a mess, and the result is downright ugly. Is there any other software that can keep Tiki's promise of being a CMS complete with wiki and forums. 

I don't have a problem in using different software for the web page, the forums and the wiki, but I'd like to know if there's a combination already proven to be easy to integrate and administer.

What I'm considering right now is:
-Joomla
-Some lightweight wiki (is MediaWiki too heavy?)
-PhpBB

So, ok, those were like many questions, but still, can anybody spare some advice?

---

### Post by Abandon on 2007-10-21
I alway's thought Ubuntu.com was made with Drupal. So why don't you give a try?

---

### Post by LanDan on 2007-10-21
ubuntu.com is not the same as launchpad and the forums
it is 3 different things.
and launchpad is owned by canonical so no open source

---

### Post by argux on 2007-10-21
Yes, I know ubuntuforums is a different thing, and that the software is closed source. I was thinking that phpBB has all the functionality I need, so that's covered, unless somebody has a better suggestion.

I don't have a need for something like launchpad (that I can see), so that's no problem actually. 

I'll check Drupal, and see if I like it better than Joomla for what I want to do. I'm still open to suggestions, though. I want to listen to what people recommend. Thanks.

---

### Post by RAV TUX on 2007-10-21
> **argux said:**
> Hi, does anybody know what software the ubuntu.com website uses?

I have a project that could use a similar design to that one, and I don't want to reinvent the wheel if I can avoid it.

The project was actually inspired on how knowledge is created (or found) in the ubuntu community.[LIST]
[*]Somebody has a problem and posts in the forums
[*]People brainstorm ideas, the original poster tries those ideas and eventually find a solution (or not, but it's documented that at some point in time, a group of people tried and couldn't find a solution to X)
[*]Whatever the outcome, if there's enough interest, somebody will post the information in the wiki
[*]Another person runs into the same problem, googles, finds the wiki and the information on what to do (or that there's no solution and he might try a different approach or give up, in any case, he would save some time).
[*]Profit![/LIST]My project is very similar, but instead of only Ubuntu-related problems, the problems discussed would be about everyday stuff. Like, How do I get rid of an ant invasion at home? or What can I do with my organic waste? or What can I feed my cat instead of processed food?

And the process would be the same. Post a question in the forums, gather knowledge from people around the world, find one or several "best anwsers", and post them to the wiki. That's it.

Since this was inspired by the Ubuntu community, I suppose a website layout similar to the Ubuntu main page would be good: A main page explaining what the thing's about, and linking  to the forum and the wiki. Hence the question, what software does the Ubuntu web site use?

I have tried TikiWiki, and I don't really like it. I think the design isn't very easy to understand. The menus are a mess, and the result is downright ugly. Is there any other software that can keep Tiki's promise of being a CMS complete with wiki and forums. 

I don't have a problem in using different software for the web page, the forums and the wiki, but I'd like to know if there's a combination already proven to be easy to integrate and administer.

What I'm considering right now is:
-Joomla
-Some lightweight wiki (is MediaWiki too heavy?)
-PhpBB

So, ok, those were like many questions, but still, can anybody spare some advice?

[ MoinMoinWiki]("http://moinmoin.wikiwikiweb.de/") is the software used (or at least it used to be used by Debian, Ubuntu and Fedora)
> **Other sites using the MoinMoin wiki engine**

   This site:
   [FCKeditor wiki]("http://wiki.fckeditor.net/")
   [JuraWiki (de)]("http://www.jurawiki.de/")
   [LinuxWiki (de)]("http://www.linuxwiki.de/")
   [OpenOffice.org Wiki (de)]("http://www.ooowiki.de/")
     On other sites:
   [Apache]("http://wiki.apache.org/") 
    [Fedora]("http://fedoraproject.org/wiki/")
   [Ubuntu]("http://help.ubuntu.com/community/") 
    [Mercurial]("http://www.selenic.com/mercurial/") 
    [Debian]("http://wiki.debian.org/")
   [CAcert.org]("http://www.cacert.org/")
   [Kernel Newbies]("http://kernelnewbies.org/")
   [Xen]("http://wiki.xensource.com/xenwiki/FrontPage")
[http://moinmoin.wikiwikiweb.de/](http://moinmoin.wikiwikiweb.de/)


Drupal is first class also and it is what I choose to use(see sig link) it is also used by Mepis.

---

### Post by RAV TUX on 2007-10-21
> **RAV TUX said:**
> [ MoinMoinWiki]("http://moinmoin.wikiwikiweb.de/") is the software used (or at least it used to be used by Ubuntu and Fedora)

Drupal is first class also and it is what I choose to use(see sig link) it is also used by Mepis.

Here are some MoinMoinWiki's


> **A selection of MoinMoin-sites with notable custom layout**
[LIST]
[*][Fedora project wiki]("http://fedoraproject.org/wiki/")
[*][EdubuntuWiki]("https://wiki.edubuntu.org/EdubuntuWiki")
[*][eXe Project wiki]("http://exelearning.org/")
[*][lagses.berkeley.edu]("http://lagses.berkeley.edu/") Latino Association of Graduate Students in Engineering and Science
[*][Opie]("http://opie.handhelds.org/cgi-bin/moin.cgi/") Open Palmtop Integrated Enviroment Applications and libraries for mobile devices
[*][Abi2oo4]("http://www.abi2oo4.de/") - Abiturientia 2004 des Einstein-Gymnasiums, Rheda-WD
[*][C-Base wiki]("http://www.c-base.info/") - a crewcommunication wiki for the crashed spacestation c-base
[*][DAVISWiki]("http://daviswiki.org/") - community wiki for Davis, California
[*][official Python Info Wiki]("http://wiki.python.org/moin/FrontPage")
[*][UbuntuUsers Wiki]("http://wiki.ubuntuusers.de/")[LIST]
[*]Similar, but english: [The official Ubuntu wiki]("https://wiki.ubuntu.com/FrontPage")[/LIST] 
[*][Visualisation Group of the Delft University of Technology]("http://visualisation.tudelft.nl/")
[*][Croatian Mountaneering Association]("http://plsavez.hr/hps")
[*][Mobbing-Gegner]("http://wiki.mobbing-gegner.de/")
[*][SIP Solutions]("http://sipsolutions.net/") - navigation is fully customisable from within wiki and can be localised
[*][Sprungbrett Firmenkontaktmesse]("http://sprungbrett.tu-clausthal.de/") - variation on the SIP Solutions theme with the same advantages and per-category coloring
[*][http://linuxwireless.org]("http://linuxwireless.org/")
[*][Bazaar - distributed version control software]("http://bazaar-vcs.org/")
[*][Skype Developer Zone wiki]("https://developer.skype.com/")
[*][http://ict.viaisn.nl/Menu_hack](http://ict.viaisn.nl/Menu_hack) - using left menu hack like [http://www.ffii.org]("http://www.ffii.org/") and [http://kernelnewbies.org/](http://kernelnewbies.org/)
[*][SQI-Inc]("http://sqi-inc.com/") - macro formating extensions, DocBook integration, PDF macro and Lucene search engine integration[/LIST]**In English language**
[LIST]
[*]this wiki [IMG]http://static.wikiwikiweb.de/moin_static157/modern/img/smile.png[/IMG]
[*][Alberg Wiki]("http://www.alberg30.org/collaborate/")
[*][Anansi-Wiki]("http://wiki.anansi-web.com/")
[*][Apache Wiki Farm]("http://wiki.apache.org/") - featuring 48 wikis![LIST]
[*][Ant wiki]("http://wiki.apache.org/ant/FrontPage") about the [Ant]("http://ant.apache.org/") project
[*][APR wiki]("http://wiki.apache.org/apr/FrontPage") about the [APR]("http://apr.apache.org/") project
[*][Avalon wiki]("http://wiki.apache.org/avalon/FrontPage") about the [Avalon]("http://avalon.apache.org/") project
[*][Cocoon wiki]("http://wiki.apache.org/cocoon/FrontPage") about the [Cocoon]("http://cocoon.apache.org/") project
[*][Lenya wiki]("http://wiki.apache.org/cocoon-lenya/FrontPage") about the [Lenya]("http://cocoon.apache.org/lenya/") project
[*][DB wiki]("http://wiki.apache.org/db/FrontPage") about the [DB]("http://db.apache.org/") project[LIST]
[*][DB-Commons wiki]("http://wiki.apache.org/db-commons/FrontPage") about the [DB Commons]("http://db.apache.org/commons/") project
[*][OJB wiki]("http://wiki.apache.org/db-ojb/FrontPage") about the [OJB]("http://db.apache.org/ojb/") project
[*][Torque wiki]("http://wiki.apache.org/db-torque/FrontPage") about the [Torque]("http://db.apache.org/torque/") project[/LIST] 
[*][Excalibur wiki]("http://wiki.apache.org/excalibur/FrontPage") about the [Excalibur]("http://excalibur.apache.org/") project
[*][Jakarta wiki]("http://wiki.apache.org/jakarta/FrontPage") about the [Jakarta]("http://jakarta.apache.org/") project[LIST]
[*][Cactus wiki]("http://wiki.apache.org/jakarta-cactus/FrontPage") about the [Cactus]("http://jakarta.apache.org/cactus") project
[*][HiveMind wiki]("http://wiki.apache.org/jakarta-hivemind/FrontPage") about the [Hivemind]("http://jakarta.apache.org/hivemind/") project
[*][JMeter wiki]("http://wiki.apache.org/jakarta-jmeter/FrontPage") about the [JMeter]("http://jakarta.apache.org/jmeter") project
[*][Slide wiki]("http://wiki.apache.org/jakarta-slide/FrontPage") about the [Slide]("http://jakarta.apache.org/slide/") project
[*][Taglibs wiki]("http://wiki.apache.org/jakarta-taglibs/FrontPage") about the [Taglibs]("http://jakarta.apache.org/taglibs") project
[*][Tapestry wiki]("http://wiki.apache.org/jakarta-tapestry/FrontPage") about the [Tapestry]("http://jakarta.apache.org/tapestry/FrontPage") project
[*][Turbine wiki]("http://wiki.apache.org/jakarta-turbine/FrontPage") about the [Turbine]("http://jakarta.apache.org/turbine/") project
[*][Tomcat wiki]("http://wiki.apache.org/jakarta-tomcat/FrontPage") about the [Tomcat]("http://jakarta.apache.org/tomcat") project
[*][Velocity wiki]("http://wiki.apache.org/jakarta-velocity/FrontPage") about the [Velocity]("http://jakarta.apache.org/velocity") project
[*][Commons wiki]("http://wiki.apache.org/jakarta-commons/FrontPage") about the [Commons]("http://jakarta.apache.org/commons") project[/LIST] 
[*][Gump wiki]("http://wiki.apache.org/gump/FrontPage") about the [Gump]("http://gump.apache.org/") project
[*][Geronimo wiki]("http://wiki.apache.org/geronimo/FrontPage") about the [Geronimo]("http://geronimo.apache.org/") project
[*][Incubator wiki]("http://wiki.apache.org/incubator/FrontPage") about the [Incubator]("http://incubator.apache.org/") project[LIST]
[*][Beehive wiki]("http://wiki.apache.org/beehive/FrontPage") about the [Beehive]("http://incubator.apache.org/beehive") project
[*][Depot wiki]("http://wiki.apache.org/incubator/Depot") about the [Depot]("http://incubator.apache.org/Depot") project
[*][Directory wiki]("http://wiki.apache.org/directory/FrontPage") about the [Directory]("http://incubator.apache.org/directory/") project
[*][iBATIS wiki]("http://wiki.apache.org/ibatis/FrontPage") about the [iBATIS]("http://incubator.apache.org/ibatis/site/") project
[*][Jackrabbit wiki]("http://wiki.apache.org/jackrabbit/FrontPage") about the [Jackrabbit]("http://incubator.apache.org/jackrabbit/") project
[*][XMLBeans wiki]("http://wiki.apache.org/xmlbeans/FrontPage") about the [XMLBeans]("http://xml.apache.org/xmlbeans/") project[/LIST] 
[*][James wiki]("http://wiki.apache.org/james/FrontPage") about the [James]("http://james.apache.org/") project
[*][Logging wiki]("http://wiki.apache.org/logging/FrontPage") about the [Logging]("http://logging.apache.org/") project[LIST]
[*][Log4J wiki]("http://wiki.apache.org/logging-log4j/FrontPage") about the [Log4J]("http://logging.apache.org/log4j") project[/LIST] 
[*][Lucene wiki]("http://wiki.apache.org/jakarta-lucene/FrontPage") about the [Lucene]("http://lucene.apache.org/") project
[*][Maven wiki]("http://wiki.codehaus.org/maven") about the [Maven]("http://maven.apache.org/") project
[*][Portals wiki]("http://wiki.apache.org/portals/FrontPage") about the [Portals]("http://portals.apache.org/") project
[*][SpamAssassin wiki]("http://wiki.apache.org/spamassassin/FrontPage") about the [SpamAssassin]("http://spamassassin.org/") project
[*][Struts wiki]("http://wiki.apache.org/struts/FrontPage") about the [Struts]("http://jakarta.apache.org/struts/") project
[*][XML Federation]("http://xml.apache.org/")[LIST]
[*][Xalan wiki]("http://wiki.apache.org/xalan/FrontPage") about the Xalan project at [Xalan-Java]("http://xml.apache.org/xalan-j/") and [Xalan-C++]("http://xml.apache.org/xalan-c/")
[*][Xindice wiki]("http://wiki.apache.org/xindice/FrontPage") about the [Xindice]("http://xml.apache.org/xindice") project
[*][Xml Beans wiki]("http://wiki.apache.org/xmlbeans/FrontPage") about the [Xml Beans]("http://xml.apache.org/xmlbeans") project
[*][XML Graphics wiki]("http://wiki.apache.org/xmlgraphics/FrontPage") about the [XML Graphics]("http://xmlgraphics.apache.org/") project[LIST]
[*][Batik wiki]("http://wiki.apache.org/xmlgraphics-batik/FrontPage") about the [Batik]("http://xmlgraphics.apache.org/batik") project
[*][FOP wiki]("http://wiki.apache.org/xmlgraphics-fop/FrontPage") about the [FOP]("http://xmlgraphics.apache.org/fop") project[/LIST] [/LIST] 
[*][Web Services]("http://wiki.apache.org/ws/FrontPage") wiki about the [Web Services]("http://ws.apache.org/") project[LIST]
[*][jUDDI]("http://wiki.apache.org/ws/jUDDI") wiki about the [jUDDI]("http://ws.apache.org/juddi") project[/LIST] [/LIST] 
[*][Albatross wiki]("http://www.object-craft.com.au/projects/albatross/wiki")
[*][Auckland.Wiki]("http://auckland.wiki.org.nz/")
[*][Blinkenshell.org Wiki]("http://blinkenshell.rog/") Free UNIX Shell Provider
[*][GNOME Live! Wiki]("http://live.gnome.org/FrontPage")
[*][WineHQ Wiki]("http://wiki.winehq.com/FrontPage")
[*][[http://www.kednos.com]("http://www.kednos.com/") PLI (PL/1) for OpenVMS and TRU64 UNIX
[*][The Brooksby Family (genealogical) Wiki]("http://www.brooksby.org/moin/")
[*][Nearly Anything]("http://riters.com/NearlyAnything/index.cgi/FrontPage")
[*][lagses.berkeley.edu]("http://lagses.berkeley.edu/") Latino Association of Graduate Students in Engineering and Science
[*][M208ers Wiki]("http://m208ers.on-wiki.net/")  Resource for Open University students on the M208 *Introduction to Pure Mathematics* course
[*][Mac OS/X Wiki]("http://tony.lownds.com/macosx/wiki/moin.cgi/FrontPage") [IMG]http://static.wikiwikiweb.de/moin_static157/modern/img/smile.png[/IMG]
[*][The Brewiki]("http://brewiki.org/") **Beer** homebrewing [IMG]http://static.wikiwikiweb.de/moin_static157/modern/img/alert.png[/IMG] has its own domain now.
[*][http://openwrt.ksilebo.net/FrontPage](http://openwrt.ksilebo.net/FrontPage) OpenWRT Wiki
[*][http://overcards.com/wiki](http://overcards.com/wiki) overcards.com Hold'em Poker Wiki
[*][http://wiki.gimp.org/](http://wiki.gimp.org/) The GIMP (open source image editing software)
[*][IRC channel #xml]("http://moinmoin.wikiwikiweb.de/InterWiki") - 2003-03-16: read only and dead
[*][SAP-DB Wiki]("http://sapdb.2scale.net/moin.cgi/FrontPage")
[*][Thinki]("http://www.thinkware.se/cgi-bin/thinki.cgi/")
[*][The Lighting Wiki]("http://lightingwiki.com/FrontPage")
[*][The TSMWiki, Tivoli Storage Manager Wiki]("http://tsmwiki.com/tsmwiki")
[*][Turbogears Documentation]("http://docs.turbogears.org/")
[*][dyne.org]("http://lab.dyne.org/FrontPage")
[*][EQUATOR city]("http://www.dcs.gla.ac.uk/equator/wiki") - research on integrating physical and digital interaction
[*][Potlatch.net]("http://www.potlatch.net/") - Gift Economy Advocacy with [Wiki]("http://potlatch.net/MoinMoin/moin.cgi/GiftWiki")
[*][http://wiki.docbook.org/topic/](http://wiki.docbook.org/topic/) - The Doc**Book Wiki **
[*]**[the.earth's UK Tech wiki]("http://wiki.earth.li/") - Free Software computing tips, Earthlings information, Debian info, some UK LUG info **
[*]**[Fresco]("http://wiki.fresco.org/index.cgi") - Wiki for the Berlin project (nice skin [IMG]http://static.wikiwikiweb.de/moin_static157/modern/img/thumbs-up.png[/IMG] ) (Site is spammed to hell and now closed). **
[*]**[Boiled Frog]("http://www.boiledfrog.org/wikiwiki") - Wiki for the Boiled Frog Trading Co-operative **
[*]**[introvert.net/notes]("http://introvert.net/notes/") - recursive diary **
[*]**[Agility Issue and Bug Tracker]("http://www.agileedge.com/") - We use [MoinMoin]("http://moinmoin.wikiwikiweb.de/MoinMoin") for our internal documentation **
[*]**[lizardsoftware.com]("http://lizardsoftware.com/thewiki") - Java and Agile Info **
[*]**[Overlake Fly Fishing Club Website Project]("http://offc.org/open/") **
[*]**[Sciasbat's Wiki]("http://slarty.polito.it:8069/%7Esciasbat/wiki/moin.cgi/FrontPage") An experiment of PIM **
[*]**[The Robot Group in Austin, Texas.]("http://www.robotgroup.net/") Showcases the groups projects and accomplishments. Amateur robotics! [IMG]http://static.wikiwikiweb.de/moin_static157/modern/img/smile.png[/IMG] **
[*]**[CVSNT Wiki]("http://www.cvsnt.org/wiki") User supported documentation for CVSNT **
[*]**[spack.org]("http://www.spack.org/") - thinking space of [AdamShand]("http://moinmoin.wikiwikiweb.de/AdamShand") and many other contributors. **
[*]**[Gnarlodious.com]("http://gnarlodious.com/") - Just a little old personal website **
[*]**[ESW Wiki]("http://esw.w3.org/topic/") - Evolving the Semantic Web **
[*]**[Gelato@UNSW ]("http://www.gelato.unsw.edu.au/IA64wiki") - IA64 Linux tricks/tips/info **
[*]**[HaWiki]("http://www.haskell.org/hawiki/") - Wiki for the programming language Haskell **
[*]**[Gwin Wiki]("http://nights.doc.ntu.ac.uk/gwinwiki") - Wiki for Gwin, a simple Windows graphics library for C++ **
[*]**[ID3.org]("http://id3.org/") - MP3 audio tagging (ID3 Tag) standard repository **
[*]**[Hermit's Cave]("http://www.hermitscave.org/cwiki/") - Wiki for the [forum]("http://www.hermitscave.org/forum/") for the [The Inquirer]("http://theinquirer.net/") tech news site. **
[*]**[MayoWiki]("http://wiki.feedle.net/") **
[*]**[XPM.NET Wiki]("http://nxpm.sourceforge.net/cgi-bin/moin.cgi") **
[*]**[http://wiki.literati.org/](http://wiki.literati.org/) - Free-market anarchism, technology, existentialism, etc. **
[*]**[The Language Wiki]("http://www.jeffandjackie.com/moin/FrontPage") - A Wiki for the discussion of programming language theory, design and implementation. **
[*]**[Geary Central]("http://www.geary.com/") - A guide to Gearys on the net - running a modified version of [MoinMoin]("http://moinmoin.wikiwikiweb.de/MoinMoin") **
[*]**[CAKE Wiki]("http://www.cakem.net/mywiki/") - The wiki for the CAKE (Key Addressed Crypto Encapsulation) project. **
[*]**[Access Grid Developers Wiki]("http://www.mcs.anl.gov/fl/research/accessgrid/wiki/") - The wiki for Access Grid Developers. **
[*]**[Oscar Documentation Wiki]("http://joust.kano.net/wiki/oscar/") - Documentation of the AOL Instant Messenger OSCAR protocol. **
[*]**[Digital Design & Construction]("http://claymore.engineer.gvsu.edu/egr326") - Design tools and resources for microcontroller-based embedded systems (mostly for a class at [Grand Valley State University]("http://www.gvsu.edu/engineering") but also useful to others) **
[*]**[MayaVi Wiki]("http://mayavi.sf.net/cgi-bin/moin.cgi") - Wiki for the MayaVi scientific data visualizer. **
[*]**[SciPy Wiki]("http://scipy.org/") - The Scientific Python Site **
[*]**[http://michaelsen.kicks-***.net/moinmoin/moin.cgi/FrontPage](http://michaelsen.kicks-***.net/moinmoin/moin.cgi/FrontPage) Gentoo Linux Kernel And Hardware Wiki **
[*]**[http://www.aspectcookbook.com]("http://www.aspectcookbook.com/") AspectJ Recipes **
[*]**[Arch Wiki]("http://wiki.gnuarch.org/moin.cgi/") **
[*]**[University of Kentucky Linux Users Group(UKLUG)]("http://linux.uky.edu/") **
[*]**[Portable Playlist Wiki]("http://playlist.musicbrainz.org/playlist/moin.cgi") **
[*]**[Gimp Wiki]("http://wiki.gimp.org/gimp/") A collaborative effort to collect GIMP-related information. **
[*]**[Location Hidden Wiki]("http://6sxoyfb3h2nvok2d.onion/") A Location Hidden Wiki.  You will need [Tor]("http://freehaven.net/tor/") to access this. **
[*]**[PyQt and PyKDE wiki]("http://www.diotavelli.net/PyQtWiki") **
[*]**[Berkeley Wiki]("http://csua.berkeley.edu/%7Etobin/wiki/moin.cgi"), a wiki for the University of California, Berkeley **
[*]**[Flash Mob]("http://flashmob.wiki.taoriver.net/") -- Global Flash Mob coordination. [MultiLingualWiki]("http://moinmoin.wikiwikiweb.de/MultiLingualWiki"). **
[*]**[Dragon Stone MUD]("http://dragonstone.wiki.taoriver.net/") **
[*]**[Awareness Wiki]("http://aware.wiki.taoriver.net/") -- For talking about the problem of Awareness. Consciousness, "is *real* artificial intelligence possible", etc. **
[*]**[GfxAlgo]("http://gfxalgo.wiki.taoriver.net/") -- graphics algorithms **
[*]**[Free Games]("http://freegames.wiki.taoriver.net/") --  Free(dom) Games -- news and reviews of open-source games **
[*]**[Futures]("http://futures.wiki.taoriver.net/") -- general future prediction **
[*]**[Visual]("http://visual.wiki.taoriver.net/") -- visual communication, "visual language", tips for designing logos, ... **
[*]**[PaperTalk]("http://papertalk.wiki.taoriver.net/") -- 2D Data Encoding -- we can use 2D barcodes for all kinds of cool things. **
[*]**[notebooks]("http://notebooks.wiki.taoriver.net/") -- notebook systems **
[*]**[OneBigStruggle]("http://onebigstruggle.wiki.taoriver.net/") -- union organizing **
[*]**[TwinPorts Wireless]("http://www.twinportswireless.net/") -- A community wireless project in the Duluth, MN / Superior, WI area **
[*]**[LearnWoodWorkingWiki]("http://www.learnwoodworking.com/woodwiki/") -- Woodworking Woodturning Topics **
[*]**[WriteHere.net]("http://www.writehere.net/moin.cgi?") -- A community for creative writers to work collaboratively on fiction and other creative forms. **
[*]**[The Society Of Lies and Stolen Ideas]("http://www.solasi.org/moin.cgi?") -- SoLaSI is the parent of WriteHere.net. SoLaSI focuses on defining goals for both projects, discussing the community, setting development initiatives, and developing Critical Theory resources for Wiki Writers. **
[*]**[libsdl.org]("http://www.libsdl.org/cgi/docwiki.cgi/FrontPage") -- The Simple [DirectMedia]("http://moinmoin.wikiwikiweb.de/DirectMedia") Layer (SDL) documentation wiki. **
[*]**[Steel Law Online Wiki]("http://steel-law.mivok.net/") -- A player run wiki for [Steel Law Online]("http://www.steel-law.com/"). **
[*]**[AlistairCockburn's Crystal Wiki]("http://alistair.cockburn.us/crystal/wiki/FrontPage") -- About software development, agile especially, and the Crystal methodologies. **
[*]**[Foundations and Methods Research Group]("http://www.cs.tcd.ie/research_groups/fmg/moin.cgi") --- Formal Methods, Functional Programming and TCS research at Trinity College Dublin (read-only for non-members) **
[*]**[Opie]("http://opie.handhelds.org/cgi-bin/moin.cgi/") Open Palmtop Integrated Enviroment Applications and libraries for mobile devices **
[*]**[The unofficial Rocks'n'Diamonds Wiki]("http://www2.semisane.de/rndwiki/") Wiki about arcade style game for Unix, Mac OS X, Windows and DOS in the tradition of Boulder Dash **
[*]**[Aspen Hill Maryland USA]("http://www.aspenhillnet.net/aspenhillwiki") -- an experimental Wiki promoting community inter-organizational communication in Aspen Hill, MD, USA *2004-10-03* **
[*]**[The Bingen Bioinformatics Wiki]("http://biwiki.fh-bingen.de/biwiki") - Bioinformatics Wiki at Bingen University of Applied Sciences, mainly in English, partly in German **
[*]**[The Proof General Documentation Wiki]("http://proofgeneral.inf.ed.ac.uk/kit/wiki") - Documentation and support for the open-source theorem proving interface Proof General, produced by Edinburgh University **
[*]**The [Exim Wiki]("http://www.exim.org/eximwiki/") - support and document evolution for the Exim MTA **
[*]**[The Unofficial CAcert Wiki]("http://cacert.webhop.org/") - FREE X.509 Digital Certificates at CAcert.org **
[*]**[Freedesktop.org]("http://www.freedesktop.org/") - free software project to work on interoperability and shared technology for desktop environments for the X Window System **
[*]**[CppUnit Wiki]("http://cppunit.sourceforge.net/cgi-bin/moin.cgi/FrontPage") - A port of JUnit to C++.  The wiki is on [SourceForge]("http://moinmoin.wikiwikiweb.de/SourceForge"), and is running [MoinMoin]("http://moinmoin.wikiwikiweb.de/MoinMoin") version 1.3.x. **
[*]**[Photo Wiki]("http://www.cdegroot.com/cgi-bin/photowiki/") **
[*]**[GreenWoodCraftWiki]("http://www.bodgers.org.uk/woodcraftwiki/FrontPage") -- Greenwood Craft Encyclopedia on official APT website **
[*]**[Fenix Project]("http://fenix-ashes.ist.utl.pt/") - FenixEDU Open-Source Project **
[*]**[V-Strom Motorcycle Wiki]("http://vstrom.info/wiki") **
[*]**[The Shuttleworth-Foundation-Wiki]("http://wiki.tsf.org.za/shuttleworthfoundationwiki/") - Mark Shuttleworth founded an organization, which sponsors [Ubuntu-Linux]("http://www.ubuntulinux.org/") and [schooltool]("http://www.schooltool.org/") **
[*]**[Power Electronics Building Blocks Wiki ]("http://web-cat.cs.vt.edu/PebbWiki/") **
[*]**[The Fedora Project Wiki ]("http://fedoraproject.org/wiki/") **
[*]**[Adventure Wiki]("http://adventurewiki.net/aw/") - Choose Your Own Adventure wiki style **
[*]**[AURA]("http://www.aura.org.au/") - Australian Usui Reiki Association **
[*]**[TokePure]("http://www.tokepure.com/") - Toke Pure The Ultimate Cannabis Resource. **
[*]**[Scientific Study of Video Games]("http://gold-saucer.afraid.org/video-games/") **
[*]**[KernelNewbies Wiki]("http://wiki.kernelnewbies.org/") - Learn how to program in the Linux kernel. **
[*]**[Linux-MM Wiki]("http://linux-mm.org/") - Documentation for the Linux memory management subsystem. **
[*]**[Spamikaze]("http://spamikaze.org/") - An open source spam blocking system. **
[*]**[The official Ubuntu wiki]("https://wiki.ubuntu.com/FrontPage") **
[*]**[Edu-Buntu]("http://wiki.edubuntu.org/") **
[*]**[MusicBrainz]("http://wiki.musicbrainz.org/") - Nicely colorized "modern"-based theme **
[*]**[TripleA]("http://triplea.sourceforge.net/mywiki/TripleA") **
[*]**[MHVLUG]("http://mhvlug.org/") - Mid-Hudson Valley Linux Users Group **
[*]**[tor hidden wiki]("http://6sxoyfb3h2nvok2d.onion/tor/") **
[*]**[Highway to hell - AC/DC Wiki]("http://www.highwaytohell.net/") **
[*]**[ArchiCAD Wiki]("http://www.archicadwiki.com/") **
[*]**[On-wiki.net]("http://on-wiki.net/") - Wiki that allows people to create their own wikis **
[*]**[CarbonDev]("http://www.carbondev.com/") - Mac OS X Carbon development **
[*]**[SourceMage.org]("http://wiki.sourcemage.org/") - Source Mage GNU/Linux Documentation **
[*]**[PlanetNepal Wiki]("http://planetnepal.org/wiki/") - An online repository of information on Nepal **
[*]**[gDeskletsWiki]("http://gdesklets.gotdns.org/gDeskletsWiki") - gDesklets Development Pages **
[*]**[The Hahnwiki]("http://hahndorf.soho.on.net/hahnwiki") - The Town of Hahndorf Community Wiki in the Adelaide Hills Region of South Australia. **
[*]**[AllegroGL]("http://allegrogl.sf.net/") - Wiki site for the OpenGL addon to the Allegro library **
[*]**[CDFG]("http://wiki.cdfg.org/") - the Wiki of the CEN/ISSS Cultural Diversity Focus Group **
[*]**[Xen Wiki]("http://wiki.xensource.com/xenwiki/FrontPage") **
[*]**[The Final Fantasy Wiki]("http://www.ffwiki.net/") - A "fan wiki" for the Final Fantasy franchise of games, movies, and animated series. **
[*]**[Portland State Aerospace Society]("http://psas.pdx.edu/") - a rocket club, converted from TWiki after last year's exploit (Yay parsers!) **
[*]**[JWiki]("http://www.jsoftware.com/jwiki") - Jsoftware wiki **
[*]**[Pajama]("http://pajama.conal.net/") - tool for creating interactive, continuous, web-embeddable imagery **
[*]**[http://smg.tophi.net]("http://smg.tophi.net/") - personal wiki **
[*]**[e164.org - a public ENUM service]("http://www.e164.org/wiki/") **
[*]**[X.Org Foundation]("http://xorg.freedesktop.org/wiki/") **
[*]**[Nokia Corporation wiki for maemo]("http://maemo.org/maemowiki/") **
[*]**[RPM wiki]("http://wiki.rpm.org/") **
[*]**[CsoundWiki]("http://tobiah.org/csoundwiki") **
[*]**[Jokosher Userdocs]("http://userdocs.jokosher.org/") (FLOSS audio application) **
[*]**[EverybodyLovesEricRaymond]("http://johnleach.co.uk/wiki/EverybodyLovesEricRaymond") - Used by an artist to develop new comics, collecting ideas from users. **
[*]**[Hercules Wiki]("http://www.hercules-390.org/hercwiki/") - for users of the Hercules System/370, ESA/390, and z/Arhictecture Systems Emulator **
[*]**[Emusic-DIY Archive]("http://www.emusic-diy.org/") - The long running Emusic-DIY archive, now reformatted and moved to [MoinMoin]("http://moinmoin.wikiwikiweb.de/MoinMoin") **
[*]**[Ren'Py Wiki]("http://www.renpy.org/wiki/renpy/Home_Page") - home of the Ren'Py engine for writing visual novels (interactive story-based games) **
[*]**[Banu Wiki]("https://wiki.banu.com/") - Wiki for [Banu]("http://www.banu.com/") project communities to discuss ideas and store project information **
[*]**[GCC Wiki]("http://gcc.gnu.org/wiki/") - Wiki for the  GNU Compiler Collection **
[*]**[GRUB wiki]("http://grub.enbug.org/") - Wiki for GNU GRUB **
[*]**[SciPy wiki]("http://www.scipy.org/SciPy") - Scientific Tools for Python **
[*]**[Caltech's help wiki]("https://wiki.hss.caltech.edu/help/") **
[*]**[Freevo Wiki]("http://freevo.sourceforge.net/cgi-bin/doc/Index") - Freevo is an open source, Python based home theatre platform**[/LIST]**[http://moinmoin.wikiwikiweb.de/MoinMoinWikis](http://moinmoin.wikiwikiweb.de/MoinMoinWikis)**

---

### Post by RAV TUX on 2007-10-21
Also reference this Brief MoinMoinWiki thread:

[http://ubuntuforums.org/archive/index.php/t-206853.html](http://ubuntuforums.org/archive/index.php/t-206853.html)

Also here is a nice MoinMoinWiki Howto:

[http://moinmoin.wikiwikiweb.de/MoinMoin/InstallDocs](http://moinmoin.wikiwikiweb.de/MoinMoin/InstallDocs)

---

### Post by hellmet on 2007-10-21
Ubuntu.com uses Plone.

---

### Post by argux on 2007-10-22
Great! I will look into MoinMoin. The first time I heard about that one was a few years ago, but at the time I was young and stupid and thought that MediaWiki was the only wiki software worth looking. If I had been a bit wiser, my project would probably be running by now.

Thanks RAV TUX, that really looks like what I have in mind.

---

### Post by RAV TUX on 2007-10-22
> **argux said:**
> Great! I will look into MoinMoin. The first time I heard about that one was a few years ago, but at the time I was young and stupid and thought that MediaWiki was the only wiki software worth looking. If I had been a bit wiser, my project would probably be running by now.

Thanks RAV TUX, that really looks like what I have in mind.Good Welcome. ;)

---

### Post by ThinkBuntu on 2007-10-22
The forums are vBulletin, and the website is Drupal. Drupal is also used by Lifetime TV and a bunch of other pretty noteworthy companies. I use it for many of my clients' sites, and am currently completing an e-commerce site on this platform. The funny thing about Drupal is that, unless you can get at Ubuntu.com's themes, module setup, customizations, etc. you'll have to in a way re-invent the wheel. Drupal is very flexible which is a strength and a weakness: It's as good as you can make it (within the limits of PHP, etc.).

---

### Post by zero244 on 2007-10-22
I dont have a need for running a web server or website.........but it is very interesting to see what other sites are using to run there enterprise.
The power of open source software is very impressive.
I find it mind boggling that you can run a large enterprise site with Free software.
That is precisely why I think open source software will eventually overtake Microsoft and Apple.
Anything that is superior and free will win over a inferior costly product.

---

### Post by argux on 2007-10-24
Thanks all for your help.

Plone looks *really* interesting, but running it is a bit cost-prohibitive for me. I'll check Drupal and see how I like it. The integration with the wiki and the forum software might be a bit difficult for me, because I don't know a lot about those esotheric things (like the ability to have users register once and use the same account for the wiki, the forums and Drupal). 

But I disgress, thanks again for your suggestions. I hope I can get this to work. Now, off to work!

---

