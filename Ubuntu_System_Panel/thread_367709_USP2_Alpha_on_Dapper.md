---
title: "USP2 Alpha on Dapper"
date: 2007-02-22
forum: Ubuntu System Panel
---

### Post by Malac on 2007-02-22
Thought I'd try USP2 from the SVN on Dapper (as it's supposed to be LTS) and it all seems to work well.
Apart from the recent plugin which due to recent manager differences won't run on Dapper.
However the USPrecent_D plugin does, so recent documents is available.
The only thing I had to do before getting it to run was to open gconf-editor and replace the recent with USPrecent_D in the plugin_list and copy that into .usp/plugins
Anyway here are some screenshots. (Please ignore the ugly theme effect. :) )
[ATTACH]25901[/ATTACH][ATTACH]25902[/ATTACH][ATTACH]25903[/ATTACH]

---

### Post by jhorner on 2007-02-22
I am curious, what amount of resources is USP using when you have that many plugins?

---

### Post by Malac on 2007-02-22
I haven't actually profiled it properly but these are from System Monitor.
They are from Edgy which has a couple of extra plugins running as well.
First is Closed, Second is Open.
[ATTACH]25907[/ATTACH][ATTACH]25908[/ATTACH]
The only real CPU hog on the Dapper version is the USPrecent_D plugin because it has to poll the recently-used file to get it's info as there is no "hook" into the Recent-Manager in Dapper.(Not a problem on Edgy.)
This raises the CPU usage to about 9% everytime it reads the file but this can be set to check every 1 second, 10 seconds, 1 minute, 5 minutes or whatever so is the best compromise I could come up with.

---

