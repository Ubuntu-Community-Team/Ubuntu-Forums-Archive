---
title: "Dell PowerEdge 2850 graphics problem"
date: 2010-01-08
forum: Server Platforms
---

### Post by illjutsu on 2010-01-08
I work for a city government.  I have been trying to convert our backup web server, Dell PowerEdge 2850, from Windows 2003 to Ubuntu.  The box had been hosting a couple of web sites for the past 4 years.  It was light stuff, PHP/Joomla on Apache 2 and DotNetNuke on IIS.  There was also Apache Tomcat on there.  Recently, we also added Subversion and TeamCity for version control plus continuous integration.  All of the .NET stuff has been moved over to another server that we acquired.  Right now I am trying to get Sun Glassfish 3 and Alfresco WCM to run on Windows on the old server, but it is a major pain in the butt.  I could use OpenSolaris, except there are a couple things that are easier in Ubuntu.  The box must also be able to run FreeNX properly so that my boss, who is a GUI guy, will be able to log in to a desktop.  That leaves Ubuntu, since I am somewhat familiar with it.
  
I was able to get FreeNX, Glassfish and Alfresco (up to a point) to run using a Turnkey Linux image.  The problem is the server is proving to be difficult.  I tried starting with the desktop 9.1 CD that I downloaded; however, there is massive graphics corruption on the desktop.  It'll boot fine to the Gnome desktop, but the system will become really slow and the windows disappear, leaving just a border.  Switching to another VT shows blurry, shaky text.  I suspect there is an issue with the graphics driver, but I can't even type in any commands to find out what is going on.

Btw, I also downloaded 9.04 Server edition and it installed fine with no shaky text.  How hard would it be to build on top of that for XWindows and FreeNX to work?  Why is the text shaking in the first place?  Thanks.

---

### Post by cjking on 2010-01-15
Had the same problem with a couple of 24OOs a few years ago.  The problem with them was the built in graphics adaptor.  Could not get any drive from many distributions to work with them.  Finally gave up, disabled the on board adaptor and put in an nVidia card.  Problem was solved.

You could install X11 through apt-get on the server edition you installed, but would most like get the same results.  If you want to try let me know and I send you a How to.

cjking

---

### Post by Vegan on 2010-01-16
I am lucky, my server's built-in graphics work fine. 

As for graphics I am surprised that built-in adapters are not well supported.

---

