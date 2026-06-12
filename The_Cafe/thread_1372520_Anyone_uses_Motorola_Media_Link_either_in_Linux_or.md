---
title: "Anyone uses Motorola Media Link either in Linux or Windows?"
date: 2010-01-04
forum: The Cafe
---

### Post by legolas_w on 2010-01-04
Hi
I saw that Motorola has something like Itune to control the Android based phones. I am wondering whether anyone is using it in Linux based on Wine or not? 

[http://www.motorola.com/Consumers/US-EN/Consumer-Product-and-Services/Software/Motorola-Media-Link-US-EN](http://www.motorola.com/Consumers/US-EN/Consumer-Product-and-Services/Software/Motorola-Media-Link-US-EN)


Thanks.

---

### Post by vgrisham on 2010-03-13
Isn't it ironic that Moto Media Link isn't Linux compatible when their phone is Linux based?

---

### Post by i531qooq on 2010-05-23
Incredibly ironic and equally annoying.  Just got the motorola milestone, going to try to run it under wine tonight, keep you posted

Installed cleanly, but fails to start application. Still working on it...

Update:

Motorola media link uses the .NET framework, and so I tried to run it using Mono, and this is the error i get:

[EMAIL="screaminsemen@Ubuntu-laptop:%7E/.wine"]screaminsemen@Ubuntu-laptop:~/.wine[/EMAIL]/drive_c/Program Files/Motorola Media Link$ mono MML.exe

** (MML.exe:13735): WARNING **: The following assembly referenced from /home/screaminsemen/.wine/drive_c/Program Files/Motorola Media Link/MML.exe could not be loaded:
     Assembly:   PresentationFramework    (assemblyref_index=0)
     Version:    3.0.0.0
     Public Key: 31bf3856ad364e35
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/screaminsemen/.wine/drive_c/Program Files/Motorola Media Link/).

Update:

I installed the windows version of mono using wine, and attempted to run the program through wine but got the same error.
open for ideas, please help!

---

