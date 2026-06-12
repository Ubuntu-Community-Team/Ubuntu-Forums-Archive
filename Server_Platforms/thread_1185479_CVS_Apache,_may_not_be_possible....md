---
title: "CVS Apache, may not be possible..."
date: 2009-06-12
forum: Server Platforms
---

### Post by nitecon on 2009-06-12
Okay I'm trying to do something that I'm not sure will actually work so I need some input!

Here is the scenario.  We have several virtual servers available for use all running ubuntu server!  The way it traditionally worked was each developer would have 1 server to do his project.  The dev would edit files directly on the server and apache would point to the developer files that way anyone can pull up a web browser and look at the code to see progress / test the application.  All of this is absolutely great and all the devs love to do it this way.  However...

I am now at the turning point where there will be more than one dev per project and they still want to be able to use the web browser to view the project *live*.

CVS is introduced for version control and team collaboration.  However a checkout needs to be done on the server for it to display the project etc.  This creates a huge bottle neck.

Basically what I'm trying to have is a checkout system for the code and still have apache pointing to the code being worked on for testing.

Any ideas on how I can have it checkout/update dynamically for the devs, or does anyone have any other ideas on how to accomplish this?

A little more explanation:
Dev scenario :

CVSRoot/the_project (CVS Repository for devs to work on)
/var/www (Apache web server root)
Dynamic / Continuous sync (CVSROOT <--> Apache Root)

---

