---
title: "Simpit hardware, interfaces and drivers for LinUX"
date: 2012-06-15
forum: The Cafe
---

### Post by bcschmerker on 2012-06-15
As part of my interest in aviation, I have a preliminary concept for developing a complete baseline set of hardware for training in many common cockpit and flight deck tasks in pilot education.  Many aircraft systems are designed for 24-30 volts DC, and some for 26 volts RMS 400 Hz AC; interface hardware is available for the programmer serious enough to learn the commonly used data formats published for the aerospace industry by [ARINC®/Carlyle®]("http://www.arinc.com/").  Although both gamers and general aviators have a lot of applications available for the PC under Microsoft® Windows® 6-up, not much in the way of serious aviation hardware has support in the OS cited.

The preliminary simulated cockpit (simpit) design I am currently refining, as of 14 June 2012, involves elements of the glass cockpit, major switchgear support integrated into the stick(s) and engine controls (HOTAS/HOCAS), appropriate mechanical gauges and controls for visual flight, &c.  Among involved instrumentation for computer control are a pitot-static system with temperature scaling (3 ATI IAS/Machmeter, 3 ATI three-pointer altimeter, 3 ATI vertical speed/TCAS display); 26 VAC flight gauges (3 ATI 360/360 attitude director-indicator display for remote vertical and yaw gyroscopes or inertial reference system with inclinometer, ILS deviation/elevation crosshair and yaw-rate needle and scale; 3 ATI radio magnetic indicator for remote directional gyroscope or inertial reference system); and 28 VDC flight gauges (3 ATI radio altimeter CDU; engine and fuel display/selectors of undetermined size formats; 2 ATI clock).  In order to allow for a reasonably wide range of control formats across several makes and models of aircraft, both fixed- and rotary-wing, the HOTAS/HOCAS installation will use a centerline control grip based on the Mason®/Esterline® 732 (stick/cyclic); a four-control throttle quadrant with throttle grips based on Essex® grips intended for the stillborn McDonnellDouglas XA-12 carrier attack aircraft; and a switch pod of yet-to-be-determined design for a twist-grip-equipped Johnson bar (collective).  I already anticipate a need for dual side consoles for 5.5" racks of control/display units for engine and electrical-system control, radiocommunications and -navigation, environmental controls, autopilot/inertial-navigation, &c.; dual corner panels for hydraulics, landing gear, arresting hook, caution/advisory telltales, and related switchgear; and dual LED danger panels integrated into the instrument-panel glareshield along with an option for a head-up display.

What interface electronics are available to drive the involved busses for the above simpit?  With manufacturer and part-number data, one should be able to locate copies of necessary datasheets, which are necessary for programming drivers in C++.  And does our Ubuntu® Community have any suggestions for prioritizing the HOTAS/HOCAS switchgear?  Any suggestions are welcome.

---

### Post by bcschmerker on 2012-07-10
Bump!  Be advised that the U. S. Air Force AVU-8/A airspeed/Machmeter gauge, which is marked for 80 - 850 knots (fixed outer scale) and 0.1-2.8 Mach (moving inner scale), is a stylistic match for three-pointer pressure altimeters (e.g., the United Instruments 5934PA3L) rather than the counter-drum pointer altimeters (e.g., the U. S. Air Force AAU-34/A) standard on recent high-altitude aircraft.  Also, L3 Avionics has a suitable standby attitude director indicator for reference in their 360/360-capable Model ADI-350AT (Jet Electronics & Technology Division), which packs a deviation/elevation cross-pointer and integrated turn-and-slip display for a remote yaw-rate gyroscope sender.

---

### Post by mips on 2012-07-10
I have zero knowledge about what you are talking about but maybe go have a look over at the X-Plane resources [http://www.x-plane.com/x-world/landing/](http://www.x-plane.com/x-world/landing/)

They have some serious aeronautical nuts over there with people building emulator cockpits from scrapped planes and I know x-plane also has FAA certification for flight training in simulators.

There might just be some knowledgeable folk over there that could point you in the right direction ;)

Sorry I could not be of more assistance but if I did you would probably crash & burn :biggrin:

---

