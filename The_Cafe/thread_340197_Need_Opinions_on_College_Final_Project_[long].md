---
title: "Need Opinions on College Final Project [long]"
date: 2007-01-16
forum: The Cafe
---

### Post by Phatfiddler on 2007-01-16
Well its that time of the year.  I have to do a final project in order to receive my degree.  It has to be associated with electronics and optics/photonics, and I have to design and build the product within 14 weeks.

Here is what I have so far:

I plan on building a "weather updater" that will go on the roof of the building.  It will be the size of a full-size computer tower laying on it's side.  It will detect sunlight intensity, haziness, temperature, and wind speed.  It will update it's results to a web-server every 30 minutes so that students/employees may visit the site to see what the weather is like ON CAMPUS, and not 45 miles away in a major city.

The site will be PHP based so it will be able to update continuously.  The uploaded data from the weather station will be a module for the site, so that it may be accessed via a simple link.

**The Hardware**

The entire system will be built on top of Debian server, and the upload/ftp scripts will be written in python.  The actual sensors i.e. photometer, thermistor will be accessed using a 8000 series microprocessor, and the collected data will be sent to the pc via the serial port twice every hour.  Using python scripts, the data will be formed into a simple PHP module that will then be uploaded to the website for viewing.

The outside enclosure is a water-tight, EMI shielded aluminum case.  The collected data will be sent to the pc which will be inside one of the laboratories, and the data then sent via Ethernet to te web server


All of the C, Python, and schematics will be open-source so that future students can improve upon the system, or build and add new modules like atmospheric pressure etc.  This will also provide a chance for my classmates to have hands-on experience with a Linux Server, the Python Language, and what open-source is all about.

[B]
Any opinions?[/B]

---

### Post by meng on 2007-01-16
I like it! Make sure when you write the report you use "its" not "it's"

---

### Post by steven8 on 2007-01-16
> **meng said:**
> I like it! Make sure when you write the report you use "its" not "it's"

No grammar for you! - The grammar Nazi strikes again.

I think the project sounds fantastic!  It is an excellent idea and the application will earn you high marks!!

Good luck!

---

### Post by meng on 2007-01-16
> **steven8 said:**
> No grammar for you! - The grammar Nazi strikes again.
I do look like Al Pacino ... hoo-AHHHH!

---

### Post by FuturePilot on 2007-01-16
Yes! Based on Debian. I like it. Sounds like a great project and a lot of fun. Go for it and good luck!:D

---

### Post by steven8 on 2007-01-16
> **meng said:**
> I do look like Al Pacino ... hoo-AHHHH!

I love that bit. :-)

---

### Post by saulgoode on 2007-01-16
Have you considered cutting out the middleman and having your weather station serve up the webpage itself? I would think that even a low-powered pentium would have little problem handling several hundred simultaneous connections while still monitoring the instruments.

Also, if you are going to place the unit in a sealed box, don't forget to take into account thermal considerations. :)

---

### Post by irish_flu on 2007-01-16
I think that sounds awesome, fun, and actually useful.

---

### Post by Phatfiddler on 2007-01-16
Thanks for the feedback!

The server is not a problem, since I own <see sig>.  The pc that will be on the campus will do nothing more than upload a text document to a server twice an hour.  The microcontroller will handle all of the required calculations and will end up doing most of the work.  The aluminum box that will hold all of the equipment has baffles on one side that allow for ventilation, but won't let water in - unless it's raining upwards at about 20 mph:) 

Overall, it's gonna be similar to :
Sensors -> Microprocessor -> PC -> Web Server

---

### Post by irish_flu on 2007-01-16
> **Phatfiddler said:**
> unless it's raining upwards at about 20 mph 

In that case, you should write a script so that if the sensor box floods and breaks the webserver just reports "OMG Crappy".  :-D

---

### Post by Phatfiddler on 2007-01-19
Well I've finished the user interface for the PC.  I made a custom desktop interface for future users that may need to do maintenance on the machine.  I made it as idiot-proof as possible, since I know of few students in my school that use or understand Linux.  It is basically a core system with only the needed libraries for the server to operate.

The user "student" is the default and is automatically logged in when the computer is started so that the server and cron jobs start right away.  Icons are locked in place, and the desktop is owned by root so that it may not be modified.  The terminal button opens root-terminal, but the password is required.  The user may only start the server, run diagnostics, read source codes and help documents explaining the system, and turn the computer off.

Depending on how everything goes, and the popularity of it, I may release full documentation so that others may reproduce the system, including schematics and equipment.

[IMG]http://cutlersoftware.com/images/Screenshot2.png[/IMG]

---

### Post by kogber on 2007-01-19
> I made it as idiot-proof as possible


LOL at the screenshot! indeed you did!  Nice work, I think a cat could be trained to use this interface.

---

### Post by FuturePilot on 2007-01-19
Hey, it looks like it's coming along very well. That's a nice simple UI you have there:D

---

