---
title: "Use AMD apl"
date: 2008-01-05
forum: Ubuntu Brainstorm
---

### Post by banaantje12 on 2008-01-05
[http://developer.amd.com/articles.jsp?id=180&num=1](http://developer.amd.com/articles.jsp?id=180&num=1)

Alot of people here have AMD processors. So why not use this to add alot more performance?

>  Features

The AMD Performance Library (APL) is a collection of popular low-level software routines beginning with simple arithmetic and extending into rich domains, such as image and signal processing.

    * New! Video Decoding (H.264) support
    * New! JPEG support
    * New! AMD &#8220;Barcelona&#8221; Processor Optimizations
    * New! Sun Studio for Solaris support
    * Leverages multi-core processors
    * Accelerates application development
    * Available both as static and dynamic libraries
    * Future-proof interfaces to the processor
    * Future-proof upgrade path to new processor technologies
    * Multiple OS and platform support
    * Multiple code paths based upon various processor features
    * Highly scalable and configurable thread management

AMD Performance Library version 1.1 is here!
[IMG]http://developer.amd.com/content/images/misc/apl1_1.jpg[/IMG]
AMD Performance Library version 1.1

Benefits
Simple interface to take advantage of latest hardware innovations
APL tunes for the latest hardware so you can easily tap into new processor features, including:

    * MMX
    * SSE, SSE2
    * Multi-cores

Faster development of multimedia projects
With thousands of routines dedicated to image and signal processing, APL enables you to accelerate projects such as:

    * Media players
    * Codecs
    * Image editors
    * Audio applications
    * and many more...

Easy path to multi-threading
APL's aggressive internal threading features mean that you don't have to worry about managing sophisticated threading models or complex debugging. Whether you are using dynamic or static linking, Windows, Linux or Solaris 32- or 64-bit, threading just works.

Configuration
APL is available in the following configurations:
  	
Windows®
32 & 64
	
Linux®
32 & 64
	
Solaris
32 & 64
Static Library (.lib/ .a) 	
	
	
Dynamic Library (.dll / .so) 	
	
	

The static library (.lib/ .a) version is currently available for the Microsoft Visual Studio 2005, GCC version 4.1 and Sun Studio version 12.

New! Please visit the APL forum for FAQs, tips and tricks and peer support.
New! Please visit the AMD Libraries blog for the latest information and updates on the AMD Performance Library.

Send all feedback to [email]tech.support@amd.com[/email] with the subject line "APL-Support."

Support for Third-Generation AMD Opteron&#8482; Processors
APL version 1.1 provides optimized routines to speed codec performance on AMD &#8220;Barcelona&#8221;-based processor platforms. This new and improved library infrastructure includes:

    * A new threading method that allows for both internal and external threading
    * A new pixel engine architecture enabling multiple code paths (e.g. &#8220;Greyhound&#8221; and &#8220;Barcelona&#8221; support)
    * Platform Support for the Sun Solaris 10 operating system

---

### Post by smartboyathome on 2008-01-05
I don't have an AMD processor. Maybe add this to the AMD version of Ubuntu (or is it already included)?

---

### Post by Game_boy on 2008-01-05
> **smartboyathome said:**
> I don't have an AMD processor. Maybe add this to the AMD version of Ubuntu (or is it already included)?

There is no AMD version of Ubuntu.

x86 means Intel or AMD 32-bit processors
amd64 means Intel or AMD 64-bit processors

--
That appears to be a compile-time library, not a kernel modification. Every program compiled for Ubuntu would have to have it included. I don't think it's feasible especially as it could degrade performance on Intel processors.

---

### Post by banaantje12 on 2008-01-06
But that doesn't mean we can't include it, and work with it ;)

---

### Post by Game_boy on 2008-01-06
When I said "could degrade performance on Intel processors", I meant "*will *degrade performance on Intel processors"

Ubuntu cannot favour one manufacturer at the expense of another. If you want to recompile every program to optimise it for your system in particular, get a distribution that specialises in that like Gentoo.

---

### Post by red4ub on 2008-08-12
APL be Framewave Project now, an open-source APL derivative, is a collection of popular low-level software routines beginning with simple arithmetic and extending into rich domains, such as image and signal processing.

---

