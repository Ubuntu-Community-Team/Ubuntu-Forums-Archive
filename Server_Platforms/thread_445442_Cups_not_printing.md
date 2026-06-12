---
title: "Cups not printing"
date: 2007-05-15
forum: Server Platforms
---

### Post by Yumi on 2007-05-15
I set up ubuntu feisty server and installed/configured cupssys. 

I can access the server via [http://192.168.1.2:631](http://192.168.1.2:631) . 
Connected (USB) the printer and installed it on the server.
Installed the network printer on two windowsXP machines and printed from there.
I can see the documents from both machines in the print-cue

Problem: The documents do not print, printer is paused.

I noted the following:
 from the windows machine in firefox accessing cups on http:/192.168.1.2:631 brings up the cups administration page. In "printers" I choose "print test page". It sends the test page but then says "Network host '192.168.1.2' is busy; will retry in 25 seconds..."!

and

when I select "Purge alle jobs" it delets all jobs but then returns an error "Server nor found". In the address the 192.168.1.2 changes to "raceserver1.domain" which is the correct hostname of the ubuntu server

What could be the problem. Wire ok, Printer is switched on, Power indicator lit up

Michael

---

