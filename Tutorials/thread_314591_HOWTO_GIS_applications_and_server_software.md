---
title: "HOWTO: GIS applications and server software"
date: 2006-12-07
forum: Tutorials
---

### Post by Garyu on 2006-12-07
Some of the most advanced tools for GIS/GIT is freely available for the Ubuntu community, but few are aware of their true power. The applications listed here will cost you anywhere from 10'000 USD to a couple of million USD in their commercially licensed counterparts (like ESRI ArcMap/ArcSDE, Oracle, and so on).

To begin with, you should take a look at this wiki page:
[https://wiki.ubuntu.com/UbuntuGIS](https://wiki.ubuntu.com/UbuntuGIS)
On this page several GIS applications are listed. There are also howto's on how to install bleeding edge (development) versions from source of a couple of them. 

Why do you need GIS? Well, maybe you want to know which way is the fastest to drive to work, or the most beautiful one. Maybe you are a forest owner and need to keep track of your stands and where to do clearcuts. Maybe you would just like to draw a treasure map for your kids. Maybe you have 973 terabyte of data about the soils and ground coverage in Great Britain that you need to write a report about. Anything that has to do with maps or area representations can be done with GIS software.

If you want lots of users to access your data, and make the access really fast, you should go with OpenGIS as a foundation. This is an addon for the PostgreSQL database which makes it possible to store data like points, lines and polygons in the data tables. If you're just doing something small for home or small-business use, you can store the data as files in your home directory.

If you want to manipulate data, look at 3D-representations of landscapes, do advanced automated edits on rasters or anything else you can think of, you will need GRASS - one of the worlds most advanced (and most difficult to learn) GIS applications. If you just need to draw some vectors and use a bitmap ortophoto as a background, you will be better off with QGIS (or Quantum GIS as it is really called) which has a more easy to use interface but much less power. QGIS and GRASS work really well together, so you should proably install both and try them out. 

If you want to publish your data on a webserver, you should install MapServer, one of the most widely used GIS web-applications in the world. 

***GRASS***

To install GRASS, simply type in a terminal 
> **sudo apt-get install grass**
This will give you version 6.0, at least with the edgy repositories (oh, you have to enable the Universe repo). But the latest version is 6.2 and the bleeding edge version is 6.3. Problem is, the 6.2 version requires some libraries not in the repositories with the right version. Installing these libraries meant for me that I had to uninstall gnucash. So there are some drawbacks to using the latest version, but you get some new features as well, so you will have to decide on what you think is most important. I can't even get GRASS 6.2 to work with the newest QGIS (0.8). Anyway, these are the files you need if you want to try it out:
libreadline5_5.2-1_i386.deb
libgdal1-1.3.2_1.3.2-2_i386.deb
You can get them from here: [http://packages.debian.org/unstable/libs/libgdal1-1.3.2](http://packages.debian.org/unstable/libs/libgdal1-1.3.2)
As usual, you install .deb packages with
> **dpkg -i package_name.deb**
After you have installed these libraries you will of course need to install the GRASS 6.2 version, which can be found here: [http://packages.debian.org/experimental/science/grass](http://packages.debian.org/experimental/science/grass)
At the bottom of that page is .deb's for both i386 and AMD-64 architectures. 

GRASS documentation:
[http://www.gdf-hannover.de/media.php?id=0&lg=en](http://www.gdf-hannover.de/media.php?id=0&lg=en) (University of Hannover)
[http://cemml.carleton.ca:8080/OGUG/ogug-community/tutorials/](http://cemml.carleton.ca:8080/OGUG/ogug-community/tutorials/) (Ottawa GRASS GIS User Group)
[http://grass.itc.it/grass60/manuals/html60_user/index.html](http://grass.itc.it/grass60/manuals/html60_user/index.html) (Official User Manual)

***Quantum GIS (QGIS)***

QGIS can be installed from the repo's with:
> **sudo apt-get install qgis**
Oh, and if you're running GRASS as well, don't forget:
> **sudo apt-get install qgis-plugin-grass**
The latest version is 0.8-preview2, which isn't fully developed and therefore not in the repos (0.7.4 in the repo). You can find .deb's for both 0.7.9 and 0.8 at: [http://qgis.org/uploadfiles/ubuntu_edgy/](http://qgis.org/uploadfiles/ubuntu_edgy/)
There are some unresolved dependencies here, and I haven't had time to look at solving them yet. Currently I have a conflict with GRASS 6.2 which I am evaluating. But just try installing the deb's and locate the missing libraries and what not at the Debian unstable repo: [http://packages.debian.org/unstable/](http://packages.debian.org/unstable/)

Documentation for Quantum GIS:
[http://qgis.org/releases/userguide.pdf](http://qgis.org/releases/userguide.pdf) (Official documentation)
[http://blog.qgis.org/?q=node/10](http://blog.qgis.org/?q=node/10) (Tutorial for programmers wanting to implement QGIS features)

***PostGIS***

If you want the PostGIS database extension, it's very easy to install:
> **sudo apt-get install postgis**
I did this on a system where I already had PostgreSQL installed, so I'm actually not sure if you need to install that first. If you get errors from the above, just do a 
> **sudo apt-get install postgresql-8.1**
That will get you going. To administer your database, you will want a graphical tool (GUI) rather than using the terminal and typing commands for everything. So go ahead and install pgAdmin3:
> **sudo apt-get install pgadmin3**
This is a very easy to use tool to do whatever you want with your PostgreSQL/PostGIS database.
The version installed from the repo's (edgy) is 1.1.2, but the newest version is 1.1.6. If you want to get that, the source is available for your own compilation from: [http://postgis.refractions.net/download/](http://postgis.refractions.net/download/)

Documentation on PostGIS: [http://postgis.refractions.net/docs/postgis.pdf](http://postgis.refractions.net/docs/postgis.pdf)

***MapServer***

To install from repositories:
> **sudo apt-get install cgi-mapserver mapserver-bin perl-mapscript php4-mapscript php5-mapscript python-mapscript**
I haven't actually tried this yet, because these things conflicts with my new GRASS libraries (as I said, having versions that aren't in the repo's will give you some troubles). But everyone tells me it is a very good application. Of course, you will need a webserver, such as apache, and the OpenGIS or a MySQL database running, as well as PHP.

Documentation for MapServer (official homepage):
[http://mapserver.gis.umn.edu/docs](http://mapserver.gis.umn.edu/docs)



Now install these things, learn more about GIS, and help develop these applications. Several of them are the best in the world at what they do, but they also (particularly GRASS) have very hostile user interfaces. A lot of work remains to be done in other words. :cool:

---

### Post by johnrobot on 2006-12-27
I would like to use Ubuntu for my daily GIS projects, but have so far not found the right tools to do the job. Currently, I use Manifold System, [http://www.manifold.net/](http://www.manifold.net/) , on Windows, and I have yet to discover any free/open source alternatives with the same amount of power, ease of use and flexibility. I have had a look at QGIS, but it lacks much of the power that I need. I have tried GRASS as well, but recommending it to my clients is out of the question due to the complexity of the interface, so I guess I will have to keep looking.

Magnus

---

### Post by Garyu on 2007-01-09
I have heard many good things about manifold, but I have yet to try it out for myself. 

But have you looked at the new QGIS 0.8 (titan)? It has a lot of added functionality and makes a very good front-end to GRASS with the GRASS Tools. The only thing I have noticed is that you have to run GRASS 6.0 (rather than 6.2 which is the newest version) because of some dependency conflicts.

Also, in march the new GRASS manual is out from the publisher. It will be a good thing to have in the bookshelf if you want to work with this piece of software. :)

---

### Post by shat on 2007-01-09
Garyu,

Do you know if any of these are able to provide functionality like ESRI's NetworkAnalyst plugin for ArcMap?  I need this for my undergrad project and, frankly, Windows AND ESRI's products are a big pain, and I can't get ArcMap tutorials/documentation without spending tons of cash.

---

### Post by Garyu on 2007-01-10
> **shat said:**
> Do you know if any of these are able to provide functionality like ESRI's NetworkAnalyst plugin for ArcMap?  I need this for my undergrad project and, frankly, Windows AND ESRI's products are a big pain, and I can't get ArcMap tutorials/documentation without spending tons of cash.

I haven't been working with these particular things in GRASS, but there are some things to play with. Actually, for some tasks I know that GRASS is even more capable than ESRI's products, but when it comes to network analysis I am not even a novice yet, so I'm not sure how good these tools are. But please try them out and let us know what you think of them. The command-line interface of GRASS takes some getting used to, but it's very powerful once you get the hang of if.

This is a quote from the [GRASS homepage]("http://grass.itc.it/gdp/html_grass63/vectorintro.html"):
**Vector network analysis**
GRASS provides support for vector network analysis. The following algorithms are implemented:
    * Vector maintenance: v.net
    * Shortest path: d.path and v.net.path
    * Traveling salesman (round trip): v.net.salesman
    * Allocation of sources (create subnetworks, e.g. police station zones): v.net.alloc
    * Minimum Steiner trees (star-like connections, e.g. broadband cable connections): v.net.steiner
    * Iso-distances (from centers): v.net.iso
Vector directions are defined by the digitizing direction (a-->--b). Both directions are supported, network modules provide parameters to assign attribute columns to the forward and backward direction.

---

### Post by johnrobot on 2007-01-21
Yes, I have tried QGIS 0.8. It´s getting better, but it´s no match for Manifold 7x. I will do my best to spread the word abouth both these products and I hope to see QGIS in the pole position some day.

Magnus

---

### Post by padeco on 2007-01-28
hi there!

i am just wondering if you guys would like to have a look at the following GIS software. it is available in english, spanish and portuguese.

[http://www.dpi.inpe.br/spring/english/index.html](http://www.dpi.inpe.br/spring/english/index.html)

just follow the short registration prompt and download the latest linux version. i would like to read some feedback on this one! hope it helps!

padeco.

---

### Post by Garyu on 2007-01-28
I have only glanced at it, but it looks quite capable. It's not any competition for GRASS though, at least not at this stage. But it is always good to see free software challenging the large commercial actors. I think the best attempt at this though (aside from GRASS/QGIS) is the chinese governments GIS SuperMap: [http://www.supermap.com/](http://www.supermap.com/)

---

### Post by thyyykri on 2007-02-16
> **shat said:**
> Do you know if any of these are able to provide functionality like ESRI's NetworkAnalyst plugin for ArcMap?

You might also want to have a look at [pgdijkstra]("http://www.cartoweb.org/contribs.html").

---

### Post by rpimn on 2007-02-16
Does somebody come across with terralib ([http://www.terralib.org/](http://www.terralib.org/)) ?

---

### Post by UberN00b on 2007-02-23
Hi Guys,

Have you had a look at Mapguide OS, basically Autodesk have released opensource versions for their Mapguide software [[http://mapguide.osgeo.org/]](http://mapguide.osgeo.org/]). It works well on RH servers, haven't tested it under Ubuntu yet.

Ta,

---

### Post by BLTicklemonster on 2008-01-24
Our GIS department uses Arc, and the files are shared on our network.

I've tried qgis, but I can't figure out how to open anything using it. I try to open a layer, but the open screen comes up, and I can't access the network with it. I see folders aplenty, but they are all on my machine, nothing on the network shows up anywhere.

Also, would qgis or grass even work trying to open the files we have on the server?

---

### Post by Go_Bucks on 2008-05-12
Everybody is missing gvSIG, which is the closest thing to ESRI that is available. If you look on youtube, you can see videos of the upcoming 2.0 version which will have symbology very similar to ArcGIS 9.2. The interface is very similar to ArcView 3.x, and has the best built-in open source cartographic capability outside of trying to learn GMT. It is the only software I have been able to use consistently in an entirely ESRI shop and have no one see the difference on final maps. Add in the Sextante analysis plugin and you have advanced spatial analysis ability. They also have 3D mapping and network analysis plugins.

This is a government project (Valencia, Spain) and is very well funded through, I believe, 2013. They are currently in the OSGEO incubator.

[http://www.gvsig.gva.es/]("http://www.gvsig.gva.es/")

Choose your language at the top of the page.

---

### Post by Grandma_DOG on 2008-06-21
> **johnrobot said:**
> I would like to use Ubuntu for my daily GIS projects, but have so far not found the right tools to do the job. Currently, I use Manifold System, [http://www.manifold.net/](http://www.manifold.net/) , on Windows, and I have yet to discover any free/open source alternatives with the same amount of power, ease of use and flexibility. I have had a look at QGIS, but it lacks much of the power that I need. I have tried GRASS as well, but recommending it to my clients is out of the question due to the complexity of the interface, so I guess I will have to keep looking.

Magnus

I'm in the same spot.  We have Manifold which is user friendly, cheap, and powerful.  But I'm migrating my office to Linux, and GRASS is nastily dependent on Command lines still, its GUI hasn't been completely developed.

We're starting a new data acquisition project in Oil and Gas, and I think we'll use QGIS to be the daily GIS to create datalayers, then store them in POSTGIS to be manipulated later with GRASS/other.

Our Problem is that we need to develop some plug in that can take 'metes and bounds' legal description and create polygons out of it.  Anyone know Linux plugin/script that can do that?

---

### Post by laptoppana on 2008-09-02
I just instal QGIS on my UBUNTU laptop, but I feel the speed of qgis is very slow compare to arcgis, any body have same problem?

---

### Post by Grandma_DOG on 2008-09-03
Wow, we've just evaluated gvSIG GIS.  Its the closest thing Linux has to Manifold.  Unfortunately, its not in the repositories.

This is your answer if you want to get the equivalent of ESRI/Arc.

Quantum, is very light and lacking power. GRASS is so complex and user unfriendly, its nearly hopeless.

---

### Post by lpuente on 2009-08-14
Why don't you try gvSIG?  I hope it helps you out. It's in different languages and is platform independent. It runs on Mac, Linux (Ubuntu too) and Windows. Developed in Spain's Valencia by the University of Valencia :)

---

### Post by Uchiha_madara on 2009-08-17
Just for Raising the Topic ...... intersting .... i have comment's i well discuss this topic later

---

### Post by BLTicklemonster on 2012-06-04
At the risk of being accused WRONGLY of necromancy AGAIN, I am compelled to ask if this this thread is still relevant. Is this thread still relevant? I use ArcGIS at work and want to have the ability to do some projects on Ubuntu from my house, too.

---

### Post by Garyu on 2012-06-05
> **BLTicklemonster said:**
> At the risk of being accused WRONGLY of necromancy AGAIN, I am compelled to ask if this this thread is still relevant. Is this thread still relevant? I use ArcGIS at work and want to have the ability to do some projects on Ubuntu from my house, too.

I haven't been using any GIS for a long while now. But it should be alright. Check out these links:
[http://hub.qgis.org/projects/quantum-gis/wiki/How_do_I_do_that_in_QGIS](http://hub.qgis.org/projects/quantum-gis/wiki/How_do_I_do_that_in_QGIS)

[http://gis.stackexchange.com/questions/7957/migrate-from-arcgis-to-qgis](http://gis.stackexchange.com/questions/7957/migrate-from-arcgis-to-qgis)

---

### Post by BLTicklemonster on 2012-06-05
I read in another thread that gvSIG was as close to esri/arcgis as you can get, so I'm download it right now. I've been doing some family research and I want to be able to map out old family lands, grave sites in cemeteries, old rail lines, etc. here at the house, not at work. That way I'm not "doing it on my work computer when I ought to be napping. I mean mapping", and I have access to it here at all times. 

Thanks, I'll check that out, too.

---

### Post by markMDW on 2012-06-30
Qgis 1.7 works well for me on Ubuntu 10.04.  

I do have a problem trying to load data into a sqlite database, which I'm trying to learn how to use. I figured this would be the equivalent of an .mdb geodatabase.  spatialite extends the sqlite database for additional GIS functions while the qspatialite python plugin should create a GUI tool for use with QGIS.  Apparently everything was installed 'out of the box' from the ubuntugis repositories, but I can't get qspatialite to work.  I keep getting a message that says 'PySpatiaLite python module is required for QspatiaLite' even though I checked my filesystem and there is a Qspatialite folder that installed under plugins.  The plugin might not be the correct version (should be 2.6 rather than 3, I discovered).  

If anyone knows of a quick fix to this spatiaLite problem please let me know.

I really like the ability to download OSM data files from [http://downloads.cloudmade.com/](http://downloads.cloudmade.com/)  you can download larger areas vs TIGER data, although it's not as up to date.  it makes for a quick basemap layer


BLT, which qgis software repository did you use? 

here's the repository I installed from--
[http://ppa.launchpad.net/ubuntugis/ppa/ubuntu](http://ppa.launchpad.net/ubuntugis/ppa/ubuntu)

GVsig looks to be well documented.  I might give it a try.

---

