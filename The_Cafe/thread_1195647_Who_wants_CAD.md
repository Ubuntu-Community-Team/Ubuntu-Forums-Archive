---
title: "Who wants CAD?"
date: 2009-06-24
forum: The Cafe
---

### Post by aquavitae on 2009-06-24
There are a lot of really good opensource packages out there which can replace (and usually improve on) almost any commercial app, but one that seems to be missing is a really good AutoCAD replacement.  Over the last ten years there have been numerous CAD projects started but for some reason none of them have really taken off - I've only found a couple that are any good, but nothing that comes close to having the same power as AutoCAD, and I just can't figure out why.  Maybe there's just not a demand.  I work with AutoCAD daily, so my perspective of what's important might be skewed, but it seems that a CAD program should be no less in demand than, say, a music scoring program (e.g. Rosegarden). 

I've thought about starting a CAD project myself, or attempting to revive and old one, but I first want to figure out why the others failed so I'm trying a poll to see how many people actually have any interest in a FOSS CAD program.

---

### Post by aquavitae on 2009-06-24
Well I guess that answers that one...

---

### Post by ad_267 on 2009-06-24
I selected "It would be useful." I don't do a lot of CAD work but it would be nice to have a full featured open source CAD application, I'm only a student at the moment though. I think one of the major hurdles would be compatibility with commercial applications. I've heard that AutoCAD's dwg file format is very complex and would be difficult to reverse engineer.

