---
title: "Server advice"
date: 2015-11-02
forum: Server Platforms
---

### Post by chrisdudeperson on 2015-11-02
Hi all,

I need a bit of advice as to what type of server I need for a project I'm doing. Please excuse my lack of knowledge in this area, I've used linux for a couple of years but have had little to no experience with servers.

My project involves the monitoring of a temperature sensor (arduino and ESP8266 wifi chip) via an app on an Android device. The temperature sensor and Android need to communicate via WiFi on a with a server to send and receive information about the temperature readings which should be stored in a database on the server. For now the temperature sensor, Android device and server will all be on the same local network. This project doesn't require a web browser, just communication between a temperature sensor and an Android device via a server.

Do you guys have any advice as to what type of server I should be using (Web sever, application server...), what protocol is best to use for this (HTTP, Websockets...) and if possible what packages are best to use for this (LAMP...)?

Apologies if this information is a little vague, please ask questions if you need me to elaborate!

Many thanks,
Chris

---

### Post by Bucky Ball on 2015-11-02
What is the project for?

---

### Post by sandyd on 2015-11-02
Using POST requests would probably be the simplest way.

You can probably adapt the script at [http://www.instructables.com/id/PART-1-Send-Arduino-data-to-the-Web-PHP-MySQL-D3js/](http://www.instructables.com/id/PART-1-Send-Arduino-data-to-the-Web-PHP-MySQL-D3js/) to work with your arduino.

---

### Post by 1clue on 2015-11-02
You could do a pure sockets app easily enough on a project this simple, or you could use any of hundreds of languages that fit into a web container like apache2 or similar. In the former case you learn socket programming and get an extremely lightweight app. In the latter case you can ignore the sockets part and conveniently pull values from a web form and sent back a string.

You could also do something like cron with ssh and bash scripts, but while that's kinda fun and educational it's not very practical or maintainable.

---

### Post by tgalati4 on 2015-11-03
Perhaps describe the "Use Case".  How are you going to use this monitoring system?  Do you only need current temperature?  Do you need to scroll back to see past temperatures?  Do you need a graph over 8 hours?  Multiple phones will be accessing this data?

---

### Post by chrisdudeperson on 2015-11-03
My apologies for not giving enough detail

The app will need access to past temperatures hence the need for a database of some description and will use this past data to create a graph.

I've looked into HTTP POST and Websockets, both look like the kind of thing I need for this project. Would you recommend using Apache2 for this?

---

### Post by 1clue on 2015-11-03
What you want to do is well within the minimum functionality of a web server. So you could pick pretty much any web server software and make it work.

---

### Post by tgalati4 on 2015-11-03
You can use apache with HTML5 to draw the graphs.  

You can use the Processing language to draw the graphs:  [http://arduining.com/2013/08/05/arduino-and-processing-graph-example/](http://arduining.com/2013/08/05/arduino-and-processing-graph-example/)

And:  [http://forum.arduino.cc/index.php?topic=335018.0](http://forum.arduino.cc/index.php?topic=335018.0)

And:  [http://www.instructables.com/id/Drive-a-webpage-in-real-time-using-Arduino-Sensor/](http://www.instructables.com/id/Drive-a-webpage-in-real-time-using-Arduino-Sensor/)

---

### Post by chrisdudeperson on 2015-11-03
Ok brilliant. So just to confirm it's a web server not an application server that I'm after?

---

### Post by SeijiSensei on 2015-11-03
I don't see much difference to be honest, since many applications are written that use HTTP as the communication protocol.

So can you tell us what a likely request from the client would look like?  It might be just as easy to use an HTTP GET request like this:
```
http://server_name/?device=myandroid&temp=43
```
Are you writing the client side as well, or using an existing package?  

Parsing requests like that and writing the data to a database like PostgreSQL or MySQL is pretty easy if you know basic programming.  Something like this using PHP:
```

<?php
$devicename=$_GET['device'];
$devicetemp=$_GET['temp'];

$db=pg_connect("user=tempmonitor dbname=tempmonitor");
$timestamp=time();
$insert_data=pg_exec($db,"insert into temps values($timestamp,'$devicename',$devicetemp);");
?>

```
where there is a table called "temps" in a PostgreSQL database "tempmonitor" owned by a Postgres user called "tempmonitor."  The table would have at least three fields, an integer timestamp, a "varchar" field to hold the name of the reporting device, and a floating-point field to store the temperature it reports.

You might want to have the client-side application generate the timestamp to ensure each record has a unique identifier.  I often use Unix timestamps for record IDs unless it's possible that more than one record will be generated within a one-second interval. Using timestamps as IDs lets you easily include the times in any reports with a simple function like PHP's [date()]("http://php.net/manual/en/function.date.php").

---

