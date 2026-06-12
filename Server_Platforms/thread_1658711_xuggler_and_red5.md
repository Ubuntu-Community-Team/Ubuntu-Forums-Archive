---
title: "xuggler and red5"
date: 2011-01-03
forum: Server Platforms
---

### Post by n.brenner on 2011-01-03
If anybody knows or has a working tutorial on xuggler, ill trade my

"it works" tutorial about installing red5


took me 7 tries but I got red5 working and learned  some of the things

u cant find

How about xuggler....anybody


Install red5

1.	clean harddrive(no os ...nothing)
2.	Install clean os....(I used linux mint 10. You only have to remove 5 programs to clean it)
3.	Reset screen saver and power options...can be changed later
4	Reset IP..(My system uses static)
5	Reset software sources..(use all except games)
6	Install printer...(you will use it to troubleshoot)
7	DO NOT UPDATE YET AND DO NOT INSTALL ANYTHING ELSE AT THIS TIME

	NOW WE ARE GOING TO INSTALL RED5
8	Online find the details of package libred5-java(0.9.1-4)
9	use this list to install all of its dependencies..they are all in synaptic
10	INSTALL ant, perl, gcc, g++, subversion, sun-java6-jre and jdk, ivy, yasm....they are in synaptic
11	Download and install gmake

12	CHECK /usr/lib/jvm/java-6-openjdk/lib/tools.jar...if it is not there, copy it from Java-6-sun-1.6.0.22/lib/
13	Download and install libred5-java_0.9.1-4_all.deb
14	mkdir /usr/local/red5-server
15	Download red5-server_0.9.1-4_all.deb to /usr/local/red5-server....dpkg from there

16	restart computer and update/upgrade
17	open web browser, in address bar---http://local host:5080
18	you should see the red5 front page....scroll down and follow directions
	.flv files go into /var/lib/red5/webapps/oflaDemo/streams
	also--service red5-server start, restart, stop

19	OK, THIS IS THE AHA MOMENT
20	in another computer, open webbrowser and in address bar put in [http://(the](http://(the) server ip):5080
21	scroll to "launch a demo"..select ofla Demo and view demo
22	In the view box, change the address to rtmp://(the server IP)/oflaDemo
23	Connect
24	In "library" select movie and watch
25	this is as far as I have gotten ...my server controls the internet input as well as the localnet..so it works both localnet
	as well as internet..try it crosscountry, it works....if you are behind a router then look into port forwarding on the router
	Port 1935 is input to red5 and port 5080 is output from red5

26	ADD APACHE2 OR CHEROKEE OR ANY OTHER SERVER YOU WANT

IT WORKS.....from there you are on your own

XUGGLER is the interconnect from streaming-whatever to red5-stream.flv

---

