---
title: "Ubuntu Touch computers on motorcycles"
date: 2014-07-17
forum: The Cafe
---

### Post by bcschmerker on 2014-07-17
Several manufacturers and research groups have been experimenting with general-purpose computers with a variety of operating systems, both open- and closed-source, on motorcycles such as the University of New Hampshire Harley-Davidson® FLHP 80 used in Project 54, over the years.  As of 2014, several full-dress touring models from various locations worldwide can use up to a 10" screen, including but not limited to the Kawasaki® ZG14 Concours ABS; Honda® GL1800 Gold Wing®  and SL 1800 Valkyrie™; BMW® R1200RT; Indian® Chieftain™ 105; and Harley-Davidson® FLHT 103.  The last motorcycle potentially able to mount the Panasonic®/Matsushita TOUGHBOOK® was the Harley-Davidson FLTR 88, discontinued 2013 while the manufacturer redesigns the fairing for both producibility and drag reduction as part of Project Rushmore; I am awaiting preliminary specifications on the upcoming FLTR 103, as its fleet-only counterpart the FLTP 103 may be the only motorcycle able to carry the Collins®/Rockwell® iFORCE® police systems-integration package, developed for and adopted fleetwide by the California (USA) Highway Patrol under the Consolidated Patrol Vehicle Environment program and, as of July 2014, installed across the CHP's Ford Crown Victoria P71 sedan, Explorer P71 utility, and F-Series truck platforms, along with other vehicles.

As of July 2014, Ubuntu® Touch™ has been demonstrated across a variety of tablet computers; I suspect it a viable option for the mobile-computer market, which should include motorcycles in addition to cars and trucks.  Has anybody tested Ubuntu® Touch™ on x86 machinery such as the aforementioned TOUGHBOOK®; and, if so, how close to deployment-ready and how many bugs still awaiting fixes?  Links to Threads on applicable tests would be appreciated.

---

### Post by PJs Ronin on 2014-07-18
Touch screen on a motorcycle... interesting concept.   Only to be used whilst stationary I presume.

---

### Post by john_burns2 on 2014-07-19
> **PJs Ronin said:**
> Touch screen on a motorcycle... interesting concept.   Only to be used whilst stationary I presume.

Nah, quite safe to use for about a  few milliseconds when your on the motorway doing 70mph. :D:D:D:D:D

---

### Post by bapoumba on 2014-07-19
> **john_burns2 said:**
> Nah, quite safe to use for about a  few milliseconds when your on the motorway doing 70mph. :D:D:D:D:D

Special gloves ?

---

### Post by grahammechanical on 2014-07-19
The Canonical Ubuntu Touch developers use 3 nexus devices as reference devices. Although Ubuntu Touch is being ported to other devices that work is a community development. Right now the main effort for Canonical developers is to get Ubuntu Touch to a suitable state for it to be released to manufacturers (RTM) to be pre-installed on OEM devices. They have set sometime in Augest as the deadline for that.

Then the effort will switch to converging the phone/tablet code base into the Ubuntu desktop code base. When that is complete then any installation of Ubuntu on any compliant device will have both desktop Ubuntu and phone/tablet Ubuntu capabilities. 

The first release of Ubuntu to have this converged code base will be Ubuntu 16.04. We have an ISO image that is just a few weeks old called ubuntu-Desktop-Next. It is where all this convergence is happening in parallel to the development of the standard Ubuntu desktop releases. This installs on X86 architechure. I have it running on my Intel Core two Duo. But I cannot get beyong the login screen. There is a problem with Nvidia GPUs. Well, my GT220 anyway. It seems to work on Intel graphics.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/20140718/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/20140718/)

Forum discussion thread

[http://ubuntuforums.org/showthread.php?t=2229306](http://ubuntuforums.org/showthread.php?t=2229306)

[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1298914](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1298914)

Regards.

---

### Post by bcschmerker on 2014-07-22
Thanks, grahammechanical, for the advance information on Ubuntu® Touch™ x86/amd64.  I do not yet have sufficient information on the Rockwell Collins® CDU-P7000's internals to assess the complications of adapting Touch thereto, although Rockwell International used LinUX from the outset for iFORCE® to satisfy 24/7/365 reliability requirements.  However, Matsushita-Kotobuki has used Intel® Media Accelerators™, which are known working in the Ubuntu® Desktop Next project as of this post, on the TOUGHBOOK® range.

---

### Post by fkkroundabout on 2014-07-24
oh yeah they put tablets and GPS trackers on bicycles you can rent, in copenhagen
[http://cleantechnica.com/2013/08/19/copenhagen-bike-sharing-program-to-be-most-high-tech-bike-sharing-program-yet/](http://cleantechnica.com/2013/08/19/copenhagen-bike-sharing-program-to-be-most-high-tech-bike-sharing-program-yet/)

but i do think these kinds devices should become unresponsive once the vehicle goes above a certain speed, surely ?

---

### Post by bcschmerker on 2014-07-25
Not as far as I'm aware, [@fkkroundabout](http://ubuntuforums.org/member.php?u=1884253).  Reading the [Article cited](http://cleantechnica.com/2013/08/19/copenhagen-bike-sharing-program-to-be-most-high-tech-bike-sharing-program-yet/), I found the Gobike bicycles to have a screen size on their built-in tablets that is consistent with the Boom! Box™ CDU's on the 2014-up Harley-Davidson® FLHT's and FLHX's; the internal GPS mapping should be good to track groundspeeds up to at least 100km/h (a top speed generally unrealistic on pedal power).  (The aforementioned Boom! Box™ includes four additional buttons on the display flanks, plus tie-ins to dedicated switches on the handlebar; don't know about the FLHT/FLHX internal GPS capabilities, however.)

---

### Post by bcschmerker on 2014-08-24
A scenario that I see for an Ubuntu® Touch&#8482; motorcycle installation for the unnamed (as of August 2014) 15.12a1 involves a contingency tourer project based on a Harley-Davidson® FLTR 88 or 96:  The CDU would mount on the fairing on a bracket running through the factory stereo provision (about where I picture the Rockwell Collins® iFORCE® CDU on the proposal for a Harley-Davidson® Custom Vehicle Operations&#8482; FLTPSE-CHP 110 for the State of California), the Mini-ITX system unit in a radio box consistent with the H-D® P/N 53637-04.  Similar installations can potentially be done on numerous other make and model full-dress tourers on account of the modest required volume and weight.

---

### Post by bcschmerker on 2014-10-19
**Complication:**  From new and/or updated data (as of September 2014) from both Harley-Davidson Motor Company and Rockwell International, I found that the available area on the Rushmore FLTR fairing is less than optimum, potentially less than required, for the iForce® CDU; the installation would definitely obstruct the fairing gauges, and potentially the fork-mounted speedometer and tachometer, on the 2014 FLTR.  Should the size problem be proved, development of the proposed FLTPSE-CHP will have to start with an FLTX*n* Road Glide® Project Special, using an FLHP with tank console-mounted speedo/tach, and the Rushmore sharknose fairing with a new inner section to house the iForce® CDU, for the baseline.  In any case, the iForce® Integrated Management Unit will force the use of a modified HD King Tour-Pak®, potentially enlarged with a new and taller lid to a new California King Tour-Pak standard, to house both the IMU and the radio transceivers that CPVE will require.

This complication should not affect civilian users, as most Mini-ITX system units from Dell, Acer, Hewlett-Packard, &c., will fit the available space of Harley-Davidson® P/N 53637-04.

---