Edit: This is interesting: [http://www.fsf.org/campaigns/priority.html#opendwgreplacement](http://www.fsf.org/campaigns/priority.html#opendwgreplacement). Found that from a link on the [.dwg]("http://en.wikipedia.org/wiki/.dwg") article on Wikipedia. The [.dxf]("http://en.wikipedia.org/wiki/Dxf") article is also interesting.

---

### Post by Bucky Ball on 2009-06-24
> **aquavitae said:**
>  ... my perspective of what's important might be skewed, but it seems that a CAD program should be no less in demand than, say, a music scoring program (e.g. Rosegarden). 

FYI, Rosegarden is not a patch on Sibelius (Windows). I still use Windows for that one program, refuse to use it in wine and it is a drag, so you could consider Sibelius the musical equivalent of AutoCAD; there is absolutely nothing like Sibelius in the open-source software universe (yet!).

> **aquavitae said:**
> I've thought about starting a CAD project myself, or attempting to revive and old one, but I first want to figure out why the others failed so I'm trying a poll to see how many people actually have any interest in a FOSS CAD program.

If you get it up, get back to me. I have a friend that's dying to AutoCAD in Ubuntu!

Good luck. =D>

Not that I know much about it but what about QCad?

---

### Post by ad_267 on 2009-06-24
Yeah QCad is the closest there is (Or KAD which is QCad for KDE). It does seem alright and uses DXF but isn't anywhere near AutoCAD.

---

### Post by Kazade on 2009-06-24
There is an active project called FreeCAD[1] which has been designed as a kind of CAD platform. It has a built in Python intepreter and everything about it can be altered using Python modules. It's massively extensible and powerful. The GUI frontend only provides access to a tiny tiny subset of what the backend can do. 

My brother works with AutoCAD and he is increasingly frustrated that his company is "locked" in to using it for 3 reasons:

 1. There is no OSS alternative which matches AutoCAD on features
 2. His work requires a (crappy) proprietary plugin (specific to timber frame design)
 3. The DWG file format is closed and (Autodesk want to keep it that way)

The first 2 points can be built using FreeCAD. Already his user-perspective has helped me forward on minor usability issues to the developers (think 100 papercuts) and he's sent me a list of features he requires for work so I can begin developing them.

The 3rd point can be fixed by writing an open source DWG loading library. This isn't a trivial undertaking, but it's not overly difficult either the OpenDWG project has written a spec[2] for the R13/14/15/2000/2004/2007 versions of the DWG format. 

[1] [http://sourceforge.net/projects/free-cad/](http://sourceforge.net/projects/free-cad/)
[2] [http://www.opendwg.org/guestfiles](http://www.opendwg.org/guestfiles)

---

### Post by ad_267 on 2009-06-24
FreeCAD looks like it has quite a lot of potential. Thanks for pointing that out.

---

### Post by aquavitae on 2009-06-24
> **Bucky Ball said:**
> FYI, Rosegarden is not a patch on Sibelius (Windows). I still use Windows for that one program, refuse to use it in wine and it is a drag, so you could consider Sibelius the musical equivalent of AutoCAD; there is absolutely nothing like Sibelius in the open-source software universe (yet!).Just and example, althought maybe not a good one ;)  How about firefox/IE?

> 
Not that I know much about it but what about QCad?
qcad is ok, but its only 2D and seems to be one of those projects that's actually just an old release of the commercial version.

> There is an active project called FreeCAD[1] which has been designed as a kind of CAD platform. It has a built in Python intepreter and everything about it can be altered using Python modules. It's massively extensible and powerful. The GUI frontend only provides access to a tiny tiny subset of what the backend can do.
Now how did I miss that one!  Thanks for the pointer, I'll investigate it further - it looks quite promising!

---

### Post by Blacklightbulb on 2009-06-24
I more than once tried to learn CAD but the long learning curve just makes me quit every time. Anyway I'm not going to need it every day but when I building something once a month or so...

Anyway I still prefer a pencil, a ruler and a paper. It's much faster for me.

So..

IMHO FOSS CAD would most probably be much more difficult to learn so for now if I want to design something I go to a "friend of a friend" who has a commercial one already installed. :D

---

### Post by cb951303 on 2009-06-24
I would like to have a sketch-based (catia, solidworks etc) CAD package in linux. I don't care if it's commercial or not.

---

### Post by Bucky Ball on 2009-06-24
> **aquavitae said:**
> Just and example, althought maybe not a good one ;)  How about firefox/IE?

? Sounds fine to me. Can you tell me why it is not a good one? There is nothing like Sibelius in OSS as there is nothing like AutoCAD it seems. If I am wrong, please enlighten me.

---

### Post by sim-value on 2009-06-24
I would atleast help testing

---

### Post by touf on 2010-01-18
Hi AquaVitae,

In my opinion there is not "One" CAD, but several depending on what you intend to do with it. here some points for discussion (as a professional user):
For example in my company I use daily Qcad, which fits very well my need of doing very quickly some conceptual 2D sketches (I'm doing aircraft design/analysis, but then I have to give them to a guy doing the 3D in SolidWorks).
Today the CAD alone is not enough for compagnies. A 2D CAD should have at least some motion simulation (For example a combination of QCAD and the freecad from askoh.com)
In 3D it's an even biggest challenge. A software doing only CAD is not enough. It must be directly "linkable" to a mesher, and in the next generation will be also linked to solvers. Have a look for example at SALOME, they integrated it with code_aster (FEA) and are trying to link it with code_saturne (CDF). Same case is with Solidworks which have bought COSMOS (I tried it, they need still some time to do a real product)
Then it should be linked to a CAM system....

At the end I would point out that the cost of bringing a software into a company is not only a matter of buying cost, because the cost of learning it can be on the same order of magnitude.

Anyway I will strongly encourage you if you wish to develop something as powerfull as autocad :D
Cheers
Touf

---

### Post by koenn on 2010-01-18
that's probably the reason open source CAD is not really flourishing :
people that *need* CAD will have jobs where such tools are provided by the employer. It's not something you need at home. 
Also, technical drawings is not really something a lot of people do as a hobby, so the chances that someone would start working on a CAD program as a hobby, is rather slim.

---

### Post by benjamimgois on 2010-01-18
The strange thing is that exists lots of Free CAD programs but they do not have Linux Versions, take a look at DoubleCAD ([http://www.doublecad.com/](http://www.doublecad.com/)) that is free equivalent to AutoCAD, but there's only windows versions. 

CAD is a really missing application on linux.

---

### Post by koenn on 2010-01-19
> **benjamimgois said:**
> The strange thing is that exists lots of Free CAD programs but they do not have Linux Versions, take a look at DoubleCAD ([http://www.doublecad.com/](http://www.doublecad.com/)) that is free equivalent to AutoCAD, but there's only windows versions. 

CAD is a really missing application on linux.

They may be free (as in beer), but they're not open source. Linux users traditionally prefer open source programs

---

### Post by audiomick on 2010-01-19
Hi.
I have been sporadically looking for a decent AutoCAD (or vectorworks) alternative for the last couple of years. I work as a free lance sound engineer. These days, any job of any size at all, at least in the corporate event part of the branch, involves plans which generally go through several sets of hands (stage construction, lighting, sound, caterer and so on) before they are finished. I don't have a CAD program at all, because I can't justify the cost of a commercial one on the of chance that it might generate enough extra work to pay for itself, and there are no open source alternatives that will do what AutoCAD / Vectorworks will do, most importantly in the area of file transfers. I would need to be able to accept files from others, alter them, and pass them back or along knowing that formats, layers and what have you will definitely stay intact. I think there is enough Linux awareness and interest in my branch that there would be other takers if a real alternative were available.

---

### Post by koenn on 2010-01-19
> **audiomick said:**
> .... I think there is enough Linux awareness and interest in my branch that there would be other takers if a real alternative were available.

but what you really need is people like you (need/use CAD, don't have an employer to provide it to them, interested in Linux, ...)  and who, on top of that, can actually write (parts of) CAD software, and have enough free time to do so. 

That, or a CAD software company that decides to go open source or start supporting linux (or both)

Apparently, there are some linux-compatible CAD proghrams (according to Wikipedia)  - the OP was about the fact that they don't really measure up compared to AutoCAD. 

It's a bit like photoshop : there aren't quite enough linux enthousiasts that can both develop  a graphic design program  and be a professional graphics designer at the same time. And the industry has already picked its tool of choice ...

---

### Post by audiomick on 2010-01-19
@ koenn
I know, you are dead right.

---

### Post by touf on 2010-01-19
I also worked several years as freelance engineer and also faced this problem. The workaround I found to replace Autocad was, when getting DWG files, use of everydwg from openDWG with wine (free download from [http://www.opendwg.org/guestfiles](http://www.opendwg.org/guestfiles)) to convert in DXF and then work with QCAD.
for 3D, salome (import/export IGES and STEP). It's not parametric but for "easy" projects it's work fine.

I'm afraid the problem is that Linux is quite a new OS in the conservative industry. Initially CAD were develloped under UNIX and were costly, so I doubt that those will became open-source. Compagnies develloping CAD under windows will come to linux, but it will take some time (if feasible, for example Solidworks make extensive use of microsoft MFC for grafic interface, migrating to linux will need a complete change of their system. Furthermore they use MS office to export data...).

In 3D Salome is still the more advance, but FreeCAD seems promising

Cheers
Touf

---

### Post by audiomick on 2010-01-19
@ touf, that sounds interesting. I might have to look into that.

---

### Post by juancarlospaco on 2010-01-19
> **aquavitae said:**
> 
I've thought about starting a CAD project myself, or attempting to revive and old one, 

Nice..., 
start with [BRL-CAD with its 100% complete and packaged,]("http://www.tecnicoslinux.com.ar/livecd/brlcad_7.10_i386.deb")
and its powerfull like Autodesk product *(but different)*

[IMG]http://sourceforge.net/dbimage.php?id=13032[/IMG]

Build a AutoCAD-Like GUI for these backend, and you are done.

---

### Post by cvmostert on 2010-02-04
I would so like a propper CAD program that works in DWG in Linux! 

I work with Autocad and Caddie every day and would really use CAD on
Linux if it exists.

I hear Bricscad are develping a Linux version of their CAD software.
I would even pay if it is worth it in Linux.

Regards

---

### Post by Kazade on 2010-02-04
> **cvmostert said:**
> I would so like a propper CAD program that works in DWG in Linux! 

The only problem with this is the DWG format is obfuscated (intentionally) and difficult to decrypt and read. I've looked into it, reading or writing a recent DWG file is currently impossible unless you pay a huge amount of money to the OpenDWG project (which isn't open like you might think).

The OpenDWG project has reversed engineered the format, but if you follow their spec ([http://www.opendwg.org/files/guestdownloads/DwgFormatSpec13-2007.rtf](http://www.opendwg.org/files/guestdownloads/DwgFormatSpec13-2007.rtf)) you will find the following gem:

> 
If ComprLen is positive, the ComprLen bytes of data are compressed, and should be decompressed using the OdDwgR21Compressor::decompress() function,


The decompress function is part of the tools that you have access to when you sign up as a member of OpenDWG (which costs money). When I asked about it I was told that the spec will be updated towards the end of the year... it hasn't been.

Of course this whole situation is because AutoDesk intentionally lock people in with their DWG format. It's a real shame.

---

### Post by Chronon on 2010-02-04
> **juancarlospaco said:**
> Nice..., 
start with [BRL-CAD with its 100% complete and packaged,]("http://www.tecnicoslinux.com.ar/livecd/brlcad_7.10_i386.deb")
and its powerfull like Autodesk product *(but different)*

[IMG]http://sourceforge.net/dbimage.php?id=13032[/IMG]

Build a AutoCAD-Like GUI for these backend, and you are done.

It looks like they just published a new release in January.  I'm interested in trying it out.  (Looks like they aren't providing binaries for it, though.)

---

### Post by cvmostert on 2010-02-05
I installed it but dont have a clue how to work it!

---

### Post by Dr Belka on 2010-02-05
I have alot of experience and I get alot of use out of Delcam Powershape and Solidworks.  I really really wish we had something of that scale available for linux.  That and itunes are the only reasons I keep that dang huge windows partition around...

---

### Post by m4tic on 2010-02-05
I use solidworks all the time and its on of the reasons im using windows and also i can't login as root here :(

---

### Post by Gemnoc on 2010-02-28
> **cvmostert said:**
> I hear Bricscad are develping a Linux version of their CAD software.
I would even pay if it is worth it in Linux.

Regards
Bricscad for Linux is at the early alpha stage right now, and Bricsys has released a few builds since Dec. 31st to the general public (provided you register) to prove its resolve. It's nice to be aware of its progress, but the software is in no way reliable or stable at the moment. Bricsys plans an early Q2 final release, but I'm not sure they'll be able to make it that soon.

There's no direct link on Bricsys' website, you have to monitor [their Bricscad for Linux forum]("https://www.bricsys.com/common/support/forumtopics.jsp?forum=20").

Another company, Graebert from Germany, is working on its AutoCAD clone running on Linux. [Their website]("http://graebert.com/") has a form to request an invite to a closed Beta program.

Both products aren't FOSS, unfortunately, but may be strong alternatives to AutoCAD at 10-15% the cost, and with v2009 DWG and ACIS modeling support.

BTW for those hoping for an open source 3d parametric package, there are two interesting projects right now: [FreeCAD]("http://sourceforge.net/projects/free-cad/") and [HeeksCAD]("http://code.google.com/p/heekscad/"), both based on OpenCASCADE. Unfortunately, the development teams are small and are years from having a complete and usable software. A third project, NaroCAD, has unfortunately decided to limit themselves to Windows and use .NET. They're even using the Microsoft ribbon bar (called Fluent interface).

---

### Post by rodrigors on 2010-05-09
> **Kazade said:**
> The only problem with this is the DWG format is obfuscated (intentionally) and difficult to decrypt and read. I've looked into it, reading or writing a recent DWG file is currently impossible unless you pay a huge amount of money to the OpenDWG project (which isn't open like you might think).

Take a look at [LibreDWG]("http://gnu.org/software/libredwg") for a free (as in freedom) implementation of the DWG format. We support R13, R14, R2000 and R2004 reading currently, and writing is on the way. It is just a library but we have implemented a simple dwg2svg converter. We expect other free CADs to adopt it as soon as we have a stable release.

---

### Post by Gemnoc on 2010-05-09
Hey rodrigors,

In light of recent events in cases between Autodesk vs. Solidworks, and Autodesk vs ODA (both have agreed not to use the DWG letters in their projects anymore), aren't you afraid that Autodesk may come after you next? You may be forced to change your project's name...

---

### Post by rodrigors on 2010-05-10
> **Gemnoc said:**
> Hey rodrigors,

In light of recent events in cases between Autodesk vs. Solidworks, and Autodesk vs ODA (both have agreed not to use the DWG letters in their projects anymore), aren't you afraid that Autodesk may come after you next? You may be forced to change your project's name...

We did not try to register any trademark, so I think they have no reason to come after us.

---

### Post by Martiini on 2010-05-11
ONE CAD to RULE THEM ALL !!!!

Humans are a strange species - always end up each pulling their own way.
Linux Torvalds started a revolution ... now we see linux kernel on all CPU-embedded devices, Google Inc. open source solutions .. etc. etc.

[COLOR="DarkRed"]**We need 2 open source solutions for linux workstations:**[/COLOR]

- accounting software that incorporates best of quickoffice, MS accounting, gnucash, turbocash etc.

- CAD modular platform that incorporates best of CAD, CAM, CAE, LiDAR, ArcGIS, CIS,  Autocad, Sketchup, Solidworks, Archicad, Catia, Revit, Solid Edge, qcad, freecad

we need open CAD formats (like odt,pdf) that kill proprietary filetypes like DWG, SKP, 3DS

ONE CAD to RULE THEM ALL !!!!
The TIME IS NOW !!!

[http://en.wikipedia.org/wiki/List_of_CAD_companies](http://en.wikipedia.org/wiki/List_of_CAD_companies)
[http://en.wikipedia.org/wiki/Computer-aided_engineering](http://en.wikipedia.org/wiki/Computer-aided_engineering)
[http://en.wikipedia.org/wiki/Comparison_of_CAD_editors_for_AEC](http://en.wikipedia.org/wiki/Comparison_of_CAD_editors_for_AEC)
[http://en.wikipedia.org/wiki/Comparison_of_3D_computer_graphics_software](http://en.wikipedia.org/wiki/Comparison_of_3D_computer_graphics_software)

---

### Post by benjamimgois on 2010-05-11
There's a great Brazilian free CAD application called MSCAD  and support 2D and 3D projects and filetypes DWG, DXF of AutoCad 2.5 - 2007. WSCAD is a freeware Windows only application, developed by Marcelo S. Carvalho and is written in DELPHI 7 enviroment. Maybe we could contact Marcelo and ask him to opensource MSCAD, maybe port it to LAZARUS might not be a hard task. What do you all think ?


[http://www.mscad.com.br/](http://www.mscad.com.br/)

MSCAD Video: [http://www.mscad.com.br/video.html](http://www.mscad.com.br/video.html)

---

### Post by jetsam on 2010-05-11
I don't know the language, but the site is very impressive looking.  There's a long list of collaborators, so surely he's already thought about the issue before.  It might(??) be best to approach gingerly (as in buy the software and sign up for the mailing list), and hope for good advice more than a huge code donation.

If I were going to start on CAD in earnest, I'd first look at Blender.  How big a project would it be to add the required accuracy and measurement tools to Blender?  It would probably mean a different data structure for coordinates, so that sounds hairy, but I don't know anything about Blender internals and actually barely know Blender at all.

---

### Post by Gemnoc on 2010-05-11
jetsam,

Blender would never do as a real MCAD package. Similarly to 3DS Max, it generates polygon meshes, subdivision surfaces and NURBS surfaces. These are in no way precise enough for MCAD. Plus, everything you work with in Blender is surfaces.

What happens if you create a section view of your model? Your view will show that your object is hollow.

An MCAD package creates [3D solids]("http://en.wikipedia.org/wiki/Solid_modeling"). The most used type is boundary representation.

A 3D CAD package builds upon a geometric modeling kernel. There are a few such kernels in the market:
[LIST]
[*]Parasolid from Siemens PLM is used in NX, Solid Edge, SolidWorks, TopSolid and a bunch of others;
[*]ACIS by Spatial Corp (owned by Dassault Systèmes) is used by Autocad, Inventor, SpaceClaim and a boatload of others too;
[*]Granite is PTC's and to my knowledge used only in Pro|Engineer;
[*]CATIA by Dassault Systèmes uses its own kernel.
[/LIST]

All those are commercial and could not be used by an open source program since they require paying huge licencing fees.

There is only one open source geometric modeling kernel, Open CASCADE. Actually it is a whole software development framework. Any open source MCAD app will inevitably have to be built on it. And right now, there are two projects for Linux that do, FreeCAD and HeeksCAD, as I said in [post #29]("http://ubuntuforums.org/showthread.php?p=8893955#post8893955").

P.S. The open source BRL-CAD is an odd beast, as it works with Constructive Solid Geometry (CSG). To my (limited) knowledge, no commercial package uses that anymore, since boundary representation is more advanced.

---

### Post by mesuhas_sit on 2010-05-11
Hi,

I use Siemens UG/NX day in and day out at work. It is an awesome piece of software.

The thing i like the most is it can be easily learned faster than Catia or any other cad package.

Here is the catch, I use this not as a designer, but as a programmer. I customize UG/NX for our specific tasks and it provides me about 90% of its functionality in the form of easy APIs in C, C++, Java, dotNET.

I will very much love to be part of this effort to make an alternate CAD package.

Let me know your thoughts.

Thanks

---

### Post by johndharvey on 2010-05-11
I've read that some engineering company in South Africa got an older version of AutoCAD working with Wine, but I agree that it would be good to have a FOSS alternative.  I really don't think Blender would be a good starting point, because it really works nothing like AutoCAD (I've got experience with both).  Among other things, AutoCAD works mostly with whole solid shapes, whereas Blender works with individual faces, edges, and vertices.  Maybe you could take some of the basic parts of the engine and retool them into a CAD program, but I don't see a way of turning Blender as it is into a CAD program.

---

### Post by Gemnoc on 2010-05-11
> **mesuhas_sit said:**
> I will very much love to be part of this effort to make an alternate CAD package.
Then head to [my post #29]("http://ubuntuforums.org/showthread.php?p=8893955#post8893955"), use the links to the FreeCAD and HeeksCAD projects. I'm sure they will welcome any help.

BTW UG/NX is available on Linux and OS X up to NX6. I've never seen it running on Linux though, I'd love to see that. NX7 which was released last year is available on Windows only. I don't know if it will be ported.

---

### Post by Martiini on 2010-05-12
so ... in conclusion ... 
is there anyone out there who is able to and has will, motivation, expertise .. 
to take all this CAD thing seriously and start a successful project ??

---

### Post by jetsam on 2010-05-12
I'm sure there's someone out there!

Is it you?  It ain't me!

But, aside from starting a new project, maybe with more support and attention FreeCad or one of the other projects can take off.

I'm too busy right now trying to count to 500 before the mods reset to one, or I'd look more seriously at it.

---

### Post by Gemnoc on 2010-05-12
Martiini, reading your post leaves me with the impression that you haven't payed attention to what I've been posting here **three times already**. #-o

**There are already two very promising projects, FreeCAD and HeeksCAD** (I can't believe I'm writing their names *yet again*) and if the people involved are few, they seem to know what they are doing.

Unless some big software company like Siemens PLM or PTC or whatever announces they open source their big MCAD package (*never* going to happen*), or that an equally big company decides to put its energies into development of an open source MCAD package (also *highly* unlikely), those two small projects I've talked about are our **best bet** for a usable free & open source parametric MCAD package in the foreseeable future.

*Well I suppose it could happen... It kind of *did* happen already. The Open CASCADE framework was originally developed as CASCADE in the early 90s by French company MATRA Datavision; it was open sourced around 2000 after MATRA abandoned software development.

---

### Post by McRat on 2010-05-12
I ran CADKEY v19 yesterday on a 32bit Ubuntu 10.04 under WINE on a 28" monitor.  Spiffy.  It does both solids and surfaces, with two different engines.  One uses NURBS math, and the other uses bi-cubic parametric surfacing.

It has so-so parametric solid modeling features, but does create cross-sections and assemblies.  It has two built in languages to customize it with, the CADKEY SDK and CADL.

It is smoking fast to do 2D mechanical drafting with.  Not that it's 3D features aren't good, it's just a very good paper CAD tool. Nothing else is quicker to learn and use.

As far as a universal format goes, this has been debated for 30 years.  The closest to a universal format is IGES, but STEP is certainly a solid contender.  I said SOLID, yuk, yuk!

It is no longer supported by Kubotek, who is now selling it's newest version KeyCreator.

---

### Post by Gemnoc on 2010-05-12
Interesting. How old is CADKEY V19? (Looks like there's no Wikipedia page on it)

It would be nice if you were to create an entry into the [CAD/CAE section]("http://appdb.winehq.org/objectManager.php?sClass=category&iId=59&sAction=view&sTitle=Browse+Applications") of the AppDB Wine application database to share your experience. And screenshots (posted either there or here) would be nice too, if you have the time! :)

---

### Post by McRat on 2010-05-12
> **Gemnoc said:**
> Interesting. How old is CADKEY V19? (Looks like there's no Wikipedia page on it)

It would be nice if you were to create an entry into the [CAD/CAE section]("http://appdb.winehq.org/objectManager.php?sClass=category&iId=59&sAction=view&sTitle=Browse+Applications") of the AppDB Wine application database to share your experience. And screenshots (posted either there or here) would be nice too, if you have the time! :)

I even got it to print!  :)  

How do I do a screen capture in Ubuntu?

---

### Post by McRat on 2010-05-12
Figured it out.  This is the TRIAL version of the software.  It runs for 30 days then asks for the License file.  It is full functioning.  First is a 3D solid assy from their tutorials, the second is a 2D blueprint I taught a college kid to do in less than 1 week.  I had to redraw 1,300 paper blueprints into CADKEY, so I grabbed 4 students at the local JC, 3 guys and a girl, taught them in a week, and finished the contract in 90 days.  This was back in 2000.  Cadkey is the oldest true 3D software to run on a desktop computer.  When it came out in the 1980's only "big" computers could do true 3D stuff.  It would do Bi-Cubic Parametric Surface Modeling of complex shapes like turbocharger impellers on a ....

80286 DOS machine running PharLap DOS extender and a 80287 math-coprocessor.

Back then, that was a serious CAD cruncher.

I did not try it with their newest product = KeyCreator.  Simply because I don't use KeyCreator.  I bought it, but I still use the old stuff.

EDIT:  Added a 3rd shot.  This is a organic part made of bi-cubic parametric surfaces.  It came in as an IGES file from Unigraphics running on a mainframe, we read it in, and did surface verification of the master tooling.  That was in the late 1990's, it's now flight hardware on many of the Boeing planes.

---

### Post by Gemnoc on 2010-05-12
Awesome! Thanks for sharing! :)

---

### Post by McRat on 2010-05-12
You can see there is a bug in the ScreenShot utility.  The window for the screenshot program is overlaying the screenshot.  

Possible fix?

When user clicks the menu ScreenShot, do not open a new window yet.  First close pulldown.  Allocate memory equal to screen resolution and depth.  Next store  the screen area, NOW create a new window.  Should you need to remove the ScreenShot window, you now have that option.

---

### Post by Gemnoc on 2010-05-12
Uh. Odd. I always use the PrintScreen keyboard button when doing a full-screen capture. Never had this problem.

When doing a capture of the active application window, with Alt+PrintScreen or through the app's option, there is a bug that removes the window title and border. For such captures, I've installed Shutter, which is an nice little app for when you take a lot of screen captures (I started a blog called CAD on Linux, and I need to create screen caps for CAD packages I review). Just set Alt+PrintScreen to Shutter, it will automatically load (takes a few seconds though) and require window selection input before activating.

---

### Post by Martiini on 2010-05-13
Point 1. Any serious software runs in a "cloud" or server+terminal or frontend+backend implementation.

All these linux/unix opensource CAD programs presented here can be called workstation "applications"

FOSS CAD project can be considered successful when leading aerospace, automotive, architectural companies ditch their Autocad, Solidworks, Catia workstations in favour of common FOSS/GPL software.

so ... it is obvious there is no hope for anything similar in our lifetime

---

### Post by jetsam on 2010-05-13
> **Martiini said:**
> Point 1. Any serious software runs in a "cloud" or server+terminal or frontend+backend implementation.

All these linux/unix opensource CAD programs presented here can be called workstation "applications"

FOSS CAD project can be considered successful when leading aerospace, automotive, architectural companies ditch their Autocad, Solidworks, Catia workstations in favour of common FOSS/GPL software.

so ... it is obvious there is no hope for anything similar in our lifetime

Thank goodness it's hopeless!

Seriously, when you set the bar at the stratosphere, of course you'll never leap it in a single bound.  

I'm sure people have used Qcad to draw plans and elevations for their woodsheds, which they then built.  That's a success.  I'm sure people have learned a lot about graphics programming just by downloading and looking over the source code of FreeCAD.  That's a success.  

I'm sure there's a dude(tte) in a suit at AutoDesk headquarters nervously reading this thread.  THAT'S A SUCCESS.  

It makes them do stuff like release Autocad LT at an outrageously high-- but lower than it would have been-- price because nothing makes a monopolist nervous like open source software.  That's success.  

We've won already.  We want to win more.

Less militantly, it would be really nice to have great free CAD software available so that students and amateurs and tinkerers and independents and underfunded start-ups would have a chance to use the same design tools that the big boys do...  And not only that, they would be able to make their own tools better if they wanted to.
That's succes.  We're already there!  

And even though we've already succeeded, We want sucessfuller!  It's hopeless!

---

### Post by Gemnoc on 2010-05-13
> **Martiini said:**
> Point 1. Any serious software runs in a "cloud" or server+terminal or frontend+backend implementation.
*EXCUSE ME?!?*

Where did you get that idea?!? Apart maybe for CATIA V6 (and I'm not sure about that), to my knowledge no other "serious" CAD software runs in a cloud at the moment! So Pro|E, Solidworks, Inventor, Solid Edge and al, they're all crap, is that it?

It looks to me like you bought into the whole "the cloud is our salvation" thing. Come on! Get yourself informed! Cloud computing is not about making your life better. It's not about making you more free! It's not about letting you use the apps YOU want, it's about you using what THEY want you to use and nothing else! It's in big part a scheme by big corporations to lock you in further! :roll:

> FOSS CAD project can be considered successful when leading aerospace, automotive, architectural companies ditch their Autocad, Solidworks, Catia workstations in favour of common FOSS/GPL software.

Again with the arbitrary affirmation. The Linux desktop supposedly has only about 1% of the desktop market. Is it a failure? You use it, I use it, and looking at the number of people who visit the ubuntuforums, a whole lot of other people use it... So, again, is it a failure?

Does a FOSS project needs to be the top dog to be a success? Firefox has 25% of the market, OpenOffice.org hasn't beat the MS Office suite by a long shot, GIMP hasn't replaced Photoshop, neither Blender has 3DS Max... Google Chrome has a few % of market share but has managed to shake everyone into reconsidering what should be a good browser. So they are all failures by your standards??? ](*,)

OK, me stop argue with the guy now. Waste of time. :roll:

@ jetsam: I was so worked up I didn't even notice your response to our friend. Doh! And THANK YOU!!!

---

### Post by McRat on 2010-05-13
> **Martiini said:**
> Point 1. Any serious software runs in a "cloud" or server+terminal or frontend+backend implementation.

All these linux/unix opensource CAD programs presented here can be called workstation "applications"

FOSS CAD project can be considered successful when leading aerospace, automotive, architectural companies ditch their Autocad, Solidworks, Catia workstations in favour of common FOSS/GPL software.

so ... it is obvious there is no hope for anything similar in our lifetime

All CAD is, is published math washed down with a nice GUI.

There is no magic in the box.  You could write a simple CAD program in a week that was usable for making parts.

Now, if you are designing a whole airplane, you aren't going to be running 100% freeware, but I can tell you the roots of the CAD engines were based on open source.  I probably have some ASCII printouts of Fortran code from the 1970's still floating around somewhere.

If your software was written to use IGES or STEP as it's external data format, it's a published data type that is widely used and transportable to ALL current CAD systems.

The reason I use CADKEY is that it is transportable.  My files work on CATIA, UG, NX, ProE, SW, etc.  And I can read customer files in no matter what they are using natively.

Something that might be of minor interest, there were many CAD/CAM companies I had to write native translators for in the late 1980's that are no longer in existence.  It makes you wonder if you could get the source code for a song.

One thing to realize is that the CAD industry is very dynamic, and what is #1 today is unlikely to be #1 tomorrow.  The lead has changed many times.  And the best tool didn't always win.  AutoCAD was not a very technically competitive product in 1990? but it had a HUGE market share.  There were better products that failed or were absorbed.

Sidebar - My first CAD system I did a lot of work on was Generic CADD.  It was very fast on a DOS machine, and had better features than AutoCAD at a fraction of the price.  So AutoDesk bought Generic CADD and shut it down.  Kind of like what MicroSoft did to FoxPro.  You see a better product, you just get rid of it instead of improving what you sell.

---

### Post by Martiini on 2010-05-14
Any of you CAD people know where to find professional DWG files for house building with detailed drawings. 
Please no 3dwarehouse or other kids stuff.

---

### Post by TeoBigusGeekus on 2010-05-14
I'd give my left bollock for a FOS-CAD... 
Read also my signature.

---

### Post by ali_bongos_dad on 2010-05-14
Bricsys have released in the past couple of days a beta version of Bricscad V10 specifically for Linux.
A trial version can be downloaded for free and used for two weeks.
The website is [http://www.bricsys.com]("http://www.bricsys.com")
For those who don't know Bricscad is an Autocad clone and can read/write .dwg files.
Although not free software it is a lot cheaper than Autocad.

---

### Post by gsch on 2010-05-23
dwg files can be found at [http://cben.net](http://cben.net) (answer to a previous question)

I installed a free windows CAD application in WINE (A9CAD, the editor, not the converter), which can open and save dwg and dxf files. So I open a dwg there, save it as a dxf, and open it in QCAD or FreeCAD. You can of course create a dxf in QCAD, open it in A9CAD and save it as a dwg. This gives a solution for those who work for themselves without needing to shelve out $3000.

FreeCAD can of course open and edit STEP and IGES as well. FreeCAD is achingly close to being usable (2D drafting doesn't work for me).

---

### Post by Martiini on 2010-05-25
Russia has joined Europe. Once China and Middle-East join the coalition , USA will be wiped out indefinitely.

---

### Post by jetsam on 2010-05-25
That's not extreme enough.  Suggest Stupeskstansylvania vs. The World instead.  No, actually...  Just hands off Poland, or I'll phone a friend.

---

### Post by Gemnoc on 2010-05-27
@ jetsam

I've discovered a marvelous feature of this forum: the ignore list. Does great for those nonsensical posts made by trolls. Gone, just like that! :)

---

### Post by Kazade on 2010-05-27
> **rodrigors said:**
> Take a look at [LibreDWG]("http://gnu.org/software/libredwg") for a free (as in freedom) implementation of the DWG format. We support R13, R14, R2000 and R2004 reading currently, and writing is on the way. It is just a library but we have implemented a simple dwg2svg converter. We expect other free CADs to adopt it as soon as we have a stable release.

Sorry for the late reply, I missed this post. I'm aware of your project, but as you said you don't yet have support for the latest versions (I've read through the OpenDWG spec and there is a specific part where it refers to a decryption function that is only available to paid members - I assume that's where you are stuck?**)

Also, licensing under the GPLv3 rather than an LGPL license is potentially problematic for many applications (open and closed). For example, I can't remember the details but I know it's impossible for FreeCAD to use LibreDWG due to licensing incompatibility. So although you guys are working towards a solution, and I wish you all the best in that effort, someone else is going to have to reinvent the wheel for projects like FreeCAD. Of course, everyone can benefit from your work to help understand the format, so thanks for your efforts and good luck with it! :D

** I did email OpenDWG a while back asking about that specific part of the spec. They said that they were in the process of updating the spec and it would be ready by the end of 2009, but last time I checked it's still not there :(

---

### Post by jetsam on 2010-05-27
I suppose hiding and or locking layers is kinda usefull.

It takes wizrdry to:
hide a layer.

Hide another layer.

Lock them both wile revealing a different view of the drawing and cobvering the first.

Builkd a staircase out of legos using four points and two to seven letters.

---

### Post by blur xc on 2010-05-27
What I want will most likely never happen - 3d parametric solid modeling.  Autocad is like being in the stone ages...or like using a hatchet while the other guy has one of [these]("http://www.youtube.com/watch?v=FvAI7-Qa2Io&feature=related").

BM

---

### Post by Gemnoc on 2010-05-27
blur xc,

You've probably not followed the whole thread. There are already 2 active projects to bring open source 3D parametric solid modeling on Linux. They are still work-in-progress, but already offer some functionality.

---

### Post by blur xc on 2010-05-27
> **Gemnoc said:**
> blur xc,

You've probably not followed the whole thread. There are already 2 active projects to bring open source 3D parametric solid modeling on Linux. They are still work-in-progress, but already offer some functionality.

I'll re-read the thread- thanks...  Might be worth poking around with...

BM

---

### Post by TeoBigusGeekus on 2010-05-27
See [this]("http://gitorious.org/spadi") and [this.]("http://www.youtube.com/watch?v=i3D7CLdhvuk")

---

### Post by Gemnoc on 2010-05-27
It looks like an interesting project, TeoBigusGeekus, good thing you linked a video though, because the first link doesn't say much for "plain users".

The video implies Spadi aims to be a free ArchiCAD alternative. I'm wondering if it will be solid-based.

---

### Post by Martiini on 2010-05-28
3d architectural timescale simulation would be nice - 
feed archi DWG files, some accounting numbers (labour cost, material cost etc) and it simulates project timeframe and 3d plans

---

### Post by bad_cables on 2010-07-20
would be really nice. i am required to use the same software that the engineers use (by contract). there is nothing preventing me from editing in another application, just as long as i exported it back to the DWG file format. also i think that a linux app might handle corrupted drawings (mainly due to microsoft project turning on 1099 annotation scales and creating many unreconciled layers). i use land desktop 2009 that has features like civil points and point lists, also there is an extensive menu for terrain calculations. i have been looking at brics cad [http://www.bricsys.com/en_INTL/](http://www.bricsys.com/en_INTL/) they have many civil plugins commercially available.

thank you for your concern for this matter

---

