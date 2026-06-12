---
title: "Car Performance Simulator for Linux"
date: 2011-07-10
forum: The Cafe
---

### Post by nxgtrsim on 2011-07-10
Hello Linux users!,
My name is Carlos, and I have been a Linux user since Kubuntu 7.04, I started working on a Car Performance Simulator (not like TORCS, more like CarTest for DOS) for a PhD several years ago.

This simulator can give you very close to reality performance figures for your car, for any car in the world, that exist or will exist in near future, since you give all needed car specifications as parameters to the sim.

This simulator was written by me with GCC under my linux machine, and recently a Silverlight application port (NxGTR Sim) has been done, but as a Linux user I notice two things:

1) Moonlight is not ready for Silverlight 4, so, web application does not work under Linux, at least not with my linux environment
2) There is no a tool like this for Linux (as far as I know)

I could update that GCC code, fix some bugs and release it for Free at my webpage for all Linux users that cant use the Silverlight app, however, I dont even know if there is people interested in a comand line tool like that.

Here is a pic of Silverlight version working:
[IMG]http://www.nxgtrsim.com/imagebrowser/ib_p004_0_16.jpg[/IMG]

If you like cars and are a bit interested please reply, and I will look for a way to bring this to Linux.

---

### Post by handy on 2011-07-10
What are the vehicle specifications that your good looking program requires to do its job?

More than just engine power & torque?

Do you need the gear ratios, final drive ratio?

---

### Post by nxgtrsim on 2011-07-10
> **handy said:**
> What are the vehicle specifications that your good looking program requires to do its job?

More than just engine power & torque?

Do you need the gear ratios, final drive ratio?
Well, a lot of more, than just power and torque, just to name a few here they are:

engine readline 
power at crank or at wheels?
hp @ rpm
torque @ rpm
gear ratios up tu 8 (for GCC version, up tu 14 for SL version)
Final Drive Ratio #1 
Final Drive Ratio #2 (for supercars that switch for Super high top speed)
torqueloss % for drivetrain
clutch slip factor
weight overall
weight distribution 
gravity center
wheelbase 
drag Coff 
frontal area 
traction tire Diameter 
non traction tire diameter
intertia for tire traction
intertia for non traction tire
rolling factor 
static factor 
environment temperature 
Barometric Pressure environment
car Roll Out 
Launch at what RPM?
Manually shift points or computer calculated for efficiency
time to engage new gear?
FWD? RWD? or AWD?
car height 
car width 
tire width 
tire profile 
rim size 
engine type (NA?, Forced?)
boost starts at? (for Forced)
and lots more are computer calculated, because are so hard to setup even for some advanced users)
and more to keep posting here.

For Linux, I am working only at command line, I run it like this: (of course it needs some usability upgrades before release, if Linux people need it)

./nxgtrsim 7500 0 140 6400 3.33 1.83 1.29 0.98 0.76 0.0 0.0 0.0 4.18 0.0 15 1.0 2461 40 25.9 95.7 0.29 18.18 18.52 18.52 0.33 0.33 0.00 0.013 1.0 65 29.38 0.0 3600 7470 7160 6930 6810 0 0 0 250 250 250 250 0 0 0 130 4800 0 1 51.8 66.1 195 55 14 0 0

---

### Post by wafflesausage on 2011-07-10
I'm certainly interested. Work on the usability a little more and put your finished product on Sourceforge; I'm sure you'll find that many people will make good use of it :)

---

