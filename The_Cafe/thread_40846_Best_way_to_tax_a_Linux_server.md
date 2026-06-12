---
title: "Best way to tax a Linux server?"
date: 2005-06-10
forum: The Cafe
---

### Post by poofyhairguy on 2005-06-10
Does anyone know a good program in synaptic (or in the base Ubuntu install) that will allow me to max out a media server I'm building? I want this thing to be a mythtv box one day and so I want to make sure that I can get it running at tip top shape. The best would be something I can measure with hard data and not subjective "it runs a little faster." I need a good benchmark.

So....how would you push a server to the limit in the comfort of your own home?

---

### Post by ubuntu_demon on 2005-06-10
I don't know but on a related matter you should try isag for monitoring performance during general usage.

$sudo apt-get install isag

isag uses sysstat. This will configure the sysstat cronjob for you :

$sudo dpkg-reconfigure sysstat

---

### Post by gil-galad on 2005-06-10
Well looking around at the packages I found cpuburn

cpuburn     - a collection of programs to put heavy load on CPU

---

### Post by GrumpySimon on 2005-06-10
How are you serving the files? If it's via web-interface, you can test that part of it with 'ab', apache-benchmark. Should come installed with apache. 

It allows you to hammer the server with x request per timeperiod, with n concurrancies. You can specify post payloads etc. Very useful tool, and tests the whole system at once (database -> scripting lang. -> webserver), in a way that's relevant for the end users.

It should be in the apache*-utils package. 

There's also 'siege', which is similar, but I haven't used this much.

--Simon

---

