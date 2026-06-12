---
title: "GNU/Linux and HDCP enabled hardware... ?!?"
date: 2007-03-31
forum: The Cafe
---

### Post by mac.ryan on 2007-03-31
I recently took time to read the well-known and celebrated [Peter Gutmann's study]("http://www.cs.auckland.ac.nz/%7Epgut001/pubs/vista_cost.html") on Vista & DRM.

Amongst the many shocking information in the report, there is one who affects GNU/Linux users very closely. Verbatim from the section "Elimination of Open Source hardware support":

> In order to prevent the creation of hardware emulators of protected output devices, Vista requires a Hardware Functionality Scan (HFS) that can be used to uniquely fingerprint a hardware device to ensure that it's (probably) genuine.  In order to do this, the driver on the host PC performs an operation in the hardware (for example rendering 3D content in a graphics card) that produces a result that's unique to that device type.


  In order for this to work, the spec requires that the operational details of the device be kept confidential.  Obviously anyone who knows enough about the workings of a device to operate it and to write a third-party driver for it (for example one for an open-source OS, or in general just any non-Windows OS) will also know enough to fake the HFS process.  The only way to protect the HFS process therefore is to not release any technical details on the device beyond a minimum required for web site reviews and comparison with other products.


Is there anyone who can articulate this further? In particular:
[LIST=1]
[*]**To which extent new hardware will be unreferenced?** Will this concern only those features about HDCP (already bad), the HD features as a whole (worse), or the entire piece of hardware (orwell scenario)?
[*]**Is there any measure taken to counteract this scenario?** (I know of the "[Bad Vista]("http://badvista.fsf.org/")" or the "[Defective by design]("http://defectivebydesign.org/")" FSF's excellent campaigns already, but I am thinking more about "technological solutions" to be implemented in the short run...)[/LIST]I am looking forward for info, ideas, suggestions, impressions, etc...

Many thanks in advance! :)

---

### Post by xzero1 on 2007-05-22
Whew, I'm sure glad Microsoft isn't a monopoly! I think the article mentions that ms doesn't want to completely specify any of this, but it will use its monopoly power to ensure compliance as it sees fit. By using the 'excuse' of DRM enforcement, it can play both sides of the game. Publicly, ms can claim they did not force hardware manufacturers not to publish their specs. Privately, they have complete control. We all know what they think about open source. 
     The question is how will this play out? Does one buy a computer to play protected content? How long would Nvidia and Ati be able to compete with their extra DRM burden for the best gaming card?
      If DRM fails and its content becomes universally available, perhaps manufacturers will eventually break these constraints. This could be the longest suicide note in history as the author suggests.

---

